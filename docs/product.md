# Product

AllowIt gives an agent bounded spending authority without handing it the owner's signing key. The initial users are agent builders and wallet owners who need unattended token transfers with an explicit daily budget and an owner recovery path.

## User journey

1. Generate the supported daily-limit policy and inspect the actual pinned Rust source.
2. Create the vault and grant standing approval in an owner-signed transaction.
3. Fund the vault and export SKILL.md plus public executor configuration.
4. Configure a separate executor signer and execute transfers within the daily cap.
5. Inspect finalized receipts; pause, revoke or withdraw through owner commands.

## Product boundary

On-chain enforcement covers approval, executor identity, the bound asset, daily accounting, nonce and revision. Task purpose and PaySH discovery instructions are metadata. The MVP has no recipient allowlist or semantic-policy enforcement, and separate vaults have separate budgets.

The distinction from unrestricted agent signing is that the executor key authorizes only supported vault spending. The distinction from approving every transfer is standing approval with a chain-enforced daily ceiling. No market share, performance advantage, customer traction or competitor feature claims are asserted here.
