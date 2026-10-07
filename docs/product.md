# Product

## What is AllowIt?

> AllowIt lets your AI agents spend and invest, within a policy you set.

**Go on. On your terms.**

You decide how much freedom each agent gets. AllowIt gives any agent you control the autonomy and resource access you are comfortable with. Within those terms, the agent does the work you assign at its own pace. When a request needs your judgement, AllowIt asks you. You keep control.

### Problem

Agents now buy data, tools and services to finish real work. Owners have two poor choices. Give the agent a wallet key, and it can spend everything on anything. Approve every payment, and the work stops while the agent waits. A plain spending limit cannot tell whether a purchase serves the job.

### Policy profiles

- **Generic policy.** You describe your terms in plain language. The Rust backend applies exact rules. For terms such as “prefer verified green investments”, it consults a preference oracle and asks you when the answer is unclear.
- **Native Solana vault.** A designated executor spends one asset under your standing approval, within a daily limit. On-chain programs enforce it. A request outside those terms fails.

- **Owner-signed allowance.** The backend evaluates each exact transfer. You authorize settlement with your wallet signature.

## Target Users

- **Wallet owners:** fund a bounded vault and keep pause, revocation and withdrawal controls.
- **Agent builders:** give an agent one CLI and a scoped skill instead of a wallet key.
- **Application developers:** build on the Rust SDK and backend APIs.
- **Bond issuers and servicers:** automate coupons, redemption and holder votes under policy.

### User journeys

Generic policy review and owner questions:

1. **Describe.** You state your terms. AllowIt drafts a policy.
2. **Review.** You read the steps, revise through dialogue and approve one revision.
3. **Ask.** An unclear request waits for your answer in the app. Your answer decides that one request.
4. **Refine.** Your feedback becomes a new revision. You review and approve it.

Native vault setup:

1. **Approve.** You sign vault setup and standing approval in your wallet. You fund the vault separately.
2. **Authorize agent.** Your agent receives its skill and private executor configuration.
3. **Work.** The executor spends within the daily limit. Requests outside it fail.
4. **Control.** You pause, tune the limit, revoke or withdraw at any time.

## Core Value Propositions

1. **Your terms.** Each agent gets the autonomy and resource access that you choose.
2. **Your judgement.** A dialogue with the policy engine lets you explain what you mean. Your feedback personalizes your policies.
3. **Their pace.** Within your terms, agents finish their work without asking you about each step.
4. **Your control.** In the native vault, pause spending, tune the limit, revoke approval or withdraw at any time.

### Requirements

| ID | Requirement |
| --- | --- |
| FR-1 | Draft a policy from plain language and show it as readable steps. |
| FR-2 | Revise and approve policies as explicit revisions. |
| FR-3 | Ask the owner about unclear generic requests. The agent waits for the answer. |
| FR-4 | Enforce a native daily-limit vault with standing approval. |
| FR-5 | Let native vault owners pause, tune, revoke and withdraw. |
| FR-6 | Give agents one CLI with no access to owner keys. |
| FR-7 | Service KASE corporate actions: coupons, maturity redemption and advisory votes. |
| FR-8 | Pay on the Tempo rail under owner policy. |
| FR-9 | Let agents delegate to sub-agents within the owner's terms. |

### Operational requirements

- Keep owner signing keys separate from executor credentials.
- Bound deterministic evaluation size, depth and arithmetic.
- Bind native execution to approved network, asset and programs.
- Confirm exact finalized effects before recording settlement.

### Scope

The native vault profile uses Solana Testnet and test tokens. The KASE demonstration uses Solana Devnet, a test bond and test settlement tokens. Corporate actions snapshot holders at each record date, pay exact entitlements and record advisory votes. Tempo payments bind network, asset, fees and signer, with verified receipts. See the [roadmap](roadmap.md) for delivery status.

### Success criteria

- An owner sets terms, approves once and keeps the owner key.
- An executor spends within the daily limit. An over-limit request fails.
- An unclear request reaches the owner and resumes after the answer.
- The KASE demo pays the exact scheduled entitlements for each coupon and at maturity, and refuses duplicates.
- One Tempo payment passes policy and produces a verified receipt.

## How It Differs from Unrestricted Agent Signing

| Control | Unrestricted agent signer | AllowIt |
| --- | --- | --- |
| Spending authority | All permissions of the key. | Designated executor, standing approval and bound policy. |
| Owner key | The agent can hold it. | Stays with the owner. |
| Budget | Depends on external controls. | Native custody enforces each vault's daily limit. |
| Judgement | None. | Generic policies ask the owner about unclear requests. |
| Owner control | Depends on account permissions. | Native vault: pause, tune, revoke and withdraw. |

### Boundaries

The native vault enforces asset, approval and daily limit. The backend evaluates preferences and routes unclear requests to the owner.

[Architecture](architecture.md) · [Roadmap](roadmap.md)
