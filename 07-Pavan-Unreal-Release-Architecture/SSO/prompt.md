# Image Prompt - Employee SSO Flow

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, polished system architecture style, rounded rectangles, pastel fills, thin borders, readable text, no 3D, no dark background, no decorative clutter.

Title: Employee SSO Flow - Unreal + Perforce Access

Goal: Show how employee identity gates Unreal project access and Perforce source-control access through a Fluke backend token flow.

Create three horizontal swimlanes:

1. Employee Tools
Boxes:
Employee
P4V Client
Unreal Editor
Packaged Unreal Build

2. SSO + Access Gate
Boxes:
Credential Prompt
P4LOGINSSO Helper
Unreal AccessGate Plugin
Platform Context
Token Result

3. Backend + Perforce Validation
Boxes:
Fluke Auth Backend
Helix auth-check-sso Trigger
Helix Core Server
Allow / Deny Access

Flow:
Employee -> P4V Client -> P4LOGINSSO Helper -> Fluke Auth Backend -> Token Result -> Helix auth-check-sso Trigger -> Helix Core Server -> Allow / Deny Access
Employee -> Unreal Editor -> Credential Prompt -> Unreal AccessGate Plugin -> Fluke Auth Backend -> Token Result -> Allow / Deny Access
Employee -> Packaged Unreal Build -> Credential Prompt -> Unreal AccessGate Plugin -> Fluke Auth Backend -> Token Result -> Allow / Deny Access

Explicitly label platform values:
project
version_control

Use arrow colors:
Blue = employee interaction
Orange = auth request
Green = access allowed
Red = access denied
Purple = token validation

Bottom caption:
Employee access is centrally governed by backend-issued platform tokens for Unreal project and Perforce workflows.

Do not show customer login in this diagram. Keep customer access separate.
Every box must be connected with arrows.
```
