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
