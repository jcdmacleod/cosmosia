# Service Placement

To optimize resource usage including network/bandwidth, disk space and disk io; need to control service placements.


## Snapshot Service Placement

Snapshot for each chain is configured in the [chain-registry](../data/chain_registry.ini)

See more on [snapshot doc](snapshot.md).

---
## RPC Service Placement

https://github.com/notional-labs/cosmosia/issues/195

| No | Chain                 | Node1       | Node 2      | Node3       | Node 4      | Node 5      |
|---:|:----------------------|:-----------:|:-----------:|:-----------:|:-----------:|:-----------:|
| 1  | osmosis               | cosmosia1   | cosmosia2   | cosmosia3   | cosmosia4   | cosmosia5   |
| 2  | starname              | cosmosia2   | cosmosia3   |             |             |             |
| 3  | regen                 | cosmosia3   | cosmosia4   |             |             |             |
| 4  | akash                 | cosmosia4   | cosmosia5   |             |             |             |
| 5  | cosmoshub             | cosmosia5   | cosmosia6   | cosmosia7   | cosmosia8   | cosmosia9   |
| 6  | sentinel              | cosmosia6   | cosmosia7   |             |             |             |
| 7  | emoney                | cosmosia7   | cosmosia8   |             |             |             |
| 8  | ixo                   | cosmosia8   | cosmosia9   |             |             |             |
| 9  | juno                  | cosmosia9   | cosmosia10  | cosmosia11  | cosmosia12  | cosmosia13  |
| 10 | sifchain              | cosmosia10  | cosmosia11  | cosmosia12  | cosmosia13  | cosmosia14  |
| 11 | likecoin              | cosmosia11  | cosmosia12  |             |             |             |
| 12 | kichain               | cosmosia12  | cosmosia13  |             |             |             |
| 13 | cyber                 | cosmosia13  | cosmosia14  |             |             |             |
| 14 | cheqd                 | cosmosia14  | cosmosia15  |             |             |             |
| 15 | stargaze              | cosmosia15  | cosmosia16  |             |             |             |
| 16 | bandchain             | cosmosia16  | cosmosia17  |             |             |             |
| 17 | chihuahua             | cosmosia17  | cosmosia18  |             |             |             |
| 18 | kava                  | cosmosia18  | cosmosia1   |             |             |             |
| 19 | bitcanna              | cosmosia1   | cosmosia2   |             |             |             |
| 20 | konstellation         | cosmosia2   | cosmosia3   |             |             |             |
| 21 | omniflixhub           | cosmosia3   | cosmosia4   |             |             |             |
| 22 | terra                 | cosmosia4   | cosmosia5   |             |             |             |
| 23 | vidulum               | cosmosia5   | cosmosia6   |             |             |             |
| 24 | provenance            | cosmosia6   | cosmosia7   |             |             |             |
| 25 | dig                   | cosmosia7   | cosmosia8   |             |             |             |
| 26 | gravitybridge         | cosmosia8   | cosmosia9   |             |             |             |
| 27 | comdex                | cosmosia9   | cosmosia10  |             |             |             |
| 28 | cerberus              | cosmosia10  | cosmosia11  |             |             |             |
| 29 | bitsong               | cosmosia11  | cosmosia12  |             |             |             |
| 30 | assetmantle           | cosmosia12  | cosmosia13  |             |             |             |
| 31 | fetchhub              | cosmosia13  | cosmosia14  |             |             |             |
| 32 | evmos                 | cosmosia14  | cosmosia15  | cosmosia16  | cosmosia17  | cosmosia18  |
| 33 | persistent            | cosmosia15  | cosmosia16  |             |             |             |
| 34 | cryptoorgchain        | cosmosia16  | cosmosia17  |             |             |             |
| 35 | irisnet               | cosmosia17  | cosmosia18  |             |             |             |
| 36 | axelar                | cosmosia18  | cosmosia1   |             |             |             |
| 37 | pylons                | cosmosia1   | cosmosia2   |             |             |             |
| 38 | umee                  | cosmosia2   | cosmosia3   |             |             |             |
| 39 | sei                   | cosmosia3   | cosmosia4   |             |             |             |
| 40 | evmos-testnet-archive | cosmosia4   | cosmosia5   |             |             |             |
| 41 | injective             | cosmosia5   | cosmosia6   |             |             |             |
| 42 | kujira                | cosmosia6   | cosmosia7   |             |             |             |
| 43 | passage               | cosmosia7   | cosmosia8   |             |             |             |
| 44 | osmosis-testnet       | cosmosia8   | cosmosia9   |             |             |             |
| 45 | evmos-archive         | cosmosia9   | cosmosia10  | cosmosia16  | cosmosia17  | cosmosia18  |
| 46 | stride                | cosmosia10  | cosmosia11  |             |             |             |
| 47 | dig-archive           | cosmosia11  | cosmosia12  |             |             |             |
| 48 | osmosis-archive       | cosmosia4   | cosmosia10  |             |             |             |


#### Docker commands

To add label to a node:
```console
docker node update --label-add cosmosia.rpc.osmosis=true cosmosia1
```

To remove label to a node:
```console
docker node update --label-rm cosmosia.rpc.osmosis cosmosia1
```

To list node with label:
```console
docker node ls -f node.label=cosmosia.rpc.osmosis=true
```

---
## Load-Balancer Service Placement

https://github.com/notional-labs/cosmosia/issues/197

Need at least 2 nodes in case one node down.

| No | Chain                 | Node1       | Node 2      |
|---:|:----------------------|:-----------:|:-----------:|
| 1  | osmosis               | cosmosia1   | cosmosia2   | 
| 2  | starname              | cosmosia2   | cosmosia3   |
| 3  | regen                 | cosmosia3   | cosmosia4   |
| 4  | akash                 | cosmosia4   | cosmosia5   |
| 5  | cosmoshub             | cosmosia5   | cosmosia6   |
| 6  | sentinel              | cosmosia6   | cosmosia7   |
| 7  | emoney                | cosmosia7   | cosmosia8   |
| 8  | ixo                   | cosmosia8   | cosmosia9   |
| 9  | juno                  | cosmosia9   | cosmosia10  |
| 10 | sifchain              | cosmosia10  | cosmosia11  |
| 11 | likecoin              | cosmosia11  | cosmosia12  |
| 12 | kichain               | cosmosia12  | cosmosia13  |
| 13 | cyber                 | cosmosia13  | cosmosia14  |
| 14 | cheqd                 | cosmosia14  | cosmosia15  |
| 15 | stargaze              | cosmosia15  | cosmosia16  |
| 16 | bandchain             | cosmosia16  | cosmosia17  |
| 17 | chihuahua             | cosmosia17  | cosmosia18  |
| 18 | kava                  | cosmosia18  | cosmosia1   |
| 19 | bitcanna              | cosmosia1   | cosmosia2   |
| 20 | konstellation         | cosmosia2   | cosmosia3   |
| 21 | omniflixhub           | cosmosia3   | cosmosia4   |
| 22 | terra                 | cosmosia4   | cosmosia5   |
| 23 | vidulum               | cosmosia5   | cosmosia6   |
| 24 | provenance            | cosmosia6   | cosmosia7   |
| 25 | dig                   | cosmosia7   | cosmosia8   |
| 26 | gravitybridge         | cosmosia8   | cosmosia9   |  
| 27 | comdex                | cosmosia9   | cosmosia10  |
| 28 | cerberus              | cosmosia10  | cosmosia11  |
| 29 | bitsong               | cosmosia11  | cosmosia12  |
| 30 | assetmantle           | cosmosia12  | cosmosia13  | 
| 31 | fetchhub              | cosmosia13  | cosmosia14  |
| 32 | evmos                 | cosmosia14  | cosmosia15  | 
| 33 | persistent            | cosmosia15  | cosmosia16  |
| 34 | cryptoorgchain        | cosmosia16  | cosmosia17  |
| 35 | irisnet               | cosmosia17  | cosmosia18  |
| 36 | axelar                | cosmosia18  | cosmosia1   |
| 37 | pylons                | cosmosia1   | cosmosia2   |
| 38 | umee                  | cosmosia2   | cosmosia3   |
| 39 | sei                   | cosmosia3   | cosmosia4   |
| 40 | evmos-testnet-archive | cosmosia4   | cosmosia5   |
| 41 | injective             | cosmosia5   | cosmosia6   |
| 42 | kujira                | cosmosia6   | cosmosia7   |
| 43 | passage               | cosmosia7   | cosmosia8   |
| 44 | osmosis-testnet       | cosmosia8   | cosmosia9   |
| 45 | evmos-archive         | cosmosia9   | cosmosia10  |
| 46 | stride                | cosmosia10  | cosmosia11  |
| 47 | dig-archive           | cosmosia11  | cosmosia12  |
| 48 | osmosis-archive       | cosmosia12  | cosmosia13  |


#### Docker commands

To add label to a node:
```console
docker node update --label-add cosmosia.lb.osmosis=true cosmosia1
```

To remove label to a node:
```console
docker node update --label-rm cosmosia.lb.osmosis cosmosia1
```

To list node with label:
```console
docker node ls -f node.label=cosmosia.lb.osmosis=true
```
