# Image Prompt - Unreal CI/CD Build Pipeline

```text
Create a detailed but clean technical architecture diagram for LinkedIn.

Canvas: 16:9 landscape, white background, polished technical diagram, pastel boxes, thin arrows, readable text.

Title: Unreal CI/CD Build Pipeline - Pavan Release Automation

Goal: Show how the current manual RunUAT packaging process should become a traceable automated build pipeline.

Create a left-to-right pipeline:

Perforce Changelist
-> CI Trigger
-> Clean Build Workspace
-> Unreal Engine 5.6
-> UBT Compile
-> Cook
-> Stage
-> Pak / IoStore
-> Archive
-> Build Metadata + Logs
-> Release Candidate Artifact

Add a lower connected row:
Build Provenance
Subtext: changelist, stream, engine version, build config, hash, logs

Connect Build Provenance to Archive and Release Candidate Artifact.

Add a future-state branch:
Release Candidate Artifact -> Release Approval -> Protected Object Storage -> Customer Release Catalog

Use arrow colors:
Purple = Perforce source
Blue = Unreal build stages
Green = successful artifact
Orange = metadata/provenance
Red = approval gate

Bottom caption:
A repeatable Unreal build pipeline packages exact Perforce changelists into traceable release artifacts.

Every box must be connected with arrows.
```
