<div align="center">

# UMBRA

*In the deepest dark, the light.*

### Find exposed credentials. Understand the risk.

**Windows PowerShell 5.1 · Single file · Offline-first**

[Why Umbra?](#why-umbra) · [Scope](#know-the-scope) · [Download](https://github.com/s33ke3/Umbra/releases/tag/v4.2.4-public1) · [Security policy](SECURITY.md)

</div>

---

## Why Umbra?

Credentials can be left behind in configuration files, scripts, application settings and other local artifacts. Finding those traces helps security teams understand where sensitive information is exposed and what needs attention.

**Umbra brings local credential exposure discovery into one PowerShell script.** It is designed for authorized security assessments, lab environments and defensive triage, with an emphasis on useful findings and clear coverage limits.

The goal is practical: make exposed secrets easier to find, investigate and remediate.

## Built to stay simple

**One script.** The Windows edition is distributed as a single `.ps1` file. It uses Windows PowerShell and the components available to it, without requiring third-party PowerShell modules.

**Offline-first.** Local assessment is the default workflow. Umbra does not require a cloud service. Optional network-root access is separate from the default local scope and must be explicitly authorized.

**Useful context.** Findings include information that helps explain where an exposure was observed. A detected value is a lead for investigation, not proof that a credential is valid.

**Visible limits.** Access restrictions, unreadable inputs, unsupported formats and partial coverage matter. Review them alongside the findings rather than treating a finished run as a clean bill of health.

## Know the scope

This repository contains **Umbra for Windows**, version **4.2.4**, publication revision **public1**. The runtime version remains `4.2.4` and the script filename remains `Umbra_v4.2.4.ps1`. The script requires **Windows PowerShell 5.1, Desktop edition**. It is not a PowerShell 7 or Linux release.

The assessment workflow includes targeted local checks, environment settings, registry checks and, depending on the selected mode, a broader filesystem phase. Actual coverage depends on the options, account permissions and artifacts present on the host.

> **A path is not a sandbox.** In this version, `-Path` limits the full filesystem phase. It does not restrict every targeted, environment or registry check to that directory. Do not use it as a whole-process isolation boundary.

Git history is outside the supported credential-discovery scope. A finding that identifies a protected or encrypted artifact does not mean its contents have been decrypted or that authentication has been tested.

**Read the parameter notes at the top of the script and its `param` block before use.** The inherited header retains an older `-candidate.ps1` filename in its examples; the distributed filename is `Umbra_v4.2.4.ps1`. `Get-Help` can show parameter syntax, but this version does not provide a complete comment-based help manual.

Start in a controlled environment with synthetic data, an explicitly authorized scope and an agreed approach to handling findings.

## Treat results as confidential

Umbra writes TXT and CSV results. Captured secret values are redacted by default, but **redaction is not anonymization**.

Result filenames include the computer name and a timestamp. Results can also contain paths, account names, endpoints and application details. Do not publish real results, even when passwords appear hidden. Options that reveal captured values require additional care.

A match is not necessarily a live credential. False positives are possible, and an empty result does not establish that a system is free of exposed secrets. Broad assessments can take substantial time; inspect the final summary, output status and coverage limitations together.

## Tests and feedback

The script includes a SelfTest with embedded test inputs. These intentionally resemble passwords, tokens, connection strings and credential artifacts, so secret scanners may flag them. Review alerts in context rather than excluding the whole script from scanning.

**Publication revision public1:** two historical `cpassword` recognition fixtures now contain the Base64 encoding (without trailing padding) of the synthetic marker `UMBRA_SYNTHETIC_TEST_DATA_000001`. This is recognition-only test data, not a valid encrypted GPP password or a credential intended for authentication. Output-filename fixtures also use synthetic host and date values. Changes are limited to eight test-data lines; production code and test assertions are unchanged. This revision has not been requalified by running the complete SelfTest on Windows PowerShell 5.1 in the preparation environment.

For public bug reports, include the tool version, Windows and PowerShell versions, and a minimal example using entirely synthetic data. Never attach real credentials, raw assessment output, private keys, client information or confidential training material.

For security-sensitive reports, follow [SECURITY.md](SECURITY.md).

## Responsible use

Use Umbra only on systems you own or are explicitly authorized to assess. Respect the agreed scope and protect any information discovered during an assessment.

## Credits

Maintained on GitHub by [s33ke3](https://github.com/s33ke3).

> Summoned by: An0mal1  
> Manifested by: The Ghost in The Machine


## License

See [LICENSE](LICENSE) for the terms governing this release.
