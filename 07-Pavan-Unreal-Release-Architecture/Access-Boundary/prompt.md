# Image Prompt - Employee vs Customer Access Boundary

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, pastel boxes, thin arrows, readable text.

Title: Employee vs Customer Access Boundary

Goal: Make it clear that employee access and customer access are separate realms connected only through governed backend release metadata.

Create two large side-by-side containers separated by a red vertical boundary line.

Left container title:
Employee Realm
Boxes:
Employee SSO
Unreal Editor
P4V / Helix Core
CI Build Workspace
Admin Backend
Release Approval

Right container title:
Customer Realm
Boxes:
Customer Login
Customer Session
Entitlement Service
Release Catalog
Protected Downloads
Game Session API

Middle bridge across boundary:
Governed Release Metadata
Subtext: product, version, platform, changelist, hash, channel

Flow:
Employee SSO -> Unreal Editor -> P4V / Helix Core -> CI Build Workspace -> Release Approval -> Governed Release Metadata
Governed Release Metadata -> Release Catalog -> Entitlement Service -> Protected Downloads -> Game Session API
Customer Login -> Customer Session -> Entitlement Service

Use arrow colors:
Blue = employee access
Teal = customer access
Orange = backend/release metadata
Red = access boundary

Bottom caption:
Employees manage source and releases; customers consume approved builds through entitlement-backed services.

Every box must be connected with arrows.
```
