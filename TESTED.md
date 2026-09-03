# TESTED - v1.9.1 GitHub-ready package

Local validation completed:

- `node --check src/gc-core.js`
- `node --check src/mcp-server.js`
- `npm pack --dry-run` confirmed repo/package contents exclude `node_modules` and secrets
- Package has executable shebang in `src/mcp-server.js`
- Package has npm/npx binary entry: `genesys-cloud-org-audit-mcp -> ./src/mcp-server.js`
- Package keeps Node.js v1.9.0 tool catalogue plus GitHub/npx packaging support

Live Genesys Cloud tests must be performed from Claude Desktop with valid OAuth credentials.
