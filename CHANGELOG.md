# Changelog

## 1.2.1

- `firmary-os` (`plugins/`) is now the source of truth for both plugins; this repository mirrors it. Change them there first, then sync here.
- Added the `get-started` skill to the staff `firmary` plugin, matching `firmary-os` `plugins/firmary` 1.2.1.
- Renamed the client plugin `firmary-portal` to `pocketfirm` ("PocketFirm by Firmary", `plugins/pocketfirm`) and replaced "portal" with "PocketFirm" in user-facing text. The MCP server URL is unchanged. Reinstall with `claude plugin install pocketfirm@firmary`.

## 1.1.0

- Added the `pocketfirm` plugin ("PocketFirm by Firmary") for clients of a firm: the PocketFirm MCP connector (`https://portal.firmary.app/api/mcp`) and a client skill, in `plugins/pocketfirm`.
- Added a Claude Code marketplace (`.claude-plugin/marketplace.json`) listing both plugins.
- The staff `firmary` plugin is unchanged apart from its version.
- The client skill covers answering "I don't have this" on a document request, message attachments in the upload card, booking from open times, and searching PocketFirm help.

## 1.0.0

- Initial release: Firmary remote MCP connector and the Firmary skill.
