# AllowIt

Owner-approved, policy-bound vaults for agent spending on Solana. The owner funds a vault and grants standing approval; a designated executor can transfer the bound token only within the on-chain daily limit.

[App](https://app.allowit.xyz) · [Architecture](docs/architecture.md) · [Recorded Testnet evidence](docs/evidence.md) · [Completion guide](docs/completion-guide.md)

## Colosseum submission

Draft. Event name and submission URL: **TODO — confirm the registered event and project page.**

| Team member | Role | Public contact |
| --- | --- | --- |
| TODO | TODO | TODO |

## Problem and Solution

Agents need spending authority to complete tasks. Repeated owner signatures interrupt execution, while unrestricted signing access gives the agent more authority than the task requires.

AllowIt places funds in a policy-bound vault. The owner approves the vault once, selects a daily limit and designates an executor. Each spend invokes the approved native Rust policy; custody checks approval, executor identity, asset, nonce, revision and limits before transferring tokens. The owner can pause, revoke and withdraw.

## Why Solana

Program-derived vault accounts separate custody from the executor's signing key. A native policy invocation and SPL Token transfer share one transaction, so spending counters and token movement commit together. Finalized transaction receipts expose the policy invocation and exact token changes.

## Summary of Features

- Display the pinned Rust policy and configure its daily-limit parameter.
- Create a policy-bound vault with standing owner approval, then fund it.
- Hand off SKILL.md and public executor.json without the owner's signing key.
- Execute transfers using the designated executor and verify finalized receipts.
- Persist signed bytes before broadcast and recover the same operation after uncertainty.
- Tune the daily limit, pause with zero, revoke approval and withdraw remaining funds.

The MVP uses one pinned kernel, UTC calendar days and six-decimal test tokens. Limits are per vault. The executor may select any recipient within that limit; recipient allowlists and semantic-purpose enforcement are not implemented. Prompt generation parameterizes existing policy code rather than compiling arbitrary new Rust. PaySH discovery is optional; paid API execution is future work.

## Tech Stack

| Layer | Technology |
| --- | --- |
| Browser | React, Vite, TypeScript, AllowIt JavaScript SDK |
| CLI candidate | Rust with the pinned AllowIt native Rust SDK |
| Policy and custody | Native Rust Solana programs; minimal Pinocchio policy adapter |
| Tokens and signing | Classic SPL Token, Wallet Standard sign-only, separate owner/executor identities |
| Recovery | Durable local journal; browser IndexedDB signed-proof storage |
| Verification | Rust/compiled-program tests, SDK conformance and public Testnet journeys |

## Architecture

Owner → AllowIt SDK → policy-bound vault → approval/funding → skill and executor context → executor-signed custody call → native policy → SPL transfer → finalized receipt.

Shared immutable programs are deployed once; each owner creates vault state. The deployed executable identity is pinned separately from the policy source bundle. See [architecture](docs/architecture.md).

## Quick Start

This repository contains submission documentation. Use the AllowIt app, SDK, CLI and contract checkouts for execution; this repository does not build an application.

The Rust CLI candidate builds with `cargo build --locked --release`. Configure an explicit Testnet RPC, bound mint, verified deployment and private owner/executor signer files. See [lifecycle commands](docs/api.md). The current Rust candidate is not a tagged release. The recorded public acceptance used the earlier Go/JavaScript bundle.

## Roadmap

- Recorded: public Solana Testnet SDK, compiled CLI and browser journeys.
- Pending: release/platform acceptance for the Rust CLI candidate and native Phantom/iPhone acceptance.
- Future: PaySH spending and delivery, distributed recovery and additional rail integration.

See [roadmap](docs/roadmap.md). Mainnet deployment and a production security audit are not claimed.

## Resources

- [App entrypoint](https://app.allowit.xyz) — native Testnet requires a configured release-matching environment.
- [Testnet evidence and example execution](docs/evidence.md).
- **TODO:** exact configured native demo URL, video walkthrough, presentation, submission URL and public team contacts.

## License

The documentation template is MIT-licensed; its original notice is retained in [LICENSE](LICENSE). Application and contract licensing must be confirmed separately.

Adapted from [Marakaya/colosseum_example](https://github.com/Marakaya/colosseum_example/tree/315695b07dbf4c2fff3c0144a31c9153ddc0fdce). Architecture and acceptance details checked against local AllowIt records on October 6, 2026.
