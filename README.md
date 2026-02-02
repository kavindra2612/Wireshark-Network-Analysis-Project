# Wireshark Network Traffic Analysis Project

This project demonstrates real network traffic analysis using Wireshark in a virtual lab environment.  
Traffic was generated from an attacker machine (Kali Linux) and captured on a victim machine (Windows) using Host-Only networking in VMware.

The goal of this project is to understand how normal and abnormal network traffic looks at the packet level and how security analysts detect suspicious patterns.

---

## 🛠 Tools Used

- Wireshark
- Nmap
- Kali Linux
- Windows Host
- VMware Workstation (Host-Only Network)

---

## 📁 PCAP Files Included

### 1️⃣ ICMP Traffic (Ping Test)
File: `icmp_traffic.pcapng`  
Shows basic ICMP echo request and reply between attacker and victim to verify connectivity.

Filter used: icmp


---

### 2️⃣ SYN Scan Detection (Nmap Scan)

File: `port_scan.pcapng`  
Nmap SYN scan was performed from Kali to Windows machine.

Filter used: tcp.flags.syn == 1 && tcp.flags.ack == 0


This shows multiple SYN packets sent to different ports, which is a clear indication of a port scan.

---

### 3️⃣ DNS Query / DNS Anomaly

File: `dns_anomaly.pcapng`  
DNS queries were generated in a Host-Only network where no DNS server was available.

Filter used: dns


This demonstrates DNS query attempts without response, useful for understanding DNS-related anomalies.

---


---

## 🟢 ICMP and DNS Traffic Analysis
Files:(icmp_dns.png)

This capture shows both ICMP and DNS traffic observed together in the Host-Only lab network.

Filter used: icmp || dns


### What was observed

- ICMP Echo requests and replies between attacker and victim (host discovery)
- DNS query attempts from Kali machine
- No DNS response due to isolated Host-Only network

### Analysis

This demonstrates how an analyst can correlate host discovery activity (ICMP) with DNS query behavior to understand what a machine is trying to access on the network.

---

## 🔵 TCP 3-Way Handshake, HTTP Request and Keep-Alive

File: `tcp_handshake_http_keepalive.pcapng`

This capture demonstrates a complete TCP session between Kali and Windows after opening a listening port on the victim machine.

Filter used: tcp.port == 9000


### TCP 3-Way Handshake observed

1. SYN — Client initiates connection  
2. SYN, ACK — Server acknowledges  
3. ACK — Client confirms

### HTTP Communication

After the handshake, an HTTP GET request is observed from Kali to the Windows listener.

### TCP Keep-Alive

Later packets show TCP Keep-Alive and Keep-Alive ACK packets, proving the connection remained active.

### Analysis

This demonstrates how Wireshark can be used to analyze:

- TCP connection establishment
- Application layer communication (HTTP)
- TCP session maintenance (Keep-Alive)




## 🎯 Learning Outcome

- Understanding of packet-level network traffic
- Identifying SYN scan patterns
- Identifying DNS query behavior and anomalies
- Practical use of Wireshark filters
- SOC-style traffic investigation

---

## 📌 Conclusion

This project simulates real-world attacker and victim communication and demonstrates how a security analyst can detect suspicious activities using Wireshark packet analysis.



