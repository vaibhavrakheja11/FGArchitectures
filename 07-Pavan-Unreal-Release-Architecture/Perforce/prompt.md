# Image Prompt - Perforce Collaboration Flow

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, rounded rectangles, pastel fills, thin borders, readable text, no 3D, no dark background.

Title: Perforce Collaboration Flow - Unreal Source Control

Goal: Show governed Unreal asset/code collaboration through Helix Core, workspaces, changelists, locking, review, and CI handoff.

Swimlane 1: Contributors
Boxes:
Artist
Developer
Technical Lead

Swimlane 2: Perforce Client Workflow
Boxes:
P4V Client
Workspace Sync
Checkout / Lock
Changelist
Review Gate
Submit

Swimlane 3: Helix Core + Automation
Boxes:
Helix Core on EC2
Depot Streams
Typemap Rules
CI Build Workspace
Build Trigger

Flow:
Artist -> P4V Client -> Workspace Sync -> Checkout / Lock -> Changelist -> Review Gate -> Submit -> Helix Core on EC2
Developer -> P4V Client -> Workspace Sync -> Checkout / Lock -> Changelist -> Review Gate -> Submit -> Helix Core on EC2
Helix Core on EC2 -> Depot Streams -> CI Build Workspace -> Build Trigger
Typemap Rules -> Checkout / Lock

Include stream examples:
//GOAT/main/...
//GOAT/dev/...
//GOAT/release/...

Use arrow colors:
Blue = user workflow
Purple = depot/stream flow
Yellow = review/approval
Green = CI handoff

Bottom caption:
Perforce provides the source-of-truth for Unreal assets, code, locks, and build-triggered changelists.

Every box must be connected with arrows.
```
