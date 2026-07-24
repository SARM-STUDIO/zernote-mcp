# Installing the Zernote MCP Server

This guide is for an AI agent (e.g. Cline) setting up the Zernote MCP server for a user.

Zernote is a **remote** MCP server. There is **no package to install, no repository to clone, and no local process to run**. Setup is purely a matter of registering the remote endpoint in the MCP client config and letting the user complete a browser OAuth flow.

## Steps

1. **Add the remote server to the MCP settings.** Insert the following entry into the client's MCP servers configuration:

   ```json
   {
     "mcpServers": {
       "zernote": {
         "url": "https://zernote.com/mcp"
       }
     }
   }
   ```

2. **Do not ask the user for an API key or token.** Authentication is OAuth 2.0 (Authorization Code + PKCE) with Dynamic Client Registration. The client registers itself automatically and opens the OAuth flow in the user's browser.

3. **Prompt the user to complete authentication.** Tell the user to approve access in the browser window that opens, using their Zernote account (they can sign up or log in at https://zernote.com/login first if needed).

4. **Verify the connection.** Once authorized, call `list_folders` to confirm the server responds with the user's research projects.

## Notes

- Endpoint: `https://zernote.com/mcp`
- Transport: Streamable HTTP
- Auth: OAuth 2.0 + PKCE + Dynamic Client Registration (no static credentials)
- No environment variables are required.
- Full connection guide: https://zernote.com/connect-claude
