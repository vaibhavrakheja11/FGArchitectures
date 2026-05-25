# FGArchitectures

FGArchitectures is a visual architecture archive for the Fluke Games digital studio platform. It is organized by architecture pipeline first, then by domain category such as Website, Internal, InterviewPrepApp, UnrealMCP, or AWS.

## Platform Overview

![Fluke Games Digital Studio Platform](0.Cover.png)

The overview shows the platform as more than a public website. It connects public discovery, talent acquisition, customer access, studio operations, agentic AI, governance, and AWS deployment into one digital studio operating model.

## Quick Navigation

| Pipeline | Category | Preview | README |
|---|---|---|---|
| 01. Public Website Experience | Website | Visitor discovery, page rendering, public APIs, AI chat | [Open](01-Public-Website-Experience/Website/README.md) |
| 02. Careers & Talent | Website | Public jobs, dynamic applications, applicant review, notifications | [Open](02-Careers-Talent/Website/README.md) |
| 03. Customer Portal | Website | Signup, verification, sessions, entitlements, downloads | [Open](03-Customer-Portal/Website/README.md) |
| 04. Studio Operations | Internal | Updates, timelogs, analytics, reports, recognition | [Open](04-Studio-Operations/Internal/README.md) |
| 05. Agentic AI | Internal | LangGraph, LlamaIndex RAG, memory, MCP tools, approvals | [Open](05-Agentic-AI/Internal/README.md) |
| 05. Agentic AI | Website | Public assistant and website-facing AI plans | [Open](05-Agentic-AI/Website/README.md) |
| 05. Agentic AI | InterviewPrepApp | Interview coaching and adaptive practice AI plans | [Open](05-Agentic-AI/InterviewPrepApp/README.md) |
| 05. Agentic AI | UnrealMCP | Unreal Engine and MCP game/tool automation plans | [Open](05-Agentic-AI/UnrealMCP/README.md) |
| 06. Integration & Governance | Internal | Endpoint registry, RBAC, integrations, auditability | [Open](06-Integration-Governance/Internal/README.md) |
| 07. Pavan Unreal Release Architecture | SSO | Employee SSO for Unreal AccessGate and Perforce validation | [Open](07-Pavan-Unreal-Release-Architecture/SSO/README.md) |
| 07. Pavan Unreal Release Architecture | Perforce | Helix Core collaboration, locking, streams, changelists, CI handoff | [Open](07-Pavan-Unreal-Release-Architecture/Perforce/README.md) |
| 07. Pavan Unreal Release Architecture | CI/CD | Unreal BuildCookRun automation, artifact metadata, release promotion | [Open](07-Pavan-Unreal-Release-Architecture/CICD/README.md) |
| 07. Pavan Unreal Release Architecture | Customer Entitlement | Release catalog, customer login, entitlements, signed downloads, sessions | [Open](07-Pavan-Unreal-Release-Architecture/Customer-Entitlement/README.md) |
| 07. Pavan Unreal Release Architecture | Access Boundary | Separation between employee tools and customer product access | [Open](07-Pavan-Unreal-Release-Architecture/Access-Boundary/README.md) |
| 07. Pavan Unreal Release Architecture | Secure Release | End-to-end governed release path from source to customer session | [Open](07-Pavan-Unreal-Release-Architecture/Secure-Release/README.md) |
| AWS Deployment | AWS | GitHub Actions, IAM/OIDC, Lambda, API Gateway, DynamoDB, S3, SQS, SES, CloudWatch | [Open](AWS/README.md) |

## Pipeline Index

- [01. Public Website Experience Pipeline](01-Public-Website-Experience/README.md)
- [02. Careers & Talent Pipeline](02-Careers-Talent/README.md)
- [03. Customer Portal Pipeline](03-Customer-Portal/README.md)
- [04. Studio Operations Pipeline](04-Studio-Operations/README.md)
- [05. Agentic AI Pipeline](05-Agentic-AI/README.md)
- [06. Integration & Governance Pipeline](06-Integration-Governance/README.md)
- [07. Pavan Unreal Release Architecture](07-Pavan-Unreal-Release-Architecture/README.md)
- [AWS Deployment + Platform Architecture](AWS/README.md)

## Category Model

- `Website`: public-facing and customer-facing web architecture.
- `Internal`: admin, operations, governance, AI, and backend platform architecture.
- `InterviewPrepApp`: interview preparation product architecture.
- `UnrealMCP`: Unreal Engine and MCP-driven game/tooling architecture.
- `SSO`, `Perforce`, `CICD`, `Customer-Entitlement`, `Access-Boundary`, `Secure-Release`: Pavan Unreal project release and access architecture.
- `AWS`: deployment, infrastructure, security, and observability.
