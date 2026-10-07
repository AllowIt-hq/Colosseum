# Submission checklist

Use the [architecture](architecture.md), [product](product.md), [commands](api.md) and [evidence](evidence.md) as the technical report. Keep the submission focused on the native Rust architecture and bounded Solana vault lifecycle.

## Required submission material

- Check the registered event and public project page.
- Supply team names, roles and public contact links.
- Supply the configured demo URL, video and presentation.
- Show owner review, deployment, funding, executor spending and finalized receipts.
- Show one policy denial, recovery, revocation and withdrawal.
- Identify the exact app, backend, CLI, SDK and contract revisions used in the demo.
- State the network and test mint clearly.

## Repository and release checks

Initialize the [public submodules](../repos/README.md) at their committed gitlinks. Build the CLI from its pinned source. Follow its checksum and provenance instructions when using workflow binaries. Keep private backend, frontend and contract repositories outside the public submodule set.

Match public release configuration with the actual program identities before execution. Separate source identity from deployed executable identity. Use the owner wallet or local owner signer for owner operations. Use only the designated executor signer for native spending.

Keep capabilities, signer files, journals and signed proofs out of public recordings and Git. A generated executor bundle can contain a private audit capability.

## Claims and readiness

Describe current Rust Preview behavior and the recorded Testnet cycle. Keep Production migration, hosted provider repair, physical-wallet acceptance and native binary publication in the [roadmap](roadmap.md).

Describe the native kernel's actual approval and daily-limit rules. Generic policy evaluation and Jev evidence are separate capabilities. PaySH, Etherfuse and Stellar need their own integration and delivery evidence.

The repository's [MIT notice](../LICENSE) applies to this documentation. The [SDK license](../repos/AllowIt-hq--allowit-sdk/LICENSE) and [CLI license](../repos/AllowIt-hq--allowit-cli/LICENSE) remain in their source repositories. Confirm licenses separately for other components.
