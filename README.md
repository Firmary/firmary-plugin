# Firmary

Connects your AI assistant to [Firmary](https://firmary.app) through Firmary's official remote [Model Context Protocol](https://modelcontextprotocol.io/) server, so it can work with your firm's clients, documents, invoices, tasks, time, and workflows — within your own Firmary permissions.

Works in Grok Bot, Cursor, Grok Build, and Claude Code.

## MCP

```json
{
  "mcpServers": {
    "firmary": {
      "type": "http",
      "url": "https://os.firmary.app/api/mcp"
    }
  }
}
```

Auth is OAuth 2.0 with PKCE and Dynamic Client Registration. Your client registers itself and prompts you to sign in to Firmary when the plugin connects — there is no API key, client ID, or secret to configure, and this repository contains no credentials or configuration placeholders. Requested scopes are `firmary.mcp` and `offline_access`.

## What agents can do

| Kind | What it covers |
| --- | --- |
| Discover | Search and describe the capabilities your firm has published, and check whether an action is permitted before running it |
| Read | Client, document, invoice, task, and time records, and reports |
| Change | Create and update records, send invoices, message clients, and start workflows |

Changes can have effects outside Firmary, such as an email to a client or a signature request. Your firm's AI app policy is checked on every call, and actions that need your approval or a fresh sign-in return an approval link instead of running.

The hosted server is the source of truth for tool names and schemas.

## Access and data

- Every call runs as the Firmary user who connected and is limited to what that user can already see and do in Firmary.
- Connecting gives the assistant access to the firm and client records that user can see, including client, document, invoice, task, and time data.
- Installing the plugin grants no access by itself. Access starts when you sign in and approve the connection.
- Your Firmary password is never shared with the assistant or its provider; the connection is an OAuth authorization.
- Disconnect at any time in Firmary under **Settings → AI apps**.

Firmary's [privacy policy](https://firmary.app/privacy), [terms](https://firmary.app/terms), and [security overview](https://firmary.app/security) apply.

## Docs

- Firmary: https://firmary.app
- Server URL: https://os.firmary.app/api/mcp

## License

MIT
