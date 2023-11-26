## Custom RPC ENDPOINT
```bash
ape run scripts/main.py --network http://customURL
```

## Mainnet and mainet fork
```sh
# ethereum
ape run scripts/monitor.py --network :mainnet:infura

# hardhat provider
ape run scripts/monitor.py --network ethereum:mainnet-fork:hardhat
```

## Testnets using different provider

#### Have to install infura, alchemy plugins
```sh
# alchemy
ape run scripts/attack.py --network ethereum:sepolia:alchemy

# infura
ape run scripts/attack.py --network ethereum:goerli:infura
```

## Using foundry
```sh
ape run scripts/API.py --network arbitrum::foundry
```

## Debug mode
```sh
ape run scripts/monitor.py --network :mainnet:infura --verbosity DEBUG
```