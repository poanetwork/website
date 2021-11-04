---
description: Instructions for validators to reset the Netstats client
---

# NetStats Dashboard

The Netstats Dashboard monitors validator nodes, uptime and basic chain statistics. It is available at [https://core-netstat.poa.network/](https://core-netstat.poa.network).

If the dashboard goes down or has issues it may need to be restarted.  In the case where the dashboard has been restarted, the following steps can be followed to restart the Docker Netstats client on your node WITHOUT restarting the blockchain client.&#x20;

{% hint style="warning" %}
Please check in the validators telegram channel to be sure this is the case before proceeding.
{% endhint %}

### Open Ethereum

1. Log in to your POA Core Validator Node
2. Switch to your local OpenEthereum directory, for example:`  cd /home/openethereum/openethereum  `or wherever you installed
3. see which local Docker Containers are running:\
   `docker-compose ps` \
   you should see the following:`ethstats       docker-entrypoint.sh npm start   Up                                                                                                   openethereum   /home/openethereum/openeth ...   Up (healthy)   0.0.0.0:30303->30303/tcp,:::30303->30303/tcp,                                                                                                0.0.0.0:30303->30303/udp,:::30303->30303/udp `
4. restart JUST the ethstats container\
   `docker container restart ethstats`
5. Refresh the Netstats page to see your Validator node. &#x20;

### Nethermind

_Instructions in process_
