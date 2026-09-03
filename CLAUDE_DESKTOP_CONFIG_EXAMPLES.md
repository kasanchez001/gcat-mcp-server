# Claude Desktop Configuration Examples

This package can be used from Claude Desktop in three ways.

## Option A - Local clone, most stable

Clone the GitHub repository locally, run `npm install`, then point Claude Desktop to the local `src/mcp-server.js` file.

```json
{
  "mcpServers": {
    "genesys-cloud-data-collector": {
      "command": "node",
      "args": [
        "C:\\MY_FILES\\AI_Learning\\DEV\\genesys-cloud-org-audit-mcp\\src\\mcp-server.js"
      ],
      "env": {
        "GC_REGION": "mypurecloud.com",
        "GC_SERVICE_CLIENT_ID": "<client ID>",
        "GC_SERVICE_CLIENT_SECRET": "<client secret>",
        "API_CONCURRENCY_LIMIT": "4"
      }
    }
  }
}
```

## Option B - Run directly from a public GitHub repo with npx

This works when the repository is public and the package has a valid `bin` entry in `package.json`.

Replace `YOUR_GITHUB_USERNAME` and `genesys-cloud-org-audit-mcp` with your actual owner and repository name.

```json
{
  "mcpServers": {
    "genesys-cloud-data-collector": {
      "command": "npx",
      "args": [
        "-y",
        "github:YOUR_GITHUB_USERNAME/genesys-cloud-org-audit-mcp"
      ],
      "env": {
        "GC_REGION": "mypurecloud.com",
        "GC_SERVICE_CLIENT_ID": "<client ID>",
        "GC_SERVICE_CLIENT_SECRET": "<client secret>",
        "API_CONCURRENCY_LIMIT": "4"
      }
    }
  }
}
```

You can also pin a branch, tag, or commit:

```json
"args": ["-y", "github:YOUR_GITHUB_USERNAME/genesys-cloud-org-audit-mcp#v1.9.1"]
```

## Option C - Published npm package

If you publish this repository to npm, use the package name instead of a GitHub source.

```json
{
  "mcpServers": {
    "genesys-cloud-data-collector": {
      "command": "npx",
      "args": [
        "-y",
        "genesys-cloud-org-audit-mcp"
      ],
      "env": {
        "GC_REGION": "mypurecloud.com",
        "GC_SERVICE_CLIENT_ID": "<client ID>",
        "GC_SERVICE_CLIENT_SECRET": "<client secret>",
        "API_CONCURRENCY_LIMIT": "4"
      }
    }
  }
}
```

## Important notes

- Do not commit real OAuth credentials to GitHub.
- Keep credentials in Claude Desktop config or a local `.env` only.
- For private GitHub repositories, `npx github:owner/repo` may require GitHub authentication on the workstation.
- Claude Desktop runs the package locally after npx downloads/installs it. It does not execute code inside GitHub remotely.
