# AppSkyline Agent Plugin

App Store Optimization research for agents. This open Agent Plugins 1.0
package bundles the [AppSkyline connector](https://mcp.appskyline.com/mcp)
with a skill that teaches compatible agents how to use it — keyword ranks and
history across the iOS App Store, macOS App Store, Google Play and Microsoft
Store, search-volume and difficulty lookups, store-listing audits, and
competitor research.

## Requirements

An [AppSkyline](https://www.appskyline.com/) account with access to at least one
tracked app. The plugin connects to AppSkyline's hosted MCP server at
`https://mcp.appskyline.com/mcp` over OAuth; you authorize it on install. Your
AppSkyline permissions decide which apps and organizations the host can see. No
API key is embedded, and there is nothing to self-host.

## Portable package

The repository root contains the vendor-neutral
[Agent Plugins](https://agent-plugins.org/) files:

- `plugin.json` — portable identity and metadata;
- `mcp.json` — the production Streamable HTTP connector; and
- `skills/aso-research/SKILL.md` — the portable workflow.

Compatible clients can install the repository directly or through their
marketplace. The same tree also contains the host adapters below; they all use
the same OAuth-protected endpoint and embed no credentials.

## Install in Claude

In Claude Code:

```shell
/plugin marketplace add anthropics/claude-plugins-community
/plugin install appskyline@claude-community
```

Or install it from the plugin directory in claude.ai and Cowork.

## Install in Gemini CLI

```shell
gemini extensions install https://github.com/appskyline/claude-plugin
```

The root `gemini-extension.json` maps the portable package to Gemini CLI's
native extension loader. Restart Gemini CLI after installation, then complete
the AppSkyline OAuth flow when the connector first authenticates.

## Install in Antigravity CLI

Antigravity's current native `plugin.json` schema conflicts with the portable
root manifest, so its adapter lives in the Agent Plugins client-extension
namespace `com.google.antigravity/`:

```shell
git clone https://github.com/appskyline/claude-plugin.git
agy plugin install ./claude-plugin/com.google.antigravity
```

The adapter's `mcp_config.json` uses Antigravity's `serverUrl` field and its
built-in OAuth DCR flow. This repository layout can become a direct portable
install when Antigravity adopts the vendor-neutral root schema.

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

Revoke access at any time by removing the connector in the host, or from your
AppSkyline account settings.

## Support

`info@appskyline.com` · [www.appskyline.com](https://www.appskyline.com/)

## Updates

Update behavior is host-specific. Claude Code refreshes marketplaces shortly
after a session starts and prompts you to run `/reload-plugins` when a new
version has landed. Update Gemini CLI with:

```shell
gemini extensions update appskyline
```

Reinstall the Antigravity adapter from the latest checkout.

See [CHANGELOG.md](./CHANGELOG.md) for what changed in each release.

## License

Apache-2.0. See [LICENSE](./LICENSE).
