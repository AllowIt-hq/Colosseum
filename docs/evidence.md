# Recorded Solana Testnet evidence

The October 5, 2026 acceptance record documents public Testnet execution. It is evidence of the recorded runtime, not a fresh verification of today's deployment.

| Component | Accepted revision |
| --- | --- |
| Contracts | `756eed28b67c45d03b5ea529724248eeeced6b73` |
| SDK | `c1b62623b6b8b17ea0e7ca40cf76d7ef22e6b2f1` |
| Go/JavaScript CLI | `525732fe083158792490fb8944d4301ab70b3ab5` |
| Hosted app | `25c25fe064497f4693094512d7d9e841b9b3dc5c` |

Network genesis: `4uhcVJyU9pJkvQyS88uRDiswHXSCkY3zQawwpjk2NsNY`.

Both recorded loader-v3 programs were immutable and byte-verified:

| Program | Address |
| --- | --- |
| Policy | `7fsLjSRWo8wtqgyq3SZEXZKFCrTkeAWwnmnK8URH4Dde` |
| Custody | `J2PZaK9Zgu2UeZH4vj8EJdbnuFNjirCvQwDZExgLu3Vg` |

The six-decimal mint `CFHNohV4F1MDxrZNuF1hZiQcJEx4qXTmST7p3zuTkuBk` contains test tokens, not USDC. No Mainnet funds were used.

[Recorded browser-to-CLI execution](https://explorer.solana.com/tx/5feUAnCYFBPD8o2KMoCQP6j5mRxFceHhEBVieAy52Dj3YM57HXBeeURMYxNK7UUAuKgGBDZJaYfDYq6iiWm1NGLW?cluster=testnet).

SDK and compiled CLI journeys covered generate/deploy/fund/execute, same-signature replay, over-limit rejection, pause/revoke and withdrawal. Hosted Chromium and mobile WebKit exercised the public-chain journey and handoff using a Wallet Standard sign-only fixture. That proves public-chain interaction; it does not prove native Phantom, extension or physical-iPhone acceptance.

The current Rust CLI checkout is an untagged `0.3.0-dev` candidate and is outside this acceptance record. PaySH spending, service delivery, Mainnet, arbitrary prompt compilation and a production security audit are not demonstrated.

Source: locally retained public Testnet acceptance record, captured October 6 from the accepted AllowIt app release. Retain and supply the original machine-readable receipts with the final submission.
