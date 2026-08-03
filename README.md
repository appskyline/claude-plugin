# AppSkyline plugin for Claude

App Store Optimization research inside Claude. This plugin bundles the
[AppSkyline connector](https://claude.ai/directory/connectors/appskyline) with a
skill that teaches Claude how to use it — keyword ranks and history across the
iOS App Store, macOS App Store, Google Play and Microsoft Store, search-volume
and difficulty lookups, store-listing audits, and competitor research.

## Requirements

An [AppSkyline](https://www.appskyline.com/) account with access to at least one
tracked app. The plugin connects to AppSkyline's hosted MCP server at
`https://mcp.appskyline.com/mcp` over OAuth; you authorize it on install and
your AppSkyline permissions decide which apps and organizations Claude can see.

No API key, and nothing to self-host.

## Install

In Claude Code:

```shell
/plugin marketplace add anthropics/claude-plugins-community
/plugin install appskyline@claude-community
```

Or install it from the plugin directory in claude.ai and Cowork.

## What you can ask

- "Where does my app rank for _dental software_ on the US App Store?"
- "Give me an ASO report for my app."
- "Which of my tracked keywords have real search volume?"
- "Audit my App Store metadata — am I wasting keyword-field characters?"
- "Who ranks above me for _restaurant pos_, and what does their listing say?"

## What it contains

- **`aso-research` skill** — how to sequence AppSkyline's tools into an ASO
  workflow: which identifier each tool takes, how to read a rank result
  honestly, when a single rank is noise, and how to batch the billable
  search-volume lookup.
- **AppSkyline MCP connector** — fourteen tools. Twelve read-only; two
  (`add_keyword`, `delete_keyword`) modify your tracked keywords and prompt for
  approval before running.

Two of the read tools render interactive cards — a keyword-rank card and an
app-overview card — in hosts that support MCP Apps.

## Privacy

The connector reads and writes AppSkyline data on your behalf, scoped to your
own account. See the [privacy policy](https://www.appskyline.com/en/privacy-policy/)
and the [connector documentation](https://www.appskyline.com/developers/#claude-mcp).

Revoke access at any time by removing the connector in Claude, or from your
AppSkyline account settings.

## Support

`info@appskyline.com` · [www.appskyline.com](https://www.appskyline.com/)

## Updates

Installed copies update themselves. Claude Code refreshes marketplaces shortly
after a session starts and prompts you to run `/reload-plugins` when a new
version has landed; otherwise it loads on your next launch.

See [CHANGELOG.md](./CHANGELOG.md) for what changed in each release.

## License

Apache-2.0. See [LICENSE](./LICENSE).
