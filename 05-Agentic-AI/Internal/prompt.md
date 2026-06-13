# Image Prompt - Agentic AI Pipeline (Internal + MCP Server)

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, polished technical diagram, pastel boxes, thin arrows, readable text.

Title: Agentic AI Pipeline - Internal + MCP Server Bridge

Goal: Show the full internal agentic AI pipeline alongside the new MCP server layer that lets Claude Code, Codex CLI, and other external agents call the same Fluke tools through a governed JSON-RPC bridge.

Divide the diagram into four horizontal swim lanes from top to bottom.

---

Swim Lane 1 title: Entry Points
Two groups side by side:

Left group label: Internal Users
Boxes: Portal Chat | Weekly Update | Voice Intake

Right group label: External CLI Agents
Boxes: Claude Code | Codex CLI | Cursor / Cline

---

Swim Lane 2 title: MCP Server Bridge (ue-auth Lambda)
Boxes left to right:
JSON-RPC 2.0 /mcp Endpoint
  Subtext: x-mcp-key auth header
fluke_login Tool
  Subtext: email + password → Bearer token
Session Store
  Subtext: DynamoDB — PK: mcp_session_<key>, SK: session
27 Fluke Tools
  Subtext: contexts, jobs, jira, users, mail, updates, analytics
callSelf HTTP
  Subtext: tool calls → internal ue-auth API routes

---

Swim Lane 3 title: Internal AI Pipeline (ue-auth + ue-worker-ai)
Boxes left to right:
AI Chat API
  Subtext: /ai/chat, /ai/chat-sync
SQS Jobs Queue
  Subtext: async AI jobs
ue-worker-ai Lambda
Agent Route Planner
  Subtext: AI employee, role, context policy
Context Builder
  Subtext: site, team, activity, analytics, policies
Memory Layer
  Subtext: conversation history, prior context
LangGraph Workflow
  Subtext: intent, planning, validation, execution
LlamaIndex RAG
  Subtext: action retrieval, heuristic fallback
LLM Provider
  Subtext: Anthropic Claude / OpenAI / local fallback
Approval Guardrails
  Subtext: RBAC, agent policy, MCP policy

---

Swim Lane 4 title: Shared Business APIs + Data Stores
Boxes left to right:
Jobs API | Mail API | Jira API | Updates API | Analytics API
DynamoDB (AI Agent Store) | S3 (Context + Logs) | Vector Store (RAG)

---

Flow:
Portal Chat -> AI Chat API -> SQS Jobs Queue -> ue-worker-ai Lambda -> Agent Route Planner -> Context Builder -> Memory Layer -> LangGraph Workflow -> LlamaIndex RAG -> LLM Provider -> Approval Guardrails -> Jobs API
Claude Code -> JSON-RPC 2.0 /mcp Endpoint -> fluke_login Tool -> Session Store
Claude Code -> JSON-RPC 2.0 /mcp Endpoint -> 27 Fluke Tools -> callSelf HTTP -> AI Chat API
callSelf HTTP -> Jobs API
callSelf HTTP -> Jira API
callSelf HTTP -> Mail API
Approval Guardrails -> Jobs API
Approval Guardrails -> Jira API
Jobs API -> DynamoDB (AI Agent Store)
Session Store -> DynamoDB (AI Agent Store)
LlamaIndex RAG -> Vector Store (RAG)
LangGraph Workflow -> S3 (Context + Logs)

Use arrow colors:
Blue = internal user requests
Purple = external CLI / MCP agent requests
Green = tool execution and API calls
Orange = data store reads and writes
Red = approval and auth gates

Bottom caption:
A governed agentic AI system where internal users and external CLI agents share the same Fluke tools through a JSON-RPC MCP bridge, backed by LangGraph orchestration, LlamaIndex RAG, and per-user session auth.

Every box must be connected with arrows.
```
