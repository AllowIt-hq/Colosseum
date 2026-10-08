# Roadmap

## v1.0 — Hackathon MVP (current)

- [x] Native Rust policy SDK, compiler and language server, and separate Solana client.
- [x] Native Rust CLI for agent and owner commands, with no Node runtime.
- [x] Rust backend with API, engine, storage and integration crates.
- [x] Independent React frontend with a thin same-origin proxy.
- [x] Solana Testnet vault lifecycle: deploy, fund, executor spend, revoke, withdraw and recovery.
- [x] CLI workflow builds for Linux x64, macOS Apple Silicon and macOS Intel.
- [ ] KASE: corporate-action ABI, holder custody and record snapshots.
- [ ] KASE: `allowit::` coupon, maturity redemption and advisory vote operations on `corporate_actions` domain state.
- [ ] KASE: shared `allowit` base library linked into custody gate.
- [ ] KASE: SDK, backend, CLI and skill operations, plus issuer and holder views.
- [ ] KASE: Devnet demo with exact entitlements and duplicate refusal.
- [ ] Tempo: rail adapter with network, asset, fee and signer binding.
- [ ] Tempo: signing adapter, receipt handling and compatible policy enforcement.
- [ ] Tempo: one policy-bound payment with a verified receipt.
- [ ] Hosted generic generation and preference-provider acceptance.
- [ ] Event, demo URL, video and presentation.

Hackathon integration outputs: deployed Devnet corporate-action programs, a KASE servicing skill, a Tempo profile in backend capabilities and CLI support for both.

## v1.1 — Production Release

- [x] Rust Production runtime with independent frontend and backend routing.
- [x] PostgreSQL production storage and restore.
- [ ] Tagged native CLI Release with platform checksums and provenance.
- [ ] Windows CLI target.
- [ ] Physical-wallet and selected iPhone acceptance.
- [ ] Explicit Mainnet authority, configuration and security acceptance.

## v2.0 — Additional Rails and Operations

- [ ] Stellar client, credentials, network binding and journal.
- [ ] Etherfuse compatibility test and operation adapter.
- [ ] Community verifier modules through one namespace registry.
- [ ] PaySH payment delivery and recovery.
- [ ] Rail-specific settlement acceptance.

Each integration must keep exact action binding and owner authority. Generic semantic checks do not add on-chain semantic enforcement.

## v3.0 — Ecosystem

- [ ] Delegation: let an agent delegate parts of its assigned work to sub-agents, within the terms its owner sets.
- [ ] Optional hosted-agent integration.
- [ ] Distributed recovery and journal coordination.
- [ ] Additional integration patterns selected through explicit product decisions.
