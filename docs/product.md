# Product

## What is AllowIt?

> AllowIt lets your AI agents spend and invest, within a policy you set.

You describe the job, the money and the judgement calls in your own words. AllowIt turns them into a policy, gives the agent a skill and checks every request. Inside the policy, the agent goes ahead. Unclear requests come back to you. When you revoke spending authority, further spending stops.

Policy evaluation follows two paths:

- **Native Solana vault.** A designated executor spends one bound asset under your standing approval, within a daily limit. The on-chain programs enforce the executor, approval, asset, daily limit, nonce and policy revision.
- **Generic restricted policies.** The Rust backend evaluates these policies. The backend obtains semantic evidence and binds it to the exact action. These policies can send questions to you.

The Rust SDK and backend handle policy requests, signing and recovery.

## Target Users

- **Agent builders:** inspect an agent's permissions and run supported operations through the Rust CLI.
- **Wallet owners:** fund a bounded vault and keep pause, revocation and withdrawal controls.
- **Application developers:** build policy, signing and recovery workflows on the native SDK and backend APIs.

## Core Value Propositions

1. **You set the terms.** You choose the executor and the daily limit, and you approve the policy once.
2. **The agent keeps working.** Transfers that pass the policy need no new signature from you.
3. **You keep the key.** Your owner key stays separate from the executor key. You can pause, tune, revoke or withdraw at any time.
4. **You can see what happened.** Finalized receipts and signed journals record each operation. The client uses them to recover after a lost response.

In practice, you inspect the policy, sign the vault initialization and standing approval, then fund the vault in a separate step. The agent receives its skill and its private executor configuration. From then on, you can inspect receipts, tune the limit, pause, revoke or withdraw.

## How It Differs from Unrestricted Agent Signing

| Control | Unrestricted agent signer | AllowIt native vault |
| --- | --- | --- |
| Spending authority | The key's ordinary account permissions. | Designated executor, standing approval and bound daily policy. |
| Owner key | The agent can hold the spending account's signer. | Owner key stays separate from the executor. |
| Budget | Depends on external controls. | Shared custody enforces the per-vault daily ceiling. |
| Recovery | Depends on the client implementation. | SDK journals original proofs and checks finalized effects. |
| Owner control | Depends on account permissions. | Owner can pause, tune, revoke and withdraw. |

The native profile permits any recipient within its daily limit. The separate allowance profile requires an owner signature for each transfer. Main Preview uses the Rust backend. Production also uses the Rust stack. Hosted generic-provider acceptance remains a release milestone.

[Architecture](architecture.md) · [Evidence](evidence.md) · [Roadmap](roadmap.md)
