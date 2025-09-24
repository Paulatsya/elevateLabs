# Local Network Port Scan with Nmap

## Overview
This repository documents a local network reconnaissance exercise to discover open TCP ports on devices within a private /24 segment using an Nmap TCP SYN scan, with results saved to a text file for evidence and auditability. The raw results are stored in `scan_results.txt`, and this README focuses on interpretation, risks, and remediation rather than reproducing the full output inline to keep the report concise.

## Scope and Command
- **Target:** 10.254.203.0/24 (authorized internal segment) scanned with a TCP SYN technique to rapidly determine port states without completing full handshakes.
- **Command executed:**
```bash
nmap -sS -oN scan_results.txt 10.254.203.0/24
```

## Results Summary
- **Hosts up:** 10 as reported by the scan footer, indicating active devices responded during probe windows on the subnet.
- **Observed open TCP services** across hosts include 80/tcp (http), 5000/tcp (upnp), 7000/tcp (afs3-fileserver), 49152/tcp (unknown/high-ephemeral), and 62078/tcp (iphone-sync), as recorded in `scan_results.txt` for follow-up validation and hardening.
- **Several ports reported filtered** (e.g., 7/tcp echo, 23/tcp telnet, 8000/tcp http-alt, 8080/tcp http-proxy), indicating packet filtering prevented a definitive open/closed determination.

## How to Interpret the States
- **open:** A service accepted the SYN with a SYN/ACK; Nmap infers a listening application and reports it as open.
- **closed:** The host is reachable but returned an RST to the SYN probe, meaning nothing is listening on that port at scan time.
- **filtered:** A firewall or packet filter blocked the probes or responses; Nmap cannot determine if the port is open or closed.
- **SYN scan behavior:** `-sS` sends SYN and classifies SYN/ACK as open and RST as closed without completing the TCP handshake, which is quick and broadly reliable for TCP enumeration.

## Risk Highlights from Findings
- **80/tcp open:** HTTP service in cleartext; consider TLS migration or restricted access if internal only.
- **5000/tcp open (UPnP):** Device control/discovery interface reachable; restrict or disable if not required to reduce lateral-movement risk.
- **62078/tcp open (iPhone sync):** Limit to trusted hosts or disable if unnecessary.
- **Filtered results:** Controls exist but do not guarantee safety; review policies to ensure default-deny with explicit allowlists.

## Recommended Next Actions
- **Confirm services and versions:**
```bash
nmap -sS -sV -p 80,5000,7000,49152,62078 <host>
```
- **Tighten exposure:** Enforce least-privilege firewall rules, disable unused services, and segment user, management, and IoT/VLAN zones.
- **Optional UDP spot checks:** Run selective UDP scans on critical ports only (e.g., DNS on 53/udp).
- **Preserve machine-readable outputs:** Consider `-oX` or `-oA` for future scans to support post-processing and reporting.

## Re-run and Extend (If Time Allows)
- **Live hosts first:**
```bash
nmap -sn 10.254.203.0/24
```
- **Full TCP port sweep on a specific host:**
```bash
nmap -sS -p- -sV <host>
```
- **Ethical scope:** Only scan systems with explicit authorization within allowed policy and time window.

## Repository Contents
- `scan_results.txt`: Raw Nmap output for the 10.254.203.0/24 scan, stored as evidence and for future parsing.
- `README.md`: Methodology, interpretation, risks, and remediation recommendations.

## Interview Q&A
- **What is an open port?**
  An endpoint where a listening service accepts connections or datagrams, necessary functionality but expands attack surface if unmanaged.
- **How does Nmap perform a TCP SYN scan?**
  Sends SYN probes; interprets SYN/ACK as open and RST as closed without completing the handshake.
- **What risks are associated with open ports?**
  Open ports expose services that may be vulnerable or misconfigured.
- **Explain the difference between TCP and UDP scanning.**
  TCP scans provide clear feedback using handshake semantics; UDP scans are slower and often ambiguous.
- **How can open ports be secured?**
  Restrict exposure via firewall rules, disable unnecessary services, segment networks, and keep services patched.
- **What is a firewall’s role regarding ports?**
  Evaluates traffic against rules; best practice is default-deny and explicit allowlists.
- **What is a port scan and why do attackers perform it?**
  Systematically probes ports to discover reachable services and enumerate entry points.
- **How does Wireshark complement port scanning?**
  Captures packets to validate scan behavior, confirm SYN/SYN-ACK/RST patterns, and troubleshoot filtered results.

## Notes
- Focuses on interpreting Nmap port states and prioritizing remediation.
- Preserves raw output for traceability and future parsing.

## References
- Nmap Port Scanning Basics
- Nmap Reference Guide (man)
- TCP SYN Scan (-sS) details
- UDP scan behavior and ambiguity
- Firewall rules and least privilege
- Ethical scanning reminders
- Host discovery with `-sn`
- Common port references, including 62078/tcp
- Open port risk perspective

