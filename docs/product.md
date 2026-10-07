# Product

## What is AllowIt?

AllowIt provides owner-approved spending controls for agents. The native Rust SDK and backend validate policy requests. Shared Solana programs enforce the native vault policy. The owner retains signing and recovery controls.

The native kernel binds approval, executor, asset, daily spending, nonce and revision. Generic restricted policies can also request semantic evidence or owner input through the backend. Those functions do not extend the native kernel's on-chain rules.

## Target Users

- **Agent builders:** inspect permissions and execute supported operations through the Rust CLI.
- **Wallet owners:** fund a bounded vault and retain pause, revocation and withdrawal controls.
- **Application developers:** use the native SDK and backend APIs for policy, signing and recovery workflows.

## Core Value Propositions

1. **Bounded authority:** the designated executor spends within the approved native policy.
2. **Separate signing:** the owner keeps the owner key. The executor uses its own key.
3. **Reviewed policy behavior:** source, executable identity and actual enforcement remain explicit.
4. **Recoverable operations:** signed proofs preserve original identity through lost responses and reconciliation.

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
