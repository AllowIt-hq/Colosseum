# Product

## What is AllowIt?

> AllowIt lets your AI agents spend and invest, within a policy you set.

You decide how much freedom each agent gets. AllowIt gives any agent you control the autonomy and resource access you are comfortable with. Within those terms, the agent does the work you assign at its own pace. When a request needs your judgement, AllowIt asks you, and you can use that dialogue to refine your policies.

Policy evaluation follows two paths:

- **Native Solana vault.** A designated executor spends one bound asset under your standing approval, within a daily limit. The on-chain programs enforce the executor, approval, asset, daily limit, nonce and policy revision.
- **Generic restricted policies.** The Rust backend evaluates these policies. The backend obtains semantic evidence and binds it to the exact action. These policies can send questions to you.

The Rust SDK and backend handle policy requests, signing and recovery.

## Target Users

- **Agent builders:** inspect an agent's permissions and run supported operations through the Rust CLI.
- **Wallet owners:** fund a bounded vault and keep pause, revocation and withdrawal controls.
- **Application developers:** build policy, signing and recovery workflows on the native SDK and backend APIs.

## Core Value Propositions

1. **Your terms.** Each agent gets the autonomy and resource access that you choose.
2. **Your judgement.** A dialogue with the policy engine lets you explain what you mean. Your feedback personalizes your policies.
3. **Their pace.** Within your terms, agents finish their work without asking you about each step.
4. **Your control.** Pause spending, tune the limit, revoke approval or withdraw at any time.

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

[Architecture](architecture.md) · [Roadmap](roadmap.md)
