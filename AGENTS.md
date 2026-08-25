# Appskyline agent guide

Use Appskyline for App Store Optimization research across the iOS App Store,
macOS App Store, Google Play, and Microsoft Store.

## Connect

The plugin configures the OAuth-protected remote MCP server at
`https://mcp.appskyline.com/mcp`. Follow the host's OAuth prompt; never ask a
user to paste an access token into a conversation or configuration file.

## Operating rules

- Read `skills/aso-research/SKILL.md` before performing Appskyline work.
- Prefer read tools for discovery and analysis.
- Confirm with the user immediately before `add_keyword` or `delete_keyword`.
- Treat store, country, and language as explicit inputs. Do not infer a country
  from the user's current location.
- Report a missing rank as "not found in the scanned results", not as proof the
  app is absent from the store.

The public developer documentation is at
https://www.appskyline.com/developers/.
