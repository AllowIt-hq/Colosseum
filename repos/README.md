# Repositories

This directory pins repositories as Git submodules. GitHub opens each repository at its recorded revision.

## [AllowIt SDK](AllowIt-hq--allowit-sdk/)

[GitHub](https://github.com/AllowIt-hq/allowit-sdk) · [README](AllowIt-hq--allowit-sdk/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-sdk/blob/main/README.md))

Restricted Rust compiler, evaluator, registry and language server. The separate `native-rust/` package supplies the Solana transaction, signing, receipt and journal client. The repository retains JavaScript lifecycle references and generic IR contract adapters. Native custody programs belong to the separate Solana contracts repository. See [architecture](../docs/architecture.md).

## [AllowIt CLI](AllowIt-hq--allowit-cli/)

[GitHub](https://github.com/AllowIt-hq/allowit-cli) · [README](AllowIt-hq--allowit-cli/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-cli/blob/main/README.md))

The pinned SDK README still describes the action CLI as Go. The CLI supplied here uses Rust.

Native Rust agent and owner commands. HTTP commands use the service API. Native policy commands embed the SDK. See [commands](../docs/api.md).

## [AllowIt Solana Contracts](AllowIt-hq--allowit-contracts-solana/)

[GitHub](https://github.com/AllowIt-hq/allowit-contracts-solana) · [README](AllowIt-hq--allowit-contracts-solana/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-contracts-solana/blob/main/README.md))

Shared native Rust policy and custody programs. Owner instances create PDA state and SPL token accounts under an accepted shared release. See [architecture](../docs/architecture.md).

## [AllowIt Application](AllowIt-hq--app.allowIt.xyz/)

[GitHub](https://github.com/AllowIt-hq/app.allowIt.xyz) · [README](AllowIt-hq--app.allowIt.xyz/README.md) ([GitHub README](https://github.com/AllowIt-hq/app.allowIt.xyz/blob/main/README.md))

Consumer frontend for policy authoring, owner wallet approvals, agent access and request review. A thin API proxy connects it to the Rust backend.

## [AllowIt Engine](AllowIt-hq--allowit-engine/)

[GitHub](https://github.com/AllowIt-hq/allowit-engine) · [README](AllowIt-hq--allowit-engine/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-engine/blob/main/README.md))

Rust backend and headless policy service. It handles authentication, policy evaluation, durable requests, owner questions, spending reservations and execution receipts.

## [AllowIt Website](AllowIt-hq--allowit.xyz/)

[GitHub](https://github.com/AllowIt-hq/allowit.xyz) · [README](AllowIt-hq--allowit.xyz/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit.xyz/blob/main/README.md))

The AllowIt story website at [allowit.xyz](https://allowit.xyz). It contains the product narrative, interactive scenes and website build tooling.

## [AllowIt Stellar Contracts](AllowIt-hq--allowit-contracts-stellar/)

[GitHub](https://github.com/AllowIt-hq/allowit-contracts-stellar) · [README](AllowIt-hq--allowit-contracts-stellar/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-contracts-stellar/blob/main/README.md))

Native Rust policy, custody vault and owner-bound factory for Stellar. Contracts enforce standing approvals, daily limits, revocation and owner withdrawal.

## [AllowIt Project](AllowIt-hq--allowit.xyz-project/)

[GitHub](https://github.com/AllowIt-hq/allowit.xyz-project) · [README](AllowIt-hq--allowit.xyz-project/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit.xyz-project/blob/main/README.md))

Private knowledge workspace for AllowIt. It contains the project wiki, original sources, local tooling and application repository registry.

## Retrieve the pinned sources

The SDK, CLI and Solana contracts can be retrieved without access to private repositories:

```sh
git submodule update --init --recursive \
  repos/AllowIt-hq--allowit-sdk \
  repos/AllowIt-hq--allowit-cli \
  repos/AllowIt-hq--allowit-contracts-solana
```

The application, engine, website, Stellar contracts and knowledge workspace require authorized GitHub access. With that access, retrieve all pinned repositories:

```sh
git submodule update --init --recursive
git submodule status --recursive
```

Update gitlinks only after reviewing compatible revisions. Source changes belong in the child repository.
