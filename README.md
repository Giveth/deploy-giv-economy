# Deploy the Giveth GIV Economy contracts

This package contains the CLI script for deploying the Giveth GIVEconomy smart contracts across any EVM (Ethereum Virtual Machine) compatible networks.

## Licensing

This code is provided under the GNU GPL-3.0 Public License. See `LICENSE` file for more details.

The codebase relies heavily on the [deploy-v3 script](https://github.com/Uniswap/deploy-v3) by Uniswap.

## Usage

This package vends a CLI for executing a deployment script that results in a full deployment of the Giveth GIV Economy contract suite.
Get the arguments for running the latest version of the script via `npx @giveth/deploy-giv-economy --help`.

As of `v1.0.0` the arguments are:
```text
> npx @giveth/deploy-giv-economy --help
Usage: npx @giveth/deploy-giv-economy [options]

Options:
  -pk, --private-key <string>               Private key used to deploy all contracts
  -h, --help                                display help for command
```

The script runs a set of migrations, with each migration deploying a contract or executing a transaction. Migration state is
saved in a JSON file at the supplied path (by default `./state.json`).

To use the script, you must fund an address, and pass the private key of that address to the script so that it can construct
and broadcast the deployment transactions.

The block explorer verifi
cation process (e.g. Etherscan) is specific to the network you are deploying to. For the existing deployments,
we have used the `@nomiclabs/hardhat-etherscan` hardhat plugin in the individual repositories to verify the deployment addresses.

Note that in between deployment steps, the script waits for confirmations. By default, this is set to `2`. If the network
only mines blocks when the transactions is queued (e.g. a local testnet), you must set confirmations to `0`.

## Development

To run unit tests, run `yarn test`.

For testing the script, run `yarn start`.

To publish the script, first create a version: `npm version <version identifier>`, then publish via `npm publish`.
Don't forget to push your tagged commit!
