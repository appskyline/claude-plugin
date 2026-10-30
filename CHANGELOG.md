# Changelog

All notable changes to the AppSkyline agent plugin are documented here.

This project follows [Semantic Versioning](https://semver.org). The public
interface is the bundled skill's behaviour and the connector it configures:

- **MAJOR** — a skill is removed, or a host's MCP configuration changes in a
  way that breaks existing installs.
- **MINOR** — a new skill, host adapter, or newly supported connector tool.
- **PATCH** — wording, clarifications, and fixes that do not change what the
  plugin can do.

Every published change needs a version bump. Claude Code keys plugin updates on
the version string rather than the commit, so shipping new content under an
unchanged version silently leaves installed users on the old copy.

## 0.4.0

- `aso-research` 1.2.0: documents the connector's new `suggest_store_metadata`
  tool, which answers which tracked keywords belong in each app's title,
  subtitle, keyword field or short description with drafts that already fit
  each store's limits, and checks proposed wording. One call without an app
  covers every app in its main market.
- The skill now asks for concrete per-app text rather than a method, says to
  rewrite list-like drafts naturally and check them again, and to suggest a
  competitor-title word only when it describes the user's app, never a brand.
- The standard ASO report audits the listing with `suggest_store_metadata`.

## 0.3.1

- `aso-research` 1.1.1: the tool tables now say when to use each tool in the
  words users ask with, matching the connector's rewritten tool descriptions.
- Synced store metadata is documented as also answering whether the latest
  version is still in review or approved.
- Keyword volume is documented as Google web-search demand, a proxy for
  interest rather than a count of store searches.
- Rank history is documented as one row per stored search snapshot (tracked
  keywords are re-checked weekly), and new keywords need a country to be
  re-checked at all.
- Google Play reviews are documented as the last 7 days the Google Play API
  returns.
- Same fourteen connector tools; no new capability.

## 0.3.0

- Add a Codex plugin manifest that uses the same skills and OAuth MCP endpoint.
- Add repository-level `AGENTS.md` operating rules for coding agents and public
  discovery crawlers.

## 0.2.0

- Add the portable Agent Plugins 1.0 `plugin.json` and `mcp.json` package.
- Add a Gemini CLI extension manifest for Gallery discovery and direct install.
- Add an Antigravity-native adapter under the standard client-extension
  namespace `com.google.antigravity/`.
- Keep the portable, Claude, Gemini, and Antigravity packages on one canonical
  skill and production OAuth MCP endpoint.

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
