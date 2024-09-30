# Secure Remote Access Configuration for Home CCTV System

## Overview
This lab outlines the process of configuring secure remote access for a home CCTV system by using port forwarding and understanding the implications of using different protocols (TCP/UDP). Additionally, we will review the use of NTP (Network Time Protocol) for time synchronization and analyze security risks associated with wide port range configurations.

## Objective
- To configure secure remote access to a CCTV system using port forwarding.
- To understand the differences between TCP and UDP protocols.
- To evaluate the security implications of broad port ranges and restrict access to necessary ports.
- To document the configuration of NTP settings and ensure accurate system time for CCTV recordings.

## Prerequisites
- Basic knowledge of networking (ports, protocols, firewall rules).
- Access to the router settings and the CCTV system’s network configuration interface.
- Tools: Web browser, router admin login, NVR/CCTV system.

## Lab Setup
1. **CCTV System**: Reolink RLN8-410 8-Channel NVR (or any compatible NVR system).
2. **Router**: (info hidden for security reasons) (ensure you have admin access).
3. **Network Details**: IP address for NVR, router configuration page.

## Lab Steps

   ### 1. Log in to the Router Settings
   - Open your browser and go to your router’s configuration page (typically `192.168.1.1` or `192.168.0.1`).
   - Log in using the admin credentials.

   ### 2. Configure Port Forwarding
   - Navigate to the **Port Forwarding** or **Virtual Server** settings.
   - Create a new rule:
     - **Service Name**: CCTV Remote Access
     - **Protocol**: TCP/UDP
     - **External Port**: 12345
     - **Internal Port**: 12345 (or your NVR’s configured port)
     - **Internal IP**: [NVR’s local IP address]
     - **Enable Rule**: Yes

   ### 3. Enable NTP Time Synchronization on the NVR
   - Log into your NVR’s settings panel.
   - Go to **System** > **NTP Settings**.
   - Configure the following:
     - **NTP Server**: `pool.ntp.org`
     - **Port**: 123 (UDP)
     - **Synchronization Interval**: 3600 seconds (1 hour)
   - Save and apply the settings.

   ### 4. Verify the Setup
   - Open a browser on a remote device and navigate to `http://[PublicIP]:12345`.
   - Ensure that you can view the live feed and that timestamps are accurate.

   ### 5. Security Assessment
   - Identify open ports using `nmap` or a similar tool to ensure only the necessary ports are open.
   - Implement strong passwords and disable unnecessary services like Telnet if present.

## Results and Observations
- Successful remote access was achieved using port 12345.
- NTP time synchronization ensured accurate event logging on the CCTV system.
- Security risks identified with a broad port range configuration.

## Recommendations
- Limit port ranges to reduce potential attack vectors.
- Use a VPN for remote access instead of direct port forwarding.
- Enable SSL/TLS encryption for all web-based communication with the NVR.

## Conclusion
This lab demonstrated the process of securely configuring remote access to a CCTV system while analyzing potential security risks and optimizing NTP settings for accurate time management.
