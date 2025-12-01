# ajcoin

AJCoin is a simple fungible token implemented as a Clarity smart contract using the Clarinet development framework.

This repository contains the main project metadata. The Clarinet-based smart contract implementation lives in the sibling directory `../ajcoin-clarinet`.

## Project layout

- `ajcoin/` – this repository (you are here)
- `ajcoin-clarinet/` – Clarinet project containing the `ajcoin` smart contract and tests

## Getting started

### Prerequisites

- [Clarinet](https://github.com/hirosystems/clarinet) installed and available on your `PATH`.

You can verify your installation with:

```bash path=null start=null
clarinet --version
```

### Cloning the repo and navigating

```bash path=null start=null
# from your workspace
cd /home/anthony/Documents/GitHub
# ajcoin repo
cd ajcoin
# Clarinet project (smart contract and tests)
cd ../ajcoin-clarinet
```

## AJCoin smart contract

The AJCoin smart contract is located at:

- `../ajcoin-clarinet/contracts/ajcoin.clar`

### Features

- Fungible token with configurable initial supply
- Owner-only `initialize` function to mint the initial supply
- Basic `transfer` and `transfer-from` functions
- Read-only views for balances and token metadata

#### Key entrypoints

- `initialize (amount uint)` – mints `amount` tokens to the contract owner. Can only be called once by the contract owner.
- `transfer (recipient principal, amount uint)` – sends `amount` tokens from `tx-sender` to `recipient`.
- `transfer-from (sender principal, recipient principal, amount uint)` – owner-only helper to move tokens from `sender` to `recipient`.
- `get-balance-of (owner principal)` – returns the balance of `owner`.
- `get-total-supply ()` – returns the total token supply.
- `get-name (), get-symbol (), get-decimals ()` – basic token metadata.

## Working with the Clarinet project

Change into the Clarinet project directory:

```bash path=null start=null
cd ../ajcoin-clarinet
```

### Check the contract

Run Clarinet’s static checks against all contracts:

```bash path=null start=null
clarinet check
```

### Running tests

The Clarinet project is scaffolded with TypeScript tests.

From `../ajcoin-clarinet`:

```bash path=null start=null
npm install
npm test
```

## Development notes

- The contract currently includes a commented-out `impl-trait` line where you can wire in a concrete SIP-010 trait implementation principal for stricter interface conformance.
- Error codes are defined as constants for clarity:
  - `u100` – not authorized
  - `u101` – insufficient balance
  - `u102` – already initialized

## License

This project uses the license file found at `LICENSE` in this directory.
