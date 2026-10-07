# Repositories

The SDK, CLI and Solana contracts are pinned submodules.

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

## Retrieve the pinned sources

```sh
git submodule update --init --recursive
git submodule status --recursive
```

Update gitlinks only after reviewing compatible revisions. Source changes belong in the child repository.

The backend, application, website and Stellar contract repositories are private. They remain separate architecture components.
