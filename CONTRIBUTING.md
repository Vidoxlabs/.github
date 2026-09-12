# Contributing to Vidoxlabs

Thank you for your interest in contributing to Vidoxlabs projects. This document covers the basics for external contributors.

## Public repositories

Vidoxlabs maintains a mix of public and private repositories. External contributions are welcome on public repos:

| Repository | Focus |
|---|---|
| [videsign](https://github.com/Vidoxlabs/videsign) | Design system, semantic tokens, MCP server |
| [vitools-public](https://github.com/Vidoxlabs/vitools-public) | Skills, plugins, and tooling (public subset) |

## Before you start

1. Check existing issues and PRs to avoid duplicates.
2. For new features, open an issue first to discuss the approach.
3. For bug fixes, include reproduction steps in your issue.

## Pull request process

1. Fork the repository and create a branch from `main`.
2. Make your changes. Follow existing code style and conventions.
3. Ensure CI passes (lint, tests, validation checks).
4. Keep PRs focused — one logical change per PR.
5. Use the PR template when submitting.

## Code standards

- **videsign:** All design tokens must follow the `category-role-variant-state` matrix defined in `DESIGN.md`. No arbitrary Tailwind values. Run `npm run lint` and `npm run tokens` before submitting.
- **vitools-public:** Follow the existing skill/plugin structure. Each tool should be self-documenting.

## Commit messages

Use conventional commit format:

```
type(scope): description

Optional body explaining what and why.
```

Types: `feat`, `fix`, `docs`, `refactor`, `ci`, `chore`, `test`

## Security

Do not include secrets, API keys, internal hostnames, or private network details in any contribution. See [SECURITY.md](SECURITY.md) for vulnerability reporting.

## License

All contributions to Vidoxlabs repositories are subject to the license in each repository. Unless otherwise stated, repositories are proprietary — see the repository's LICENSE file for terms.
