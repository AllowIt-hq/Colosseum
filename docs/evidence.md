# Validation

## Latest validated execution

The Rust lifecycle completed vault deployment, funding, executor spending, revocation and withdrawal on Solana Testnet. The run used a test token and a Wallet Standard signing fixture.

The owner funded 2 tokens. The executor spent 1 token. After revocation, the owner withdrew the remaining token. The final vault balance was zero, with approval disabled.

Independent checks matched signed proofs, immutable program hashes, finalized receipts, token movements and settled database records. Recovery preserved the original signed operations through lost responses and backend redeployment. All five operations remained settled.

The run used App `063fed7`, backend `3639e87`, CLI `8953ba8` and SDK `6406b1a`. Source checks and 125 Rust-backed browser cases passed, with desktop, portrait and landscape coverage.

## Current release

Production serves the Rust frontend and backend. The release checks cover frontend routing, backend APIs and compatible native SDK sources. The PostgreSQL backup and isolated restore matched. Compatibility checks preserved policy, allocation and session state across the Go/Rust transition.

## Source repositories

The [SDK](../repos/AllowIt-hq--allowit-sdk/README.md), [CLI](../repos/AllowIt-hq--allowit-cli/README.md) and [Solana contracts](../repos/AllowIt-hq--allowit-contracts-solana/README.md) are pinned under [repos/](../repos/README.md). Git submodule revisions identify the supplied source snapshots.
