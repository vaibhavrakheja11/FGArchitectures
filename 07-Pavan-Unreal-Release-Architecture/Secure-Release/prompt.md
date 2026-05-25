# Image Prompt - End-to-End Secure Release Pipeline

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, polished system diagram style, rounded boxes, pastel fills, thin arrows, readable text.

Title: End-to-End Secure Release Pipeline

Goal: Show the complete governed path from employee login to customer session enablement.

Create one connected left-to-right pipeline:

Employee SSO
-> Perforce Submit
-> CI Runner
-> Unreal BuildCookRun
-> Artifact Signing / Hashing
-> Release Approval
-> Release Catalog
-> Customer Login
-> Entitlement Check
-> Protected Download
-> Game Session Enablement

Add lower supporting boxes connected upward:
Helix Core Depot
Build Logs + Metadata
Protected Object Storage
Audit Trail

Connections:
Perforce Submit -> Helix Core Depot -> CI Runner
CI Runner -> Build Logs + Metadata
Artifact Signing / Hashing -> Build Logs + Metadata
Release Approval -> Audit Trail
Protected Download -> Protected Object Storage
Entitlement Check -> Audit Trail
Game Session Enablement -> Audit Trail

Use arrow colors:
Blue = identity
Purple = source control
Green = build/release
Orange = artifact/storage
Teal = customer access
Red = approval/security gate

Bottom caption:
Secure release operations connect governed development to customer access without exposing internal systems.

Every box must be connected with arrows.
```
