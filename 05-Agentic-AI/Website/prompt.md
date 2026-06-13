# Image Prompt - Agentic AI Pipeline (Website / Public)

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, polished technical diagram, pastel boxes, thin arrows, readable text.

Title: Website AI Pipeline - Public Assistant Experience

Goal: Show how a visitor question flows through the public AI chat widget into a context-aware response pipeline, with clear separation between public-safe data and internal systems.

Create a left-to-right pipeline with three rows.

---

Top row title: Visitor Entry
Boxes left to right:
Website Visitor
  Subtext: flukegames.com
Floating Chat Widget
  Subtext: React — always-on assistant
Voice Intake (Public)
  Subtext: WebRTC interview — real-time voice AI
Team Member Page
  Subtext: profile-specific prompt injection

---

Middle row title: Public AI Pipeline (ue-auth)
Boxes left to right:
Public AI Chat API
  Subtext: /ai/chat — no login required
Chat Request Builder
  Subtext: normalise provider, model, context, thread
Context Router
  Subtext: selects flukegames public context
Public Context Builder
  Subtext: games, services, careers, team, awards, studio
Public-Safe Filter
  Subtext: strips internal ops, financials, private data
LLM Provider
  Subtext: Anthropic Claude — public response generation
Response Formatter
  Subtext: guided discovery, follow-up suggestions
WebRTC Session Manager
  Subtext: OpenAI Realtime API — voice interview sessions
Transcript Processor
  Subtext: post-interview email delivery + storage

---

Bottom row title: Public Data Sources
Boxes left to right:
Games Catalog | Studio Services | Careers + Jobs | Team Profiles | Awards + Press | Site Content

---

Flow:
Website Visitor -> Floating Chat Widget -> Public AI Chat API -> Chat Request Builder -> Context Router -> Public Context Builder -> Public-Safe Filter -> LLM Provider -> Response Formatter -> Floating Chat Widget
Website Visitor -> Voice Intake (Public) -> WebRTC Session Manager -> LLM Provider -> WebRTC Session Manager -> Transcript Processor
Team Member Page -> Floating Chat Widget
Public Context Builder -> Games Catalog
Public Context Builder -> Studio Services
Public Context Builder -> Careers + Jobs
Public Context Builder -> Team Profiles
Public Context Builder -> Awards + Press
Public Context Builder -> Site Content
Transcript Processor -> Website Visitor

Use arrow colors:
Blue = visitor interaction
Teal = public data retrieval
Green = AI response generation
Orange = voice and transcript processing
Red = public-safe boundary filter

Bottom caption:
A public-facing AI layer that guides visitors through studio content using context-aware chat and voice intake, with a strict public-safe filter separating what visitors see from internal operations.

Every box must be connected with arrows.
```
