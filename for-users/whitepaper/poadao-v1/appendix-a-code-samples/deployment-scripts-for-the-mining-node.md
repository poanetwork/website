# 为挖矿节点的部署脚本

```bash
#!/bin/bash
set -e
set -u
set -x

EXT_IP="$(curl ifconfig.co)"

# Install logentries daemon /*
start_logentries() {
    echo "=====> start_logentries"
    sudo bash -c "echo 'deb http://rep.logentries.com/ trusty main' > /etc/apt/sources.list.d/logentries.list"
    sudo bash -c "gpg --keyserver pgp.mit.edu --recv-keys C43C79AD && gpg -a --export C43C79AD | apt-key add -"
    sudo apt-get update
    sudo apt-get install -y logentries
    sudo le reinit --user-key=0665901a-e843-41c5-82c1-2cc4b39f0b21 --pull-server-side-config=False

    mkdir -p /home/${ADMIN_USERNAME}/logs
    touch /home/${ADMIN_USERNAME}/logs/netstats_daemon.err
    touch /home/${ADMIN_USERNAME}/logs/netstats_daemon.out
    touch /home/${ADMIN_USERNAME}/logs/parity.err
    touch /home/${ADMIN_USERNAME}/logs/parity.out
    touch /home/${ADMIN_USERNAME}/logs/parity.log
    touch /home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.out
    touch /home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.err

    sudo bash -c "cat >> /etc/le/config << EOF
[install_err]
path = /var/lib/waagent/custom-script/download/0/stderr
destination = AlphaTestTestNet/${EXT_IP}
[install_out]
path = /var/lib/waagent/custom-script/download/0/stdout
destination = AlphaTestTestNet/${EXT_IP}
[netstats_daemon_err]
path = /home/${ADMIN_USERNAME}/logs/netstats_daemon.err
destination = AlphaTestTestNet/${EXT_IP}
[netstats_daemon_out]
path = /home/${ADMIN_USERNAME}/logs/netstats_daemon.out
destination = AlphaTestTestNet/${EXT_IP}
[parity_err]
path = /home/${ADMIN_USERNAME}/logs/parity.err
destination = AlphaTestTestNet/${EXT_IP}
[parity_out]
path = /home/${ADMIN_USERNAME}/logs/parity.out
destination = AlphaTestTestNet/${EXT_IP}
[parity_log]
path = /home/${ADMIN_USERNAME}/logs/parity.log
destination = AlphaTestTestNet/${EXT_IP}
[transferReward_out]
path = /home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.out
destination = AlphaTestTestNet/${EXT_IP}
[transferReward_err]
path = /home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.err
destination = AlphaTestTestNet/${EXT_IP}
EOF"
    sudo apt-get install -y logentries-daemon
    sudo service logentries start
    echo "<===== start_logentries"
}

start_logentries

# */

echo "========== AlphaTestTestNet/mining-node/install.sh starting =========="
echo "===== current time: $(date)"
echo "===== username: $(whoami)"
echo "===== working directory: $(pwd)"
echo "===== operating system info:"
lsb_release -a
echo "===== memory usage info:"
free -m
echo "===== external ip: ${EXT_IP}"
echo "===== environmental variables:"
printenv

# script parameters
#INSTALL_DOCKER_VERSION="17.03.1~ce-0~ubuntu-xenial"
#INSTALL_DOCKER_IMAGE="parity/parity:v1.6.8"
INSTALL_CONFIG_REPO="https://raw.githubusercontent.com/poanetwork/test-templates/AlphaTestTestNet/TestTestNet/mining-node"
GENESIS_REPO_LOC="https://raw.githubusercontent.com/poanetwork/oracles-scripts/alphadevtestnet/spec.json"
GENESIS_JSON="spec.json"
NODE_TOML="node.toml"
NODE_PWD="node.pwd"

export HOME="${HOME:-/home/${ADMIN_USERNAME}}"

#echo "===== will use docker version: ${INSTALL_DOCKER_VERSION}"
#echo "===== will use parity docker image: ${INSTALL_DOCKER_IMAGE}"
echo "===== repo base path: ${INSTALL_CONFIG_REPO}"

# this should be provided through env by azure template
NETSTATS_SERVER="${NETSTATS_SERVER}"
NETSTATS_SECRET="${NETSTATS_SECRET}"
MINING_KEYFILE="${MINING_KEYFILE}"
MINING_ADDRESS="${MINING_ADDRESS}"
MINING_KEYPASS="${MINING_KEYPASS}"
NODE_FULLNAME="${NODE_FULLNAME:-Anonymous}"
NODE_ADMIN_EMAIL="${NODE_ADMIN_EMAIL:-somebody@somehere}"
ADMIN_USERNAME="${ADMIN_USERNAME}"

prepare_homedir() {
    echo "=====> prepare_homedir"
    #ln -s "$(pwd)" "/home/${ADMIN_USERNAME}/script-dir"
    cd "/home/${ADMIN_USERNAME}"
    mkdir -p logs
    mkdir -p logs/old
    echo "<===== prepare_homedir"
}

add_user_to_docker_group() {
    # based on https://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo
    echo "=====> add_user_to_docker_group"
    sudo groupadd docker
    sudo gpasswd -a "${ADMIN_USERNAME}" docker
    newgrp docker
    echo "===== Groups: "
    groups
    echo "<===== add_user_to_docker_group"
}

install_ntpd() {
    echo "=====> install_ntpd"
    sudo timedatectl set-ntp no
    sudo apt-get -y install ntp

    sudo bash -c "cat > /etc/cron.hourly/ntpdate << EOF
#!/bin/sh
sudo service ntp stop
sudo ntpdate -s ntp.ubuntu.com
sudo service ntp start
EOF"
    sudo chmod 755 /etc/cron.hourly/ntpdate
    echo "<===== install_ntpd"
}

install_haveged() {
    echo "=====> install_haveged"
    sudo apt-get -y install haveged
    sudo update-rc.d haveged defaults
    echo "<===== install_haveged"
}

allocate_swap() {
    echo "=====> allocate_swap"
    sudo apt-get -y install bc
    #sudo fallocate -l $(echo "$(free -b | awk '/Mem/{ print $2 }')*2"  | bc -l) /swapfile
    sudo fallocate -l 1G /swapfile
    sudo chmod 600 /swapfile
    sudo mkswap /swapfile
    sudo swapon /swapfile
    sudo sh -c "printf '/swapfile   none    swap    sw    0   0\n' >> /etc/fstab"
    sudo sh -c "printf 'vm.swappiness=10\n' >> /etc/sysctl.conf"
    sudo sysctl vm.vfs_cache_pressure=50
    sudo sh -c "printf 'vm.vfs_cache_pressure = 50\n' >> /etc/sysctl.conf"
    echo "<===== allocate_swap"
}

install_nodejs() {
    echo "=====> install_nodejs"
    # curl -sL https://deb.nodesource.com/setup_0.12 | bash -
    curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
    sudo apt-get update
    sudo apt-get install -y build-essential git unzip wget nodejs ntp cloud-utils

    # add symlink if it doesn't exist
    [[ ! -f /usr/bin/node ]] && sudo ln -s /usr/bin/nodejs /usr/bin/node
    echo "<===== install_nodejs"
}

install_docker_ce() {
    echo "=====> install_docker_ce"
    sudo apt-get -y install apt-transport-https ca-certificates curl software-properties-common
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
    sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
    sudo apt-get update
    sudo apt-get -y install docker-ce=${INSTALL_DOCKER_VERSION}
    sudo docker pull ${INSTALL_DOCKER_IMAGE}
    echo "<===== install_docker_ce"
}

pull_image_and_configs() {
    echo "=====> pull_image_and_configs"

    # curl -s -O "${INSTALL_CONFIG_REPO}/../${GENESIS_JSON}"
    curl -s -o "${GENESIS_JSON}" "${GENESIS_REPO_LOC}"
    curl -s -O "${INSTALL_CONFIG_REPO}/${NODE_TOML}"
    sed -i "/\[network\]/a nat=\"extip:${EXT_IP}\"" ${NODE_TOML}
    cat >> ${NODE_TOML} <<EOF
[misc]
logging="engine=trace,network=trace,discovery=trace"
log_file = "/home/${ADMIN_USERNAME}/logs/parity.log"
[account]
password = ["${NODE_PWD}"]
unlock = ["${MINING_ADDRESS}"]
[mining]
force_sealing = true
engine_signer = "${MINING_ADDRESS}"
reseal_on_txs = "none"
EOF
    echo "${MINING_KEYPASS}" > "${NODE_PWD}"
    mkdir -p parity/keys/OraclesPoA
    echo ${MINING_KEYFILE} | base64 -d > parity/keys/OraclesPoA/mining.key.${MINING_ADDRESS}
    echo "<===== pull_image_and_configs"
}

# based on https://get.parity.io
install_netstats() {
    echo "=====> install_netstats"
    git clone https://github.com/poanetwork/eth-net-intelligence-api
    cd eth-net-intelligence-api
    #sed -i '/"web3"/c "web3": "0.19.x",' package.json
    npm install
    sudo npm install pm2 -g

    cat > app.json << EOL
[
    {
        "name"                 : "netstats_daemon",
        "script"               : "app.js",
        "log_date_format"      : "YYYY-MM-DD HH:mm:SS Z",
        "error_file"           : "/home/${ADMIN_USERNAME}/logs/netstats_daemon.err",
        "out_file"             : "/home/${ADMIN_USERNAME}/logs/netstats_daemon.out",
        "merge_logs"           : false,
        "watch"                : false,
        "max_restarts"         : 100,
        "exec_interpreter"     : "node",
        "exec_mode"            : "fork_mode",
        "env":
        {
            "NODE_ENV"         : "production",
            "RPC_HOST"         : "localhost",
            "RPC_PORT"         : "8545",
            "LISTENING_PORT"   : "30300",
            "INSTANCE_NAME"    : "${NODE_FULLNAME}",
            "CONTACT_DETAILS"  : "${NODE_ADMIN_EMAIL}",
            "WS_SERVER"        : "http://${NETSTATS_SERVER}:3000",
            "WS_SECRET"        : "${NETSTATS_SECRET}",
            "VERBOSITY"        : 2
        }
    }
]
EOL
    cd ..
    cat > netstats.start <<EOF
cd eth-net-intelligence-api
pm2 startOrRestart app.json
cd ..
EOF
    chmod +x netstats.start
    sudo -u root -E -H ./netstats.start
    echo "<===== install_netstats"
}

install_netstats_via_systemd() {
    echo "=====> install_netstats_via_systemd"
    git clone https://github.com/poanetwork/eth-net-intelligence-api
    cd eth-net-intelligence-api
    #sed -i '/"web3"/c "web3": "0.19.x",' package.json
    npm install
    sudo npm install pm2 -g

    cat > app.json << EOL
[
    {
        "name"                 : "netstats_daemon",
        "script"               : "app.js",
        "log_date_format"      : "YYYY-MM-DD HH:mm:SS Z",
        "error_file"           : "/home/${ADMIN_USERNAME}/logs/netstats_daemon.err",
        "out_file"             : "/home/${ADMIN_USERNAME}/logs/netstats_daemon.out",
        "merge_logs"           : false,
        "watch"                : false,
        "max_restarts"         : 100,
        "exec_interpreter"     : "node",
        "exec_mode"            : "fork_mode",
        "env":
        {
            "NODE_ENV"         : "production",
            "RPC_HOST"         : "localhost",
            "RPC_PORT"         : "8545",
            "LISTENING_PORT"   : "30300",
            "INSTANCE_NAME"    : "${NODE_FULLNAME}",
            "CONTACT_DETAILS"  : "${NODE_ADMIN_EMAIL}",
            "WS_SERVER"        : "http://${NETSTATS_SERVER}:3000",
            "WS_SECRET"        : "${NETSTATS_SECRET}",
            "VERBOSITY"        : 2
        }
    }
]
EOL
    cd ..
    sudo bash -c "cat > /etc/systemd/system/oracles-netstats.service <<EOF
[Unit]
Description=oracles netstats service
After=network.target
[Service]
Type=oneshot
RemainAfterExit=true
User=${ADMIN_USERNAME}
Group=${ADMIN_USERNAME}
Environment=MYVAR=myval
WorkingDirectory=/home/${ADMIN_USERNAME}/eth-net-intelligence-api
ExecStart=/usr/bin/pm2 startOrRestart app.json
[Install]
WantedBy=multi-user.target
EOF"
    sudo systemctl enable oracles-netstats
    sudo systemctl start oracles-netstats
    echo "<===== install_netstats_via_systemd"
}

start_docker() {
    echo "=====> start_docker"
    cat > docker.start <<EOF
sudo docker run -d \\
    --name oracles-poa \\
    -p 30300:30300 \\
    -p 30300:30300/udp \\
    -p 8080:8080 \\
    -p 8180:8180 \\
    -p 8545:8545 \\
    -v "$(pwd)/${NODE_PWD}:/build/${NODE_PWD}" \\
    -v "$(pwd)/parity:/build/parity" \\
    -v "$(pwd)/${GENESIS_JSON}:/build/${GENESIS_JSON}" \\
    -v "$(pwd)/${NODE_TOML}:/build/${NODE_TOML}" \\
    ${INSTALL_DOCKER_IMAGE} --config "${NODE_TOML}" > logs/docker.out 2> logs/docker.err
container_id="\$(cat logs/docker.out)"
sudo ln -sf "/var/lib/docker/containers/\${container_id}/\${container_id}-json.log" logs/parity.log
EOF
    chmod +x docker.start
    ./docker.start
    echo "<===== start_docker"
}

use_deb() {
    echo "=====> use_deb"
    curl -LO 'http://parity-downloads-mirror.parity.io/v1.7.0/x86_64-unknown-linux-gnu/parity_1.7.0_amd64.deb'
    sudo dpkg -i parity_1.7.0_amd64.deb
    sudo apt-get install dtach

    cat > parity.start << EOF
dtach -n parity.dtach bash -c "parity -l engine=trace,discovery=trace,network=trace --config ${NODE_TOML} >> logs/parity.out 2>> logs/parity.err"
EOF
    chmod +x parity.start
    ./parity.start
    echo "<===== use_deb"
}

use_deb_via_systemd() {
    echo "=====> use_deb_via_systemd"
    curl -LO 'http://parity-downloads-mirror.parity.io/v1.7.0/x86_64-unknown-linux-gnu/parity_1.7.0_amd64.deb'
    sudo dpkg -i parity_1.7.0_amd64.deb

    sudo bash -c "cat > /etc/systemd/system/oracles-parity.service <<EOF
[Unit]
Description=oracles parity service
After=network.target
[Service]
User=${ADMIN_USERNAME}
Group=${ADMIN_USERNAME}
WorkingDirectory=/home/${ADMIN_USERNAME}
ExecStart=/usr/bin/parity --config=node.toml
Restart=always
[Install]
WantedBy=multi-user.target
EOF"
    sudo systemctl enable oracles-parity
    sudo systemctl start oracles-parity
    echo "<===== use_deb_via_systemd"
}

use_bin() {
    echo "=====> use_bin"
    sudo apt-get install -y dtach unzip
    curl -L -o parity-bin-v1.7.0.zip 'https://gitlab.parity.io/parity/parity/-/jobs/61863/artifacts/download'
    unzip parity-bin-v1.7.0.zip -d parity-bin-v1.7.0
    ln -s parity-bin-v1.7.0/target/release/parity parity-v1.7.0

    cat > parity.start << EOF
dtach -n parity.dtach bash -c "./parity-v1.7.0 -l discovery=trace,network=trace --config ${NODE_TOML} >> logs/parity.out 2>> logs/parity.err"
EOF
    chmod +x parity.start
    ./parity.start 
    echo "<===== use_bin"
}

compile_source() {
    echo "=====> compile_source"
    sudo apt-get -y install gcc g++ libssl-dev libudev-dev pkg-config
    curl https://sh.rustup.rs -sSf | sh -s -- -y
    source "/home/${ADMIN_USERNAME}/.cargo/env"
    rustc --version
    cargo --version

    git clone -b "v1.7.0" https://github.com/paritytech/parity parity-src-v1.7.0
    cd parity-src-v1.7.0
    cargo build --release
    cd ..
    ln -s parity-src-v1.7.0/target/release/parity parity-v1.7.0

    cat > parity.start << EOF
./parity-v1.7.0 -l discovery=trace,network=trace --config "${NODE_TOML}" >> logs/parity.out 2>> logs/parity.err
EOF
    chmod +x parity.start
    dtach -n parity.dtach "./parity.start"
    echo "<===== compile_source"
}

install_scripts() {
    echo "=====> install_scripts"
    git clone -b alphadevtestnet --single-branch https://github.com/poanetwork/oracles-scripts
    ln -s ../node.toml oracles-scripts/node.toml
    cd oracles-scripts/scripts
    npm install
    sudo bash -c "cat > /etc/cron.daily/transferRewardToPayoutKey <<EOF

#!/bin/bash
cd "$(pwd)"
echo \"Starting at \\\$(date)\" >> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.out\"
echo \"Starting at \\\$(date)\" >> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.err\"
node transferRewardToPayoutKey.js >> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.out\" 2>> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.err\"
echo \"\" >> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.out\"
echo \"\" >> \"/home/${ADMIN_USERNAME}/logs/transferRewardToPayoutKey.err\"
EOF"
    sudo chmod 755 /etc/cron.daily/transferRewardToPayoutKey
    cd ../..
    echo "<===== install_scripts"
}

setup_autoupdate() {
    echo "=====> setup_autoupdate"
    sudo docker pull poanetwork/docker-run
    sudo bash -c "cat > /etc/cron.daily/docker-autoupdate << EOF
#!/bin/sh
outlog='/home/${ADMIN_USERNAME}/logs/docker-autoupdate.out'
errlog='/home/${ADMIN_USERNAME}/logs/docker-autoupdate.err'
echo \"Starting: \\\$(date)\" >> \"\\\${outlog}\"
echo \"Starting: \\\$(date)\" >> \"\\\${errlog}\"
sudo docker run --rm -v /var/run/docker.sock:/tmp/docker.sock poanetwork/docker-run update >> \"\\\${outlog}\" 2>> \"\\\${errlog}\"
echo \"\" >> \"\\\${outlog}\"
echo \"\" >> \"\\\${errlog}\"
EOF"
    sudo chmod 755 /etc/cron.daily/docker-autoupdate
    echo "<===== setup_autoupdate"
}

configure_logrotate() {
    echo "=====> configure_logrotate"

    sudo bash -c "cat > /etc/logrotate.d/oracles.conf << EOF
/home/${ADMIN_USERNAME}/logs/*.log {
    rotate 10
    size 200M
    missingok
    compress
    copytruncate
    dateext
    dateformat %Y-%m-%d-%s
    olddir old
}
/home/${ADMIN_USERNAME}/.pm2/pm2.log {
    su ${ADMIN_USERNAME} ${ADMIN_USERNAME}
    rotate 10
    size 200M
    missingok
    compress
    copytruncate
    dateext
    dateformat %Y-%m-%d-%s
}"
    echo "<===== configure_logrotate"
}

# MAIN
main () {
    sudo apt-get update

    prepare_homedir
    #add_user_to_docker_group

    install_ntpd
    install_haveged
    allocate_swap

    install_nodejs
    #install_docker_ce
    pull_image_and_configs

    #start_docker
    #use_deb
    use_deb_via_systemd
    #use_bin

    #setup_autoupdate

    #install_netstats
    install_netstats_via_systemd
    install_scripts
    configure_logrotate
}

main
echo "========== AlphaTestTestNet/mining-node/install.sh finished =========="
```

