# Product

AllowIt lets an owner grant an agent bounded spending authority. The owner chooses the policy, supplies funds and retains approval and recovery controls. The agent uses the Rust CLI to inspect permissions, request decisions and execute supported operations.

## Owner and agent journey

1. Select the supported native policy and inspect its pinned Rust source.
2. Review the network, mint, executor and daily limit.
3. Sign vault initialization and standing approval.
4. Fund the vault in a separate owner operation.
5. Give the executor the generated skill and its private configuration.
6. Inspect finalized spending records and remaining funds.
7. Tune, pause, revoke or withdraw through owner controls.

The browser uses backend APIs for validation and preparation. The owner wallet signs the exact prepared operation. Native owner CLI commands provide another local signing surface. The executor signs spending with its own key.

## Policy profiles

The native Solana profile uses shared custody and policy programs. Its pinned kernel enforces approval, executor identity, asset, daily spending, nonce and revision. The daily budget applies per vault. Recipients remain selectable within that budget.

The application also supports restricted Rust policy evaluation, semantic evidence and owner questions. Those decisions use the backend policy SDK. They do not add semantic-purpose enforcement to the native kernel. The separate allowance profile requires owner signing for each transfer.

## Recovery and controls

Exact signed proofs survive lost responses. Status reconciles the original operation. A displayed approval, submitted transaction or local journal entry does not establish settlement. The system records spending after receipt checks verify finalized effects.

Zero daily limit pauses native spending. Revocation removes standing approval. Owner withdrawal does not require successful policy execution. Owner and executor keys remain separate.

## Current scope

The bounded Rust lifecycle passes on Solana Testnet with a six-decimal test token. Main Preview uses the Rust backend and thin frontend proxy. Hosted generic policy generation still requires provider repair. Production release, physical wallet acceptance and additional rails have separate completion criteria.

[Architecture](architecture.md) · [Evidence](evidence.md) · [Roadmap](roadmap.md)
