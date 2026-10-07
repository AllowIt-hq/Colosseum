# Lifecycle commands

The native lifecycle uses the AllowIt SDK and public Solana RPC. No payment gateway API is required for this MVP.

```sh
allowit policy generate 'Spend up to 5 test tokens per day'
allowit policy deploy
allowit policy fund 10
allowit policy execute RECIPIENT_TOKEN_ACCOUNT 2
allowit policy status
allowit policy tune 0
allowit policy revoke
allowit policy withdraw 8
```

`generate` prints the actual pinned Rust source and saves a unique policy instance. `deploy` creates the vault and standing approval; `fund` deposits the bound test token. `execute` takes a recipient token-account address, not a wallet address. `status` reconciles saved operations without signing a replacement. `tune 0` pauses spending. Withdrawal uses owner authority.

Configure the selected network, RPC, mint, verified deployment, executor identity and private policy/journal directory. Owner operations require the owner signer; execution requires only the executor signer. Status requires no signing key. Testnet is the default; Devnet is explicit; the native CLI refuses Mainnet.

Amounts are exact decimal strings. Preserve policy identity and request ID on retries. Use a fresh request ID only for a genuinely new intended operation. Never place key material in this repository, SKILL.md, executor.json or demo recordings.

## Result handling

| Exit | Meaning |
| --- | --- |
| 0 | Generation/status or finalized success; inspect the returned result |
| 3 | Invalid configuration |
| 5 | Uncertain; reconcile the stored operation |
| 6 | Replay of an earlier settled operation |
| 20 | Policy denial or finalized failure |

The Rust CLI candidate calls native Rust modules directly. Its release validation remains separate from acceptance of the earlier Go/JavaScript bundle.
