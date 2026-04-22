# Security Policy

## Reporting a Vulnerability

Please report suspected vulnerabilities **privately** via GitHub's
[Private Vulnerability Reporting](https://github.com/3ncr/3ncr.org/security/advisories/new)
on the Security tab. Do not file public issues for security-sensitive reports.

This covers both the [v1 envelope specification](https://3ncr.org/1/) itself
(e.g. a flaw that lets an attacker forge or recover plaintext across all
conforming implementations) and the site content — notably the in-browser
[WebCrypto demo](https://3ncr.org/1/demo/), which runs untrusted input through
`SubtleCrypto` in the visitor's browser.

We aim to acknowledge reports within 5 business days and to ship a fix or
documented mitigation within 30 days for confirmed vulnerabilities, depending
on severity and complexity. Spec-level issues are coordinated across every
[official implementation](https://3ncr.org/1/#implementations) before public
disclosure.

## Supported Versions

The `3ncr.org/1#` envelope (AES-256-GCM, 12-byte random IV, 16-byte GCM tag)
is the only supported format. There is no v0 or v2.

| Envelope | Supported |
| -------- | --------- |
| v1       | Yes       |
