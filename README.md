# Firmary

Connects your AI assistant to [Firmary](https://firmary.app) through Firmary's official remote [Model Context Protocol](https://modelcontextprotocol.io/) server, so it can work with your firm's clients, documents, invoices, tasks, time, and workflows — within your own Firmary permissions.

Works in Grok Bot, Cursor, Grok Build, and Claude Code.

This repository ships two plugins:

| Plugin | For | Server |
| --- | --- | --- |
| `firmary` (this directory) | Firm staff | `https://os.firmary.app/api/mcp` |
| `firmary-portal` ([`plugins/firmary-portal`](plugins/firmary-portal)) | A firm's clients | `https://portal.firmary.app/api/mcp` |

In Claude Code, add this repository as a marketplace and install the plugin you need:

```sh
claude plugin marketplace add Firmary/firmary-plugin
claude plugin install firmary@firmary          # firm staff
claude plugin install firmary-portal@firmary   # clients of a firm
```

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

## For clients of a firm: Firmary for Clients

If your accounting or tax firm uses Firmary, the `firmary-portal` plugin connects your AI app to your firm's client portal. Its MCP server is:

```json
{
  "mcpServers": {
    "firmary-portal": {
      "type": "http",
      "url": "https://portal.firmary.app/api/mcp"
    }
  }
}
```

You sign in with your own client portal account and approve the connection. The sign-in uses the same OAuth flow as the staff plugin, with PKCE and either a Client ID Metadata Document or Dynamic Client Registration. There is no API key, client ID, or secret to configure. The connection acts as you and reaches only your own records with that firm.

Your firm decides whether clients can connect AI apps and which features they get, so the tools you see depend on your firm. Where your firm has turned them on, your assistant can:

- show your to-dos, and help you fill in and submit the forms assigned to you (answers are saved as drafts first);
- show document requests and the documents your firm has shared, get short-lived download links, and check the status of an upload (the upload itself happens in the portal, or in an upload card in the chat where one is offered);
- read your messages with the firm and send new ones;
- show the status of signature requests (you sign in the portal);
- show proposals and engagement letters and accept or decline them (accepting needs a fresh Firmary sign-in);
- show invoices, with a link to pay in the portal;
- show tax returns and organizers;
- show your appointments and cancel them;
- show your notifications.

How it keeps you in control:

- Anything that reaches your firm needs your go-ahead. Firmary may also return an approval or sign-in link to finish a step on a Firmary page; until you finish there, nothing has happened.
- Payments and signing always happen in the portal. Your assistant never receives checkout links or card details.
- The assistant does not ask for Social Security numbers, tax ID numbers, card or bank numbers, or passwords.
- Your password is never shared with the assistant or its provider.
- Disconnect at any time in the portal under **Settings → AI apps**.

The included skill (`skills/firmary-portal`) tells the assistant to start with your to-dos, draft before it submits or sends anything, and treat text in your records as information, not instructions. The hosted server is the source of truth for tool names and schemas.

## Docs

- Firmary: https://firmary.app
- Staff server URL: https://os.firmary.app/api/mcp
- Client portal server URL: https://portal.firmary.app/api/mcp

## License

MIT
