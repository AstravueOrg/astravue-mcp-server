<p align="center">
  <img src="assets/logo-full.svg" alt="Astravue" width="300">
</p>

# Astravue MCP Server

The Astravue MCP Server is a cloud-based bridge between your [Astravue](https://astravue.com) workspace and compatible AI tools. Once configured, it enables those tools to interact with your spaces, projects, tasks, time entries, and custom fields in real time. All actions are authenticated via OAuth 2.0 and respect the user's existing access controls.

With the Astravue MCP Server, you can:

* **Search and browse** spaces, projects, and tasks without switching tools.
* **Create and update** tasks, subtasks, checklists, and comments through natural language.
* **Track time** with live timers or manual entries and generate timesheet reports.
* **Manage custom fields** including dropdowns, dates, currencies, and more.
* **Automate workflows** like sprint planning, status reporting, and bulk task updates.

It's designed for project managers, developers, and teams who use AI-powered IDEs or assistants and want to manage work without context switching.

---

## Supported Clients

All clients connect to the same endpoint: `https://api.astravue.com/mcp`
You will be asked to sign in to Astravue in your browser the first time you connect.

| Client | Docs | Transport |
| :----- | :--- | :-------- |
| [Claude Code](#claude-code) | [MCP setup](https://code.claude.com/docs/en/mcp) | Streamable HTTP |
| [Claude Desktop](#claude-desktop) | [MCP setup](https://support.claude.com/en/articles/10949351-getting-started-with-local-mcp-servers-on-claude-desktop) | Streamable HTTP |
| [Claude.ai (Web)](#claudeai-web) | [Remote MCP](https://support.claude.com/en/articles/11175166-getting-started-with-custom-connectors-using-remote-mcp) | Streamable HTTP |
| [Claude Mobile](#claude-mobile-ios--android) | — | Streamable HTTP |
| [Cursor](#cursor) | [MCP setup](https://docs.cursor.com/context/model-context-protocol) | Streamable HTTP |
| [VS Code](#vs-code) | [MCP setup](https://code.visualstudio.com/docs/copilot/customization/mcp-servers) | Streamable HTTP |
| [Windsurf](#windsurf) | [MCP setup](https://docs.windsurf.com/windsurf/cascade/mcp) | Streamable HTTP |
| [Cline](#cline) | [MCP setup](https://docs.cline.bot/mcp/configuring-mcp-servers) | Streamable HTTP |
| [JetBrains IDEs](#jetbrains-intellij-webstorm-pycharm-etc) | [MCP setup](https://www.jetbrains.com/help/ai-assistant/mcp.html) | Streamable HTTP |
| [Gemini CLI](#gemini-cli) | [MCP setup](https://geminicli.com/docs/tools/mcp-server/) | Streamable HTTP |

---

## Setup Instructions

### Claude Code

Run the following command in your terminal:

```bash
claude mcp add --transport http astravue-mcp https://api.astravue.com/mcp
```

Your browser will open automatically. Sign in with your Astravue account and click **Approve**.

To confirm the connection, run `/mcp` in a new Claude Code session. You should see **astravue-mcp** listed with a green connected status.

<details>
<summary>Share connection across a project team</summary>

Add the `--scope project` flag to create a `.mcp.json` file in your project root:

```bash
claude mcp add --transport http --scope project astravue-mcp https://api.astravue.com/mcp
```

Commit `.mcp.json` to your repository so teammates automatically get the connection.

</details>

---

### Claude Desktop

> Requires a Claude Pro, Max, Team, or Enterprise plan.

1. Go to **Settings → Connectors** in Claude Desktop.
2. Click **Add custom connector** and enter: `https://api.astravue.com/mcp`
3. Sign in with your Astravue account in the browser and click **Approve**.

<details>
<summary>Manual config file setup (advanced)</summary>

If Connectors is not available in your Claude Desktop version, edit:

**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`

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

Save the file and restart Claude Desktop.

</details>

---

### Claude.ai (Web)

> Requires a Claude Pro, Max, Team, or Enterprise plan.

1. Go to [claude.ai](https://claude.ai) → **Settings → Connectors**
2. Click **Add connector** and enter: `https://api.astravue.com/mcp`
3. Sign in with your Astravue account in the browser and click **Approve**.

---

### Claude Mobile (iOS / Android)

Claude Mobile uses the same connector ecosystem as Claude.ai.

Add the connector on **Claude.ai (web)** or **Claude Desktop** first — it will automatically appear on your mobile app. No separate setup needed.

---

### Cursor

1. Go to **Cursor Settings → Tools & MCP**
2. Click **New MCP Server** — this opens your `mcp.json` file
3. Add the following configuration:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

4. Save the file. Your browser will open — sign in with your Astravue account and click **Approve**.

<details>
<summary>Project-level configuration</summary>

Create a `.cursor/mcp.json` file in your project root with the same config above. This scopes the connection to that project only.

</details>

---

### VS Code

1. Add a `.vscode/mcp.json` file to your project root:

```json
{
  "servers": {
    "astravue-mcp": {
      "type": "http",
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

2. Open Command Palette (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows), run **MCP: List Servers**, and click **Start** next to `astravue-mcp`.
3. Authenticate with your Astravue account in the browser.

<details>
<summary>User-level configuration (all projects)</summary>

Add this to your **User Settings (JSON)**:

```json
{
  "mcp": {
    "servers": {
      "astravue-mcp": {
        "type": "http",
        "url": "https://api.astravue.com/mcp"
      }
    }
  }
}
```

</details>

---

### Windsurf

1. Open the Windsurf MCP config file:
   * **macOS / Linux:** `~/.codeium/mcp_config.json`
   * **Windows:** `C:\Users\[username]\.codeium\mcp_config.json`
   * Or go to **Settings → Tools → Windsurf Settings → Add Server**

2. Add the following:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "serverUrl": "https://api.astravue.com/mcp"
    }
  }
}
```

> If you already have other servers in your config, add `astravue-mcp` alongside them inside the existing `mcpServers` object — don't replace the entire file.

3. Reload Windsurf and authenticate with your Astravue account.

---

### Cline

1. Click the **Cline icon** in the VS Code sidebar → click the **menu (⋮)** in the top right → select **MCP Servers**.
2. Go to the **Remote Servers** tab and fill in:
   * **Server Name:** `astravue-mcp`
   * **Server URL:** `https://api.astravue.com/mcp`
   * **Transport Type:** `Streamable HTTP`
3. Click **Add Server**. Your browser will open — sign in and click **Approve**.

<details>
<summary>Manual JSON configuration</summary>

Click **Configure MCP Servers** in the Configure tab to open `cline_mcp_settings.json` and add:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp",
      "type": "streamableHttp"
    }
  }
}
```

</details>

---

### JetBrains (IntelliJ, WebStorm, PyCharm, etc.)

1. Go to **Settings → Tools → AI Assistant → Model Context Protocol (MCP)**
2. Click **Add** → Select **Streamable HTTP** → Paste:

```json
{
  "mcpServers": {
    "astravue-mcp": {
      "url": "https://api.astravue.com/mcp"
    }
  }
}
```

3. Click **OK**, then **Apply**. Sign in with your Astravue account in the browser.

---

### Gemini CLI

Copy `gemini-extension.json` from this repository to your Gemini CLI extensions directory, or add the server URL to your Gemini MCP configuration.

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

The Astravue MCP Server provides **87 tools** across the following categories.

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
<summary><strong>Tasks</strong> (13 tools)</summary>

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
<summary><strong>Tags</strong> (3 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_tags` | Lists all tags available in your organization | "What tags do we have?" |
| `astravue_add_tag_to_task` | Adds an existing tag to a task | "Tag the login task as 'urgent'" |
| `astravue_remove_tag_from_task` | Removes a tag from a task | "Remove the 'blocked' tag from the deployment task" |

</details>

<details>
<summary><strong>Attachments</strong> (2 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_list_attachments` | Lists all attachments on a task | "What files are attached to the design task?" |
| `astravue_delete_attachment` | Deletes an attachment from a task | "Remove the old mockup file from the design task" |

</details>

<details>
<summary><strong>Time Tracking</strong> (10 tools)</summary>

| Tool | Description | Example Prompt |
| :--- | :---------- | :------------- |
| `astravue_start_timer` | Starts a timer on a task | "Start tracking time on the API documentation task" |
| `astravue_stop_timer` | Stops the active timer | "Stop my timer" |
| `astravue_get_active_timers` | Lists running timers | "Do I have any active timers?" |
| `astravue_log_manual_time` | Logs a time entry with a specific duration | "Log 2 hours on the API documentation task" |
| `astravue_log_time_range` | Logs time with a start and end time | "Log time from 9am to 11:30am on the backend refactor" |
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

## Skills

This repository includes ready-to-use skills that automate common project management workflows:

| Skill | Description |
| :---- | :---------- |
| [Sprint Planning](skills/sprint-planning/SKILL.md) | Analyzes backlog, overdue tasks, and dependencies to build a prioritized sprint plan |
| [Status Report](skills/generating-status-report/SKILL.md) | Generates executive project status reports covering progress, budget, and risks |
| [Time Tracking](skills/tracking-time/SKILL.md) | Guides timer usage, manual time logging, and timesheet report generation |
| [Custom Fields](skills/managing-custom-fields/SKILL.md) | Creates, configures, and manages custom fields and dropdown options |

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
