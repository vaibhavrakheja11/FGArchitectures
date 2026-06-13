# Agentic AI Pipeline - Internal + MCP Server Bridge

![Agentic AI Pipeline](5.AgenticAI.png)

## Summary

This diagram shows the internal agentic AI architecture alongside the MCP server bridge layer. It connects internal chat entry points, external CLI agents, the JSON-RPC MCP server, sync and async request paths, agent routing, context building, memory, LangGraph orchestration, LlamaIndex RAG, LLM providers, approval guardrails, MCP tools, internal business APIs, and result delivery.

## Two Entry Paths

### Internal Users
Portal chat, weekly updates, and voice intake submit requests directly to the AI Chat API. Async jobs travel through SQS to `ue-worker-ai` for full LangGraph orchestration.

### External CLI Agents (MCP Server Bridge)
Claude Code, Codex CLI, Cursor, and any MCP-compatible client connect to the `/mcp` endpoint on `ue-auth`. The MCP server speaks JSON-RPC 2.0 and exposes 27 Fluke tools. Agents authenticate once using the `fluke_login` tool (email + password → Bearer token stored in DynamoDB per session key). Subsequent tool calls use that session token to call internal `ue-auth` API routes directly via `callSelf` HTTP.

## End-To-End Flow — Internal Path

1. User submits a question through portal chat, weekly update, or voice intake.
2. Chat request builder normalizes provider, model, context, thread, and agent fields.
3. Request travels through sync `/ai/chat-sync` or async `/ai/chat`.
4. `ue-auth` creates access profile and context metadata.
5. Async jobs move through SQS to `ue-worker-ai`.
6. Agent route planner selects AI employee, role, allowed context, and source policy.
7. Context builder loads site, team, activity, analytics, policies, and other allowed data sources.
8. Memory layer retrieves prior conversation context.
9. LangGraph Manager Workflow handles intent detection, planning, payload building, validation, and execution state.
10. LlamaIndex RAG supports action retrieval and memory retrieval with heuristic fallback.
11. LLM provider generates reasoning or structured content through Anthropic Claude, OpenAI, or local fallback.
12. Approval guardrails validate RBAC, agent assignment, MCP policy, and approval decision.
13. MCP action tools call internal business APIs such as jobs, mail, Jira, updates, and analytics.
14. Result delivery returns WebSocket responses, sync JSON responses, errors, and run logs.

## End-To-End Flow — MCP / CLI Agent Path

1. Developer opens Claude Code, Codex CLI, or any MCP-compatible terminal.
2. Client connects to `POST /mcp` on the `ue-auth` Lambda with a static `x-mcp-key` header.
3. MCP server responds to `initialize` and `tools/list` handshake — agent discovers all 27 Fluke tools.
4. Agent calls `fluke_login` tool with email and password.
5. `ue-auth` login API validates credentials and returns a JWT Bearer token.
6. Token is stored in DynamoDB (`PK: mcp_session_<key>`, `SK: session`) with a 55-minute expiry.
7. Agent calls any Fluke tool (e.g. `list_contexts`, `create_jira_ticket`, `get_user_updates`).
8. MCP server retrieves the session token from DynamoDB and calls the matching internal `ue-auth` API route via `callSelf` HTTP.
9. Result is returned to the CLI agent as a JSON-RPC tool response.
10. Session expires after 55 minutes — agent re-authenticates with `fluke_login`.

## System Components

- MCP Server (`/mcp` route on `ue-auth`) — JSON-RPC 2.0 protocol handler.
- 27 Fluke MCP Tools — contexts, jobs, Jira, users, mail, updates, analytics, and more.
- Per-user session store — DynamoDB keyed by static `x-mcp-key` with 55-minute token TTL.
- AI Chat API in `ue-auth` — `/ai/chat` and `/ai/chat-sync`.
- SQS AI Jobs Queue.
- `ue-worker-ai` Lambda.
- Agent Route Planner and Context Builder.
- Conversation memory and AI data stores.
- LangGraph Manager Workflow.
- LlamaIndex RAG.
- Anthropic Claude / OpenAI / local LLM provider fallback.
- Approval Guardrails and MCP Action Tools.
- Internal Business APIs: Jobs, Mail, Jira, Updates, Analytics.
- Shared Data Stores: DynamoDB (AI Agent Store), S3 (Context + Logs), Vector Store (RAG).

## Technology Leadership Lens

This architecture treats AI as a governed workflow layer accessible from both internal products and external developer tools. The MCP server bridge extends the same governed tool set to any CLI agent without duplicating logic — routing, auth, context, memory, and approval all remain in one place. A developer using Claude Code or Codex CLI operates under the same access controls and audit trail as the internal portal, just through a different entry point.
