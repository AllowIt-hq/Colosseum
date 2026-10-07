# Commands and API

The [Rust CLI](../repos/AllowIt-hq--allowit-cli/README.md) has two command groups. HTTP commands use the application service. Native lifecycle commands use the [Solana SDK](../repos/AllowIt-hq--allowit-sdk/native-rust/src/lib.rs) locally.

## Build and HTTP commands

```sh
cd repos/AllowIt-hq--allowit-cli
cargo build --locked --release
./target/release/allowit --help
```

Set `ALLOWIT_URL` to the exact service origin. Set `ALLOWIT_TOKEN` to the policy-scoped capability from the generated skill. Keep both values in the local environment. The CLI rejects redirects and mismatched policy identities.

- `show` reads policy details and execution requirements.
- `eval` requests a decision with JSON runtime context.
- `exec` requests an operation under the selected application profile.
- `status` reads the durable result for the original request.

Use the [CLI command reference](../repos/AllowIt-hq--allowit-cli/README.md#use) for exact arguments and response states. Permission, owner input, submission and settlement are separate results. Preserve the request ID when a response is uncertain.

## Native owner and executor commands

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

These commands form an example sequence. Each command requires its own result check. `generate` saves parameters and prints the pinned source. `deploy` initializes the vault and standing approval. `fund` deposits the bound token. `execute` takes a token-account address. `tune 0` pauses spending. `revoke` removes approval. `withdraw` uses owner authority.

Configure `ALLOWIT_POLICY_DIR`, `ALLOWIT_NETWORK`, `ALLOWIT_RPC_URL`, `ALLOWIT_MINT`, `ALLOWIT_EXECUTOR` and `ALLOWIT_DEPLOYMENT_FILE`. Set `ALLOWIT_REQUEST_ID` for the intended operation. Keep it unchanged on retries. Owner operations use `ALLOWIT_OWNER_KEYPAIR`. Execution uses `ALLOWIT_EXECUTOR_KEYPAIR` and the public `ALLOWIT_OWNER`. Status needs no signing key. Native commands do not require the ordinary HTTP capability.

Testnet is the default. Devnet requires explicit network and RPC configuration. The native CLI refuses Mainnet. Amounts are exact decimal strings. See [native configuration](../repos/AllowIt-hq--allowit-cli/README.md#owner-policy-lifecycle).

## Backend and signing protocol

The frontend proxy forwards versioned API requests with original authentication and request identity. Backend APIs supply release metadata, native generation, validation, transaction preparation, submission, status and recovery. Native backend routes use the SDK directly. Browser wallet intent checks and journals remain in the application.

Browser owner operations persist signed proofs locally and in backend SQL before broadcast. An exported hosted-executor audit capability allows reporting to `/api/native/report`. When that capability exists, the CLI requires durable acknowledgement before executor broadcast. Standalone native execution uses its local journal and RPC. The backend independently reconciles receipts and vault nonces. That capability grants no owner or signing authority.

Keep exported bundles, journals and capabilities private. A bare public executor address contains no secret. A backend-exported executor bundle can contain a reporting secret.

## Result handling

| Native exit | Meaning |
| --- | --- |
| 0 | New generation, status result or finalized success. Inspect the result. |
| 2 | Invalid command arguments. |
| 3 | Invalid configuration or authority. |
| 5 | Uncertain operation. Reconcile the original proof. |
| 6 | Replay of an earlier settled operation. |
| 20 | Policy denial or finalized failure. |

HTTP command exits differ. Use the [HTTP state reference](../repos/AllowIt-hq--allowit-cli/README.md#states-and-exit-codes). `status` never creates a replacement spend. Additional funding or withdrawal after an expired uncertain operation requires explicit owner consent. Set `ALLOWIT_ADDITIONAL_OWNER_OPERATION=1` and a fresh `ALLOWIT_REQUEST_ID` for that additional operation.
