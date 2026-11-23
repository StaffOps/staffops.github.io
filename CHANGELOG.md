# Changelog

All notable changes to this site are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and commit messages follow [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/).

The site is not versioned: there are no tags or releases. Every push to `main` deploys it to
<https://staffops.github.io/>.

## [Unreleased]

### Added

- Backstage `catalog-info.yaml` and technology tags.
- Grafana Plugins product page.
- Maturity Score Card and OTel Libs product pages; the OTel Libs page links its live sub-site and
  marks Go as Production.
- StaffOps portal: home page, product pages, principles and contributing guide.

### Changed

- Product pages reference Prometheus instead of VictoriaMetrics.
- The Helm Charts pages use the chart name `anomaly-detection` (formerly
  `staffops-anomaly-detection`).

### Removed

- Agent Definition and ChaiTops product pages.

### Fixed

- Deploys keep the sub-sites that other repos publish under the same GitHub Pages branch
  (`keep_files`, no `--clean`).

[Unreleased]: https://github.com/StaffOps/staffops.github.io/commits/main
