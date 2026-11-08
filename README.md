# Phishing Email Investigation

SOC-style investigation of a real-world phishing email: a spoofed "Microsoft account unusual signin activity" alert.

**Verdict:** Malicious. High confidence the email is malicious; medium confidence on its exact purpose (callback lure with open tracking, no credential-harvesting page observed).

## What this covers
- Email header analysis: sender mismatch (From, Return-Path, Reply-To), SPF/DKIM/DMARC results, Received chain
- Body analysis: `mailto:` callback links, hidden 1x1 tracking pixel, filler text
- Infrastructure checks: WHOIS, DNS, VirusTotal, AbuseIPDB, RIPE
- Campaign pivot: searched the full phishing_pot corpus for the indicators (the tracking domain appears in 217 emails, the sending IP in 26)
- Defanged IOC list, MITRE ATT&CK mapping, response actions and detection ideas
- Limitations: what could not be verified, and why

## Sample and safety
- Sample: `sample-10.eml` from the public [phishing_pot](https://github.com/rf-peixoto/phishing_pot) corpus
- The email was read as plain text only in a Kali Linux VM. It was never opened in a mail client, no URL was visited, and nothing was detonated.
- All indicators are defanged (`hxxp`, `[.]`). The original .eml is not included.

## Tools
Linux command line (`sed`, `grep`, `less`, `whois`, `dig`), VirusTotal, AbuseIPDB, CyberChef, Python (corpus search)

## Repository contents
- `report.pdf`: full investigation report with step-by-step screenshots
- `iocs.csv`: indicators with context and verdicts (remove this line if you didn't upload it)

## Author
Tushar Mishra, B.Tech Cybersecurity student, UPES
