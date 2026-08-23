# tester-studio

Repository for Cursor Cloud Agents and MCP integrations.

## GitHub MCP (israeltesler)

This project connects the official [GitHub MCP server](https://github.com/github/github-mcp-server) to the `israeltesler` GitHub account.

### 1. Create a GitHub Personal Access Token

1. Open [GitHub token settings](https://github.com/settings/personal-access-tokens/new).
2. Sign in as **israeltesler**.
3. Create a fine-grained token (recommended) or classic token with the scopes you need, for example:
   - `repo`
   - `read:org`
   - `read:user`
4. Copy the token. You will not be able to see it again.

### 2. Cursor IDE (local)

1. Set the token in your shell profile:

```bash
export GITHUB_PERSONAL_ACCESS_TOKEN="ghp_..."
```

2. Restart Cursor.
3. Open **Settings → Tools & MCP** and confirm the `github` server is enabled.
4. Test in chat: `List my GitHub repositories`.

The project config lives in `.cursor/mcp.json`.

### 3. Cursor Cloud Agents

Cloud Agents do not read secrets from your local shell. Configure GitHub MCP in the dashboard:

1. Open [cursor.com/agents](https://cursor.com/agents).
2. In the MCP dropdown, add or enable the **GitHub** server.
3. Paste the Personal Access Token for **israeltesler** when prompted.
4. Start a new Cloud Agent on `israeltesler/tester-studio` and enable the GitHub MCP tools for that run.

For team-wide shared MCP servers, admins can configure them under [Dashboard → Integrations & MCP](https://cursor.com/dashboard/integrations).

### Verify

After setup, ask the agent:

```text
List repositories for user israeltesler
```

If GitHub MCP is connected correctly, the agent can read your GitHub data through MCP tools.
