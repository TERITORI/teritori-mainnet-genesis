# Teritori mainnet genesis

This is the repo to manage gentxs and create mainnet genesis.

## List of validators to be on genesis

```
Forbole
StakeLab
HashQuark
Lavender
Polkachu
Crost nest
Active Nodes
WhisperNode
Nodes.Guru
Chill Validation
Inter Blockchain Services
Noderunners
StakingCabin
Golden Ratio Staking
RHINO
Web34ever
Cosmic Validator
Oni Validator
Node Jumper
Nysa Network
Wetez
AAA MetaHuahua
Samouraï World
NodesBlocks
ibrahimarslan
Munris
Silk Nodes
Gata DAO
Orbital Apes
Orbital Apes
Atlas DAO
Stake-Take
```

## How to create gentx

1. Install `go` and configure `GOPATH`
2. Install `teritorid` binary from `https://github.com/TERITORI/teritori-chain/tree/mainnet`
3. Generate gentx

```sh
# remove previously used home directory
rm -rf $HOME/.teritorid/

# init files on default home directory
teritorid init --chain-id=teritori-1 <moniker> --home=$HOME/.teritorid

# add key to be used for validator (or import if there's already one using `--recover flag`)
teritorid keys add <val_key> --keyring-backend=test --home=$HOME/.teritorid

# add genesis account on default home directory
teritorid add-genesis-account $(teritorid keys show <val_key> -a --keyring-backend=test --home=$HOME/.teritorid) 10000000utori --home=$HOME/.teritorid

# create gentx to create validator
teritorid gentx <val_key> 5000000utori --moniker="<>" --min-self-delegation="1000000" --commission-max-change-rate="<>" --commission-max-rate="<>"  --commission-rate="<>" --website="<>" --identity="<>" --security-contact="<>" --details="<>" --keyring-backend=test --home=$HOME/.teritorid --chain-id=teritori-1

# Note:
# 1. Save <val_key> seed phrase, `node_key.json` and `priv_validator_key.json` to be used when running validator.
# 2. Do not add more than 10 TORI (10000000 utori) on genesis account, since at genesis 10 TORI is given to validators.
```

4. Fork this repository and clone the repo
5. Copy `$HOME/.teritorid/config/gentx/gentx-<xxxxx>.json` to `<repo>/gentx/<Moniker>.json`
6. Create PR into the repo
