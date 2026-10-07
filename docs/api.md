# API Reference

## AllowIt Backend Endpoints

The frontend proxy forwards versioned API requests with original authentication, cookies and request identity. Owner and public POST routes require an allowlisted frontend Origin. `native/report` uses the bearer audit capability. Owner routes require the authenticated wallet session. Agent reporting credentials grant no owner or signing authority.

### Generate Native Policy

```text
POST /api/native/generate
```

**Request:**

```json
{
  "network": "solana:testnet",
  "prompt": "Spend up to 5 test tokens per day"
}
```

**Response:** `policy`, `release` and `diagnostics` describe the validated pinned profile. Unsupported constraints fail. Native generation parameterizes the existing daily-limit template.

### Save Native Policy

```text
POST /api/native/save
```

**Request:** `{policy}` contains the exact generated and validated policy. The authenticated owner wallet session saves its immutable identity. Use the stored policy ID as `policyId` in subsequent operations.

### Prepare and Submit Owner Operation

```text
POST /api/native/prepare
POST /api/native/submit
```

**Preparation request:**

```json
{
  "policyId": "YOUR_POLICY_ID",
  "requestId": "fund-001",
  "method": "fund",
  "options": {
    "amount": "2"
  }
}
```

Preparation returns the original unsigned message, intent, binding and validity metadata. Check the exact wallet intent before signing.

**Submission request:**

```json
{
  "policyId": "YOUR_POLICY_ID",
  "requestId": "fund-001",
  "signedBytes": "BASE64_SIGNED_TRANSACTION"
}
```

The backend persists the owner-signed proof in SQL before broadcast. Submission alone does not establish settlement.

### Get Operation Status and Recover

```text
POST /api/native/confirm
POST /api/native/recover
```

**Request:**

```json
{
  "policyId": "YOUR_POLICY_ID",
  "requestId": "fund-001"
}
```

These operations reconcile the original finalized receipt or method-specific expiry evidence. They do not sign or broadcast a replacement. Uncertain funding or withdrawal can require another explicitly authorized owner operation.

### Read Release and Vault State

```text
GET /api/native/release
POST /api/native/state
```

Release metadata identifies the pinned sources and artifacts. It does not prove deployment. State takes `{policyId}` and returns verified state, binding and public operations.

### Export the Executor Bundle

```text
POST /api/native/export
```

**Request:** `{policyId}` identifies the saved policy. The owner session receives verified state, the skill and an executor bundle with a private audit capability. Give that bundle only to the designated executor. The capability permits proof reporting, not owner actions or signing.

### Report Executor Proof

```text
POST /api/native/report
```

The audit capability from `native/export` permits `{policyId, record}` for its bound policy. When this capability exists, the CLI requires durable SQL acknowledgement before executor broadcast. The backend independently reconciles receipts and vault nonces. Keep the capability private.

### Health Check

```text
GET /api/health
```

The response reports status, policy runtime identity, configured provider availability and source revision. Health metadata does not establish financial settlement or successful provider inference.

## Native Rust SDK and CLI

The [SDK](../repos/AllowIt-hq--allowit-sdk/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-sdk/blob/main/README.md)) supplies policy and Solana client libraries. The [CLI](../repos/AllowIt-hq--allowit-cli/README.md) ([GitHub README](https://github.com/AllowIt-hq/allowit-cli/blob/main/README.md)) calls native modules directly. The browser uses backend APIs and retains wallet intent checks and an App-owned journal.

### Build and HTTP Commands


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

Use the [CLI command reference](../repos/AllowIt-hq--allowit-cli/README.md#use) ([GitHub README](https://github.com/AllowIt-hq/allowit-cli/blob/main/README.md#use)) for exact arguments and response states. Permission, owner input, submission and settlement are separate results. Preserve the request ID when a response is uncertain.

### Native Owner and Executor Commands

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

Testnet is the default. Devnet requires explicit network and RPC configuration. The native CLI refuses Mainnet. Amounts are exact decimal strings. See [native configuration](../repos/AllowIt-hq--allowit-cli/README.md#owner-policy-lifecycle) ([GitHub README](https://github.com/AllowIt-hq/allowit-cli/blob/main/README.md#owner-policy-lifecycle)).

## Result Handling


| Native exit | Meaning |
| --- | --- |
| 0 | New generation, status result or finalized success. Inspect the result. |
| 2 | Invalid command arguments. |
| 3 | Invalid configuration or authority. |
| 5 | Uncertain operation. Reconcile the original proof. |
| 6 | Replay of an earlier settled operation. |
| 20 | Policy denial or finalized failure. |

HTTP command exits differ. Use the [HTTP state reference](../repos/AllowIt-hq--allowit-cli/README.md#states-and-exit-codes) ([GitHub README](https://github.com/AllowIt-hq/allowit-cli/blob/main/README.md#states-and-exit-codes)). `status` never creates a replacement spend. Additional funding or withdrawal after an expired uncertain operation requires explicit owner consent. Set `ALLOWIT_ADDITIONAL_OWNER_OPERATION=1` and a fresh `ALLOWIT_REQUEST_ID` for that additional operation.
