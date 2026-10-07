# Product

## What is AllowIt?

You give an agent a job and a policy for the money it can use. AllowIt checks its requests against that policy. Generic policies can ask you to decide unclear requests. You can revoke spending authority.

The native Solana vault uses standing approval and a daily spending limit. Its Rust SDK and backend handle policy requests, signing and recovery. Generic policies can request semantic evidence or owner input through the backend. The native kernel enforces approval, executor, asset, daily spending, nonce and revision.

## Target Users

- **Agent builders:** inspect permissions and execute supported operations through the Rust CLI.
- **Wallet owners:** fund a bounded vault and retain pause, revocation and withdrawal controls.
- **Application developers:** use the native SDK and backend APIs for policy, signing and recovery workflows.

## Core Value Propositions

1. **You set the policy:** approve the executor and daily limit for the native vault.
2. **The agent can continue:** standing approval permits transfers that pass the native policy.
3. **You keep control:** retain the owner key and pause, revocation and withdrawal controls.
4. **You can check what happened:** receipts and signed proofs support recovery after lost responses.

An owner inspects the policy, signs initialization and standing approval, then funds the vault separately. The executor receives its skill and private configuration. The owner can inspect receipts, tune the limit, pause, revoke or withdraw.

## How It Differs from Unrestricted Agent Signing

| Control | Unrestricted agent signer | AllowIt native vault |
| --- | --- | --- |
| Spending authority | Authority follows the key's ordinary account permissions. | Designated executor, standing approval and bound daily policy. |
| Owner key | The agent can hold the spending account's signer. | Owner key stays separate from the executor. |
| Budget | Depends on external controls. | Shared custody enforces the per-vault daily ceiling. |
| Recovery | Depends on the client implementation. | SDK journals original proofs and checks finalized effects. |
| Owner control | Depends on account permissions. | Owner can pause, revoke and withdraw. |

The native profile permits recipients within its daily cap. The separate allowance profile requires owner signing for each transfer. Main Preview uses the Rust backend. Hosted generic generation and Production release retain separate acceptance work.

[Architecture](architecture.md) · [Evidence](evidence.md) · [Roadmap](roadmap.md)
