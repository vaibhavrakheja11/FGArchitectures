# 07. Pavan Unreal Release Architecture

This architecture category focuses on the Pavan Unreal project release system: employee SSO, Perforce source control, build automation, release artifact handling, customer entitlement handoff, and secure runtime/session enablement.

## Categories

| Category | Summary | README | Diagram | Image Prompt |
|---|---|---|---|---|
| SSO | Employee authentication for Unreal AccessGate and Perforce SSO | [Open](SSO/README.md) | [Image](SSO/SSO.png) | [Prompt](SSO/prompt.md) |
| Perforce | Helix Core collaboration, workspaces, locking, changelists, and CI handoff | [Open](Perforce/README.md) | [Image](Perforce/perforce.png) | [Prompt](Perforce/prompt.md) |
| CI/CD | Unreal BuildCookRun automation, artifact packaging, logs, and provenance | [Open](CICD/README.md) | [Image](CICD/ReleasePipleLine.png) | [Prompt](CICD/prompt.md) |
| Customer Entitlement | Future build artifact to customer login, entitlement, and protected download flow | [Open](Customer-Entitlement/README.md) | [Image](Customer-Entitlement/EntitlementAccess.png) | [Prompt](Customer-Entitlement/prompt.md) |
| Access Boundary | Separation between employee tooling access and customer product access | [Open](Access-Boundary/README.md) | [Image](Access-Boundary/AccessBoundary.png) | [Prompt](Access-Boundary/prompt.md) |
| Secure Release | End-to-end governed path from employee submit to customer session enablement | [Open](Secure-Release/README.md) | [Image](<Secure-Release/Secure Release.png>) | [Prompt](Secure-Release/prompt.md) |

## Current-State Findings

- Unreal project uses Unreal Engine 5.6 with a runtime `AccessGateGuard` module and AccessGate plugin.
- AccessGate implements backend-verified login for editor and packaged-build access.
- Packaged login is enabled in `Config/DefaultGame.ini` and points to `WBP_LoginScreen`.
- Perforce SSO scripts are documented under `ProjectSetup/PerforceSSO`.
- Helix Core is documented as an EC2-hosted service with backend token validation.
- Manual Unreal packaging is documented through `RunUAT BuildCookRun`.
- Successful local package output exists, but no formal CI provider config or BuildGraph file was found.

## Future-State Direction

The target architecture should keep employee and customer access separate:

- Employees authenticate into Unreal, Perforce, CI, and admin tools.
- Customers authenticate into customer login, entitlement, protected download, and runtime session services.
- The bridge between the two worlds is release metadata and entitlement mapping, not shared credentials.

## Director of Technology Lens

The Pavan architecture is best explained as a governed release operating model, not just an Unreal project setup. The current system already has important foundations: backend-verified employee access, Perforce SSO validation, AccessGate project entry control, and a proven local packaging path. The next maturity step is to connect those pieces into automated build provenance, release approval, customer entitlements, protected downloads, and runtime session enablement.

## Recommended Diagrams

1. Employee SSO Flow
2. Perforce Collaboration Flow
3. Unreal CI/CD Build Pipeline
4. Build Artifact to Customer Entitlement Flow
5. Employee vs Customer Access Boundary
6. End-to-End Secure Release Pipeline
