# The Namada Shielded Expedition

Welcome to the Namada shielded expedition!

Here is where Namada pilots and crew members will expect to find the `balances.toml` file that allocates `NAAN` to public keys.

Using this `balances.toml` file, the included participants can generate and submit their **signed** pre-genesis *bonding* transactions in the `transactions` folder. These will be validated against, and only merged once the validation has passed.

Participants may bond ***up to*** the amount allocated to their public key. It is recommended not to bond the full allocation, as having `NAAN` to pay for gas will be useful. Any bonds greater than one's allocation will be rejected.

## Seeds
Syncing a new node may not work if the peers of other nodes are filled up, so participants should use (and consider making) seed nodes. Here is a list of seeds:
- `tcp://3c12dd31adf945bd10d551713d8dc22795b7de0c@194.163.172.168:26656` (Mandragora)
- [tbd]

## Full Nodes
Syncing a new node may not work if the peers of other nodes are filled up, so participants should use (and consider making) full nodes. Here is a list of full nodes:
- `tcp://0c4ce0c5ceb022564b111a4e4d0c0a66a9567dbe@65.109.117.113:26656` (CroutonDigital)
- `tcp://50e15e1639476ddc091d39c7e6faf4a1a3798235@38.242.152.80:26656` (EmberStake)
- [tbd]
  
## Creating the genesis files (advanced)
In order to create the genesis files for the expedition, the following steps were taken.
1. The signed transactions files were collected in the `signed_genesis_transactions` folder.
2. The python script in `scripts/txs_toml.py` was run from the root with `python3 scripts/txs_toml.py ./ ./signed_genesis_transactions` to generate the `transactions.toml` and to populate the whitelists in the `parameters.toml` file. Once this was done, it was possible to generate the chain-id.

## How to create the chain-id from the genesis files

Make sure you have the namada binaries installed and are of version `v0.31.0`. Assuming the path to the namada client binary is `$NAMADAC`, you can run the following command to generate the chain-id:

```bash
$NAMADAC utils init-network --chain-prefix shielded-expedition --genesis-time 2024-02-01T18:00:00Z --templates-path ./ --wasm-checksums-path ./utils/checksums.json --consensus-timeout-commit 10s
```
