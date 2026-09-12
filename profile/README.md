![vidoxlabs-banner-v1.png](https://github.com/user-attachments/assets/e6fef43b-575e-43c6-8c3b-ac903bde0986)

# Vidoxlabs

Vidoxlabs LLC is an autonomous systems engineering organization building sovereign AI infrastructure, deterministic agent execution, and local compute orchestration. We architect intelligence workflows that are structured, reproducible, and fully auditable — what we call **Algorithmic Determinism**.

Our flagship system is **Violet**, an AI copilot running across a native macOS client, a Python backend, and a three-node Proxmox cluster. Below is what we build and the infrastructure behind it.

---

## What we build

### Violet — AI copilot

The active Vidoxlabs Intelligence. Violet is a conversational daily-driver copilot with persistent memory, evidence-grounded job reviews, push-to-talk voice, and two-phase Mac action authorization. She operates under a defined behavioral contract with a pinned persona digest, ensuring consistent behavior across sessions.

**Architecture:**

```
Violet (persona + behavioral contract)
  ├── ViBot  — Python backend, signed BFF assertions, turn pipeline
  └── ViApp  — Native macOS client, voice, staged context, Chibi companion
```

**Key capabilities:**
- Natural conversation with mode/depth routing (behavior-v2, A–J semantic matrix)
- Commitment capture, revision, and persistent follow-ups
- Job reviews with evidence-grounded analysis (no job-description-quote-for-applicant-claim)
- Push-to-talk voice (Faster-Whisper STT + Kokoro-82M TTS)
- Two-phase Mac action authorization with signed assertions
- Context sharing via clipboard and window OCR

### ViBot — Backend & control plane

ViBot is Violet's centralized backend — a Python 3.12 / aiohttp / pydantic service running on the v37 compute cluster. It handles conversation routing, memory gateway, continuity identity, commitments, follow-ups, dev handoffs, and Mac action orchestration. Every API route requires signed HS256 BFF assertions — a listening port is not authentication.

| Metric | Value |
|---|---|
| Language | Python 3.12, aiohttp, pydantic |
| Tests | 4,341 passed, 0 failed, 6 skipped |
| Turn pipeline | classify → evidence demand → CRS → memory → provider |
| Provider | Ollama qwen3.5:4b on dedicated inference node |

### ViApp — Native macOS client

ViApp is the native macOS companion app for Violet, built in Swift (SwiftUI + AppKit). It provides the conversational interface, voice I/O, staged context sharing, the Chibi companion, and governed Mac actions. The app authenticates through a signed BFF layer to ViBot.

| Metric | Value |
|---|---|
| Language | Swift (SwiftUI + AppKit) |
| Tests | 429 passed, 0 failures |
| Voice | Faster-Whisper STT + Kokoro-82M TTS |
| Signing | Ad-hoc signed, package verification PASS |

---

## Infrastructure

### V37 cluster

A three-node Proxmox cluster purpose-built for inference workloads, agentic execution loops, and deterministic pipeline staging.

| Node | Role | Key guests |
|---|---|---|
| v37-heavy | Compute / inference / development | Inference node, dev container |
| v37-medium | Durable service substrate | PostgreSQL, Redis, Neo4j, Infisical, MinIO |
| v37-light | CRS / MCP tooling plane | Context Retrieval System |

Network and security architecture uses layered access control (DoH, mesh VPN, tunneling, edge policy). Controlled access is non-negotiable.

### CRS — Context Retrieval System

The CRS provides signed-assertion historical evidence retrieval for ViBot. During turn processing, ViBot optionally queries CRS for historical evidence before generating a response. CRS ingests content into PostgreSQL and MinIO, exposing a signed-assertion API and an MCP SSE endpoint for local tool access.

- API with HS256 signed assertions (fail-closed 401 on unsigned requests)
- MCP SSE endpoint for agent-consumable tool access
- Wired into cluster health checks and verification pipeline

### Memorix — Memory system

Memorix is the durable memory system for Violet's continuity. It provides bounded memory retrieval, consent-gated remember/forget lifecycle, canonical tombstones with epoch (no resurrection), and Neo4j candidate search with Redis caching.

- Contract version 1.1.0 with 7 capabilities and fail-closed states
- MCP-SSE gateway adapter with HMAC canonical signing
- Database schema with RLS-force (continuity identities, consent, records, tombstones, receipts)
- Status: adapter implemented and tested, provisioning pending

### ARKSRRA — Deliberation framework (research)

ARKSRRA is a seven-stage action deliberation framework: hypotheses → findings → decisions → proposals → reviews → ratification → execution. Designed to route high-risk or uncertain evidence turns through multi-agent deliberation before execution, with a durable human authority gate ("Ratify") that the LLM cannot infer.

- Historical lineage: 162 commits with multi-modal DB adapters (PG, Mongo, Redis, Neo4j, ES, Weaviate)
- Status: reconciled as permanently disabled in production — case study only
- The typed gate refuses Action on every path, truthfully reporting unavailability

---

## Portfolio

### [vidoxlabs.dev](https://vidoxlabs.dev)

An evidence-focused engineering portfolio built with Astro and served as static files by Cloudflare Workers Static Assets. Every public claim traces to stable claim IDs, evidence, and source revisions. The `/research` data plane shows AI provider pricing and comparison data, powered by a separate Cloudflare Worker with D1 + KV.

- Production since 2026-09-12 (apex cutover from legacy hold point)
- Fail-closed content model with Zod validation and publication gates
- CI: GitHub Actions with full validation chain (typecheck, lint, test, content validation, route validation, Cloudflare validation, output scanner)

---

## Public repositories

<!-- BEGIN REPO TABLE -->
| Repository | Description | Language | Stars |
|---|---|---|---|
| [.github](https://github.com/Vidoxlabs/.github) | Organization profile and community health files | HTML | 0 |
| [videsign](https://github.com/Vidoxlabs/videsign) | Nocturne Museum design system — semantic token matrix, HTML preview fragments, MCP server | JavaScript | 0 |
| [vitools-public](https://github.com/Vidoxlabs/vitools-public) | Skills, plugins, and tooling for the Vidoxlabs AI ecosystem (public portfolio subset) | | 0 |
<!-- END REPO TABLE -->

_Auto-synced weekly via CI — see [sync workflow](https://github.com/Vidoxlabs/.github/blob/main/.github/workflows/sync-repo-table.yml)._

---

## Connect

- **Website:** [vidoxlabs.dev](https://vidoxlabs.dev)
- **Email:** admin@vidoxlabs.dev
- **Location:** United States

---

<sub>Vidoxlabs LLC — sovereign AI infrastructure, deterministic agent execution, local compute orchestration.</sub>
