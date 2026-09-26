# Security policy

## Report privately

For a security-sensitive issue, use this repository's **Security → Report a vulnerability** option when private vulnerability reporting is enabled. Do not open a public issue containing vulnerability details that require private handling, credentials or real assessment data.

If the private reporting option is unavailable, open only a minimal public request for a private contact route, without the sensitive details. Wait for a private channel before sharing them.

Include the exact Umbra version and script checksum, the relevant Windows and PowerShell versions, the expected and observed behavior, and a minimal reproduction using synthetic data. Do not include passwords, tokens, private keys, session material, raw reports or confidential infrastructure information.

## Handle assessment data carefully

Treat TXT, CSV and diagnostic output as confidential. Hidden secret values do not make paths, account names, computer names or endpoints anonymous. Do not attach live output to issues or pull requests.

If a real credential has already been exposed, contact its owner and revoke or rotate it as appropriate. Removing a file does not necessarily remove copies from repository history or other locations.

## Scope of this policy

This policy describes how to report security problems in Umbra. It does not grant permission to assess any system, promise a response deadline or certify that an assessment is complete.
