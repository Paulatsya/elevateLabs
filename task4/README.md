# Firewall Configuration and Testing Report

## Task Overview

**Task 4: Setup and Use a Firewall on Windows/Linux**\
Objective: Configure and test basic firewall rules to allow or block
traffic.

**Tools Suggested:**\
- Windows Firewall\
- UFW (Uncomplicated Firewall) on Linux

------------------------------------------------------------------------

## Steps Followed

1.  Opened the firewall configuration tool:

    -   On Linux: used `ufw` (Uncomplicated Firewall).\
    -   On Windows: opened *Windows Defender Firewall with Advanced
        Security*.

2.  Listed current firewall rules:

    -   Linux: `sudo ufw status verbose`\
    -   Windows: Checked inbound/outbound rules in GUI.

3.  Added a rule to block inbound traffic on **port 23 (Telnet)**:

    -   Linux: `sudo ufw deny 23/tcp`\
    -   Windows: Added inbound rule blocking TCP port 23.

4.  Tested the rule by attempting to connect to the blocked port
    (connection failed as expected).

5.  Added a rule to allow **SSH (port 22)** (Linux only):

    -   `sudo ufw allow 22/tcp`

6.  Removed the test block rule to restore original state:

    -   Linux: `sudo ufw delete deny 23/tcp`\
    -   Windows: Deleted the inbound rule blocking port 23.

7.  Documented commands and GUI steps.

8.  Summarized how firewall filters traffic.

------------------------------------------------------------------------

## Example Firewall Rules (Linux UFW)

``` bash
# Check current status
sudo ufw status verbose

# Block Telnet (port 23)
sudo ufw deny 23/tcp

# Allow SSH (port 22)
sudo ufw allow 22/tcp

# Delete Telnet rule
sudo ufw delete deny 23/tcp
```

------------------------------------------------------------------------

## How Firewalls Filter Traffic

A firewall filters traffic by examining incoming and outgoing network
packets. Based on rules (allow/deny), it decides whether to permit or
block the traffic. This helps secure systems from unauthorized access
and network threats.

------------------------------------------------------------------------

## Interview Questions & Answers

**1. What is a firewall?**\
A firewall is a security system that monitors and controls network
traffic based on predefined rules, acting as a barrier between trusted
and untrusted networks.

**2. Difference between stateful and stateless firewall?**\
- *Stateful Firewall*: Tracks the state of network connections and
allows packets only if part of an established session.\
- *Stateless Firewall*: Filters packets individually without considering
connection state.

**3. What are inbound and outbound rules?**\
- *Inbound rules*: Control traffic coming into the system from outside.\
- *Outbound rules*: Control traffic leaving the system.

**4. How does UFW simplify firewall management?**\
UFW provides an easy-to-use command-line interface to configure firewall
rules without needing to write complex `iptables` commands.

**5. Why block port 23 (Telnet)?**\
Telnet is insecure because it transmits data (including passwords) in
plain text, making it vulnerable to interception. SSH is preferred
instead.

**6. What are common firewall mistakes?**\
- Allowing unnecessary open ports.\
- Misconfigured rules blocking essential services.\
- Not updating firewall configurations.\
- Assuming firewall alone provides full security.

**7. How does a firewall improve network security?**\
It prevents unauthorized access, reduces exposure to attacks, and
enforces access control policies.

**8. What is NAT in firewalls?**\
Network Address Translation (NAT) allows multiple devices on a private
network to share a single public IP address, improving security and
conserving IPs.

------------------------------------------------------------------------

## Outcome

This task demonstrated basic firewall management skills, including
listing rules, blocking and allowing ports, testing configurations, and
understanding how firewall rules secure a system.
