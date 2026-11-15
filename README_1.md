# SOC Copilot

A free, single-file triage helper for SOC analysts. Paste a security alert, log snippet or suspicious email and get a quick assessment: verdict, severity, MITRE ATT&CK mapping, defanged indicators of compromise (IOCs) and suggested triage steps.

**Created by [Prashant Pahwa](https://www.linkedin.com/in/prashant-pahwa-cism/), CISM** | Security operations leader, 18+ years in cybersecurity

[![License: CC BY 4.0](https://img.shields.io/badge/License-CC%20BY%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by/4.0/)

## Features

- **Two modes:** security alert or log analysis, and suspicious email analysis
- **Verdict and severity:** Likely True Positive, Suspicious, Low Confidence or Insufficient Evidence, with Critical to Informational severity
- **MITRE ATT&CK mapping** with the evidence that triggered each technique
- **IOC extraction:** IPs, domains, URLs, email addresses and file hashes, shown defanged for safe sharing
- **Local decoding:** Base64 `-EncodedCommand` PowerShell is decoded in your browser
- **Email heuristics:** SPF, DKIM and DMARC failures, Reply-To mismatch, urgency language, risky attachment types, deceptive link hosts
- **Triage output:** next steps, recommended containment (marked as needing approval), questions for the user, and false-positive checks
- **Copy triage note** button for pasting into a ticket
- **Three built-in samples:** impossible-travel sign-in with a mailbox forwarding rule, encoded PowerShell launched from Word, and an invoice phishing email

## Privacy

Everything runs in your browser. Nothing you paste is uploaded, stored or sent anywhere. Still, remove sensitive data before pasting into any tool.

## Use it

- **Locally:** download `index.html` and open it in a browser.
- **Free hosting with GitHub Pages:** in this repository go to Settings, Pages, choose the main branch and root folder, and save. GitHub gives you a public URL.

## What it detects

The detection engine is a set of transparent pattern rules, not machine learning. Current coverage:

| Area | Examples | ATT&CK |
| --- | --- | --- |
| Encoded and hidden PowerShell | `-Enc`, hidden window, download cradles | T1059.001, T1027, T1105 |
| Malicious documents | Office app spawning a shell | T1204.002 |
| Credential theft | LSASS access, Mimikatz-style tools | T1003 |
| Ransomware precursors | Shadow copy or backup deletion, ransom wording | T1490, T1486 |
| Account takeover | Impossible travel, legacy auth, no MFA | T1078 |
| BEC | Mailbox forwarding and inbox rules | T1114.003 |
| MFA fatigue | Repeated push prompts | T1621 |
| Exfiltration | Uploads, archives, bulk downloads | T1567 |
| Phishing | Link and attachment lures, credential requests | T1566.001, T1566.002, T1598 |

ATT&CK IDs were validated against ATT&CK Enterprise v20.1.

## Limits

- It is a first-pass aid. It can miss threats and can flag benign activity, so an analyst must make the final call.
- It does not check threat-intelligence reputation, sandbox files or query your tools.
- A "Benign" or "Insufficient Evidence" result is not proof that activity is safe.
- Rules are tuned for common Windows, Microsoft 365 and email scenarios.

## Customize

All rules live in the `localAnalyze` function inside `index.html`. Add a pattern, a score and an ATT&CK technique to extend it. If you share your changes, please keep the attribution.

## Related project

Pair it with the [Incident Response Playbook Pack](#) for step-by-step response procedures. Replace `#` with the link to that repository.

## License and attribution

Licensed under [Creative Commons Attribution 4.0 International (CC BY 4.0)](https://creativecommons.org/licenses/by/4.0/). You may share and adapt this work, including commercially, if you:

- credit **Prashant Pahwa** and link to this repository or his LinkedIn profile,
- link to the license, and
- indicate if you made changes.

Suggested credit: *"SOC Copilot by Prashant Pahwa, licensed under CC BY 4.0."*

## Feedback

Issues and pull requests are welcome. Connect on [LinkedIn](https://www.linkedin.com/in/prashant-pahwa-cism/).
