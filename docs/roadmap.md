# Roadmap

## v0.1 — Hackathon MVP (current)

- [x] Native Rust policy SDK, compiler and language server, and separate Solana client.
- [x] Native Rust CLI for agent and owner commands, with no Node runtime.
- [x] Rust backend with API, engine, storage and integration crates.
- [x] Independent React frontend with a thin same-origin proxy.
- [x] Solana Testnet vault lifecycle: deploy, fund, executor spend, revoke, withdraw and recovery.
- [x] CLI workflow builds for Linux x64, macOS Apple Silicon and macOS Intel.
- [x] Basic PaySH integration with a simple wallet.
- [x] KASE: corporate-action program, holder register and record snapshots.
- [x] KASE: coupon, maturity redemption and holder vote operations.
- [x] KASE: on-chain operator mandates and backend policy enforcement.
- [x] KASE: agent API and generated skill, plus issuer console and holder register.
- [x] KASE: Devnet demo with exact entitlements and duplicate refusal.
- [x] Tempo: rail adapter with network, asset, fee and signer binding.
- [x] Tempo: signing adapter, receipt handling and compatible policy enforcement.
- [x] Tempo: frontend payment workspace and Rust CLI payment and recovery.
- [x] Tempo: Machine Payments Protocol (MPP) purchases bound to service challenges, with response reports across SDK, backend, CLI and app.
- [x] Tempo: one policy-bound payment with a verified receipt on a public network.
- [x] Event, demo URL, video and presentation.

Hackathon integration outputs: deployed Devnet corporate-action programs, a KASE servicing skill, a Tempo profile in backend capabilities and Tempo CLI support.

## v1.0 — Production Release

- [x] Rust Production runtime with independent frontend and backend routing.
- [x] PostgreSQL production storage and restore.
- [x] Production backend configuration: Tempo enabled, KASE RPC configured and KASE agent route requires a bearer token.
- [x] Hosted generic generation and preference-provider acceptance.
- [ ] Compose KASE corporate actions with the shared `allowit` base library and custody gate.
- [ ] Add KASE SDK and CLI operations, plus holder views for the shared custody gate.
- [ ] Tagged native CLI Release with platform checksums and provenance.
- [ ] Windows CLI target.
- [ ] Physical-wallet and selected iPhone acceptance.
- [ ] Explicit Mainnet authority, configuration and security acceptance.

## v2.0 — Additional Rails and Operations

- [ ] Stellar client, credentials, network binding and journal.
- [ ] Etherfuse compatibility test and operation adapter.
- [ ] Community verifier modules through one namespace registry.
- [ ] PaySH service delivery and recovery through native vaults.
- [ ] Rail-specific settlement acceptance.

Each integration must keep exact action binding and owner authority. Generic semantic checks do not add on-chain semantic enforcement.

## v3.0 — Ecosystem

- [ ] Delegation: let an agent delegate parts of its assigned work to sub-agents, within the terms its owner sets.
- [ ] Optional hosted-agent integration.
- [ ] Distributed recovery and journal coordination.
- [ ] Additional integration patterns selected through explicit product decisions.
