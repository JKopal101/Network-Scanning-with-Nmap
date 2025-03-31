# Network Scanning with Nmap

### Project Overview

Nmap is a scanner used for determining ports and certain characteristics on a network, such as hosts, services, and potential vulnerabilities. The goal is to gain practical experience with Nmap’s scanning capabilities, analyze the results, and learn how to interpret them for cybersecurity purposes. The **Metasploitable** machine will be used for testing purposes, as it is a deliberately vulnerable machine.

---

### Approach & Tools

### Environment Setup
- Deployed a controlled test network environment using **VirtualBox**.
- Configured **Kali Linux** as the primary scanning tool.

### Tools Used
- **Kali Linux**: A penetration testing distribution with pre-installed security tools.
- **Nmap (Network Mapper)**: A powerful open-source tool for network discovery and security auditing.

### Procedure
- Identified the target systems within the test network.
- Used various Nmap scanning techniques (e.g., **ping sweep**, **SYN scan**, and **OS detection**) to gather network and host information.
- Analyzed scan results to identify **open ports**, **running services**, and **potential vulnerabilities**.

---

### Why Metasploitable Instead of My Home Network?

- **Ethical Considerations**: Scanning a live home network could disrupt devices or services unintentionally.
- **Safe Environment**: The test network is isolated, ensuring that no unintended data exposure occurs.
- **Customizability**: Metasploitable is deliberately vulnerable, so it reveals more vulnerabilities for targeted learning.

---

### Implementation & Findings

### Steps Taken
1. Launched Kali Linux and verified network connectivity to the Metasploitable VM.
2. Performed different types of scans, including:
   - **Ping Sweep**: Identified live hosts.
   - **Host Discovery Command**: Checked which hosts are up without scanning ports.
   - **Basic Port Scan**: Selected key ports to scan.
   - **Service Version Detection**: Checked versions of services.
   - **Full TCP Scan**: Scanned all TCP ports.
   - **Aggressive Scan**: Comprehensive scan of the network.
   - **SYN Scan**: Detected open ports and services.
   - **OS Detection**: Identified operating systems of targets.
3. Documented and analyzed findings from each scan.

**Metasploitable Machine IP**: `192.168.1.83`  
**Network Setup**: Both VMs used a **Bridged Adapter** to be recognized on the same network.

---

### Nmap Commands Used

#### Host Discovery Command
```bash
nmap -sn 192.168.1.83
```

#### Basic Port Scan
```bash
nmap -p 80,443 192.168.1.83
```

#### Service Version Detection & TCP Ports
```bash
nmap -sT -sV 192.168.1.83
```

#### Aggressive Scan
```bash
nmap -A 192.168.1.83
```

---

### Sample Aggressive Scan Output

```
Starting Nmap 7.95 ( https://nmap.org ) at 2025-02-03 15:47 EST
Nmap scan report for 192.168.1.83
Host is up (0.00078s latency).
Not shown: 977 closed tcp ports (reset)
PORT     STATE SERVICE    VERSION
21/tcp   open  ftp        vsftpd 2.3.4
...
8180/tcp open  http       Apache Tomcat/Coyote JSP engine 1.1
MAC Address: 08:00:27:2C:F8:2D (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Running: Linux 2.6.X
OS details: Linux 2.6.9 - 2.6.33
Network Distance: 1 hop
...
Nmap done: 1 IP address (1 host up) scanned in 33.25 seconds
```

---

## Summary

- **Host Discovery** is used to identify the presence of assets and potential threats.
- **Basic Port Scans** reveal service exposure that could be exploited.
- **Service Version Detection** maps the services to specific vulnerabilities.
- **Full TCP Scans** provide a comprehensive view of the network's attack surface.
- **Aggressive Scans** gather detailed insights into system status.

### Key Observations
- Nmap successfully identified all live hosts in the network.
- Open ports included common services like **SSH (22)**, **HTTP (80)**, and **FTP (21)**.
- Detected **outdated versions** of services, highlighting potential vulnerabilities.
- OS detection revealed detailed system information, including probable versions.

---

### Solutions & Recommendations

### Addressing the Issues

#### Vulnerable Services
- Update outdated services to mitigate potential exploits.
- Implement firewalls to restrict unnecessary open ports.

#### Network Security
- Configure **Intrusion Detection Systems (IDS)** to monitor scanning activities.
- Employ **network segmentation** to limit exposure of critical systems.

> Follow up with additional scans after applying patches and deploying security tools.

---

### Conclusion & References

This project provided valuable hands-on experience with Nmap and its various scanning techniques within a controlled test network using the Metasploitable machine.

### References
- [Nmap Documentation](https://nmap.org/docs.html)
- [Kali Linux](https://www.kali.org)
- [OWASP Network Security Testing Guide](https://owasp.org/www-project-network-security-testing-guide/)
