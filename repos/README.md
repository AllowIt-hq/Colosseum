# Repositories

This directory pins repositories as Git submodules. GitHub opens each repository at its recorded revision.

## AllowIt SDK

[GitHub](https://github.com/AllowIt-hq/allowit-sdk)

Rust policy compiler, registry and language server, plus the CLI client facade, the native Solana client and the server service facade. The `native-rust/` package supplies the Solana transaction, signing, receipt and journal client. The client facade links the Solana and Tempo vendor crates from their rail repositories at exact revisions. The repository retains JavaScript lifecycle references and generic contract adapters. Native custody programs belong to the separate Solana contracts repository. See [architecture](../docs/architecture.md).

## AllowIt CLI

[GitHub](https://github.com/AllowIt-hq/allowit-cli)

Native Rust agent and owner commands. The binary calls the SDK client facade. HTTP commands use the service API. Native policy commands run the SDK in-process. See [commands](../docs/api.md).

## AllowIt Solana Contracts

[GitHub](https://github.com/AllowIt-hq/allowit-contracts-solana)

Shared native Rust custody vault and policy programs, plus a separate PaySH program for bounded payments and swaps. Owner instances create PDA state and SPL token accounts under an accepted shared release. Offchain host crates supply the Solana vendor adapter and PaySH service packages. See [architecture](../docs/architecture.md).

## AllowIt Application

[GitHub](https://github.com/AllowIt-hq/app.allowIt.xyz)

Consumer frontend for policy authoring, owner wallet approvals, agent access and request review. A thin API proxy connects it to the Rust backend.

## AllowIt Engine

[GitHub](https://github.com/AllowIt-hq/allowit-engine)

Rust backend, standalone policy oracle and policy authoring agent. The backend handles authentication, policy evaluation, durable requests, owner questions, spending reservations and execution receipts.

## AllowIt Website

[GitHub](https://github.com/AllowIt-hq/allowit.xyz)

The AllowIt story website at [allowit.xyz](https://allowit.xyz). It contains the product narrative, interactive scenes and website build tooling.

## AllowIt Stellar Contracts

[GitHub](https://github.com/AllowIt-hq/allowit-contracts-stellar)

Owner-controlled Soroban policy wallets for Stellar. Simple, common and custom wallets share custody and administration code. The owner controls configuration, pause and recovery.

## AllowIt Project

[GitHub](https://github.com/AllowIt-hq/allowit-project)

Private knowledge workspace for AllowIt. It contains the project wiki, original sources, local tooling and application repository registry.

## Retrieve the pinned sources

The SDK, CLI and Solana contracts can be retrieved without access to private repositories:

```sh
git submodule update --init --recursive \
  repos/AllowIt-hq--allowit-sdk \
  repos/AllowIt-hq--allowit-cli \
  repos/AllowIt-hq--allowit-contracts-solana
```

The application, engine, website and knowledge workspace require authorized GitHub access. With that access, retrieve all pinned repositories:

```sh
git submodule update --init --recursive
git submodule status --recursive
```

Update gitlinks only after reviewing compatible revisions. Source changes belong in the child repository.
