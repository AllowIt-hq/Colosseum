# Public repositories

The organization has three public repositories on October 7, 2026: Colosseum, the SDK and the CLI. Colosseum is this repository. The other two are pinned submodules.

## [AllowIt SDK](AllowIt-hq--allowit-sdk/)

[GitHub](https://github.com/AllowIt-hq/allowit-sdk) · [README](AllowIt-hq--allowit-sdk/README.md)

Restricted Rust compiler, evaluator, registry and language server. The separate `native-rust/` package supplies the Solana transaction, signing, receipt and journal client. The repository retains JavaScript lifecycle references and generic IR contract adapters. Native custody programs belong to the separate private Solana contracts repository. See [architecture](../docs/architecture.md).

## [AllowIt CLI](AllowIt-hq--allowit-cli/)

[GitHub](https://github.com/AllowIt-hq/allowit-cli) · [README](AllowIt-hq--allowit-cli/README.md)

The pinned SDK README still describes the action CLI as Go. The CLI supplied here uses Rust.

Native Rust agent and owner commands. HTTP commands use the service API. Native policy commands embed the SDK. See [commands](../docs/api.md).

## Retrieve the pinned sources

```sh
git submodule update --init --recursive
git submodule status --recursive
```

Update gitlinks only after reviewing compatible revisions. Source changes belong in the child repository. This report does not change child source.

The backend, application, website and Solana/Stellar contract repositories are private. They remain separate architecture components. No private repository is included here.
