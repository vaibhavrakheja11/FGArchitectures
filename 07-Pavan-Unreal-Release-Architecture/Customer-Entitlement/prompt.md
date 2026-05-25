# Image Prompt - Build Artifact to Customer Entitlement Flow

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, rounded boxes, pastel fills, thin arrows, readable text, no 3D.

Title: Build Artifact to Customer Entitlement Flow

Goal: Show how approved Unreal builds become customer-accessible products through entitlement-backed services.

Create three swimlanes:

Build + Release
Boxes:
CI Artifact
Release Metadata
Release Approval
Protected Object Storage

Customer Services
Boxes:
Customer Login
Customer Session
Entitlement Service
Release Catalog
Signed Download URL

Runtime Access
Boxes:
Customer Download
Game Launch
Session Enablement API
Runtime Feature Flags

Flow:
CI Artifact -> Release Metadata -> Release Approval -> Protected Object Storage -> Release Catalog
Customer Login -> Customer Session -> Entitlement Service -> Release Catalog -> Signed Download URL -> Customer Download -> Game Launch -> Session Enablement API -> Runtime Feature Flags
Entitlement Service -> Signed Download URL
Protected Object Storage -> Signed Download URL

Use arrow colors:
Green = release flow
Blue = customer login/session
Orange = entitlement checks
Purple = catalog/download
Teal = runtime session
Red = denied access path

Add a small denied branch:
Entitlement Service -> Access Denied

Bottom caption:
Customer downloads are unlocked by entitlements, not by direct access to internal build storage.

Every box must be connected with arrows.
```
