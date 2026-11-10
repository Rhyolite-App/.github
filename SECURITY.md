# Security Policy

Rhyolite is local-first software built to hold personal notes, engineering runbooks, and sensitive operational context. We treat security issues with top priority.

## Supported Versions

Security updates ship in the latest release available on **[Rhyolite-App/releases](https://github.com/Rhyolite-App/releases/releases/latest)**.

| Version | Supported |
|---|---|
| `0.3.x` (latest) | Yes |
| `< 0.3.0` | Upgrade to `0.3.1` or newer |

## Reporting a Vulnerability

**Please do not report security vulnerabilities in public GitHub issues or discussions.**

Send reports privately to **[support@rhyolite.app](mailto:support@rhyolite.app)** with `SECURITY` in the subject line, or open a [private security advisory](https://github.com/Rhyolite-App/releases/security/advisories/new) on GitHub if enabled.

Helpful details to include:
- The Rhyolite version and platform (macOS, Windows, Linux, iOS, or iPadOS).
- The component involved (e.g., vault/file handling, Markdown/HTML/Mermaid rendering, MCP server & secret redaction, executable runbooks, or cloud sync).
- Minimal steps, a sample Markdown snippet, or a proof-of-concept vault layout that reproduces the issue.

## What to Expect

- **Acknowledgement:** within **48 hours** of receipt.
- **Triage & status update:** within **5 business days**, with severity assessment and target fix timeline.
- **Coordinated disclosure:** once a patched build is published, we will coordinate credit in the release notes if you wish to be acknowledged.

## Security Architecture Scope

We particularly welcome reports affecting any of Rhyolite's trust boundaries:
1. **Vault containment:** path traversal, symlink escapes outside a vault root, or cross-vault leakage.
2. **Passive note safety:** opening or previewing an untrusted `.md`, `.canvas`, or `.base` file must never execute code, make unexpected network requests, or inject active scripts into exported HTML/SVG.
3. **MCP governance:** folder read/write scopes, `ai: exclude` and `ai: read-only` note enforcement, secret redaction and placeholder restoration, loopback HTTP authentication, and audit log integrity.
4. **Runbook trust & guardrails:** bypasses of vault/connection trust prompts, changed-cell detection, environment variable restrictions, or destructive/exfiltration guardrails.
5. **Sync safety:** path validation, keychain credential isolation, and protection of machine-local configuration from synced vault files.
