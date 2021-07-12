# Substrate Migrations
A repository of Substrate runtime migrations.

## Contributing
**Feel free to open PRs to include your own examples of applying Substrate migrations and/or notes.**

## Links
+ [Storage migrations knowledgebase article](https://substrate.dev/docs/en/knowledgebase/runtime/upgrades#storage-migrations) on the DevHub.
+ [Substrate PRs](https://github.com/paritytech/substrate/pulls?q=is%3Apr+label%3AE1-runtimemigration) including migration relevant code.
+ [Collaborative Migration Guide](https://hackmd.io/@apopiak/Hyhroh0Xv/edit) on hackmd.

## Relevant PRs
+ Run [custom OnRuntimeUpgrade first](https://github.com/paritytech/substrate/pull/8687) (before `frame_system`)

-------------------------------------
## FRAME Migrations
This lists PRs that include or induce storage migrations in FRAME pallets after Substrate 2.0 with
some examples of how they were implemented in production chains.

### `2021-05-03` Remove Offence Delay
https://github.com/paritytech/substrate/pull/8414

### `2021-03-20` Decouple Staking and Election - Part 2.1: Unleash Multi Phase
https://github.com/paritytech/substrate/pull/8113

**Examples**
+ Polkadot: https://github.com/paritytech/polkadot/pull/2432

### `2021-03-12` Update Contracts Schedule to v3
https://github.com/paritytech/substrate/pull/8231

### `2021-03-10` Babe Epoch Configurations
https://github.com/paritytech/substrate/pull/8072

**Examples**
+ Polkadot: https://github.com/paritytech/polkadot/pull/2467

### `2021-03-03` Self-Sufficient Ref-Counting
https://github.com/paritytech/substrate/pull/8221

Required for: https://github.com/paritytech/substrate/pull/8220

### `2021-02-10` [Substrate v3.0.0](https://github.com/paritytech/substrate/releases/tag/v3.0.0)

### Q1 + Q2 `2021` Migrate FRAME Pallets to Procedural `#[pallet]` Macro
Using the procedural macro shifts the storage prefix from the `decl_storage` macro invocation to the pallet instantiation in the `construct_runtime` macro.
As a result migrations to the new macro do not inherently require a migration, but might incidentally create the necessity if care is not taken to make sure that the prefix stays the same.

+ https://github.com/paritytech/substrate/pull/7898
+ https://github.com/paritytech/substrate/pull/7936
+ https://github.com/paritytech/substrate/pull/7984
+ https://github.com/paritytech/substrate/pull/8078
+ https://github.com/paritytech/substrate/pull/8310
+ https://github.com/paritytech/substrate/pull/8337
+ https://github.com/paritytech/substrate/pull/8365
+ https://github.com/paritytech/substrate/pull/8440
+ https://github.com/paritytech/substrate/pull/8448
+ https://github.com/paritytech/substrate/pull/8452
+ https://github.com/paritytech/substrate/pull/8465
+ https://github.com/paritytech/substrate/pull/8620
+ https://github.com/paritytech/substrate/pull/8663
+ https://github.com/paritytech/substrate/pull/8724
+ https://github.com/paritytech/substrate/pull/8741
+ https://github.com/paritytech/substrate/pull/8761
+ https://github.com/paritytech/substrate/pull/8762
+ https://github.com/paritytech/substrate/pull/8763
+ https://github.com/paritytech/substrate/pull/8769
+ https://github.com/paritytech/substrate/pull/8824
+ https://github.com/paritytech/substrate/pull/8825
+ https://github.com/paritytech/substrate/pull/9061
+ https://github.com/paritytech/substrate/pull/9083
+ https://github.com/paritytech/substrate/pull/9087
+ https://github.com/paritytech/substrate/pull/9088

### `2021-01-20` Fix Phragmen and Proxy Issue
https://github.com/paritytech/substrate/pull/7040

**Examples**
+ Polkadot: https://github.com/paritytech/polkadot/pull/1719

### `2021-01-20` Nominator Set Kicking & Blocking
https://github.com/paritytech/substrate/pull/7930

### `2020-10-21` Pallet Storage Versions
Should not require any manual code as the version is updated automatically on every `on_runtime_upgrade`.

https://github.com/paritytech/substrate/pull/7208

### `2020-09-24` Time-Delay Proxies Migration Fix
**Note:** If using the introduced migration function, you should use storage version guards to make
sure it only runs once.

https://github.com/paritytech/substrate/pull/7205

### `2020-09-22` [Substrate v2.0.0](https://github.com/paritytech/substrate/releases/tag/v2.0.0)

## Pre 2.0 Migrations
This lists PRs that include or induce storage migrations before Substrate 2.0 with some examples of
how they were implemented in production chains.

### `2020-09-22` Move Account Refcounts from `u8` to `u32`
https://github.com/paritytech/substrate/pull/7164

### `2020-09-22` Allow Specifying Fixed Index in `construct_runtime`
https://github.com/paritytech/substrate/pull/6969

**Examples**
+ Polkadot: https://github.com/paritytech/polkadot/pull/1692

### `2020-08-23` Time-Delay Proxies
**Warning:** This migration is missing a storage guard so it might be applied more than once if included in more than one runtime uprade.
Use the extracted migration from https://github.com/paritytech/substrate/pull/7205 in combination with a storage guard if running this migration.

https://github.com/paritytech/substrate/pull/6770

### `2020-07-02` Allow Specifying Dispatch Origin
**Note:** A migration function is provided, but you will need to manually trigger this migration if it applies to your runtime.

https://github.com/paritytech/substrate/pull/6387

### `2020-06-17` Next Fee Multiplier
https://github.com/paritytech/substrate/pull/6334/

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/15

### `2020-06-09` Frozen Indices
https://github.com/paritytech/substrate/pull/6307/

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/14

### `2020-06-08` Stacked Filtering
Introduces multisigs pallet.

https://github.com/paritytech/substrate/pull/6273

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/15

### `2020-06-05` Staking Remove MigrateEra Storage Item
https://github.com/paritytech/substrate/pull/6253

### `2020-05-15` Democracy Weights
Flips the deposit order of fields.

https://github.com/paritytech/substrate/pull/5828

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/12

### `2020-04-24` Staking Migration Version Check Fix
https://github.com/paritytech/substrate/pull/5768

### `2020-04-17` Fee Multiplier
https://github.com/paritytech/substrate/pull/5673

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/6

### `2020-04-04` Simple Staking Payouts
https://github.com/paritytech/substrate/pull/5406

**Examples**
+ Edgeware: https://github.com/hicommonwealth/edgeware-node/pull/173 and https://github.com/hicommonwealth/substrate/pull/10

### `2020-03-26` Time Module Usage in Staking
https://github.com/paritytech/substrate/pull/4662

### `2020-03-26` Scheduler Introduction
and democracy refactoring. No migration in Substrate, but might require one for chains using the pallet.

https://github.com/paritytech/substrate/pull/5412

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/12

### `2020-03-23` Democracy Prime Member Selection
https://github.com/paritytech/substrate/pull/5346

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/11 and https://github.com/hicommonwealth/edgeware-node/pull/174

### `2020-03-21` Democracy Redesign
https://github.com/paritytech/substrate/pull/5294/

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/12

----------------------
### `2020-03-16` Hasher Migration (Iterable Storage Maps)
**NOTE: If included will influence how other migrations are run. (Pre-hasher migrations cannot iterate storage easily.)**

https://github.com/paritytech/substrate/pull/5226 

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/6 https://github.com/hicommonwealth/edgeware-node/pull/170
----------------------

### `2020-03-14` Unique Storage Names
https://github.com/paritytech/substrate/pull/5010/

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/6

### `2020-03-05` Introduce `on_runtime_upgrade`
https://github.com/paritytech/substrate/pull/5058 (includes balances migration, removed in  https://github.com/paritytech/substrate/pull/5224)

### `2020-03-03` Lazy Payouts
https://github.com/paritytech/substrate/pull/4474

**Examples**
+ Edgeware: https://github.com/hicommonwealth/edgeware-node/pull/173 and https://github.com/hicommonwealth/substrate/pull/10

### `2020-02-24` Lazy Reaping
https://github.com/paritytech/substrate/pull/4895

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/6/

### `2020-02-14` Composite Accounts
https://github.com/paritytech/substrate/pull/4820) (includes indices migration removed in https://github.com/paritytech/substrate/pull/5870)

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/14

### `2020-02-01` Balances Refactor
https://github.com/paritytech/substrate/pull/4649

**Examples**
+ Edgeware: https://github.com/hicommonwealth/substrate/pull/6

## Removed Migrations
This lists the PRs that removed migration code from Substrate.

### `2020-06-23`
Democracy, Indices, Multisigs, Staking, Transaction Payment

https://github.com/paritytech/substrate/pull/6476

### `2020-05-03`
Democracy, Indices, Offences, Staking, Transaction Payment

https://github.com/paritytech/substrate/pull/5870

### `2020-03-19`
Mostly account/hasher migration, epochs, opaque hashers, grandpa authorities

https://github.com/paritytech/substrate/pull/5291

### `2020-03-12`
Balances

https://github.com/paritytech/substrate/pull/5224

-------------------------------------

## Non-FRAME Migrations
### `2021-03-07` Put initial data to storage with pallet deployment
Uses `PalletVersion` to determine that pallet was not present before to do initial migration of data to storage.

+ https://github.com/galacticcouncil/HydraDX-node/pull/132

### `2021-03-07` Update storage type from Vec to OrderedSet
Uses `PalletVersion`

+ https://github.com/galacticcouncil/HydraDX-node/pull/130
