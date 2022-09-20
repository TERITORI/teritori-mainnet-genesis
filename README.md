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
Atlas DAO
```

## How to create gentx
Install few packages:  
```shell
apt install build-essential git curl gcc make jq -y
```

Install Go 1.19+:  
```shell
wget -c https://go.dev/dl/go1.19.1.linux-amd64.tar.gz && rm -rf /usr/local/go && tar -C /usr/local -xzf go1.19.1.linux-amd64.tar.gz && rm -rf go1.19.1.linux-amd64.tar.gz
``` 

Setup your environnement (you can skip this part if you already had go installed before):  
```shell
echo 'export GOROOT=/usr/local/go' >> $HOME/.bash_profile
echo 'export GOPATH=$HOME/go' >> $HOME/.bash_profile
echo 'export GO111MODULE=on' >> $HOME/.bash_profile
echo 'export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin' >> $HOME/.bash_profile && . $HOME/.bash_profile
```  

Verify the installation:  
```shell
go version
#Should return go version go1.19.1 linux/amd64
```  

Install the mainnet binary:    
```shell
git clone https://github.com/TERITORI/teritori-chain && cd teritori-chain && git switch mainnet && git checkout v1.0.0 && make install
``` 

Verify the installation:  
```shell
teritorid version
#Should return HEAD-163e8c996325471287866ef292b7e028d4e49bd5
```  

Init the chain:  
```shell
teritorid init <Moniker> --chain-id=teritori-1 
```  

Add your validator key:
```shell 
teritorid keys add <YOUR_KEY>
 ```  
 
You can also use `--recover` flag to retrieve an already existed key (but we recommend for security reason to use one key per chain to avoid total loss of funds in case one key is missing)  

Add genesis account:
```shell
teritorid add-genesis-account <YOUR_KEY> 10000000utori
```

Create the gentx:
```shell
teritorid gentx <YOUR_KEY> 5000000utori --moniker="" --min-self-delegation="1000000" --commission-max-change-rate="0.01" --commission-max-rate="0.20"  --commission-rate=0.05 --website="" --identity="" --security-contact="" --details="" --chain-id=teritori-1
```

## Note:
1. Save `<YOUR_KEY>` seed phrase and `priv_validator_key.json` from the .teritorid/config folder, in a secure place offline.
2. Do not add more than 10 TORI (10000000 utori) on genesis account or your PR gonna be rejected.


## Push the GenTx generated to the repository
Fork this repository and clone the repo  
Copy `$HOME/.teritorid/config/gentx/gentx-<xxxxx>.json` to `<repo>/gentx/<Moniker>.json`  
Create PR into the repo
