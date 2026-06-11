# Blackbox Protocol

**Tamper-evident signed receipts that prove what your software did.**

Blackbox creates cryptographic receipts for software actions — API calls, CI/CD builds, AI agent decisions, deployments, signed approvals. Each receipt is independently verifiable, replay-protected, and chained without trusting a central server.

Sign it. Verify it. Prove it later.

---

## What it does

- **Sign** structured action records with Ed25519
- **Verify** receipts across seven axes: cryptographic, semantic, authorization, temporal, revocation, replay, chain
- **Gate** actions against configurable policies before they're recorded
- **Replay-protect** with deterministic nonces and a local tracker
- **Cosign** with multi-signer thresholds for high-stakes actions

Built on Ed25519, SHA-256, deterministic CBOR (RFC 8949), and COSE_Sign1 / COSE_Sign (RFC 9052). No proprietary formats. Source-visible. Apache-2.0.

---

## Why it exists

Software does things. AI agents do things. CI/CD pipelines do things. APIs do things.

When something goes wrong — or when someone asks "did this actually happen?" — most systems can only say "the logs say so." Logs can be edited. Servers can be compromised. Databases can be rewritten.

Blackbox produces receipts that can't be silently rewritten. If someone tampers with a receipt, verification fails. If a receipt is replayed, the tracker rejects it. If a signer wasn't authorized, the gate rejects it.

It's evidence, not trust.

---

## Status

Pre-launch. v0.1.0 in hardening. Blackbox is not externally audited yet.

The code is source-visible and independently reviewable. Use it for evidence trails, not for life-safety decisions. Production key storage should use a KMS or HSM, not files on disk.

See the repo for full limitations and threat model when public.

---

## Project layout

When the repo flips public, it contains:

- `@blackbox-protocol/core` — signing, verification, COSE handling
- `@blackbox-protocol/cli` — `sign`, `verify`, `inspect`, `cosign` commands
- `@blackbox-protocol/gate` — policy evaluator
- `@blackbox-protocol/evidence` — receipt management
- Connectors for HTTP requests, GitHub Actions builds, and AI agent actions

---

## Contact

- Web: [blackboxprotocol.dev](blackboxprotocol.dev)
- Email: blackboxprotocolhq@gmail.com
- X: [@blackboxproto](https://x.com/blackboxproto)
