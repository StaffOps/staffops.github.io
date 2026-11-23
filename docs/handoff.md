# Handoff

Last updated: 2026-11-23 · Backstage docs-standard rollout · branch `main`

## State

staffops.github.io is the StaffOps public portal at <https://staffops.github.io/>, an MkDocs
Material site with product pages for AIgent Squad, Anomaly Detection, Grafana Plugins, Helm Charts,
Maturity Score Card and OTel Libs. Every push to `main` deploys it to `gh-pages`, which also hosts
sub-sites published by other repos. The Backstage catalog lists it as a `website` Component with
lifecycle `production`. The latest `Deploy docs` runs (2026-11-18) succeed. The last content change
was on 2026-08-17; the 2026-11-18 commits only add the Backstage catalog entry. There are no tags,
releases, open pull requests or open issues. No work is in progress.

## Done

- Backstage catalog and technology tags ([`a219170`](https://github.com/StaffOps/staffops.github.io/commit/a219170), [`4a246cb`](https://github.com/StaffOps/staffops.github.io/commit/4a246cb))
- VictoriaMetrics references changed to Prometheus ([`558d222`](https://github.com/StaffOps/staffops.github.io/commit/558d222))
- Grafana Plugins product page ([`fd39591`](https://github.com/StaffOps/staffops.github.io/commit/fd39591))
- Agent Definition and ChaiTops retired; Maturity Score Card and OTel Libs added ([`b36f3ff`](https://github.com/StaffOps/staffops.github.io/commit/b36f3ff), [`d129da9`](https://github.com/StaffOps/staffops.github.io/commit/d129da9))
- Deploys keep the sub-repo directories on `gh-pages` ([`182e31d`](https://github.com/StaffOps/staffops.github.io/commit/182e31d))

## In progress

- Nothing. Check with `gh pr list -R StaffOps/staffops.github.io`.

## Next steps

1. Review the product pages against the products' current state; content has not changed since
   2026-08-17 (suggested, inferred).
2. Expand the two-line README ("StartPage") into a short index (suggested, inferred).

## Decisions

No ADRs. Visible in the repo:

- One `gh-pages` branch shared by the portal and the product sub-sites, deployed with
  `keep_files: true` so neither overwrites the other.
- Each product page links to the product's own docs instead of duplicating them.

## Risks and open questions

- The catalog entity has no `backstage.io/techdocs-ref` annotation, so the Backstage Docs tab is
  absent for this repo, and the home page depends on a `custom_dir` template that TechDocs strips.
- CI builds without `--strict`, so broken links reach production unnoticed.
- This handoff is in the site nav, so it is published on the public portal.

## How to verify

```bash
gh run list -R StaffOps/staffops.github.io -L 5
docker run --rm -v "$PWD:/docs" -w /docs squidfunk/mkdocs-material:latest build --strict
curl -sI https://staffops.github.io/ | head -1
```
