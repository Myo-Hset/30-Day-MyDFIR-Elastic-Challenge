# 30-Day MyDFIR Elastic Challenge: SOC & DFIR Architecture

## Overview
This project documents my completion of the 30-Day MyDFIR Elastic Challenge, a comprehensive, hands-on SOC and DFIR lab focused on deploying, operating, and investigating security incidents using the Elastic Stack (Elasticsearch, Logstash, Kibana). The environment simulates an enterprise ecosystem by combining cloud-hosted endpoints, automated telemetry collection via Elastic Fleet, active adversary emulation, custom detection rule engineering, and incident workflow integration.

## Reference Material
* **Source Course:** [30-Day MYDFIR SOC Analyst Challenge (YouTube Playlist)](https://youtube.com/playlist?list=PLG6KGSNK4PuBb0OjyDIdACZnb8AoNBeq6&si=LaeMkm9RdSCI09_P)

### Skills Learned
* **SIEM & Logging Infrastructure:** Advanced deployment of the Elastic Stack, index configuration, and Elastic Agent/Fleet management.
* **Telemetry Analysis:** Proficient tracking of Windows Security Events and Sysmon data streams to parse host behaviors.
* **Adversary Emulation:** Simulating realistic attacks including brute-force authentication attempts and Command and Control (C2) agent setups.
* **Detection Engineering:** Developing custom SIEM logic and alert rules mapped to specific adversary behaviors and thresholds.
* **Analytical Problem Solving:** Implementing a structured, log-driven approach to security investigations and incident tracking.

### Tools & Technologies Used
* **Elastic Stack (ELK):** SIEM platform used for log ingestion, normalization, alerting, and analysis.
* **Elastic Fleet Server:** Centralized manager used to deploy and configure telemetry collection agents.
* **Sysmon:** Advanced host-level telemetry collector deployed on Windows servers.
* **Mythic C2:** Command and Control framework used to emulate sophisticated post-exploitation agent traffic.
* **Hydra:** Fast network login hacking tool used to generate brute-force authentication traffic.
* **Remmina:** Remote desktop client used to validate compromised access pathways.
* **Vultr:** Cloud infrastructure provider used to isolate and host the entire lab network.
* **Kali Linux & Windows Server 2022 / Ubuntu:** Core attacker and target operating systems.

---

## Lab Architecture & Workflow

### Network Topology
The lab infrastructure is segmented to simulate a remote enterprise target and a cloud-hosted attacker setup, routing security events into a centralized Elastic collection layer.

<img width="711" height="774" alt="Elastic drawio" src="https://github.com/user-attachments/assets/9522539b-6538-43df-9ef0-9901d89a1141" />

### Attack Lifecycle & Log Pipeline
The attack chain mirrors a typical intrusion scenario: external brute-force discovery leads to a compromised endpoint, followed by payload staging and interactive command-and-control callbacks.

<img width="642" height="1461" alt="Attack ELK 30days drawio" src="https://github.com/user-attachments/assets/d6a4efc2-4cfa-4a40-b9c1-b6a03022fbaf" />

---

## Lab Execution & Forensic Evidence

### Phase 1: Infrastructure Provisioning & Deployment
Using Vultr, I spun up an isolated testing network comprising an ELK server, Fleet server management node, a Linux/Mythic attack framework machine, and a target Windows Server instance.

<img width="1907" height="911" alt="image" src="https://github.com/user-attachments/assets/d1b193c4-fc64-4bb4-a0df-0297d34d7231" />

### Phase 2: Adversary Emulation (The Attack)

#### 1. RDP Brute-Force via Hydra
From the Kali Linux instance, I initialized a high-velocity automated RDP password spray targeting the Windows Server instance using Hydra to force entry.
<img width="939" height="85" alt="Screenshot 2026-01-18 193810" src="https://github.com/user-attachments/assets/250fc889-efc7-421d-9e74-fe9d8926b649" />

#### 2. Establishing the Remote Desktop Connection
Once Hydra cracked the administrative account credentials, I established a persistent, GUI-based interactive session over RDP using Remmina.
<img width="846" height="648" alt="Screenshot 2026-01-18 194045" src="https://github.com/user-attachments/assets/9f458fbf-2d39-4237-9cda-721564e78aef" />

#### 3. Command and Control (C2) Payload Delivery
Inside the compromised asset, I executed an agent wrapper to generate active beaconing telemetry to my Mythic C2 management portal, securing an interactive control channel.
<img width="1670" height="912" alt="Screenshot 2026-01-18 221124" src="https://github.com/user-attachments/assets/9225d961-2935-41e3-8698-56c33ee57ed4" />

---

### Phase 3: Detection Engineering & SIEM Analysis

#### 1. Macro-Level Visualization (Authentication Dashboards)
To catch the initial access attempts, I built a Kibana dashboard mapping high-volume authentication logs. This dashboard exposes clear spikes in both SSH and RDP connection failures alongside successful logins.
<img width="1887" height="839" alt="Screenshot 2026-01-19 000551" src="https://github.com/user-attachments/assets/22105165-6247-4a62-886c-6feaf0c7a560" />

#### 2. Writing Custom Security Rules
To convert passive data into proactive defenses, I generated threshold-based security rules within Elastic to flag SSH/RDP brute-force behaviors and identify signature patterns linked to Mythic C2 network footprints.
<img width="1911" height="904" alt="image" src="https://github.com/user-attachments/assets/77ce14a71-49f3-4068-820e-7ec649442f6b" />

#### 3. Isolating the C2 Binary in Elastic Security
By combing through Sysmon and Windows security event streams, I successfully parsed and flagged the exact executable and process execution path tied to the running Mythic agent beacon.
<img width="1907" height="907" alt="Screenshot 2026-01-18 221535" src="https://github.com/user-attachments/assets/bb96c5c0-c967-4711-8603-778df27f3f03" />

---

## Summary
Completing this 30-day challenge bridge the gap between basic log aggregation and true threat response capabilities. By independently constructing the ingestion network and managing the attack-to-detection workflow, I gained a deep operational understanding of how security signals transit from cloud hosts into real-world dashboard triage queues. This lab highlights the role visibility plays in isolating adversary mechanisms before they establish long-term persistence.
