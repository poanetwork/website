# Nethermind Upgrade

Sokol and POA are gradually migrating to Nethermind support.

Instructions for validators on upgrading from Open Ethereum to Nethermind: [https://forum.poa.network/t/switch-from-openethereum-to-nethermind-on-sokol/6528](https://forum.poa.network/t/switch-from-openethereum-to-nethermind-on-sokol/6528)

Once you are running Nethermind, here are the commands to bump to the latest Nethermind version:

```text
docker pull nethermind/nethermind:latest
docker-compose down
docker-compose up -d
```

