# End-to-End Secure Release Pipeline

![End-to-End Secure Release Pipeline](<Secure Release.png>)

## Summary

This architecture connects the full path from employee authentication and Perforce submission to automated builds, artifact verification, release approval, customer entitlements, protected downloads, and runtime session enablement.

## Future-State Flow

1. Employee authenticates through SSO.
2. Source and assets are synced/submitted through Perforce.
3. CI runner syncs the exact changelist.
4. Unreal build pipeline compiles, cooks, stages, paks, and archives.
5. Artifact is hashed, logged, and promoted through release approval.
6. Release catalog exposes approved builds.
7. Customer login and entitlement checks gate access.
8. Protected download service issues signed URLs.
9. Game session enablement activates runtime access.

## Strategic Goal

The release pipeline should let employees build and release safely while ensuring customers only receive approved, entitled, traceable artifacts.

## Operating Model

- Identity controls who can access source, tools, release approvals, and customer services.
- Perforce controls the authoritative source and asset history.
- CI/CD controls repeatable packaging and build evidence.
- Release approval controls what becomes customer-visible.
- Entitlements control which customer can access which build.
- Session enablement controls runtime access after download.

## Director of Technology Lens

This is the executive diagram for the Pavan release story. It should explain how governed employee development turns into customer-ready access without exposing internal systems or relying on informal manual handoffs.

## Diagram Prompt

See [prompt.md](prompt.md).
