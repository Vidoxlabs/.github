# Security Policy

## Reporting a vulnerability

If you have discovered a security vulnerability in a Vidoxlabs project, please report it
responsibly:

1. **Do not open a public issue** for security vulnerabilities.
2. Email **admin@vidoxlabs.dev** with a description of the vulnerability, reproduction steps,
   and potential impact.
3. Include the project name and relevant commit SHA if possible.
4. You will receive an acknowledgment within 48 hours.

## Scope

This policy applies to all public Vidoxlabs repositories:

| Repository | Attack surface |
|---|---|
| [`seed`](https://github.com/Vidoxlabs/seed) | Tool identity grammar, registry-entry validation, run contracts |
| [`capillary`](https://github.com/Vidoxlabs/capillary) | Provenance digests, bounded packets, relations ledger |
| [`myosotis`](https://github.com/Vidoxlabs/myosotis) | Consent records, structural forget, epoch-stamped projections |
| [`aestivation`](https://github.com/Vidoxlabs/aestivation) | Plan validation, verdict ledger, assembly gate |
| [`drosera`](https://github.com/Vidoxlabs/drosera) | Tool faces, skills, hooks, cookbook reference resolution |
| [`trellis`](https://github.com/Vidoxlabs/trellis) | Probe execution, verdict aggregation, family grid runner |
| [`bloom`](https://github.com/Vidoxlabs/bloom) | The team workspace harness |
| [`videsign`](https://github.com/Vidoxlabs/videsign) | MCP server, design tokens, CI pipeline |
| [`.github`](https://github.com/Vidoxlabs/.github) | Issue templates, org profile, org workflows |

## Out of scope

- Vulnerabilities in private Vidoxlabs repositories (not publicly accessible)
- Internal infrastructure (private; never described beyond that in public)
- Social engineering attacks
- DoS or rate-limiting issues without proven impact

## Disclosure

Vidoxlabs follows coordinated disclosure. Once a fix is released, we will credit the reporter
in the commit or advisory unless they prefer to remain anonymous.

## Security practices

- Fail-closed is the house rule: checks that throw fail, stale projections refuse to serve, storage without consent refuses admission
- Secrets are never committed to repositories or copied to local machines
- CI pipelines validate against known vulnerability patterns
- Tool effects carry their class (read / write / destructive / credential) on the face, and gated effects route the owner's decision
