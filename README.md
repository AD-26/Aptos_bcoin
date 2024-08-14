# BasicCoin Module

## Overview

The `BasicCoin` module is a Move smart contract that defines a basic cryptocurrency implementation. It allows for the creation and management of balances, providing functionalities to get a balance and mint coins. This module is designed to work with the Aptos blockchain.

## Structure

### Module: `BasicCoin`

This module includes the following key components:

- **Constants:**
  - `MODULE_OWNER`: The address that owns and controls the module.
  - `ENOT_MODULE_OWNER`: Error code for unauthorized access.
  - `EINSUFFICIENT_BALANCE`: Error code for insufficient balance.
  - `EALREADY_HAS_BALANCE`: Error code for already existing balance.

- **Structs:**
  - `Coin`: Represents a coin with a `value` field of type `u64`.
  - `Balance`: Stores the balance of a particular account with a `val` field of type `u64`.

- **Functions:**
  - `get_bal(owner: address, val: u64)`: A view function that retrieves the balance of a specified account.
  - `balance_of(owner: address): u64`: An entry function that creates a balance for an account if it doesn't already exist.
  - `mint_non_owner(account: signer)`: A test function that attempts to mint coins by a non-owner account and is expected to fail.

## Dependencies

This module depends on the following:

- `AptosFramework`: The module relies on the Aptos Framework for blockchain-specific functionality.

## Setup

To set up this module, ensure you have the following in your `.toml` file:

```toml
[package]
name = 'BasicCoin'
version = '1.0.0'

[dependencies.AptosFramework]
git = 'https://github.com/aptos-labs/aptos-core.git'
rev = 'main'
subdir = 'aptos-move/framework/aptos-framework'

[addresses]
std =  "0x1"
NamedAddr = "_"
```

## Testing

The module includes a test function `mint_non_owner` that checks if minting by a non-owner account fails as expected.

To run the tests, execute the following command:

```bash
aptos move test
```
