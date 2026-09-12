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
| [videsign](https://github.com/Vidoxlabs/videsign) | MCP server, design tokens, CI pipeline |
| [vitools-public](https://github.com/Vidoxlabs/vitools-public) | Skills, plugins, agent tooling |
| [.github](https://github.com/Vidoxlabs/.github) | Issue templates, org profile |

## Out of scope

- Vulnerabilities in private Vidoxlabs repositories (not publicly accessible)
- Internal infrastructure (cluster, network, services)
- Social engineering attacks
- DoS or rate-limiting issues without proven impact

## Disclosure

Vidoxlabs follows coordinated disclosure. Once a fix is released, we will credit the reporter
in the commit or advisory unless they prefer to remain anonymous.

## Security practices

- All API routes require signed assertions — a listening port is not authentication
- Secrets are never committed to repositories or copied to local machines
- CI pipelines validate against known vulnerability patterns
- Agent tool access is restricted via explicit allowlists (least privilege)
