<p align="center">
  <img src="assets/logo-full.png" alt="Astravue" width="300">
</p>

<p align="center">
  <a href="https://astravue.com"><img src="https://img.shields.io/badge/Website-astravue.com-1f8f75?style=flat&labelColor=555" alt="Website"></a>
  <a href="https://docs.astravue.com"><img src="https://img.shields.io/badge/Docs-docs.astravue.com-0ea5e9?style=flat&labelColor=555" alt="Documentation"></a>
  <a href="https://github.com/AstravueOrg/astravue-mcp-server/releases/latest"><img src="https://img.shields.io/github/v/release/AstravueOrg/astravue-mcp-server?label=release&style=flat&labelColor=555" alt="Latest release"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-7cb342?style=flat&labelColor=555" alt="Apache License 2.0"></a>
  <a href="https://registry.modelcontextprotocol.io/?q=astravue"><img src="https://img.shields.io/badge/MCP%20Registry-official-2563eb?style=flat&labelColor=555" alt="Official MCP Registry"></a>
  <a href="https://www.pulsemcp.com/servers/astravue"><img src="https://img.shields.io/badge/PulseMCP-official-7c3aed?style=flat&labelColor=555" alt="Official on PulseMCP"></a>
  <a href="https://vibehackers.io/mcp/astravue-mcp"><img src="https://img.shields.io/badge/Vibehackers-listed-111827?style=flat&labelColor=555" alt="Listed on Vibehackers"></a>
  <a href="https://mcpmarket.com/server/astravue"><img src="https://img.shields.io/badge/MCP%20Market-listed-0f766e?style=flat&labelColor=555" alt="Listed on MCP Market"></a>
  <a href="https://glama.ai/mcp/servers?query=astravue"><img src="https://img.shields.io/badge/Glama.ai-listed-0ea5e9?style=flat&labelColor=555" alt="Listed on Glama.ai"></a>
  <a href="https://claude.ai/directory/astravue"><img src="https://img.shields.io/badge/Claude%20Connector-verified-d97757?style=flat&labelColor=555" alt="Verified Claude Connector"></a>
  <a href=".claude-plugin/marketplace.json"><img src="https://img.shields.io/badge/Claude%20Code-plugin-d97757?style=flat&labelColor=555" alt="Claude Code plugin"></a>
</p>

<p align="center">
  <a href="https://cursor.com/en/install-mcp?name=astravue-mcp&config=eyJ1cmwiOiJodHRwczovL2FwaS5hc3RyYXZ1ZS5jb20vbWNwIn0%3D"><img src="https://cursor.com/deeplink/mcp-install-dark.svg" alt="Install MCP Server in Cursor"></a>
</p>

# Astravue MCP Server

<p align="center">
  <a href="https://github.com/AstravueOrg/astravue-mcp-server/releases/download/v1.0.2/mcp_launch.mp4">
    <img src="assets/mcp_launch.gif" alt="Astravue MCP demo" width="720">
  </a>
  <br>
  <em>Click the image to download the full demo (with audio).</em>
</p>

The Astravue MCP Server is a cloud-based bridge between your [Astravue](https://astravue.com) workspace and compatible AI tools. Once configured, it enables those tools to interact with your spaces, projects, tasks, time entries, and custom fields in real time. All actions are authenticated via OAuth 2.0 and respect the user's existing access controls.

With the Astravue MCP Server, you can:

* **Search and browse** spaces, projects, and tasks without switching tools.
* **Create and update** tasks, subtasks, checklists, and comments through natural language.
* **Track time** with live timers or manual entries and generate timesheet reports.
* **Manage custom fields** including dropdowns, dates, currencies, and more.
* **Automate workflows** like sprint planning, status reporting, and bulk task updates.

It's designed for project managers, developers, and teams who use AI-powered IDEs or assistants and want to manage work without context switching.

Learn more at **[astravue.com/mcp-server](https://astravue.com/mcp-server/)**. Setup steps for each client are [below](#setup-instructions); full product documentation lives at **[docs.astravue.com](https://docs.astravue.com)**.

Astravue is a verified and reviewed integration in the **[Claude Connectors Directory](https://claude.ai/directory/astravue)**.

---

## Supported Clients

All clients connect to the same endpoint: `https://api.astravue.com/mcp`
You will be asked to sign in to Astravue in your browser the first time you connect.

| Client | Docs | Transport |
| :----- | :--- | :-------- |
| [Claude Code](#claude-code) | [MCP setup](https://code.claude.com/docs/en/mcp) | Streamable HTTP |
| [Claude Desktop](#claude-desktop) | [Connectors Directory](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities) | Streamable HTTP |
| [Claude.ai (Web)](#claudeai-web) | [Connectors Directory](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities) | Streamable HTTP |
| [Claude Mobile](#claude-mobile-ios--android) | [Connectors Directory](https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-s-capabilities) | Streamable HTTP |
| [Cursor](#cursor) | [MCP setup](https://cursor.com/docs/context/mcp) | Streamable HTTP |
| [VS Code](#vs-code) | [MCP setup](https://code.visualstudio.com/docs/agents/reference/mcp-configuration) | Streamable HTTP |
| [Devin Desktop (Windsurf)](#devin-desktop-windsurf) | [MCP setup](https://docs.devin.ai/desktop/cascade/mcp) | Streamable HTTP |
| [Cline](#cline) | [MCP setup](https://docs.cline.bot/mcp/adding-and-configuring-servers) | Streamable HTTP |
| [JetBrains IDEs](#jetbrains-intellij-webstorm-pycharm-etc) | [MCP setup](https://www.jetbrains.com/help/ai-assistant/configure-an-mcp-server.html) | Streamable HTTP |
| [Google Antigravity](#google-antigravity) | [MCP setup](https://antigravity.google/docs/mcp/) | Streamable HTTP |
| [Kiro](#kiro) | [MCP setup](https://kiro.dev/docs/mcp/configuration/) | Streamable HTTP |
| [Zed](#zed) | [MCP setup](https://zed.dev/docs/ai/mcp) | Streamable HTTP |
| [Codex](#codex) | [MCP setup](https://learn.chatgpt.com/docs/extend/mcp) | Streamable HTTP |
| [GitHub Copilot CLI](#github-copilot-cli) | [MCP setup](https://docs.github.com/en/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers) | Streamable HTTP |
| [Gemini CLI](#gemini-cli) | [MCP setup](https://geminicli.com/docs/tools/mcp-server/) | Streamable HTTP |
| [ChatGPT](#chatgpt) | [Custom MCP servers](https://help.openai.com/en/articles/12584461-connecting-custom-mcp-servers-in-chatgpt) | Streamable HTTP |
| [Perplexity](#perplexity) | [Custom remote connectors](https://www.perplexity.ai/help-center/en/articles/13915507-adding-custom-remote-connectors) | Streamable HTTP |
| [Grok](#grok) | [Connectors](https://docs.x.ai/grok/connectors) | Streamable HTTP |
| [Muse](#muse) | [Connectors](https://www.meta.com/help/artificial-intelligence/1687253048996149/) | Streamable HTTP |
| [Zoho Zia Agents](#zoho-zia-agents) | [Zia Agents](https://www.zoho.com/agents/) | Streamable HTTP |
| [Mistral Vibe (Le Chat)](#mistral-vibe-le-chat) | Coming soon | — |

---

## Setup Instructions

### Claude Connectors Directory (recommended)

Astravue App is a verified connector across Claude.ai, Claude Desktop, Claude Mobile, Claude Code, and Cowork.

1. In Claude.ai or Claude Desktop, go to **Customize → Connectors**.
2. Click **+**, browse the Connectors Directory, and search for **Astravue App**.
3. Select **Astravue App**, click **Connect**, then sign in to Astravue and click **Allow Access**.
4. Start a new conversation and enable Astravue App from the **+ → Connectors** menu.

When Claude Code is signed in with your Claude.ai subscription, the connector is available automatically. Run `/mcp` to confirm it is connected. Claude Code sessions using an API key, Amazon Bedrock or Google Cloud do not load Claude.ai connectors; use the direct connection command below instead.

---

### Claude Code

The Connectors Directory provides the verified MCP connection. For eight guided project-management workflows as well, install the Astravue plugin. A direct MCP connection remains available for API-key, Amazon Bedrock, Google Cloud and custom setups.

#### Option A — Install as a Claude Code plugin (recommended)

The plugin bundles the MCP server with eight pre-built skills that automate common project management workflows. It is listed in Anthropic's community plugin marketplace.

Inside Claude Code, run:

```text
/plugin marketplace add anthropics/claude-plugins-community
/plugin install astravue@claude-community
/reload-plugins
```

In a session, `/plugin install` opens the plugin's details first. Choose an install scope there to finish.

Alternatively, install directly from this repository:

```text
/plugin marketplace add AstravueOrg/astravue-mcp-server
/plugin install astravue@astravue
/reload-plugins
```

After install, run `/mcp` to confirm **astravue** is connected, then open `/plugin` and switch to the **Installed** tab to view the bundled skills.

See Anthropic's [plugin discovery docs](https://code.claude.com/docs/en/discover-plugins) for installation scopes (user, project, local).

#### Option B — Install only the MCP server

If you only want the MCP server without the bundled skills, run:

```bash
claude mcp add --transport http astravue https://api.astravue.com/mcp
```

Start Claude Code and run `/mcp`. Select **astravue**, choose **Authenticate**, then sign in with your Astravue account and click **Allow Access**. Run `/mcp` again to confirm **astravue** is connected.

<details>
<summary>Share connection across a project team</summary>

Add the `--scope project` flag to create a `.mcp.json` file in your project root:

```bash
claude mcp add --transport http --scope project astravue https://api.astravue.com/mcp
```

Commit `.mcp.json` to your repository so teammates automatically get the connection.

</details>

---

### Claude Desktop

1. Go to **Customize → Connectors** in Claude Desktop.
2. Click **+**, browse the directory, and search for **Astravue App**.
3. Select **Astravue App**, click **Connect**, then sign in and approve access.

---

### Claude.ai (Web)

1. Go to [claude.ai](https://claude.ai) → **Customize → Connectors**.
2. Click **+**, browse the directory, and search for **Astravue App**.
3. Select **Astravue App**, click **Connect**, then sign in and approve access.

---

### Claude Mobile (iOS / Android)

Claude Mobile uses the same connector ecosystem as Claude.ai. Connect Astravue App from the mobile Connectors Directory, or connect it once on Claude.ai or Claude Desktop and use the same Claude account on mobile.

---

### Cursor

1. Open `~/.cursor/mcp.json` (create it if it doesn't exist). You can also manage MCP servers from Cursor's **Customize** page.
2. Add the following configuration and save the file:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

3. When Cursor asks, sign in with your Astravue account and click **Allow Access**.

<details>
<summary>Project-level configuration</summary>

Create a `.cursor/mcp.json` file in your project root with the same config above. This scopes the connection to that project only.

</details>

---

### VS Code

1. Add a `.mcp.json` file to your workspace root:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "type": "http",
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

2. Open the Command Palette (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows), run **MCP: List Servers**, select `astravue-mcp` and choose **Start Server**.
3. Sign in with your Astravue account in the browser and click **Allow Access**.

<details>
<summary>User-level configuration (all workspaces)</summary>

Add the same `mcpServers` entry to `~/.copilot/mcp-config.json` (or `$COPILOT_HOME/mcp-config.json`). GitHub Copilot CLI reads the same file.

</details>

---

### Devin Desktop (Windsurf)

1. Open the Agents window, click **Customize** in the agent sidebar, then open the **MCPs** tab.
2. Open the MCP config file and add:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

   * **User config:** `~/.config/devin/mcp_config.json` (Windows: `%APPDATA%\devin\mcp_config.json`)
   * **One project only:** `.devin/mcp_config.json` in the project root

3. When `astravue-mcp` shows **Needs authentication**, click **Authenticate**, then sign in with your Astravue account and click **Allow Access**.

<details>
<summary>Devin CLI</summary>

```bash
devin mcp add -s user astravue-mcp https://api.astravue.com/mcp
devin mcp login astravue-mcp
```

The login command opens your browser to sign in to Astravue.

</details>

---

### Cline

1. Click the **MCP Servers** icon (stacked servers) in Cline's top toolbar, open the **Configure** tab and click **Configure MCP Servers**.
2. Open the **Remote Servers** tab and fill in:
   * **Server Name:** `astravue-mcp`
   * **Server URL:** `https://api.astravue.com/mcp`
   * **Transport Type:** `Streamable HTTP`
3. Click **Add Server**. When Cline asks, sign in with your Astravue account and click **Allow Access**.

<details>
<summary>Manual JSON configuration</summary>

Click **Configure MCP Servers** to open `cline_mcp_settings.json` and add:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "type": "streamableHttp",
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

Set `type` explicitly. Without it, Cline uses the legacy SSE transport.

</details>

---

### JetBrains (IntelliJ, WebStorm, PyCharm, etc.)

1. Go to **Settings | Tools | AI Assistant | Model Context Protocol (MCP)**.
2. Click **Add**. In the **New MCP Server** dialog, paste:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

3. Click **OK**, then **Apply**. When AI Assistant asks, sign in with your Astravue account and click **Allow Access**.

---

### Google Antigravity

1. In the agent side panel, click **…** at the top and select **MCP Servers**. Click **Manage MCP Servers**, then **View raw config**.
2. This opens `~/.gemini/config/mcp_config.json`. Add the following and save the file:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "serverUrl": "https://api.astravue.com/mcp"
    }
  }
}
```

3. Antigravity runs the Astravue sign-in for you. Sign in with your Astravue account and click **Allow Access**. If Antigravity asks for an authorization code, copy it from the browser, paste it into **Enter authorization code** and click **Submit**.

<details>
<summary>Project-level configuration and Antigravity CLI</summary>

To scope Astravue to one project, put the same config in `.agents/mcp_config.json` in the project root. Antigravity CLI reads the same files; type `/mcp` in the CLI to manage servers.

</details>

---

### Kiro

1. Open the Command Palette (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows) and run **Kiro: Open user MCP config (JSON)**. This opens `~/.kiro/settings/mcp.json`.
2. Add the following and save the file:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

3. Kiro opens the Astravue sign-in page in your browser. Sign in with your Astravue account and click **Allow Access**.

<details>
<summary>Workspace configuration</summary>

Run **Kiro: Open workspace MCP config (JSON)** and add the same config to `.kiro/settings/mcp.json`. It applies to the current workspace only and overrides the user config.

</details>

---

### Zed

1. Go to **Settings → AI → MCP Servers**, click **Add Server**, then **Add Remote Server**.
2. Zed saves the server to your `settings.json`:

```json
{
  "context_servers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

   Don't add an `Authorization` header. Without one, Zed signs you in with OAuth.

3. When Zed asks, sign in with your Astravue account and click **Allow Access**. A green dot next to `astravue-mcp` means it is active.

---

### Codex

Works in the Codex CLI, the Codex IDE extension, and the ChatGPT desktop app — they share `~/.codex/config.toml`.

1. Add the server:

```bash
codex mcp add astravue-mcp --url https://api.astravue.com/mcp
```

2. Sign in:

```bash
codex mcp login astravue-mcp
```

Your browser will open — sign in with your Astravue account and click **Allow Access**.

3. Run `/mcp` in Codex to confirm `astravue-mcp` is connected.

<details>
<summary>Configure in config.toml instead</summary>

Add this to `~/.codex/config.toml`, or to `.codex/config.toml` in a trusted project to scope it to that project:

```toml
[mcp_servers.astravue-mcp]
url = "https://api.astravue.com/mcp"
```

Then run `codex mcp login astravue-mcp`.

</details>

---

### GitHub Copilot CLI

Run:

```bash
copilot mcp add --transport http astravue-mcp https://api.astravue.com/mcp
```

<details>
<summary>Manual JSON configuration</summary>

Add this to `~/.copilot/mcp-config.json`:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "type": "http",
      "url": "https://api.astravue.com/mcp",
      "tools": ["*"]
    }
  }
}
```

</details>

---

### Gemini CLI

> On 18 June 2026 Google replaced Gemini CLI with Antigravity CLI for unpaid and Google One users. If that applies to you, follow the [Google Antigravity](#google-antigravity) steps.

1. Install the Astravue extension from this repository:

```bash
gemini extensions install https://github.com/AstravueOrg/astravue-mcp-server
```

2. Start Gemini CLI and sign in:

```text
/mcp auth astravue
```

Your browser will open — sign in with your Astravue account and click **Allow Access**.

<details>
<summary>Manual configuration (settings.json)</summary>

Add this to `~/.gemini/settings.json`, then run `/mcp auth astravue-mcp`:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "httpUrl": "https://api.astravue.com/mcp"
    }
  }
}
```

</details>

---

### ChatGPT

> Full custom MCP support is on ChatGPT **Business** and **Enterprise/Edu**. **Pro** users can connect custom MCP servers with read and fetch permissions. On Business and Enterprise/Edu, workspace admins and owners create the plugin and publish it to the workspace. Custom MCP servers work on chatgpt.com only, not in the mobile apps.

1. Go to **Plugins**, select the **+** button, then **Add custom MCP server**.
2. Enter the name `Astravue`.
3. Under **Connection**, enter `https://api.astravue.com/mcp`.
4. Set authentication to **OAuth**.
5. Select **I understand and want to continue**, then **Create as a plugin**.
6. Sign in with your Astravue account and click **Allow Access**.
7. In a chat, type **@** in the prompt box and select **Astravue**.

---

### Perplexity

1. Open **Plugins** in the sidebar and select **Add custom**.
2. Enter the name `Astravue` and the MCP server URL `https://api.astravue.com/mcp`.
3. Under **Advanced**, set **Authentication** to **OAuth** and **Transport** to **Streamable HTTP**. Select **I understand custom connectors can introduce risks**, then click **Add**.
4. Sign in with your Astravue account and click **Allow Access**.
5. Ask Perplexity something Astravue can do, for example *"show my open tasks"*.

In an organization, an administrator must first turn on **Allow members to add custom connectors**.

<details>
<summary>Connected, but no tools are listed</summary>

Perplexity does not always list the tools of a custom connector. The connection still works — ask for Astravue actions directly in chat, such as *"list my Astravue spaces"*.

</details>

---

### Grok

1. Go to [grok.com/connectors](https://grok.com/connectors) and click **New Connector**.
2. Select **Custom** and enter the MCP server URL `https://api.astravue.com/mcp`.
3. Sign in with your Astravue account and click **Allow Access**.
4. Grok finds the Astravue tools and makes them available in your conversations. Ask, for example, *"show my overdue tasks"*.

On **Grok Business** and **Enterprise**, a team admin adds the connector first: in [console.x.ai](https://console.x.ai), select your team, go to **Grok Business → Connectors**, click **+ Add Connector**, select **Other**, and enter `https://api.astravue.com/mcp`. Team members then connect their own Astravue account at grok.com/connectors.

---

### Muse

1. In a Muse chat, ask Muse to create a custom connector for Astravue with the MCP server URL `https://api.astravue.com/mcp`. Muse guides you through the setup.
2. When Muse asks, sign in with your Astravue account and click **Allow Access**.
3. In Muse settings, choose whether Muse can only read your Astravue data or also take actions. You can disconnect Astravue there at any time.

---

### Zoho Zia Agents

1. In Zia Agents, go to **Tools → MCP Servers**, open the **Create** menu and select **MCP Server**.
2. Enter the connection details:
   * **Server Name:** `Astravue`
   * **Server URL:** `https://api.astravue.com/mcp`
   * **Description:** `Astravue projects, tasks and time tracking`
   * **Authentication Type:** `OAuth2.0`
3. Click **Validate & Discover Tools**. When Zia asks, sign in with your Astravue account and click **Allow Access**. Then click **Save Server**.
4. Open your agent and, under **Connectors**, click **+ Connect MCP Server** and choose **Astravue**. Use **Test Agent** to try it.

---

### Mistral Vibe (Le Chat)

Coming soon.

---

### Other MCP Clients

For any client that supports **Streamable HTTP + OAuth 2.0**:

| Setting | Value |
| :------ | :---- |
| Server URL | `https://api.astravue.com/mcp` |
| Transport | Streamable HTTP |
| Authentication | OAuth 2.0 (Authorization Code + PKCE) |

<details>
<summary>SSE-only clients (mcp-remote bridge)</summary>

If your client only supports SSE transport, run:

```bash
npx -y mcp-remote@latest https://api.astravue.com/mcp
```

Point your client to the local mcp-remote process instead of the Astravue URL.

</details>

---

## How It Works

Astravue MCP exposes workspace operations as tools that AI assistants can call. Each tool performs a specific action in your Astravue workspace such as creating projects, managing tasks, logging time, or retrieving reports.

When an AI assistant receives a request, it selects the appropriate tool based on the user's prompt and executes it with the required parameters.

> **Authentication:** All tools require an active authenticated session. If a tool call fails with `401 Unauthorized`, reconnect your AI client to refresh your session.

> **Destructive actions:** Some tools perform destructive actions such as deleting tasks, projects, or spaces. Most AI clients require confirmation before executing these operations. Always review actions before approving them.

---

## Permissions

Astravue MCP respects the same role-based access control as the Astravue web app. Every tool call is executed as your authenticated user with your existing permissions. You cannot access or modify anything through MCP that you cannot access in the app.

### Organization Roles

| Role | MCP Access |
| :--- | :--------- |
| **Account Admin** | Full access to all spaces, projects, and tasks across the organization |
| **Admin** | Full access to all spaces, projects, and tasks across the organization |
| **Manager** | Can manage spaces and projects they are a member of |
| **Member** | Can read and write within spaces and projects they belong to |
| **Guest** | Read-only. Cannot perform any write operations through MCP |

### Space-Level Permissions

| Action | Required Role |
| :----- | :------------ |
| List spaces, view space details | Space Member |
| Create, update, delete a space | Org Admin or Manager |

### Project-Level Permissions

| Action | Required Role |
| :----- | :------------ |
| List tasks, view project details | Project Member |
| Create or update tasks | Project Member |
| Add project members, delete project | Project Admin |
| Manage custom fields, statuses | Project Admin |

### Task-Level Permissions

| Action | Required Role |
| :----- | :------------ |
| View tasks, comments, checklists | Project Member |
| Create tasks, add comments, log time | Project Member |
| Delete a task | Task Owner, Task Creator, or Project Admin |
| Delete a comment | Comment Creator or Org Admin |

> If a tool call returns `403 Access Denied`, it means your account does not have the required role for that action. Contact your workspace admin to update your permissions.

---

## Example Workflow

A user asks an AI assistant:

> *"Create a new sprint called Sprint 5 and add tasks for login, payments, and API docs."*

The AI assistant may execute these tools:

1. `astravue_create_project` — creates the Sprint 5 project
2. `astravue_bulk_create_tasks` — creates the three tasks in one call
3. `astravue_update_task` — sets priorities or due dates as needed

This allows complex project setup to be completed from a single conversation.

---

## Available Tools

The Astravue MCP Server provides **88 tools** across the following categories.

<details>
<summary><strong>Spaces</strong> (5 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_spaces` | Lists all spaces in your organization | "Show me all my spaces" |
| `astravue_get_space` | Gets details of a specific space including its projects | "What projects are in the Design space?" |
| `astravue_create_space` | Creates a new space | "Create a space called Product Development" |
| `astravue_update_space` | Updates a space name or settings | "Rename the Marketing space to Growth" |
| `astravue_delete_space` | Permanently deletes a space and all its contents | "Delete the archived Test space" |

</details>

<details>
<summary><strong>Projects</strong> (6 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_projects` | Lists all projects within a space | "List all projects in the Engineering space" |
| `astravue_get_project` | Gets full details of a specific project | "What's the current status of Sprint 3?" |
| `astravue_create_project` | Creates a new project inside a space | "Create a project called Q2 Roadmap in the Product space" |
| `astravue_update_project` | Updates a project's name, status, priority, or health | "Mark Sprint 1 as completed" |
| `astravue_delete_project` | Permanently deletes a project and all its tasks | "Delete the duplicate Onboarding project" |
| `astravue_add_project_member` | Adds an existing workspace member to a project | "Add john@company.com to the Backend project" |

</details>

<details>
<summary><strong>Tasks</strong> (15 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_project_tasks` | Lists all tasks within a project | "Show all open tasks in Sprint 2" |
| `astravue_get_task` | Gets full task details | "What's the status of the login bug task?" |
| `astravue_find_tasks` | Searches tasks by keyword across all projects | "Find all tasks related to payments" |
| `astravue_create_task` | Creates a task in a project | "Create a high priority task: Fix authentication bug" |
| `astravue_update_task` | Updates task fields | "Assign the API docs task to Sarah" |
| `astravue_delete_task` | Deletes a task | "Delete the duplicate checkout task" |
| `astravue_move_task` | Moves a task from one project to another | "Move the login task from Sprint 1 to Sprint 2" |
| `astravue_duplicate_task` | Creates a copy of an existing task | "Duplicate the API integration task with all subtasks" |
| `astravue_create_personal_task` | Creates a personal task not tied to any project | "Remind me to review the design doc by Friday" |
| `astravue_update_personal_task` | Updates a personal task's title, status, priority, or dates | "Move my design doc review to next Monday" |
| `astravue_delete_personal_task` | Moves a personal task and its subtasks to Trash | "Delete my 'Call the vendor' personal task" |
| `astravue_bulk_create_tasks` | Creates multiple tasks in one call | "Create these 10 sprint tasks with owners and priorities" |
| `astravue_bulk_update_tasks` | Updates multiple tasks at once | "Set all 5 sprint tasks to In-Progress" |
| `astravue_bulk_delete_tasks` | Deletes multiple tasks at once | "Delete all the duplicate tasks from Sprint 1" |
| `astravue_get_task_counts` | Returns task count summary: total, pending, completed, overdue | "How many tasks are open vs completed?" |

</details>

<details>
<summary><strong>Subtasks</strong> (4 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_subtasks` | Lists subtasks under a parent task | "Show the subtasks of the authentication feature" |
| `astravue_create_subtask` | Creates a new subtask | "Add a subtask: Write unit tests under the API task" |
| `astravue_update_subtask` | Updates a subtask's title, status, or priority | "Mark the unit tests subtask as done" |
| `astravue_delete_subtask` | Deletes a subtask | "Delete the duplicate subtask under the API task" |

</details>

<details>
<summary><strong>Comments</strong> (4 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_get_task_comments` | Lists comments on a task | "Show me all comments on the login bug task" |
| `astravue_add_task_comment` | Adds a comment to a task | "Comment on the API task: Blocked pending design review" |
| `astravue_update_task_comment` | Edits an existing comment | "Update my comment to say: Unblocked, ready for review" |
| `astravue_delete_task_comment` | Deletes a specific comment | "Delete my last comment on the API task" |

</details>

<details>
<summary><strong>Checklists</strong> (4 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_get_task_checklists` | Gets all checklist items on a task | "Show the checklist on the deployment task" |
| `astravue_create_checklist_item` | Adds a new checklist item | "Add a checklist item: Run integration tests" |
| `astravue_update_checklist_item` | Updates a checklist item's title or completion state | "Mark 'Run integration tests' as done" |
| `astravue_delete_checklist_item` | Deletes a checklist item | "Remove the 'Update changelog' item from the checklist" |

</details>

<details>
<summary><strong>Dependencies</strong> (3 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_add_dependency` | Links two tasks with a blocking relationship | "Database schema must complete before API implementation" |
| `astravue_list_dependencies` | Shows all dependencies for a task | "What does the API implementation task depend on?" |
| `astravue_remove_dependency` | Removes a dependency link | "Remove the dependency between design and implementation" |

</details>

<details>
<summary><strong>Tags</strong> (6 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_tags` | Lists all tags available in your organization | "What tags do we have?" |
| `astravue_create_tag` | Creates a new workspace tag | "Create a tag called 'customer-facing'" |
| `astravue_bulk_create_tags` | Creates up to 50 tags in one call, skipping ones that already exist | "Create tags for frontend, backend, and QA" |
| `astravue_add_tag_to_task` | Adds an existing tag to a task | "Tag the login task as 'urgent'" |
| `astravue_remove_tag_from_task` | Removes a tag from a task | "Remove the 'blocked' tag from the deployment task" |
| `astravue_remove_tag_from_all_tasks` | Removes one or more tags from every task in the workspace | "Remove the 'old-sprint' tag from all tasks" |

</details>

<details>
<summary><strong>Attachments</strong> (2 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_attachments` | Lists all attachments on a task | "What files are attached to the design task?" |
| `astravue_delete_attachment` | Deletes an attachment from a task | "Remove the old mockup file from the design task" |

</details>

<details>
<summary><strong>Time Tracking</strong> (13 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_start_timer` | Starts a timer on a project task | "Start tracking time on the API documentation task" |
| `astravue_start_personal_task_timer` | Starts a timer on a personal task | "Start a timer on my 'Prepare board deck' task" |
| `astravue_stop_timer` | Stops a running timer on any task, project or personal | "Stop my timer" |
| `astravue_get_active_timers` | Lists running timers | "Do I have any active timers?" |
| `astravue_log_manual_time` | Logs a time entry with a specific duration on a project task | "Log 2 hours on the API documentation task" |
| `astravue_log_personal_task_time` | Logs a time entry with a specific duration on a personal task | "Log 45 minutes on my inbox cleanup task" |
| `astravue_log_time_range` | Logs time with a start and end time on a project task | "Log time from 9am to 11:30am on the backend refactor" |
| `astravue_log_personal_task_time_range` | Logs time with a start and end time on a personal task | "Log 2pm to 3pm on my 'Prepare board deck' task" |
| `astravue_get_task_time_entries` | Lists time entries for a task | "How much time was logged on the backend refactor?" |
| `astravue_get_project_time_entries` | Lists all time entries across a project | "Show all time logged in Sprint 2" |
| `astravue_get_project_time_summary` | Gets billable vs non-billable time totals | "How many total hours were spent on the Backend project?" |
| `astravue_get_timesheet_report` | Generates a timesheet report | "Show my timesheet for this week" |
| `astravue_delete_time_entry` | Deletes a time entry | "Delete the accidental time entry from yesterday" |

</details>

<details>
<summary><strong>Custom Fields</strong> (7 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_get_custom_fields` | Lists all custom fields for a project | "What custom fields are on the Backend project?" |
| `astravue_create_custom_field` | Creates a new custom field | "Add a custom field called Story Points to Sprint 2" |
| `astravue_set_custom_field_value` | Sets a custom field value on a task | "Set Story Points to 5 on the login task" |
| `astravue_create_custom_field_option` | Adds a dropdown option to a custom field | "Add option 'Critical' to the Severity field" |
| `astravue_list_custom_field_options` | Lists all options for a dropdown field | "What options are available for the Priority field?" |
| `astravue_delete_custom_field` | Deletes a custom field from a project | "Remove the Story Points field from Sprint 1" |
| `astravue_delete_custom_field_option` | Deletes a specific option from a dropdown field | "Remove the 'Trivial' option from the Severity field" |

</details>

<details>
<summary><strong>Task Statuses</strong> (5 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_task_statuses` | Lists all available statuses for tasks | "What statuses are available in Sprint 2?" |
| `astravue_list_project_statuses` | Lists status groups configured for a project | "Show the status workflow for the Backend project" |
| `astravue_create_task_status` | Creates a new task status | "Add a status called 'In Review' to Sprint 2" |
| `astravue_update_task_status` | Updates a task status name or configuration | "Rename 'In Progress' to 'Working'" |
| `astravue_delete_task_status` | Deletes a task status from a project | "Remove the 'Blocked' status from Sprint 1" |

</details>

<details>
<summary><strong>Filters</strong> (4 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_filters` | Lists saved filters | "Show me my saved filters" |
| `astravue_create_filter` | Creates a saved filter | "Create a filter for all high priority tasks assigned to me" |
| `astravue_update_filter` | Updates a saved filter | "Update my overdue filter to include medium priority" |
| `astravue_delete_filter` | Deletes a saved filter | "Delete the old sprint filter" |

</details>

<details>
<summary><strong>Scheduled & Overdue Tasks</strong> (2 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_overdue_tasks` | Lists overdue tasks assigned to the current user | "Show me everything overdue" |
| `astravue_list_scheduled_tasks` | Lists upcoming tasks with due dates | "What tasks are due this week?" |

</details>

<details>
<summary><strong>Notifications</strong> (2 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_notifications` | Lists unread notifications | "What notifications do I have?" |
| `astravue_mark_notification_read` | Marks notifications as read | "Mark all my notifications as read" |

</details>

<details>
<summary><strong>Workspace & Members</strong> (3 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_get_workspace_members` | Lists workspace members | "Who are the members of my workspace?" |
| `astravue_get_member_by_email` | Finds a member by email | "Find the profile for sarah@company.com" |
| `astravue_get_current_user` | Returns the authenticated user's profile | "Who am I logged in as?" |

</details>

<details>
<summary><strong>Interactive Views</strong> (3 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_preview_task_list` | Opens an interactive task list view for a project | "Show me the task board for Sprint 2" |
| `astravue_preview_my_tasks` | Opens a view of all tasks assigned to the current user | "Show me my tasks" |
| `astravue_preview_project_overview` | Opens a project overview with completion, health, and attention items | "Give me an overview of the Backend project" |

</details>

---

## Available Prompts

The Astravue MCP Server provides **15 prompts** — pre-built workflows that guide your AI assistant through common project management tasks.

| Prompt | Description | Arguments |
| :----- | :---------- | :-------- |
| `daily_standup` | Generate a structured daily standup update for the current user based on their tasks | — |
| `project_status_report` | Generate a professional project status report tailored for executive, stakeholder, or team audience | — |
| `weekly_team_digest` | Generate a weekly digest summarising what shipped, what is at risk, and what is coming up | — |
| `task_breakdown` | Suggest a subtask decomposition for a complex task to make it actionable | — |
| `overdue_action_plan` | Generate a prioritised recovery plan for the current user's overdue tasks | — |
| `sprint_planner` | Plan a sprint: select tasks by priority, estimate workload, assign owners, and define the sprint goal | `sprintGoal` (required) |
| `risk_assessment` | Identify at-risk projects and tasks: overdue items, off-track projects, unassigned high-priority work, and deadline conflicts | — |
| `time_tracking_report` | Generate a time tracking and effort summary for the current user across tasks | — |
| `meeting_agenda_generator` | Generate a structured meeting agenda based on current tasks, blockers, and project status | `meetingType` (optional): `standup`, `sprint_review`, `planning`, `retrospective`, `stakeholder_update` |
| `retrospective_summary` | Generate a sprint or project retrospective: what went well, what did not, and action items | — |
| `capacity_planning` | Analyse current team workload: identify who is overloaded, who has bandwidth, and suggest task redistribution | — |
| `project_kickoff` | Generate a project kickoff checklist with role assignments, initial tasks, and success criteria | — |
| `blockers_escalation` | Identify critical blockers and draft escalation messages for items requiring management attention | — |
| `milestone_review` | Review progress toward project milestones: completed work, at-risk items, and recommended adjustments | — |
| `team_workload_balancer` | Show each team member's task load and suggest reassignments to balance workload evenly | — |

---

## Available Resources

The Astravue MCP Server provides **6 resources** — context data that AI assistants can attach to conversations for richer, more accurate responses.

### Static Resources

| Resource URI | Name | Description |
| :----------- | :--- | :---------- |
| `astravue://user/me` | Current User Profile | The authenticated user's profile: ID, name, email, and organisation role. Read at session start to establish user context before assigning tasks or personalising any response. |
| `astravue://org/members` | Organisation Members | All active members of the organisation with user IDs, names, emails, and roles. Use to resolve teammate names to numeric IDs before any task assignment operation. |
| `astravue://org/spaces` | Organisation Spaces | All spaces the current user is a member of. Use to discover space IDs before calling project or task tools. |
| `astravue://dashboard/overview` | Dashboard Overview | Current user's task count summary: total, pending, completed, and overdue. Use for a quick org health snapshot. |

### Resource Templates

| Template URI | Name | Description |
| :----------- | :--- | :---------- |
| `astravue://spaces/{spaceId}/projects` | Projects in Space | All projects within a given space. Replace `{spaceId}` with the numeric space ID. |
| `astravue://spaces/{spaceId}/projects/{projectId}/overview` | Project Overview | Full details of a specific project. Replace `{spaceId}` and `{projectId}` with numeric IDs. |


---

## Skills

This repository includes ready-to-use skills that automate common project management workflows:

| Skill | Description |
| :---- | :---------- |
| [Sprint Planning](skills/sprint-planning/SKILL.md) | Analyzes backlog, overdue tasks, and dependencies to build a prioritized sprint plan |
| [Status Report](skills/generating-status-report/SKILL.md) | Generates executive project status reports covering progress, budget, and risks |
| [Time Tracking](skills/tracking-time/SKILL.md) | Guides timer usage, manual time logging, and timesheet report generation |
| [Custom Fields](skills/managing-custom-fields/SKILL.md) | Creates, configures, and manages custom fields and dropdown options |
| [Breaking Down Work](skills/breaking-down-work/SKILL.md) | Decomposes a goal, feature, or epic into a structured task tree with dependencies |
| [Capturing Meeting Actions](skills/capturing-meeting-actions/SKILL.md) | Extracts action items from meeting notes or transcripts and creates owned, dated tasks |
| [Mapping Dependencies](skills/mapping-dependencies/SKILL.md) | Maps task dependencies, finds the critical path, and detects circular dependencies |
| [Triaging Overdue Work](skills/triaging-overdue-work/SKILL.md) | Reviews overdue and at-risk tasks and proposes reschedule, reassign, or close actions |

Skills are available automatically when using the Claude Code or Cursor plugin.

---

## Data and Security

* All traffic is encrypted via HTTPS using TLS 1.2 or later.
* OAuth 2.0 authentication ensures secure access control.
* Data access respects your workspace role and project-level permissions.
* The MCP server never stores credentials — authentication is handled per session.

For more details, see [SECURITY.md](SECURITY.md).

---

## Rate Limits

Astravue MCP enforces rate limits to ensure platform stability.

| | |
| :--- | :--- |
| **Requests per user per minute** | 100 |
| **Bulk task create limit** | 100 tasks per call |

If the limit is exceeded, the server returns `HTTP 429 Too Many Requests`. Wait 60 seconds before retrying.

---

## Troubleshooting

<details>
<summary>Authentication fails or browser does not open</summary>

Sign out of Astravue at [app.astravue.com](https://app.astravue.com), sign back in, then reconnect your AI client.

</details>

<details>
<summary>401 Unauthorized error</summary>

Your OAuth session expired. Reconnect your client to trigger a new sign-in flow.

</details>

<details>
<summary>Tools not appearing in my AI client</summary>

Ensure your client supports **Streamable HTTP transport**. Clients that only support SSE must use the `mcp-remote` bridge (see [Other MCP Clients](#other-mcp-clients)).

</details>

<details>
<summary>Connection drops after some time</summary>

OAuth tokens expire periodically. Your client should refresh automatically. If it does not, reconnect once.

</details>

---

## FAQ

<details>
<summary>Do I need a paid Astravue plan?</summary>

No. Astravue MCP works on all plans including free.

</details>

<details>
<summary>Can multiple team members connect their AI clients?</summary>

Yes. Each user authenticates with their own Astravue account.

</details>

<details>
<summary>What permissions does Astravue MCP have?</summary>

Astravue MCP only has access to resources your account already has permission to access. All actions are performed as your authenticated user.

</details>

<details>
<summary>Can I use an API key instead of OAuth?</summary>

No. OAuth 2.0 is required so every action is tied to an authenticated user.

</details>

<details>
<summary>Will the AI make changes without asking me?</summary>

Most AI clients ask for confirmation before executing write operations. Check your client's tool approval settings.

</details>

---

## Contributing

We welcome contributions. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## Code of Conduct

This project follows the [Contributor Covenant](CODE_OF_CONDUCT.md).

## License

This project is licensed under the [Apache License 2.0](LICENSE).

Copyright 2026 Astravue.

---

## Support

* Open an issue on [GitHub](https://github.com/AstravueOrg/astravue-mcp-server/issues)
* Email [support@astravue.com](mailto:support@astravue.com)
* Visit [help.astravue.com](https://help.astravue.com)
