#  Vulnerability Assessment Report — Nessus Essentials

##  Project Task
**Objective**: Perform a basic vulnerability scan on your own PC using a free tool (Nessus Essentials or OpenVAS), and identify existing vulnerabilities.

---

##  Steps Performed

###  Step 1: Nessus Installation
- Registered at [tenable.com](https://www.tenable.com/products/nessus/nessus-essentials) and downloaded **Nessus Essentials**.
- Installed Nessus on Windows.
- Accessed Nessus via `https://localhost:8834` and activated with a free license key.

###  Step 2: Scan Configuration
- Created a new scan using the **Basic Network Scan** template.
- Set the **target** to `127.0.0.1` (my own computer).
- Named the scan **"My Basic Network Scan"**.

###  Step 3: (Attempted) Authenticated Scan
- Configured Windows credentials (username + password).
- Enabled options like:
  - Start Remote Registry during scan
  - Enable admin shares
- Despite proper setup, **authenticated scan failed** (`Auth: Fail`) — likely due to SMB or firewall limitations.

###  Step 4: Running the Scan
- Launched the scan and let it run for about 30 minutes.
- Scan completed successfully with **34 findings**, including:
  - 2 medium vulnerabilities
  - 32 informational findings
  - 0 high or critical

---

##  Vulnerabilities Overview

| Severity | Count |
|----------|-------|
| Critical | 0     |
| High     | 0     |
| Medium   | 2     |
| Low      | 0     |
| Info     | 32    |

---

##  Key Vulnerabilities Found

###  1. **SSL Certificate Cannot Be Trusted**
- **Plugin ID**: [51192](https://www.tenable.com/plugins/nessus/51192)
- **Risk**: Medium (CVSS 6.5)
- **Description**: The SSL certificate presented by the server is self-signed or not trusted.
- **Fix**: Install a valid certificate from a trusted CA or configure your services to use a trusted certificate.

---

###  2. **SMB Signing Not Required**
- **Plugin ID**: [57608](https://www.tenable.com/plugins/nessus/57608)
- **Risk**: Medium (CVSS 5.3)
- **Description**: SMB signing is not enforced, which can allow man-in-the-middle (MITM) attacks.
- **Fix**: Enforce SMB signing via Group Policy on Windows

  
##  Takeaways

- Gained hands-on experience with Nessus Essentials.
- Understood how unauthenticated scans detect exposed services and basic misconfigurations.
- Learned the importance of:
- Credentialed scans
- Secure service configurations (like SMB signing)
- Keeping the system patched and firewalled properly
