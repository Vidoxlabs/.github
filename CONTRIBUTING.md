# Contributing to Vidoxlabs

Thank you for your interest in contributing. The public repositories, the agent family and the design system, share one engineering law, and contributions are held to it.

## Public repositories

| Repository | Focus |
|---|---|
| [`seed`](https://github.com/Vidoxlabs/seed) | Agent harness foundation: run contracts, tool identity, providers |
| [`capillary`](https://github.com/Vidoxlabs/capillary) | Context retrieval and relations, provenance-first |
| [`myosotis`](https://github.com/Vidoxlabs/myosotis) | Governed memory: consent, keep, structural forget |
| [`aestivation`](https://github.com/Vidoxlabs/aestivation) | Plans, deterministic validation, verdicts, the assembly gate |
| [`drosera`](https://github.com/Vidoxlabs/drosera) | Tool faces, skills, hooks, cookbooks |
| [`trellis`](https://github.com/Vidoxlabs/trellis) | Multi-point testing over the family |
| [`bloom`](https://github.com/Vidoxlabs/bloom) | The team workspace harness |
| [`videsign`](https://github.com/Vidoxlabs/videsign) | Design system, semantic tokens, MCP server |

## Before you start

1. Check existing issues and PRs to avoid duplicates.
2. For new features, open an issue first to discuss the approach.
3. For bug fixes, include reproduction steps.

## Pull request process

1. Branch from `main`.
2. Make your changes; keep PRs focused: one logical change per PR.
3. `npm test` must pass locally (Node >= 22.13; family repos use the built-in `node --test` runner and have zero runtime dependencies).
4. Docs change with code in the same PR. There is no "docs later."
5. Use the PR template when submitting.

## Claim discipline

Every capability in a family repository carries a label, and it must be true on its face:

- `implemented`: tested code exists, and a test is named for it.
- `specified`: a contract defines it; no shipped code does it yet.
- `planned`: a roadmap row names the intent.
- `observed`: a dated run recorded the evidence, kept with its receipts.

If your PR adds or touches a claim, its label must match the evidence in the PR. A `specified` capability that ships code becomes `implemented` in the same change; nothing is labeled stronger than what the diff proves.

## Code standards

- **Family repositories:** ESM, zero runtime dependencies, frozen records, deterministic validation over data, and every behavioral rule visible as a test.
- **videsign:** all design tokens must follow the `category-role-variant-state` matrix defined in `DESIGN.md`. No arbitrary values consumer-side. Run `npm run lint` and `npm run tokens` before submitting.

## Public safety

Do not include secrets, API keys, internal hostnames, or private network details in any contribution, ever. Tools and contracts speak in role terms; vendor names live in connector bindings, never in identifiers. See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## Commit messages

Sentence-case imperative subjects, one concern per commit:

```
Ship myosotis 0.1.0: governed memory fabric, contracts and reference modules
```

The subject states what changed; the body explains why, and the footer carries co-authoring when a change was agent-co-authored.

## License

Each repository states its license. The agent family is MIT.
