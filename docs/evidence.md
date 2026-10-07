# Architecture and validation evidence

Updated October 7, 2026. This page records existing validation. The documentation rewrite performs no financial operation or deployment.

## Latest architecture

The report follows the fourteen diagrams authored and published on October 6. Their latest updates describe native SDK boundaries, the Rust server, frontend proxy, independent deployments and shared Solana programs. The report condenses those views for a two-to-three-page reading length.

Maintainer references: [build dependencies](https://github.com/ackrate/ackrate-project/blob/main/wiki/ackrate/allowit-build-dependencies.md), [Rust server](https://github.com/ackrate/ackrate-project/blob/main/wiki/ackrate/allowit-rust-server.md), [blockchain deployment](https://github.com/ackrate/ackrate-project/blob/main/wiki/ackrate/allowit-blockchain-deployment.md), and [Vercel deployment](https://github.com/ackrate/ackrate-project/blob/main/wiki/ackrate/allowit-vercel-deployment.md). These knowledge-repository links require maintainer access.

## Current source references

The public SDK, CLI and Solana contracts are pinned as [submodules](../repos/README.md). The backend, application, website and Stellar contracts remain private.

| Component | Main revision read on October 7 |
| --- | --- |
| SDK | `1066a0ff03693ae7a706de00b775e9df133aeaaa` |
| CLI | `c7da3f2689e35fb82f0b97947bd7d5a2286c559a` |
| Rust backend | `f5a728619aad4ada186b0037bc531187a5dff17c` |
| Frontend | `e385529897443cb5abc5ce7233021d9c3a529c04` |
| Solana contracts | `c117bf93f502bf3a54d4a88d7907eff2a59de740` |

Current source and tested release pins serve different purposes. The submodule gitlinks identify the exact public source snapshots supplied with this report.

## Rust staging lifecycle

The accepted financial run used App `063fed7`, backend `3639e87`, CLI `8953ba8` and SDK `6406b1a`. It completed Deploy, Fund 2, executor spend 1, Revoke and Withdraw 1 on Solana Testnet. Final vault balance was zero. Approval was disabled. Nonce was 1 and revision was 2.

Independent checks matched signed proofs, immutable release hashes, finalized receipts, token movement and settled SQL records. Gate instrumentation recorded SQL acknowledgement before executor broadcast. Recovery retained original proofs through lost replies. Read-only checks verified all five settled operations after backend redeployment.

Source checks, 125 Rust-backed browser cases and desktop, portrait and short-landscape captures passed. The run used a Wallet Standard signing fixture and a test token. Physical Phantom, iPhone, Mainnet and Production acceptance remain separate.

Maintainer evidence: [staging acceptance](https://github.com/ackrate/ackrate-project/blob/main/wiki/tasks/allowit-rust-staging-acceptance.md) and [latest diagnostics](https://github.com/ackrate/ackrate-project/tree/main/instance/artifacts/164-allowit-final-staging-diagnostics-and-compatibility).

## Recorded native release

The October 5 public Testnet record used contracts `756eed28b67c45d03b5ea529724248eeeced6b73`. Both loader-v3 programs were immutable and byte-verified.

| Binding | Value |
| --- | --- |
| Testnet genesis | `4uhcVJyU9pJkvQyS88uRDiswHXSCkY3zQawwpjk2NsNY` |
| Policy program | `7fsLjSRWo8wtqgyq3SZEXZKFCrTkeAWwnmnK8URH4Dde` |
| Custody program | `J2PZaK9Zgu2UeZH4vj8EJdbnuFNjirCvQwDZExgLu3Vg` |
| Six-decimal test mint | `CFHNohV4F1MDxrZNuF1hZiQcJEx4qXTmST7p3zuTkuBk` |

The mint contains test tokens, not Circle USDC. [Recorded browser-to-CLI transfer](https://explorer.solana.com/tx/5feUAnCYFBPD8o2KMoCQP6j5mRxFceHhEBVieAy52Dj3YM57HXBeeURMYxNK7UUAuKgGBDZJaYfDYq6iiWm1NGLW?cluster=testnet).

The October 5 acceptance used the earlier Go/JavaScript bundle. The subsequent Rust staging cycle has its own evidence above.

## Open acceptance items

Hosted generic generation returned 502. Diagnostics recorded Gemini 503 and timeout, followed by Gateway 403. Backup remains disabled. Local Jev inference does not establish hosted provider acceptance.

Production remains on the earlier integration. PostgreSQL restoration, pending-allocation continuity and backend native Git routing remain open. A synthetic FileStore compatibility rehearsal passed 113 checks. It does not establish PostgreSQL restoration or unknown-field preservation.

Native CLI source and workflow binaries exist. A native GitHub Release remains unpublished. Paid-service delivery, additional rails and a production security audit remain outside demonstrated acceptance.
