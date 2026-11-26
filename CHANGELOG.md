# Changelog

This repository tracks **published MCP functionality changes and client-facing capability improvements** for the Astravue MCP Server.

Because the server implementation lives in a private codebase, this changelog should document:

- New MCP tools or public capabilities
- Behavior changes visible to users or client integrations
- Compatibility changes for Claude, ChatGPT, Cursor, Gemini, and other supported clients
- Security, auth, or access-control changes that affect users

This changelog should **not** document private refactors or internal implementation details that are not exposed through the published MCP surface.

The format is based on Keep a Changelog.

## [Unreleased]

- No unreleased public functionality changes recorded yet.

## [1.0.4] - 2026-11-26

### Added

- **Personal task tools** — `astravue_update_personal_task`, `astravue_delete_personal_task` (moves the task and its subtasks to Trash, where they can be restored), `astravue_start_personal_task_timer`, `astravue_log_personal_task_time`, and `astravue_log_personal_task_time_range`. `astravue_stop_timer` now stops timers on personal tasks too.
- **Tag management tools** in the published tool list — `astravue_create_tag`, `astravue_bulk_create_tags`, and `astravue_remove_tag_from_all_tasks`. The server lists 88 tools.
- **Project finances** — `astravue_create_project` and `astravue_update_project` can set the project type, contract value, allocated budget, budget alert threshold, and not-to-exceed or retainer settings; `astravue_create_project` also sets the project category. Amounts use the workspace currency.
- **Checklist item reassignment** — `astravue_update_checklist_item` can reassign an item; assignees are checked against the task's members.
- **Output schemas** — every tool advertises an output schema, so clients can read structured results.
- Setup guides for Google Antigravity, Kiro, Zed, Devin Desktop (Windsurf), Grok, Muse, and Zoho Zia Agents.

### Changed

- **Due and start times** — task dates accept a time (`yyyy-MM-ddTHH:mm`) and are read and written in the user's Astravue time zone. A date without a time sets the due time to the end of that day, as in the web app. Responses include `due_at`, `start_at`, and `time_zone`, and a task counts as overdue once its due time has passed.
- `astravue_get_current_user`, `astravue_get_workspace_members`, and `astravue_get_member_by_email` no longer return space, project, and task counts. Use `astravue_get_task_counts` for task totals; it now counts tasks with the same rules as the task lists.
- Interactive task and project views load the latest card after each server update.
- Gemini CLI extension connects over Streamable HTTP (`httpUrl`).
- Claude plugin manifest ships PNG logos, a listing icon, and a documentation URL.
- Setup guides follow each client's current docs: Claude Code signs in through `/mcp`, VS Code uses a workspace `.mcp.json`, updated Cursor and Cline menu paths, ChatGPT plan availability, and Perplexity's **Advanced** settings. Removed the Claude Desktop config-file example, which does not support remote servers.
- Version metadata aligned across the Claude, Cursor, and Gemini client manifests and `server.json` for `1.0.4`.

### Fixed

- Clearing a task's due date with `astravue_update_task` also clears its duration in days.
- `astravue_update_subtask` updates subtasks reliably, and toggling a checklist item's completion works.
- Creating a task status without a colour uses the default colour instead of failing.
- A retried `astravue_create_project` call no longer creates a duplicate project, and project input is validated the same way as in the REST API.
- Actions from interactive view cards send numeric IDs, so they work in every client.

### Security

- Project tools check the caller's project access the same way as the Astravue web app.
- Project financial fields are returned only to members who can see project finances; project guests no longer receive them.
- The server accepts only access tokens issued for it.

## [1.0.3] - 2026-06-09

### Added

- **breaking-down-work** skill — decomposes a goal, feature, epic, or deliverable into a structured task tree (tasks, subtasks, checklists) with dependencies in Astravue.
- **capturing-meeting-actions** skill — extracts action items from meeting notes, transcripts, or brain dumps and creates them as owned, dated tasks in Astravue.
- **mapping-dependencies** skill — maps task dependencies in an Astravue project, finds the critical path and blocked work, and detects circular dependencies.
- **triaging-overdue-work** skill — reviews overdue and at-risk tasks, assesses why each is slipping, and proposes reschedule, reassign, deprioritize, or close actions.

## [1.0.2] - 2026-05-26

### Added

- Documented the Claude Code plugin install path so users can install Astravue from Anthropic's community plugin marketplace alongside the existing raw MCP setup.

### Changed

- Aligned the published version metadata across the Claude, Cursor, and Gemini client manifests for consistent client recognition of the `1.0.2` release.

## [1.0.1] - 2026-04-23

### Added

- Added Claude Code marketplace metadata for the Astravue plugin to support marketplace-based discovery and installation.

### Changed

- Aligned the published version metadata across the Claude, Cursor, and Gemini client manifests for consistent client recognition of the `1.0.1` release.
