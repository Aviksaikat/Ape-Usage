# Minimal sample config
```yaml
name: simple_storage
plugins:
  - name: solidity
    version: 0.6.3 # version of the plugin
  - name: ganache
  - name: alchemy
  - name: hardhat
  # - name: ens
  # - name: etherscan
ethereum:
  default_network: mainnet-fork
  mainnet_fork:
    default_provider: ganache
ganache:
  fork:
    ethereum:
      mainnet:
        upstream_provider: alchemy
test:
  mnemonic: test test test test test test test test test test test junk
  number_of_accounts: 10
```

# Working with local RPC with test accounts
```yaml
name: Project-Name
plugins:
  - name: solidity
  - name: alchemy
  - name: foundry
  - name: infura
  - name: etherscan
ethereum:
  default_network: mainnet-fork
  mainnet_fork:
    default_provider: foundry
    gas_limit: auto
    transaction_acceptance_timeout: 180
    default_transaction_type: 0
  mainnet:
    default_provider: alchemy
    transaction_acceptance_timeout: 180
foundry:
  host: http://127.0.0.1:8545
  fork:
    ethereum:
      mainnet_fork:
        upstream_provider: alchemy
test:
  mnemonic: test test test test test test test test test test test junk
  number_of_accounts: 10
  hd_path: "m/44'/60'/0'/0/{}" # this will generate test accounts associated with foundry
```

# Working with custom RPC
```yaml
name: Project-Name
plugins:
  - name: solidity
  - name: alchemy
  - name: foundry
  - name: etherscan
ethereum:
  default_network: mainnet-fork
  mainnet_fork:
    default_provider: foundry
    default_transaction_type: 0
  mainnet:
    default_provider: alchemy
foundry:
  host: http://127.0.0.1:8545
  fork:
    ethereum:
      mainnet_fork:
        upstream_provider: alchemy
```

# Imports & Mappings
```yaml
name: flash_loan_arbritage
plugins:
  - name: solidity
  - name: alchemy
  - name: foundry
  - name: infura
  - name: etherscan
ethereum:
  default_network: mainnet-fork
  mainnet_fork:
    default_provider: foundry
    transaction_acceptance_timeout: 99999999
  mainnet:
    transaction_acceptance_timeout: 99999999
foundry:
  host: auto
  fork:
    ethereum:
      mainnet:
        upstream_provider: alchemy
dependencies:
  - name: Uniswap-periphery
    github: uniswap/v3-periphery
    ref: 1.3.0
  - name: Uniswap-core
    github: uniswap/v3-core
    ref: 1.0.0
  - name: OpenZeppelin
    github: OpenZeppelin/openzeppelin-contracts
    version: 4.9.3
solidity:
  version: 0.8.12 # solidity version
  import_remapping:
    - "@uniswap/v3-periphery/contracts=Uniswap-periphery/1.3.0"
    - "@uniswap/v3-core/contracts=Uniswap-core/1.0.0"
    - "@openzeppelin/contracts=OpenZeppelin/4.9.3"
test:
  mnemonic: test test test test test test test test test test test junk
  number_of_accounts: 10
``` 