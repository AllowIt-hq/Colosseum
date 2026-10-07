# Colosseum template completion report

Fill this for **AllowIt’s native Solana vault MVP**, built entirely on **AllowIt infrastructure**: SDK, CLI, policy and custody programs. Use the template’s structure and replace its BBM content. These are filling instructions, not submission answers.

| Template section | How to fill it |
| --- | --- |
| Title, description, badges | Explain standing approval and bounded executor spending. Identify Testnet and the exact demonstrated release; link its CI. |
| Demo links and image | Show the native app (`?native=1`), policy source, funded vault and finalized execution. Add video/submission links and replace `assets/project.jpg`. |
| Hackathon and team | Confirm the event name, team members, roles and public contact links. Remove the example founder and contacts. |
| Problem and Solution | Describe repeated signing versus unrestricted agent custody; connect the problem to a vault, daily cap, designated executor and owner recovery. |
| Why Solana | Explain PDA custody, native policy invocation, atomic SPL transfer/accounting and verifiable finalized receipts. |
| Features | Display pinned Rust; deploy/approve, fund, execute, tune/pause, revoke/withdraw; export SKILL.md/executor.json; recover signed requests. |
| Tech Stack | Browser: React/Vite/TypeScript and AllowIt JavaScript SDK. CLI candidate: Rust plus pinned AllowIt native Rust SDK. Contracts: AllowIt native Rust policy and custody programs. |
| Architecture | Owner → AllowIt SDK → policy-bound PDA vault → standing approval/funding → skill + executor context → executor-signed AllowIt custody call → AllowIt native policy → SPL transfer → finalized receipt. |
| Quick Start | Document `?native=1`, `cargo build --locked --release` and `allowit policy` commands. Configure test cluster, mint, release and separate owner/executor signers. |
| Roadmap | Separate recorded Testnet acceptance from Rust-candidate release/platform validation, native wallets/devices, PaySH payments, distributed recovery and subsequent rails. |
| Resources | Supply the deck, video, live app, source repositories and public project contacts. Remove every `#` placeholder. |
| License | Confirm rights and the intended license for every included repository before adopting MIT. |

Adapt the four `docs/` files for audience, AllowIt policy/custody separation, SDK/ABI and acceptance gaps. Shared programs are deployed once; owners create vault state. Pin source and executable identities separately.

The BBM template contains stub code/tests and inconsistent network defaults. Reuse its presentation structure.

Scope: one pinned daily-limit kernel, UTC days and a six-decimal test token. Limits are per vault; there is no recipient allowlist or semantic-purpose enforcement. Generation parameterizes the kernel, not arbitrary prompt-authored Rust. PaySH discovery is opt-in; payment spending remains follow-up.

Evidence: October 5 acceptance records public Testnet settlement using browser signing fixtures and the earlier Go/JavaScript bundle. It excludes the Rust candidate, Phantom/iPhone, Mainnet, paid API delivery and security audit. Attach release-bound receipts, denial, recovery and revoke/withdraw evidence. Native vault spends are executor-signed under standing owner approval.

Updated October 6, 2026 from AllowIt-app `4e8314a`, allowit-cli `7761cf6`, AllowIt-sdk `21b3660`, AllowIt-contracts-solana `2554df8`, and the captured October 5 Testnet acceptance record. Template baseline: [inspected revision](https://github.com/Marakaya/colosseum_example/tree/315695b07dbf4c2fff3c0144a31c9153ddc0fdce). Deployment health and candidate tests were not rerun for this report.
