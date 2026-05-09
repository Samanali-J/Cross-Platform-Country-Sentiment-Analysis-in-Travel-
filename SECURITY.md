# Security Policy

## Supported Versions

This is an academic research project (COSC2671 Assignment 2) and does not follow a versioned release cycle. The current `main` branch is the only actively maintained version.

| Version / Branch | Supported          |
| ---------------- | ------------------ |
| `main`           | :white_check_mark: |
| Older commits    | :x:                |

## Reporting a Vulnerability

If you discover a security issue in this repository (e.g. exposed credentials, insecure API usage, or dependency vulnerabilities), please report it responsibly:

1. **Do not open a public GitHub issue** for security-sensitive findings.
2. Contact the repository owner directly via the email address on their GitHub profile.
3. Include a clear description of the vulnerability, steps to reproduce it, and any suggested remediation.

You can expect an acknowledgement within **48 hours** and a status update within **7 days**.

## Known Security Considerations

- **API credentials** — `redditClient.py` previously contained hardcoded Reddit API credentials. These should be replaced with environment variables or a secrets manager before any public deployment or sharing. If you have found exposed credentials in this repo, please report them immediately so they can be rotated.
- **Dependency security** — third-party libraries (`praw`, `transformers`, `networkx`, etc.) should be kept up to date. Run `pip list --outdated` periodically to check for vulnerable versions.
- **Data privacy** — datasets contain publicly sourced social media content. No personally identifiable information (PII) is intentionally stored, but care should be taken before redistributing raw data files.
