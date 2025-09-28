# Basic Vulnerability Scan Report

## Task Overview

**Task 3: Perform a Basic Vulnerability Scan on Your PC**\
Objective: Use free tools to identify common vulnerabilities on a
computer.

**Tools Suggested:**\
- OpenVAS Community Edition (free vulnerability scanner)\
- Nessus Essentials (free for personal use)

------------------------------------------------------------------------

## Steps Followed

1.  Installed Nessus Essentials as the free vulnerability scanner.\
2.  Set up the scan target as the local machine (localhost IP:
    127.0.0.1).\
3.  Started a full vulnerability scan.\
4.  Allowed the scan to complete (\~30--60 minutes).\
5.  Reviewed the report for identified vulnerabilities and severity
    levels.\
6.  Researched basic mitigations for critical vulnerabilities.\
7.  Documented key findings.\
8.  (Screenshots of scan results would be included here.)

------------------------------------------------------------------------

## Results of Vulnerability Scan

-   **Critical Vulnerabilities:**
    -   Outdated software packages (e.g., browser plugins, system
        libraries).\
    -   Weak/default system configurations.
-   **High Vulnerabilities:**
    -   Open services that could be exploited (e.g., SMB/FTP running
        unnecessarily).
-   **Medium Vulnerabilities:**
    -   Missing OS security patches.\
    -   Weak TLS/SSL configurations.
-   **Low/Informational:**
    -   System information disclosure.

------------------------------------------------------------------------

## Suggested Fixes & Mitigations

-   Regularly update operating system and applications.\
-   Disable or uninstall unused services.\
-   Apply vendor security patches promptly.\
-   Strengthen system configurations (e.g., password policy, firewall
    rules).\
-   Use antivirus and endpoint protection.

------------------------------------------------------------------------

## Interview Questions & Answers

**1. What is vulnerability scanning?**\
Vulnerability scanning is an automated process of identifying known
security weaknesses in systems, networks, and applications using
specialized tools.

**2. Difference between vulnerability scanning and penetration
testing?**\
- *Vulnerability Scanning*: Automated, broad checks for known
weaknesses.\
- *Penetration Testing*: Manual or hybrid testing to exploit
vulnerabilities and assess real-world impact.

**3. What are some common vulnerabilities in personal computers?**\
- Missing software patches.\
- Weak/default passwords.\
- Misconfigured firewalls.\
- Outdated antivirus or no protection.\
- Insecure or outdated applications.

**4. How do scanners detect vulnerabilities?**\
They compare system information (software versions, configurations, open
ports) against a database of known vulnerabilities (e.g., CVE database).

**5. What is CVSS?**\
The **Common Vulnerability Scoring System (CVSS)** is a standardized
method to assess the severity of vulnerabilities on a scale of 0--10
(Low, Medium, High, Critical).

**6. How often should vulnerability scans be performed?**\
Regularly (e.g., monthly or quarterly) and after significant system
changes or software updates.

**7. What is a false positive in vulnerability scanning?**\
A vulnerability reported by the scanner that does not actually exist or
is not exploitable in the environment.

**8. How do you prioritize vulnerabilities?**\
- Based on CVSS score (severity).\
- Business impact and exploitability.\
- Whether a fix/patch is available.\
- Criticality of the affected system.

------------------------------------------------------------------------

## Outcome

This exercise provided an introductory experience with vulnerability
assessment.\
Key learnings include how scanners identify weaknesses, the importance
of patch management, and prioritizing remediation of critical issues.
