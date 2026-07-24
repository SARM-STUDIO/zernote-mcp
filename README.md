# Zernote MCP Server

**Zernote** is a user research workspace to transcribe interviews and turn conversations into insights.

This repository documents how to connect to the **hosted Zernote MCP server**. It is a remote server — there is nothing to install or run locally. You connect your MCP client to the hosted endpoint and authenticate in your browser.

- **Server name:** `com.zernote/zernote`
- **Endpoint:** `https://zernote.com/mcp`
- **Transport:** Streamable HTTP
- **Auth:** OAuth 2.0 (Authorization Code + PKCE) with Dynamic Client Registration — no API keys needed
- **Docs:** https://zernote.com/connect-claude

## What it does

Zernote exposes your user-research data (projects, interviews, transcripts, and notes) to MCP-compatible clients so you can:

- List research projects/folders
- List interviews within a project
- Read an interview and its notes
- Read full interview transcripts
- Append notes back to an interview (with your approval)

## Connect

### Requirements

- An MCP client that supports **remote servers over Streamable HTTP with OAuth** (e.g. Claude, Cline, or any MCP client with remote-server support).
- A Zernote account at https://zernote.com. Sign up / log in at https://zernote.com/login before connecting.

### Add the server

Add a remote MCP server pointing at:

```
https://zernote.com/mcp
```

No API key or token is required. On first use, your client performs Dynamic Client Registration and opens an OAuth 2.0 flow in your browser. Approve access with your Zernote account and the client is connected.

#### Example client config

For clients that read a JSON config, add:

```json
{
  "mcpServers": {
    "zernote": {
      "url": "https://zernote.com/mcp"
    }
  }
}
```

Then trigger the connection; the OAuth browser flow completes authentication automatically.

## Tools

| Tool | Description |
| --- | --- |
| `list_folders` | List available research projects/folders. |
| `list_interviews` | List interviews inside a folder. |
| `get_interview` | Get an interview and its notes. |
| `get_transcript` | Get the full transcript of an interview. |
| `write_note` | Append a note to an interview (user-approved, tenant-scoped). |

## Support

Connection guide: https://zernote.com/connect-claude
