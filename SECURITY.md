# Security Policy

## Reporting a vulnerability

If you believe you have found a security vulnerability in any dot-agent project, please report it
privately. **Do not open a public issue for security problems.**

- Use GitHub's **["Report a vulnerability"](https://docs.github.com/en/code-security/security-advisories/guidance-on-reporting-and-writing-information-about-vulnerabilities/privately-reporting-a-security-vulnerability)** (Security → Advisories) on the affected repository, or
- Email **contato@daniloborg.es** with the details.

Please include, as far as you can:

- The affected project, version, and platform
- A description of the vulnerability and its impact
- Steps to reproduce (a minimal proof-of-concept helps)
- Any suggested remediation

## What to expect

- **Acknowledgement** of your report as soon as reasonably possible.
- An assessment and, if confirmed, a fix coordinated with you before public disclosure.
- Credit for the discovery, if you wish.

## Scope note

dot-agent executes `.agent` bundles, which can declare scripts, subagents, tools, and (in future)
WASM libs. Reports about the **trust boundary** — sandboxing, capability gating, bundle integrity
(magic-byte/zip-bomb checks), and signing — are especially valuable.

## Supported versions

While the project is pre-1.0, only the latest released version of each package is supported with
security fixes.
