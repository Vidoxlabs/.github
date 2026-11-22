# .github

Vidoxlabs organization profile repository. GitHub renders [`profile/README.md`](profile/README.md)
as the public landing page at [github.com/Vidoxlabs](https://github.com/Vidoxlabs).

The profile shows the current trajectory: the agent family (`seed`, `capillary`,
`myosotis`, `aestivation`, `drosera`, `trellis`, `bloom`) and the
[`videsign`](https://github.com/Vidoxlabs/videsign) design system. Everything public
follows the same rules: claims stay labeled and true, tests stay green, nothing
private goes in a public file.

## Contents

```
.github/
├── profile/README.md            Org landing page (rendered on github.com/Vidoxlabs)
├── ISSUE_TEMPLATE/               Org-wide issue forms (bug, feature, security)
├── PULL_REQUEST_TEMPLATE.md      Org-wide PR template
├── workflow-templates/           Reusable CI starter for new repos
├── .github/workflows/            Org-level automation
│   └── sync-repo-table.yml       Auto-updates the public repo table in profile/README.md
├── CONTRIBUTING.md               Contributor guide for public repos
├── SECURITY.md                   Vulnerability reporting policy
├── FUNDING.yml                   Sponsor button
├── CODEOWNERS                    Default review routing
└── README.md                      This file
```

Private governance authoring lives in
[`.github-private`](https://github.com/Vidoxlabs/.github-private).
