<div align="center">

# TrustBeat

**eIDAS-qualified digital trust & anchoring infrastructure for the EU.**

Anchor hashes, logs, and AI decisions into qualified timestamps — and prove they existed, unaltered, at a point in time. Built for **eIDAS**, **NIS2**, and the **EU AI Act**.

[Website](https://trustbeat.eu) · [API](https://api.trustbeat.eu) · [API Docs](https://api.trustbeat.eu/docs)

</div>

---

## What we build

TrustBeat is a high-performance **Trust Layer** over eIDAS-qualified timestamping. Client hashes are batched into a Merkle tree and anchored to a **qualified timestamp** roughly every 10 minutes, so thousands of proofs share the cost of a single qualified token — while each hash still gets its own independently verifiable inclusion proof.

- **No file storage** — only hashes are accepted; your content never leaves your machine.
- **Redundant qualified providers** — backed by multiple independent eIDAS QTSPs (SK ID Solutions, EuroCert) with automatic failover, so timestamping never depends on a single provider staying up.
- **Offline verification** — every proof verifies locally against the Merkle root and the qualified token, with no call back to us.

## Products

| Product | What it does | Regulation |
|---|---|---|
| **Document Anchoring** | Anchor any SHA-256 hash into a qualified eIDAS timestamp | eIDAS |
| **Tamper-Evident Logs** | Anchor application & security logs as evidence | NIS2 · Article 21 |
| **AI Act Decision Anchoring** | Anchor every AI decision (input + output hash + metadata) | EU AI Act · Article 12 |
| **Audit Trail** | Court-admissible event ledger with a proof per event | eIDAS |
| **eIDAS Signature Verification** | Validate signed documents against EU trust lists | eIDAS |
| **EU Digital Identity** | Accept EUDI Wallet credentials via OIDC4VP | eIDAS 2 |

## SDKs

Five official SDKs — **zero runtime dependencies**, local Merkle verification built in.

| Language | Package | Install |
|---|---|---|
| **Python** | [`trustbeat`](https://pypi.org/project/trustbeat/) | `pip install trustbeat` |
| **TypeScript / JS** | [`trustbeat`](https://www.npmjs.com/package/trustbeat) | `npm install trustbeat` |
| **Java** | [`eu.trustbeat:trustbeat-sdk`](https://central.sonatype.com/artifact/eu.trustbeat/trustbeat-sdk) | Maven Central |
| **C# / .NET** | [`TrustBeat`](https://www.nuget.org/packages/TrustBeat) | `dotnet add package TrustBeat` |
| **Go** | [`github.com/TrustBeat/sdk-go`](https://pkg.go.dev/github.com/TrustBeat/sdk-go) | `go get github.com/TrustBeat/sdk-go` |

### Quickstart (Python)

```python
from trustbeat import TrustBeat

tb = TrustBeat(api_key="tb_live_…")

# Submit a SHA-256 digest — returns immediately (202 Accepted)
job = tb.anchor("e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855")

# Block until the qualified inclusion proof is ready (~one batch cycle)
proof = tb.anchor_wait(job.id)

# Verify locally — no network call
assert tb.verify(proof)
```

## Why it's defensible

- **Qualified, not just trusted** — proofs chain to an eIDAS-qualified timestamp, the highest assurance tier under EU law, not a self-signed clock.
- **One regulation per product** — each product maps to a concrete compliance obligation buyers already have to meet.
- **Verifiable without us** — proofs are self-contained and verify offline, so trust doesn't depend on TrustBeat staying online.

---

<div align="center">
<sub>TrustBeat s.r.o. · <a href="https://trustbeat.eu">trustbeat.eu</a></sub>
</div>
