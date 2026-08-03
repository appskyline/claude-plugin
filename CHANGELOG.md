# Changelog

All notable changes to the AppSkyline Claude plugin are documented here.

This project follows [Semantic Versioning](https://semver.org). The public
interface is the bundled skill's behaviour and the connector it configures:

- **MAJOR** — a skill is removed, or `.mcp.json` changes in a way that breaks
  existing installs.
- **MINOR** — a new skill, or coverage of newly added connector tools.
- **PATCH** — wording, clarifications, and fixes that do not change what the
  plugin can do.

Every published change needs a version bump. Claude Code keys plugin updates on
the version string rather than the commit, so shipping new content under an
unchanged version silently leaves installed users on the old copy.

## 0.1.2

- The `aso-research` skill is now published from the canonical
  [appskyline/skills](https://github.com/appskyline/skills) source, which also
  serves `npx skills add appskyline/skills` — one source, no drift.
- Skill frontmatter gains `license`, `compatibility` and `metadata`
  (author, version, repository) keys.
- No tool coverage changes.

## 0.1.1

- Document the `show_app_overview` MCP App tool that the shared production
  connector registers alongside the thirteen core tools.
- Clarify that both keyword writes require confirmation in the shared
  Claude/ChatGPT contract.

## 0.1.0

Initial release.

- `aso-research` skill covering AppSkyline's thirteen MCP tools: keyword ranks
  and history, search-volume lookups, store-listing metadata audits, engagement
  and review signals, and competitor research.
- AppSkyline connector configured against `https://mcp.appskyline.com/mcp`,
  authorized per user over OAuth.
