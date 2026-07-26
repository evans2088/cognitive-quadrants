# Compatibility

## Core contract

`skills/cognitive-quadrants/` follows the Agent Skills convention: a directory named `cognitive-quadrants` containing a `SKILL.md` with matching frontmatter. It uses only Markdown, relative file links, and optional resource files.

The core skill requires no executable scripts, credentials, MCP server, or platform-specific command syntax. It can run without network access, but cannot verify external facts when neither a source nor network access is available.

## Expected behavior

An Agent Skills-compatible client should:

1. Discover the `name` and `description` in `SKILL.md`.
2. Load `SKILL.md` when the request matches.
3. Read only the linked file for the selected mode and any explicitly required shared protocol.
4. Treat `agents/openai.yaml` as optional product metadata.

When the client cannot access a needed source or the network, it should not present model knowledge as verified. It should request a source, provide clearly conditional reasoning with a minimal verification step, or—on high-risk matters—decline to form a final factual conclusion.

Automatic discovery, command syntax, installation paths, and UI labels vary by client. Where a client cannot auto-discover skills, copy the complete skill directory and explicitly say: “使用 cognitive-quadrants，以〈模式〉处理这个问题”。

## Verification targets

Before a public release, test the same package in at least:

- one Codex environment;
- one Claude Code environment;
- one other Agent Skills-compatible client.

Confirm explicit invocation, implicit matching, relative resource loading, a mode switch, and the no-write-without-authorization boundary. Record client version and any observed limitation in the release notes.

## Release record

Before replacing `Unreleased` in the changelog with a version tag, record the results below in that release's notes. Do not claim cross-client verification until every target has been tested.

| Client | Version | Checks passed | Limitation or deviation |
|---|---|---|---|
| Codex |  |  |  |
| Claude Code |  |  |  |
| Another Agent Skills-compatible client |  |  |  |
