# 30-Day-MyDFIR-Elastic-Challenge

## Overview

This Projecte demonstrates the my 30-Day MyDFIR Elastic Challenge, a hands-on SOC and DFIR lab project focused on deploying, operating, and investigating security events using the Elastic Stack (Elasticsearch, Logstash, Kibana). The project simulates real-world enterprise monitoring by combining endpoint telemetry, attack simulation, alerting, dashboards, and incident workflow integration. This challenge emphasizes practical detection engineering, incident investigation, and SOC workflows.

## Reference

 <a href="https://youtube.com/playlist?list=PLG6KGSNK4PuBb0OjyDIdACZnb8AoNBeq6&si=LaeMkm9RdSCI09_P">30-Day MYDFIR SOC Analyst Challenge </a>

### Skills Learned

- Understanding of SIEM concepts and practical application.
- Analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Enhanced analytical thinking and structured problem‑solving within cybersecurity operations


### Tools Used

- Elastic Stack (ELK)
-  Sysmon
-  Mythic C2
-  Kali Linux
-  Ubuntu Server 22.04
-  Windows Server 2022
-  Remmina
-  Hydra 

### Diagram

- Network Diagram
-  <img width="711" height="774" alt="Elastic drawio" src="https://github.com/user-attachments/assets/9522539b-6538-43df-9ef0-9901d89a1141" />

- Attack Flow Diagram
- <img width="642" height="1461" alt="Attack ELK 30days drawio" src="https://github.com/user-attachments/assets/d6a4efc2-4cfa-4a40-b9c1-b6a03022fbaf" />




### Key Skills Demonstrated

• SOC monitoring and alerting

• Detection engineering

• Endpoint telemetry analysis

• C2 behavior analysis

### Lab Exercise

* **Image 1** : Vultr cloud dashboard displaying the running lab infrastructure (ELK server, Fleet Server, Linux/Mythic server, and Windows Server).

   <img width="1907" height="911" alt="image" src="https://github.com/user-attachments/assets/d1b193c4-fc64-4bb4-a0df-0297d34d7231" />

* **Image 2** : Kibana dashboard displaying SSH authentication failures, successful SSH authentications, RDP authentication failures, and successful RDP authentications.

   <img width="1887" height="839" alt="Screenshot 2026-01-19 000551" src="https://github.com/user-attachments/assets/22105165-6247-4a62-886c-6feaf0c7a560" />

* **Image 3** : Elastic Security Rule Creation for suspected SSH brute-force activity, suspected RDP brute-force activity and Mythic C2 Call back 

  <img width="1911" height="904" alt="image" src="https://github.com/user-attachments/assets/7ce14a71-49f3-4068-820e-7ec649442f6b" />

* **Image 4** : Successfully brute‑forced RDP access to a Windows Server using Hydra on Kali Linux (VMware).

  <img width="939" height="85" alt="Screenshot 2026-01-18 193810" src="https://github.com/user-attachments/assets/250fc889-efc7-421d-9e74-fe9d8926b649" />


* **Image 5** : Initiated an RDP connection from Kali Linux (VMware) to the Windows Server using Remmina.

  <img width="846" height="648" alt="Screenshot 2026-01-18 194045" src="https://github.com/user-attachments/assets/9f458fbf-2d39-4237-9cda-721564e78aef" />

* **Image 6** : The Mythic C2 dashboard displays active callbacks originating from the compromised Windows Server endpoint.

  <img width="1670" height="912" alt="Screenshot 2026-01-18 221124" src="https://github.com/user-attachments/assets/9225d961-2935-41e3-8698-56c33ee57ed4" />




