SV MCP
A FastMCP server that exposes SV's SEO and GEO tools natively to AI agents — Claude Desktop, Claude Code, Cursor, and any MCP-capable host. Built directly on the sv-cli core library: no duplicated resolver, auth, or async-task logic.
How it works
sv-mcp is a FastMCP server that wraps the sv-cli core library. It exposes 15 SV API tools as MCP tools, plus get_task_status and get_task_result for async tasks. SEO Image is available through the API and CLI only. When an AI agent calls a tool, the MCP server delegates to the same resolver, auth stack, and async-task logic used by the CLI — so behaviour is identical whether you call sv seogpt generate from a terminal or invoke the seogpt MCP tool from Claude Desktop.

Async tools (GEO Audit, Prose, SEO Strategist, SEO Mapping) return a task ID straight away. The agent can pass wait: true on a call to wait up to 45 seconds for the result. If the task is still running after that, the tool returns the task ID and the agent follows up with get_task_status / get_task_result.
