# CVE-2025-26633 - Microsoft Management Console (.msc) EvilTwin Local Privilege Escalation PoC

> **Zero-day at time of disclosure (March 2025)** – Actively exploited in the wild by Water Gamayun APT  
> **ONLY FOR AUTHORIZED SECURITY TESTING AND RESEARCH**

![](https://img.shields.io/badge/CVSS-7.8%20High-red)
![](https://img.shields.io/badge/CVE-2025--26633-critical)
![](https://img.shields.io/badge/Platform-Windows-blue)
![](https://img.shields.io/badge/Type-Local%20Privilege%20Escalation-orange)

## Vulnerability Details

- **Exploit Title**: Microsoft Management Console (MMC) - MSC EvilTwin Local Privilege Escalation / Arbitrary Code Execution  
- **CVE**: [CVE-2025-26633](https://msrc.microsoft.com/update-guide/vulnerability/CVE-2025-26633)  
- **CVSS v3.1**: `7.8` (High) – `AV:L/AC:L/PR:L/UI:N/S:U/C:H/I:H/A:H`  
- **Affected Systems**:  
  - Windows 10 (all editions)  
  - Windows 11 (all editions)  
  - Windows Server 2016 – 2025  
  → **Unpatched systems before March 2025 Patch Tuesday**  
- **Patched in**: March 2025 updates (e.g., KB5053602 and later)  
- **Discovery & Disclosure**: Coordinated via Zero Day Initiative  
- **ZDI Advisory**: [ZDI-25-150](https://www.zerodayinitiative.com/advisories/ZDI-25-25-150/)  
- **Microsoft Advisory**: https://msrc.microsoft.com/update-guide/vulnerability/CVE-2025-26633

## Author

- **Mohammed Idrees Banyamer**  
  Jordan | Security Researcher  
  Instagram: [@banyamer_security](https://instagram.com/banyamer_security)  
  GitHub: [https://github.com/mbanyamer](https://github.com/mbanyamer)

## Proof of Concept

This repository contains a **proof-of-concept exploit** that demonstrates arbitrary command execution via a malicious `.msc` (MMC snap-in) file.

When a low-privileged user opens the crafted `.msc` file using `mmc.exe`, the embedded `RunCommand` action is executed **with the user's privileges** — allowing post-exploitation lateral movement or privilege escalation in certain attack chains.

The current PoC silently creates a local administrator account:

- Username: `hacker`
- Password: `P@ssw0rd123!`

### Usage 

```bash
python3 cve-2025-26633_poc.py
