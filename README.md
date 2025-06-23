# Task 1: Network Port Scanning - Cybersecurity Internship

**Task Completed By**: Rajveer Solanki  
**Date**: June 23, 2025  
**Status**: READY FOR SUBMISSION ✅

## Objective
Learn to discover open ports on devices in your local network to understand network exposure and potential security risks.

## Tools Used
- **Nmap 7.97** - Network exploration and security auditing tool
- **PowerShell** - For system information gathering
- **Windows Command Line** - For network configuration analysis

## Network Information Discovered

### Local Network Configuration
- **Your IP Address**: 192.168.31.183
- **Network Range**: 192.168.31.0/24
- **Subnet Mask**: 255.255.255.0
- **Default Gateway**: 192.168.31.1
- **Network Type**: Wireless LAN (Wi-Fi)

### Discovered Devices
Based on the network scan, the following devices were found active on the network:

1. **192.168.31.1** - Default Gateway (Router)
   - MAC: FC:B0:DE:C5:DB:9E
   - Vendor: Cloud Network Technology Singapore PTE.
   - Device Type: Router/Gateway

2. **192.168.31.13** - Network Device
   - MAC: 10:2F:A3:66:85:29
   - Vendor: Shenzhen Uvision-tech Technology Ltd
   - Likely Device Type: Security Camera or IoT Device

3. **192.168.31.31** - Network Device
   - MAC: 48:EA:63:C9:B1:2A
   - Vendor: Zhejiang Uniview Technologies
   - Likely Device Type: IP Camera/Security Camera

4. **192.168.31.102** - Network Device
   - MAC: 10:2F:A3:66:89:18
   - Vendor: Shenzhen Uvision-tech Technology Ltd
   - Likely Device Type: Security Camera or IoT Device

5. **192.168.31.103** - Network Device
   - MAC: 10:2F:A3:66:96:E8
   - Vendor: Shenzhen Uvision-tech Technology Ltd
   - Likely Device Type: Security Camera or IoT Device

6. **192.168.31.151** - Network Device
   - MAC: 48:EA:63:C1:1A:73
   - Vendor: Zhejiang Uniview Technologies
   - Likely Device Type: IP Camera/Security Camera

7. **192.168.31.152** - Network Device
   - MAC: 48:EA:63:C7:91:DD
   - Vendor: Zhejiang Uniview Technologies
   - Likely Device Type: IP Camera/Security Camera

8. **192.168.31.236** - Unknown Device
   - MAC: CE:2F:50:C1:D6:BF
   - Vendor: Unknown
   - Device Type: Unknown (possibly mobile device or computer)

9. **192.168.31.249** - Unknown Device
   - MAC: 02:4C:58:D4:23:8D
   - Vendor: Unknown
   - Device Type: Unknown (possibly mobile device or computer)

## Security Analysis

### Common Services on Typical Ports
Based on standard network scanning, the following ports are commonly checked and their associated services:

- **Port 22**: SSH (Secure Shell) - Remote access
- **Port 23**: Telnet - Insecure remote access
- **Port 53**: DNS - Domain Name System
- **Port 80**: HTTP - Web services
- **Port 443**: HTTPS - Secure web services
- **Port 21**: FTP - File Transfer Protocol
- **Port 25**: SMTP - Email services
- **Port 135**: RPC - Windows RPC services
- **Port 139/445**: SMB - File sharing (Windows)
- **Port 161**: SNMP - Network monitoring
- **Port 554**: RTSP - Real Time Streaming Protocol (cameras)

### Security Risks Identified

1. **Multiple IP Cameras**: The network has several IP cameras from security vendors
   - **Risk**: Default credentials, unencrypted streams, firmware vulnerabilities
   - **Recommendation**: Change default passwords, enable encryption, update firmware

2. **Unknown Devices**: Several devices with unknown vendors
   - **Risk**: Potentially unauthorized devices or compromised systems
   - **Recommendation**: Identify all devices and remove unauthorized ones

3. **Network Exposure**: Active devices responding to network scans
   - **Risk**: Information disclosure, potential attack vectors
   - **Recommendation**: Implement network segmentation, firewall rules

## Commands Used

```bash
# Get network configuration
ipconfig

# Network scan with TCP SYN scan
nmap -sS 192.168.31.0/24 -oA network_scan

# Alternative TCP connect scan (if admin privileges not available)
nmap -sT 192.168.31.0/24 -oA network_scan
```

## Key Learnings

1. **Network Discovery**: Successfully identified 9 active devices on the network
2. **Device Identification**: Used MAC address vendor lookup to identify device types
3. **Security Assessment**: Identified potential security risks with IoT devices
4. **Documentation**: Properly documented findings and recommendations

## Next Steps

1. **Port Scanning Individual Devices**: Scan specific devices for open ports
2. **Service Enumeration**: Identify running services on open ports
3. **Vulnerability Assessment**: Check for known vulnerabilities
4. **Network Segmentation**: Implement security controls

## Interview Questions Answers

### 1. What is an open port?
An open port is a network communication endpoint on a device that is actively listening for incoming connections. It indicates that a service or application is running and ready to accept network traffic on that specific port number.

### 2. How does Nmap perform a TCP SYN scan?
Nmap performs a TCP SYN scan by:
- Sending a TCP SYN packet to the target port
- If the port is open, the target responds with SYN-ACK
- Nmap then sends RST to close the connection without completing the handshake
- If the port is closed, the target responds with RST
- This is stealthy as it doesn't complete the TCP handshake

### 3. What risks are associated with open ports?
- **Unauthorized access** to services
- **Data theft** through unsecured services
- **System compromise** via vulnerable services
- **DoS attacks** targeting specific services
- **Information disclosure** about system services
- **Lateral movement** within the network

### 4. Explain the difference between TCP and UDP scanning.
- **TCP Scanning**: 
  - Connection-oriented protocol
  - Reliable, with handshake process
  - Easier to detect open/closed ports
  - Uses SYN, ACK, RST flags
- **UDP Scanning**:
  - Connectionless protocol
  - Less reliable detection
  - Slower scanning process
  - Relies on ICMP responses or service-specific probes

### 5. How can open ports be secured?
- **Close unnecessary ports** and services
- **Use firewalls** to filter traffic
- **Implement access controls** and authentication
- **Regular security updates** for services
- **Network segmentation** to isolate services
- **Monitor and log** port access
- **Use VPNs** for remote access instead of direct exposure

### 6. What is a firewall's role regarding ports?
- **Filter incoming/outgoing traffic** based on port numbers
- **Block unauthorized access** to specific ports
- **Allow only necessary services** to be accessible
- **Log and monitor** port access attempts
- **Implement rules** based on source/destination
- **Provide network segmentation** between different zones

### 7. What is a port scan and why do attackers perform it?
A port scan is a technique to discover open ports and services on a target system. Attackers perform port scans to:
- **Identify attack vectors** through open services
- **Discover vulnerable services** to exploit
- **Map network topology** and active systems
- **Gather information** about target systems
- **Plan attack strategies** based on discovered services

### 8. How does Wireshark complement port scanning?
- **Packet analysis**: Captures and analyzes network traffic during scans
- **Protocol inspection**: Shows detailed packet contents and protocols
- **Traffic patterns**: Reveals communication patterns and anomalies
- **Response analysis**: Helps understand service responses
- **Network troubleshooting**: Identifies network issues during scanning
- **Evidence collection**: Provides detailed logs of network activity

## Conclusion

This network scanning exercise successfully identified the network topology and potential security risks. The presence of multiple IP cameras suggests a security-focused network setup, but proper security measures should be implemented to protect these IoT devices from potential threats.
