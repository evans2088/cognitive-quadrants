# Compatibility

## Core contract

`skills/cognitive-quadrants/` follows the Agent Skills convention: a directory named `cognitive-quadrants` containing a `SKILL.md` with matching frontmatter. It uses only Markdown, relative file links, and optional resource files.

The core skill requires no executable scripts, credentials, MCP server, or platform-specific command syntax. It can run without network access, but cannot verify external facts when neither a source nor network access is available.

## Supported scope

This skill is not tied to a particular model, vendor, or agent product. Any runtime that supports Agent Skills—or can load the complete skill directory and follow `SKILL.md`—can use it. A client that does not automatically discover skills can still use the directory by following its own manual-install convention.

`agents/openai.yaml` is optional UI metadata for OpenAI surfaces; other clients may ignore it. Differences between clients affect discovery, installation, UI, and tool permissions—not the framework's four modes or its core workflow.

## Expected behavior

An Agent Skills-compatible client should:

1. Discover the `name` and `description` in `SKILL.md`.
2. Load `SKILL.md` when the request matches.
3. Read only the linked file for the selected mode and any explicitly required shared protocol.
4. Treat `agents/openai.yaml` as optional product metadata.

When the client cannot access a needed source or the network, it should not present model knowledge as verified. It should request a source, provide clearly conditional reasoning with a minimal verification step, or—on high-risk matters—decline to form a final factual conclusion.

Automatic discovery, command syntax, installation paths, and UI labels vary by client. Where a client cannot auto-discover skills, copy the complete skill directory and explicitly say: “使用 cognitive-quadrants，以〈模式〉处理这个问题”。
