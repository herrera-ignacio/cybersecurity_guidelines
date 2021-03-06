# Domain 2: Technologies & Tools

1. Install and configure network components, both hardware and software-based, to support organizational security.
2. Given a scenario, use appropriate software tools to assess the security posture of an organization.
3. Given a scenario, troubleshoot common security issues.
4. Given a scenario, analyze and interpret output from security technologies.
5. Given a scenario, deploy mobile devices securely.
6. Given a scenario, implement secure protocols.

## Networking Basics

Must know basics of:

* OSI Model and its layers
* DOM-3 mdoel
* IP Addressing
* DNS
* HTTP/S, TCP/IP, UDP.

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 1. Network Security Components

### Devices

#### Router

Connects computer networks.

* Operates at layer 3 (Network layer).
* Stores information about network destinations (routing tables).
* _Border Router_: outside connection of a LAN to a WAN.

#### Switch

Connects devices with a computer network by using packet switching to receive, process and forward data to the destination device.

* Operates either on layer 2 (data link) or layer 3 (network layer).
* Packet-forwarding decisions are based on _Media Access Control (MAC)_ addresses.

#### Bridge

Connect two different physical network.

* Layer 2 (data link).
* Replaced by switches.

#### Proxy

Boundary device between internal & external networks. It can be any device that acts on behalf of other(s), providing __security, logging and caching__.

* __Proxy Server__: blocks nown malicious websites.
* __Forward Proxy__: retrieves data on behalf of a client.
* __Reverse Proxy__: protects access to a server on the internal network.
* __Transparent proxy__ (inline, forced): caching server that redirects client requests without modifying them to reduce bandwith usage.

#### Load Balancer

Shifting burden from one device to another.

* Reduces response time.
* Maximizes throughput.
* Allows better allocation of resources.

There are different types:

* __Scheduling__: distributing load.
  * _Round-robin_: taking turns using a circular pattern.
  * _Affinity / Sticky sessions_: requests sent to a specific application.
  * _Least connections_
  * _Random_
* __Active/active__: servers work together.
* __Active/inactive__: all traffic is sent to the active server.
* __Virtual IPs (VIPs)__: at least one physical server is assigned, but more than one virtual IP address assigned.

#### Access Points

Consist of a transmitter and receiver (transceiver) device used to create a wireless LAN (WLAN).

* Typically wireless (WAP).
* Layer 2 (data link).
* Can operate as a Bridge connecting standard wired network to wireless devices or as a Router passing data transmissions from one AP to another.
* A _Centralized Access Controller (AC)_ is capable of providing management, configuration, encryption and policy settings for WLAN AP.

Three types:

* __Fat__: intelligent AP.
* __Fit__: scaled Fat AP.
* __Thin__: intelligent antennas (only transmit/receive).

Which can be _Controller-based_ or _Standalone_.

### Network Security Devices & Best Practices

#### Router security

* __Access Control Lists (ACLs)__: filtering packets by source address, destination address, protocol or port.
* __Zones__: segmenting networks based on functionality or security.
* __Antispoofing__: creating a set of access lists that deny access to private IP addresses and local host ranges from the internet.

#### Switch security

* __Virtual LANs (VLANs)__: segment networks & limit broadcast traffic.
* __Port security__ (_layer 2_): enable/disable individual switch ports based on MAC address.
  * Vulnerable to MAC address spoofing.
* __Loop prevention__: a loop is when data units can travel from a first LAN segment to a second LAN segment trough more than one path, which can happen on switches or bridges.
  * __Spanning Tree Protocol (STP)__, a link-management protocol that provides path redundancy while preventing undesirable loops in the network.
* __Flood Guard__: detect and prevent malicious traffic, normally associated with DoS attacks.

#### Wireless Management & Security

* SSID (Service Set Identifier)
  * Broadcast
  * Cloaked
* MAC Filtering
* Signal Strength
* Band Selection / Width
* Antenna types and placement
  * Omnidirectional
  * Directional

#### Firewalls

* Isolate one network from another.
* Network security device that monitors incoming and outgoing network traffic and decides whether to allow or block specific traffic based on a defined set of security rules (Cisco).
* Hardware (appliances), software or both.
* Network or host-based.

There are different types:

* __Packet filter__:
  * Passes or blocks traffic to specific ports or IP addresses based on rules.
  * _Access Control List (ACL)_ filter.
  * Little intelligence / stateless.
  * Faster than stateful inspection.
* __Proxy firewall__:
  * Acts as an intermediary.
  * Application Proxy.
  * Web Proxy.
* __Stateful packet inspection__:
  * Intelligent.
  * Analyzes data flows and traffic patterns.
  * Dynamic access control decisions.
  * Records are kept using a state table that tracks every communication channel.
  * Remembers where the packet came from and where next one should come from.

#### Firewall Rules

Configured to specify computers, programs, services, ports, or protocols.

* Order of firewall rules matters.
* __Implicit deny__: access or resource availability is restricted to only those that are explicitly granted access, all others are denied.

#### Application Firewalls

* Controls input, output, and/or access from, to, or by an application or service based on categories, rules, or heuristics.
* Deep packet inspection.
* Functions at layer 7 of the OSI model.
* _Web Application Firewall (WAF)_.
  * Protects web applications from known attacks (Injection, Buffer, Overflows, etc).
* Often included in other firewall types (Proxy, IDS/IPS).

#### IDS/IPS (Intrusion Detection/Protection Systems)

Like a burglar alamr, identify unauthorized activity, access or anomalies. They can be network-based or host-based.

* Snort (Windows & Linux)

IDS and IPS differs in whether to focus on _detection_ or _protection_:

* __Passive response (detection)__:
  * Logging.
  * Notification.
  * Shunning / Quarantine.
* __Active response (protection)__:
  * Terminating process or sessions.
  * Configuration changes.
  * _Deception Active Response_: attacker believes the attack is succeeding while the system monitors the activity and potentially redirects the attacker to a honeypot or logging system.

Also IDS/IPS can be further clasiffied by:

* __Signature/Knowledge based__:
  * Detects known vulenrabilities.
  * Rules / updates provided by vendor.
  * Reactive.
* __Behavior based__:
  * Outside of normal bounds / established profile.
  * Anomaly-based.
  * Potential for false positives.
* __Heuristic-based__:
  * Uses algorithms to analyze the activity / network traffic.
  * High initial overhead.

#### NIDS / NIPS (Network Instrusion Detection/Protection Systems)

* Analysis used to be separate, now is combined with Firewalls.
* _Passive_: traffic is mirrored to sensor.
* _Inline_: monitors traffic flow and prevent attacks in real time. Could cause latency.

#### VPN Concentrators

* A _Virtual Private Network (VPN)_ allows remote access into a network.
  * Site-to-Site.
  * User (host-to-site).
* VPN Concentrator.
  * Single device to funnel all VPN access / Connects VPN nodes.
  * Encrypted tunnels.
  * Centralized authentication (RADIUS, Kerberos, Federated ID).
* Always-on VPN.
* Network security through encryption.
  * _Internet Protocol Security (IPsec)_.
  * _Secure Sockets Layer (SSL)_.
* VPN Tunneling
  * __Full tunnel__: all requests are routed and encrypted through the VPN.
  * __Split tunnel__: only some (usually all incoming requests) are routed and encrypted over the VPN.

#### IPsec

Provides authentication services and encapsulation of data through support of the _Internet Key Exchange (IKE)_ protocol.

* Functions at layer 3 (Network layer) with the IP protocol.
* Three services:
  * Data verification.
  * Data tampering protection.
  * Private transactions.
* Two separate (mutually exclusive) protocols:
  * __Authentication Header (AH)__: authentication and integrity checking for data packets.
  * __Encapsulating Security Payload (ESP)__: encryption services.

#### UTM (Unified Threat Management) & NGFW (Next Generation Firewall)

An all-in-one appliance / single interface / single vendor:

* Network IDS / IPS.
* URL filtering (block websites based on category or URL).
* Content inspection (application aware).
* Malware inspection.

#### NAC: Network Access Control

Uses a set of protocols to define and implement a policy that describes how to secure access to network nodes by devices upon initial access (uses _IEEE 802.1X Standard_).

It consists of different components:

* __Access requestor (AR)__: Device that requests access. Assessment of the device can be self-performed or delegated to another system.
* __Policy decision point (PDP)__: System that assigns a policy based on the assessment. The PDP determines access.
* __Policy enforcement point (PEP)__: The device that enforces the policy. This device can be a switch, firewall, or router.

#### SIEM: Security Information & Event Management

SIEM tools collect, correlate, and display data feeds that support response activities.

* Log aggregation on a centralize server.
* Centrally managing security events.
* Correlating and normalizing events for context and alerting (automated alerting and triggers).
* Reporting on data gathered from various applications.

#### Data Loss Prevention . Data Leakage Protection (DLP)

* Prevent sensitive information from physically or logically leaving corporate systems by monitoring, detecting and blocking sensitive data while in use (endpoint actions), in motion (network traffic), and at rest (data storage).
* Designed to detect and prevent unauthorized use and transmission of confidential information.
* Network: _Content-filtering_ (proxy).
* System: _Application white-lising_.
* Hardware: _USB blocking_.
* Cloud data.

#### SSL / TLS Accelerators

* __SSL offloading__: shifting the burden of encrypting and decrypting traffic sent via SSL from the web server to another device.
* Accepts SSL/TLS connections from the endpoint and sends the connection to the server unencrypted.
* Associated with Load Balancers.

#### Gateways (Mail & Media)

* Centralization and routing.
* Encryption.
* Spam filters (Inbound / Outbound)
* Proxy servers (media).

#### HSM: Hardware Security Module

Hardware-based encryption that manages digital keys, accelerates cryptographic processes, and provides strong access authentication. _Trusted Platform Module (TPM)_ is used to assist with cryptographic key generation.

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 2. Security Assessment Tools

* Protocol Analyzers / Packet Sniffers.
* Network Scanners / Mappers.
* Vulnerability Scanner.
* Exploitation Frameworks.
* Wireless Scanners.
* Configuration Compliance Applications.
* Banner Grabbing.
* Password Crackers.
* Honeypots / Honeynets.
* Steganography.
* Data Sanitization Tools.

### Protocol Analyzers / Packet Sniffers

Gathering packet-level information on a network.

* Wireshark.
* TCPDump.

### Network Scanners / Mappers

Network enumeration.

* Nmap
* ZenMap
* Fing (iOS & Android)

### Vulnerability Scanner

Software utility that scans a range of IP Addresses and tests for the presence of known vulnerabilities in software configuration and accessible services. It relies upon a database of known vulnerabilities.

* Nessus (Tenable)
* OpenVAS (Linux)
* Nexpose Community Edition
* Burp Suite
* OWASP ZAP (Web Apps)

### Exploitation Frameworks

Platforms used for penetration testing and risk assessments. Frameworks contains a set of exploits for known vulnerabilities.

* Kali Linux
* Social Engineering Toolkit (SET)
* Metasploit
* Canvas
* Core Impact
* BeEF: Browser Exploitation Framework (web vulnerabilities)

#### Kali Linux

Debian-derived Linux distribution, designed for digital forensics and penetration testing, which is preinstalled with numerous toolkits.

#### Social Engineering Toolkit (SET)

Searchable information resource for people wishing to learn more about the psychological, physical and historical aspects of social engineering.

You will find typical social engineering attacks, specifically designed to target the human element during a penetration test.

#### Metasploit

Utilizing an ever growing database of exploits, you can safely simulate attacks on your network and train yourself/your team.

You can run its own exploitable machine as a VM, _Metasploitable_, and run exploits against it.

### Wireless Scanners

* Gather information about Wi-Fi networks.
* Detect AP (Rogue or valids).
* Break encryption keys.

Examples of this are:

* Aerodump
* Kismet/KisMAC
* Netstumbler
* Vistumber
* inSSIDer

### Configuration Compliance Applications

* __Microsoft Baseline Security Analyzer (MBSA)__: Software vulnerability scanner to analyze targeted Microsoft systems, to detect whether software security patches or baseline configuration settings are missing.
* __Center for Internet Security (CIS)__
* __Nessus__.

### Banner Grabbing

Technique used to identify OS, applications and services on a system. It helps to __narrow vulnerability searches__.

* Netcat

### Password Crackers

Used to disclose passwords and assess password strength. Online password-cracking tools enable you to type in the hash and get the password returned in plain text.

* Brutus
* Cain and Able
* John the Ripper
* THC Hydra

### Honeypots / Honeynets

Systems or networks exposed to capture malicious activity. They help gathering investigation evidence & study attack strategies.

### Steganography

Means "_hidden writing_", hidding messages, often in other media, so that unintended recipients are not even aware of any messaage.

There are different approaches:

* Least significant bit insertion.
* Masking and filtering.
* Algorithms and transformations.

Common steganography tools include:

* OpenPuff
* Camouflage
* Steghide
* rSteg

### Data Sanitization Tools

Sanitization is the process of removing contents from a device or media.

* DBAN
* BCWipe
* Cryptographic erase (CE)

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 3. Troubleshooting

You should be proficient with the following CLI Tools:

* man
* ping
* netstat
* tracert
* nslookup / dig
* arp
* ipconfig / ip / ifconfig
* tcpdump
* nmap
* netcat

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 4. Security Technology Output

You should be able to analyze & interpret output from the following technologies.

* Host-based FW
* Host-based HIDS/HIPS
* Antivirus / Anti-malware
* File Integrity Checker
* Application Whitelisting
* Data Loss Prevention
* Removable Media Control
* Patch Management
* Data Execution Prevention (DEP)

### Host-based Firewalls

* Firewalls
  * Windows: type `wf.msc`
  * Linux: `ufw` or `iptables`
* Firewall configuration
  * End users shouldn't be allowed to disable the firewall
  * Monitor both cincoming and outgoing network traffic
* Output depends on the FW application and OS
  * Windows Event Viewer
  * Linux logging `/var/log`

### Host-based HIDS/HIPS

* Sensors on each host relay to a centralized management console
  * Compiles data to identify distributed trends
* May be included with Host FW or AntiVirus solution
* Issues
  * False positives
  * False negatives
  * Matching traffic identified as an attack with the actual network traffic
* NIST SP 800-94
  * Guide to IDPS

### Antivirus / Anti-malware

* End-user pop-up warning
* Centralized management console warning
* Quarantine vs Removal
* Issues
  * AV not updated / outdated signatures
  * False positives
  * May be ignored or not seen
  * Incorrect decision
  * Malware may still be present
* Solutions
  * Auto update
  * Detach system from the network
  * Use multiple AV products
  * Manual removal (_hunting malware with SysInternals_)
  * Reimage the system

### File Integrity Checker

* Computes a cryptographic hash such as SHA-1 or MD5 for all selected files and creates a database of the hashes.
* Hashes are periodically recalculated and compared to the hashes in the database, to check for modification.
* Output to a centralized server.
* For alerts, determine what changed and why.

### Application Whitelisting

* Organization approves / permits software applications. All others are not allowed by default.
* _Windows AppLocker_
  * Publisher, for digitally signed files.
  * Path, which identifies an application by its location.
  * File hash, which uses a system-computed cryptographic hash.

### Data Loss Prevention (DLP)

Prevent sensitive information from physically or logically leaving corporate systems by monitoring, detecting and blocking sensitive data while in use (endpoint actions), in motion (network traffic), and at rest (data storage).

* Logging to a centralized system.

### Removable Media Control

* Detects or prevents the use of removable media.
* Local or network.
* Set by corporate policy.
* Exception handling.
* Use only corporate owned / secured devices.
* Scan removable media on each use.
* Encryption.

### Patch Management

* Automatic updates when possible
* Patching process
  * Vendor notification
  * Testing
  * Staged deployment
  * Reporting
* Alerting on failed patches
* Patching all applications / systems
  * _WSUS: Windows Server Update Services_: deploy updates to domain-joined Windows servers and workstation in a corporate network.

#### Patch Management Services

* Microsoft System Center Configuration Manager (SCCM) / Systems Management Server (SMS)
* Linux RPM (Red Hat Package Manager)

### Data Execution Prevention (DEP)

* Hardware or Software.
* Prevents malware from executing in memory space that is reserved for OS processes.
* Both AMD and Intel platforms have DEP hardware capabilities.

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 5. Mobile Device Security

* Connection methods
* Mobile Device Management concepts
* Enforcement and monitoring
* Deployment models

### Connection methods

* Cellular
* Wi-Fi
* Bluetooth
* NFC (Near-Field Communications)
* SATCOM (Satellite Communications)
* ANT (Proprietary Multicast Wireless)
* Infrared (Using light in the infrared spectrum)
* USB / Firewire

#### Celullar communications

* Components
  * Cellular layout (towers)
  * Base station (connects to the tower)
  * Mobile switching office (centerpiece of the operation)
  * Public switched telephone network (PSTN)
* Voice technologies
  * Long-Term Evolution (LTE)
  * Code Division Multiple Access (CDMA)
  * Global Systems Mobile (GSM)

#### Bluetooth

* _Personal-Area Network (PAN)_, sohrt-range wireless conectivity.
* If needed, set to __nondiscoverable__.

#### NFC (Near-Filed Communications)

* Standards for contactless communication between devices.
* Chips generate electromagnetic fields.
* Modes of operation
  * _Perr-to-peer mode_: two mobilde devices exchange data.
  * _Read/write mode_: active device receives data from a passive device.
  * _Card emulation_: device is used as a contactless credit car.

### Mobile Device Management

The administration of mobile devices in an organization.

* Software used to inventory, monitor, manage, and secure employees' mobile devices, deployed across multiple mobile service providers and across multiple mobile OS.
* Device enrollment, provisioning and inventory.
* Configuration management / updating.
* Managing applications.
* Enforcing policies.

#### Objetives

* Separate personal and business content.
* _Storage segmentation_: segregate business and personal storage.
* _Containerization_: separate sensitive corporate information from the user's personal use of the device & isolate apps functions.
* _Remote wipe / sanitization_: sending a command from a centralized management server to remotely clear data, useful when device is lost, stolen, or employee terminates.
* Full device / application encryption.
* Screen locks / lockout after specific time.
* Passwords and pins based on corporate policy.
* Biometrics.
* _Context-aware authentication_: additional criteria used for authentication or device usage, such as location, time or activity.

#### Capabilities

* __Mobile Application Management (MAM)__
  * Restricting applications
  * Digitally signing applications
  * Distribution from a centralized, controlled source
  * Managed through _whitelisting_ or _blacklisting_
* __Mobile Content Management (MCM)__
  * Controlling access to data and file storage
* __Push notitication services__
  * Brief message or alert
  * OS Push Notification Service (OSPNS)
  * Allows auto-updating base OS and client apps
* __Geolocation__
  * Uses the devices GPS
  * Some apps already include this (Maps, Foursquare)
* __Geofencing__
  * Defining a greographic permiter
* __Containerization__
  * Control access to file storage and sharing capabilities of services

### Enforcement and Monitoring

* __Third-party Apps__
  * Restrict based on policy
  * Whitelist applications
* __Rooting__ (Android) / __Jailbreaking__ (Apple)
  * Should be forbidden for corporate devices
* __Sideloading__
  * Transfer data between two devices (side-channel)
* __USB On-the-Go (OTG)__
  * Standard that enables mobile devices communication using a USB cable
* __Custom firmware__
  * Valid use: Forensics acquisition
  * Invalid use: Bypass policy
* __Carrier unlocking__
  * Modifying device to use difference cell carrier without having to purchase a new device.
* __Firmware OTA updates__
  * Automatically update device when attached to corporate Wi-Fi or computers.

### Deployment Models

* __BYOD: Bring your own device__
  * Highest risk
  * Adherence with company policies
* __CYOD: Choose your own device__
  * Employees chose from a list of approved devices
* __COPE: Copmany Owned Provided Equipment__
  * Company has complete control over the device
* __VDI: Virtual Desktop Infrastructure__

--- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- --- 

## 6. Security Protocols

* Web (SSL/TLS, HTTPS)
* DNSSEC
* SSH
* Secure Email (S/MIME, POP3S and IMAPS)
* FTPS & SFTP
* SRTP: Secure Realtime Transport Protocol
* LDAPS
* SNMPv3: Simple Network Management Protocol

### Web

* __SSL: Secure Sockets Layer__
  * Deprecated by the IETF.
  * Uses certificates for authentication and encryption form essage integrity and confidentiality.
  * Establishes a stateful connection.

* __TLS__
  * Based on SSL latest version 3.0.
  * Provices privacy (asymmetric encryption), message integrity (Message Authentication Code), and authentication (PKI digital certificates).
  * Forward secrecy ensuring that any future disclosure of encryption keys cannot be used to decrypt any TLS communications recorded in the past.

* __HTTPS__
  * Uses SSL/TLS to secure web-based communications.
  * X.509 digital certificates.
  * 256-bit encryption keys.

### DNSSEC: Domain Name Service Security

* Suite of IETF specifications
* Protects aginast DNS Cache Poisoning
* DNS extensions provide DNS clients (resolvers) origin authentication of DNS data, authenticated denial of existence, and data integrity.

### SSH: Secure Shell

* Replaces telnet for remote communications
* Establishes a session between client and host computers using an authenticated and encrypted connection
* Uses the asymmetric (public key) RSA cryptography for both connection and authentication
* Other protocols can tunnel through SSH

### Secure Email

* __Secure/Multipurpose Internet Mail Extensions (S/MIME)__
  * Standard for encryption (confidentiality) and signing (authentication) of MIME (email) data
  * Requires PKI and uses Certificate Authorities (CA)
  * Internal email

* __POP3S__ and __IMAPS__
  * Use SSL/TLS to secure emails in transit between a POP or an IMAP server and the client.
  * External email

### FTPS & SFTP, securing FTP

* FTP (File Transfer Protocol) passes credentials in clear text
* FTPS extension that adds SSL/TLS
  * Mutual authentication of parties (certificates)
  * Data confidentiality (encryption) and integrity (hashing)
  * FTPS implicit over port 990
  * FTPS explicit over port 21
* SFTP (secure FTP) uses SSH to transfer files.

### SRTP: Secure Realtime Transport Protocol

* Secure voide and video transmissions
* Voice and video calls are established with _Session Initiation Protocol (SIP)_ and data is transmitted with _Realtime Transfer Protocol (RTP)_.
* Extension to __RTP__, in both unicast and multicast applications, intended to provide:
  * Encryption
  * Message Authentication
  * Integrity
  * Replay Attack Protection

### LDAPS

* LDAP is a _Directory Protocol_ that contains sensitive unencrypted information about organizational systems and users
* LDAPS over SSL/TLS
* Uses TCP port 636

### SNMPv3

* SNMP (_Simple Network Management Protocol_) used to manage networks.
* Each managed device has a software agent reporting configuration settings and alerts to a central SNMP Management Server.
* SNMPv1 & SNMPv2 sent all data as clear text, whereas SNMPv3 __encrypts__ data.
