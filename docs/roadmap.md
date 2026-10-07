# Roadmap

Updated October 7, 2026.

## Completed architecture and staging work

The native Rust SDK and CLI source ports are merged. The Rust backend composes API, engine, storage and integrations. Main Preview reaches it through the frontend proxy. Native browser validation and preparation use backend APIs.

A bounded Solana Testnet cycle completed deployment, funding, executor spending, revocation and withdrawal. Original signed proofs, SQL records and finalized effects survived recovery and backend redeployment. See [evidence](evidence.md).

## Remaining release work

- Repair hosted generic generation and check the configured preference-provider path.
- Complete PostgreSQL restore and pending-allocation continuity checks before Production migration.
- Complete independent backend Git routing and Production release acceptance.
- Publish an accepted native CLI Release with platform artifacts, checksums and provenance.
- Complete physical-wallet and selected iPhone acceptance.
- Supply verified event, team, demo, video and presentation details for Colosseum.

## Subsequent integration work

Stellar needs its own client, credentials, network, journal and settlement acceptance. Etherfuse and PaySH need verified operation adapters and service-delivery evidence. Hosted agents remain an optional separate system outside the MVP. Mainnet requires explicit release authority, deployment configuration and security acceptance.

These integrations must preserve exact action binding, owner authority and recovery. Existing generic semantic checks do not imply native on-chain semantic enforcement.
