# Visualize Vault HA

## Postgres Backend

![Image of dashboard](./dashboard.png)

This demonstrates Vault HA backed by a Postgres backend and with automatic auto unseal using Vault Transit.
It requires Vault 1.2.0
To visualize this, ensure you have docker-compose in your path then:

1. ```git clone https://github.com/stoakes/visualize-vault-ha```
2. ```cd visualize-vault-ha/postgres```
3. ```docker-compose up```
4. go to http://admin:admin@localhost:3000

docker-compose will run:
- postgres for storage
- consul for service discovery
- prometheus, consul-exporter for metrics
- grafana for visualization
- vault with file backend and transit engine enabled for auto-unsealing other vaults
- vault1, vault2: vaults using postgres as an HA backend
- a client

vault1 and vault2 are run in such a way that they get killed and restarted regularly.

client constantly asks Consul for a healthy vault to talk to, then sends that vault a KV PUT.

When done, use `docker-compose down` to stop the containers.

**Note:** If you want to restart the demo again (after a `docker-compose stop` for instance), you will have to unseal the transit vault.
Keys are in the logs.