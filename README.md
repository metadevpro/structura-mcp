<!-- mcp-name: tools.structura/structura -->

# Structura MCP
![Logo Structura](assets/structura-logo.svg)

Public information page for the **Structura** [Model Context Protocol](https://modelcontextprotocol.io)
(MCP) server — the remote MCP endpoint that lets AI coding agents (Claude Code, OpenCode, Codex,
and other MCP clients) manage [Structura](https://structura.tools) projects and generate code
directly from a conversation.

This repository does not contain the server's implementation. It exists to give the MCP server a
public, citable home — a discoverable `repository` reference for registries such as the
[official MCP Registry](https://registry.modelcontextprotocol.io) and the
[GitHub MCP Registry](https://github.com/mcp) — while the implementation itself stays in
Structura's private monorepo.

- **Live endpoint**: `https://mcp.structura.tools/`
- **Product**: [structura.tools](https://structura.tools) — a visual domain-model designer and
  multi-stack code generator by [Metadev](https://metadev.pro).
- **Protocol version**: [2026-07-28](https://modelcontextprotocol.io/docs/2026-07-28/getting-started/intro)
- **Transport**: streamable HTTP, OAuth 2.1 (Authorization Code + PKCE, with Dynamic Client
  Registration) — no manual token to create or paste.

## What it does

- List, load, create, or delete your Structura projects.
- Summarize a project brief and turn it into a new project in Structura.
- Generate code for multiple targets (Angular, .NET, and more) from a project's domain model.
- Validate a project's domain model.
- Combine with other MCP servers — e.g. pull UI designs from Figma, then model the backend for
  them in Structura and generate the code.

## Tools

The authoritative list is always what the live server reports over `tools/list`; the table below
is a convenience summary and may lag a version behind.

| Tool | What it does |
| --- | --- |
| `list_projects` | List the caller's Structura projects. |
| `create_project` | Create a new project, optionally seeded with Structura DSL content. |
| `load_project` | Load a project the caller owns, by id. |
| `update_project` | Update a project's name, description, or DSL content. |
| `delete_project` | Permanently delete a project the caller owns. |
| `share_project` | Find or create a viewable share link for a project. |
| `query_model` | Query a model's nodes, optionally filtered by node type. |
| `summarize_model` | Summarize a model (node counts by type, connection count). |
| `get_project_statistics` | Compute model statistics (class/association counts, connectivity averages, etc.). |
| `list_generators` | List available code generators and their configurable options. |
| `generate` | Submit an async code-generation job for a project against a chosen generator. |
| `get_generation_status` | Poll a generation job's status until it completes. |
| `get_generation_artifacts` | Get a short-lived download URL for a completed job's output ZIP. |

## Install

Any MCP-capable agent can connect. A few examples:

### Claude Code

```bash
claude mcp add --transport http structura https://mcp.structura.tools/
```

Then run `/mcp` inside a Claude Code session, select **structura**, and choose **Authenticate**.

### OpenCode

```bash
opencode mcp add
```

Pick **remote**, name it `structura`, and paste `https://mcp.structura.tools/`. Then:

```bash
opencode mcp auth structura
```

### Codex

```bash
codex mcp add structura --url https://mcp.structura.tools/
codex mcp login structura
```

Each of these opens a browser window with the normal Structura login (Google/GitHub) — approve it
there, and the agent reuses that session from then on.

## Support

- Product and account questions: [structura.tools](https://structura.tools)
- Issues with the MCP server itself: open an issue on this repository.
- Support contact: [support@structura.tools](mailto:support@structura.tools)

## Legal

- [Terms of Service](https://structura.tools/legal/terms)
- [Privacy Policy](https://structura.tools/legal/privacy)

## License

See [LICENSE](./LICENSE). This repository's own content (this README, the license file) is
provided for informational and discovery purposes; it does not grant any rights to the Structura
service, product, or its non-public source code.

---

&copy; [Metadev](https://metadev.pro), 2026.
