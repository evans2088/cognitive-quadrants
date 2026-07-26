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

Before a formal release, test the same package in:

- one Codex environment;
- one other Agent Skills-compatible client on an independent runtime.

Claude Code is recommended where available, but is not a required release gate. Across the release matrix, confirm explicit invocation, relative resource loading, a mode switch, and the no-write-without-authorization boundary. Test implicit matching where the client exposes it, and record any untested behavior or limitation.

## Release record

Record results below before assigning a version tag. Do not claim a behavior check unless the corresponding row passed it.

| Client | Version | Checks passed | Limitation or deviation |
|---|---|---|---|
| Codex | codex-cli 0.146.0-alpha.3.1 | Structural validation; behavior regressions for mode selection, aliases, no-write reflection, and offline evidence handling | The packaged directory was supplied by path; automatic discovery was not separately exercised |
| Qclaw (OpenClaw) | Qclaw 0.2.34 / OpenClaw 2026.6.5 | Discovery and visibility; explicit invocation; `SKILL.md` and mode-reference loading; 追问者 → 检验者 mode switch; no file write in a two-turn session | Implicit matching was not separately tested. The client resolved a synced local copy of the release runtime files rather than a GitHub-installed directory |
