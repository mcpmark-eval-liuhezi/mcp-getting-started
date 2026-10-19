# MCP Onboarding Briefing

> Compiled October 2026 from primary sources. Documentation version referenced: MCP 2026-07-28.

## What is MCP, and why it matters

The Model Context Protocol (MCP) is an open-source standard for connecting AI applications to external systems. Announced by Anthropic on November 25, 2024, and created at Anthropic by David Soria Parra and Justin Spahr-Summers, it lets applications like Claude or ChatGPT reach data sources, tools, and workflows in a standard way. The official docs describe it as a 'USB-C port for AI applications': one connector replaces N custom integrations. MCP matters differently depending on where you sit — it cuts integration complexity for developers, expands AI applications with an ecosystem of tools and data, and gives end users more capable assistants that can act on their behalf.

Recent milestones: OpenAI adopted MCP in March 2025 across the Agents SDK, with Responses API and ChatGPT support following; and on December 9, 2025, Anthropic donated MCP to the newly formed Agentic AI Foundation (AAIF), a directed fund under the Linux Foundation co-founded with Block and OpenAI. At that point MCP reported over 97 million monthly SDK downloads and 10,000 active servers, with first-class client support in ChatGPT, Claude, Cursor, Gemini, Microsoft Copilot, and Visual Studio Code. The maintainer structure and SEP-driven governance were unchanged by the move.

## Architecture: hosts, clients, servers

MCP follows a client-server architecture. An MCP host — the AI application, such as Claude Code, Claude Desktop, or Visual Studio Code — coordinates one or more MCP clients, and each client maintains a dedicated connection to an MCP server, the program that provides context. Servers can run locally (stdio transport, typically one client each) or remotely (Streamable HTTP, typically many clients). The protocol has two layers: a data layer built on JSON-RPC 2.0 that carries discovery and the core server primitives — tools, resources, and prompts — and a transport layer that handles connection establishment, message framing, and authorization, recommending OAuth for remote connections. Note that sampling is deprecated as of protocol version 2026-07-28.

## Getting started

Start with the official docs: the introduction, the architecture overview, and the quickstart at modelcontextprotocol.io. Build your first server with an official SDK — there are ten, tiered by feature completeness and maintenance: Tier 1 (TypeScript, Python, C#, Go, Rust, Ruby), Tier 2 (Java), and Tier 3 (Swift, PHP, Kotlin). All SDKs support building servers that expose tools, resources, and prompts, building clients that connect to any server, local and remote transports, and protocol compliance with type safety. Use the MCP Inspector for development, and browse the reference server implementations and pre-built servers (e.g., GitHub, Postgres, Slack) as working examples.

## Sources

1. Official introduction — What is the Model Context Protocol?: https://modelcontextprotocol.io/docs/getting-started/intro
2. Official architecture overview: https://modelcontextprotocol.io/docs/learn/architecture
3. Official SDK documentation: https://modelcontextprotocol.io/docs/sdk
4. Anthropic — Introducing the Model Context Protocol (Nov 25, 2024): https://www.anthropic.com/news/model-context-protocol
5. MCP Blog — MCP joins the Agentic AI Foundation (Dec 9, 2025): https://blog.modelcontextprotocol.io/posts/2025-12-09-mcp-joins-agentic-ai-foundation/
6. Linux Foundation press release — Formation of the Agentic AI Foundation (Dec 9, 2025): https://www.linuxfoundation.org/press/linux-foundation-announces-the-formation-of-the-agentic-ai-foundation
7. TechCrunch — OpenAI adopts rival Anthropic's standard (Mar 26, 2025): https://techcrunch.com/2025/03/26/openai-adopts-rival-anthropics-standard-for-connecting-ai-models-to-data/
8. Wikipedia — Model Context Protocol (used only to cross-check the announcement date): https://en.wikipedia.org/wiki/Model_Context_Protocol
