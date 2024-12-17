# Google Tasks MCP Server

This MCP server integrates with Google Tasks to allow listing, reading, and searching over files.

## Components

### Tools
### TODO UPDATE ME WITH TOOLS
- **search**
  - Search for tasks Google Tasks
  - Input: `query` (string): Search query
  - Returns file names and MIME types of matching files

### Resources

The server provides access to Google Tasks files:

### TODO UPDATE ME WITH RESOURCES
- **Files** (`gtasks:///<file_id>`)
  - Supports all file types
  - Google Workspace files are automatically exported:
    - Docs → Markdown
    - Sheets → CSV
    - Presentations → Plain text
    - Drawings → PNG
  - Other files are provided in their native format

## Getting started

1. [Create a new Google Cloud project](https://console.cloud.google.com/projectcreate)
2. [Enable the Google Tasks API](https://console.cloud.google.com/workspace-api/products)
3. [Configure an OAuth consent screen](https://console.cloud.google.com/apis/credentials/consent) ("internal" is fine for testing)
4. Add scopes `https://www.googleapis.com/auth/tasks`
5. [Create an OAuth Client ID](https://console.cloud.google.com/apis/credentials/oauthclient) for application type "Desktop App"
6. Download the JSON file of your client's OAuth keys
7. Rename the key file to `gcp-oauth.keys.json` and place into the root of this repo (i.e. `servers/gcp-oauth.keys.json`)

Make sure to build the server with either `npm run build` or `npm run watch`.

### Authentication

To authenticate and save credentials:

1. Run the server with the `auth` argument: `node ./dist auth`
2. This will open an authentication flow in your system browser
3. Complete the authentication process
4. Credentials will be saved in the root of this repo (i.e. `servers/.gdrive-server-credentials.json`)

### Usage with Desktop App

To integrate this server with the desktop app, add the following to your app's server configuration:

```json
{
  "mcpServers": {
    "gtasks": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-gtasks"
      ]
    }
  }
}
```

Locally you can test with:
```json
{
  "mcpServers": {
    "gtasks": {
      "command": "/opt/homebrew/bin/node",
      "args": [
        "/Users/zachcaceres/mcp/google-tasks/dist/index.js"
      ]
    }
  }
}
```

## License

This MCP server is licensed under the MIT License. This means you are free to use, modify, and distribute the software, subject to the terms and conditions of the MIT License. For more details, please see the LICENSE file in the project repository.
