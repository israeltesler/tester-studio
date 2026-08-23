# tester-studio

Repository for Cursor Cloud Agents and MCP integrations.

## Important: two different GitHub connections

Cursor has **two separate** GitHub setups. If GitHub does not show as connected, check both:

| What you see in Cursor | What it is | Where to configure |
| --- | --- | --- |
| **Integrations → GitHub connected** | OAuth app access for repos, Cloud Agents, PRs | [cursor.com/dashboard](https://cursor.com/dashboard) → Integrations |
| **Tools & MCP → github (green dot)** | GitHub MCP tools in chat/agent | `.cursor/mcp.json` + MCP dropdown in [cursor.com/agents](https://cursor.com/agents) |

`mcp.json` alone does **not** make the dashboard show "GitHub connected".

## Connect GitHub OAuth (dashboard)

1. Open [cursor.com/dashboard](https://cursor.com/dashboard) in an incognito window.
2. Sign in with the **same Cursor account** you use in the IDE.
3. Go to **Integrations** and click **Connect** next to GitHub.
4. Authorize as **israeltesler** and allow access to `tester-studio`.
5. Confirm the dashboard shows your GitHub username and repositories.

If Connect fails or shows the wrong account:

1. On GitHub: **Settings → Applications** → revoke Cursor under **Authorized OAuth Apps** and **Installed GitHub Apps** for every GitHub account you own.
2. Clear cookies for `cursor.com`, or use incognito.
3. Reconnect from the dashboard.

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
