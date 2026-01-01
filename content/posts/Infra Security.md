+++
title = '17 essential points for securing your sensitive IT infrastructures exposed to the Internet'
draft = false
date  = 2020-04-02
tags = ["Infrastructure Security", "Internet"]
+++

## Intro

_This is an old article I wrote early in my career when I worked as a consultant_

<!--more-->

The year 2020, much like 2019, has been marked by a wave of highly publicized cyberattacks. Many major organizations worldwide have already faced cyberattack incidents, and none of them wish to deal with information leaks or resource losses.

Organizations must implement comprehensive security measures to protect customer data against the growing and diversifying threats. To strengthen the security of your sensitive infrastructures exposed to the internet, and as a complement to the technical and methodological recommendations of ANSSI (the French National Cybersecurity Agency), here is a set of measures aimed at addressing risks that could compromise the availability, integrity, and confidentiality of your informational assets. Each organization can adapt these measures based on its specific context and challenges.

---

## Design Principles for Internet-Exposed Infrastructures

### Availability

1. **Server Redundancy**: A single failure should not cause visible service interruptions for users, and failovers must be swift. Most equipment should have built-in redundancy capabilities (e.g., power supply, network cards).

2. **Performance-Oriented Architecture**: The architecture must ensure the level of performance expected by users. Therefore, network or security equipment should only be selected if it passes load and robustness tests. Additionally, if possible, no network or security equipment should be virtualized to ensure high throughput.

---

### Confidentiality & Integrity

3. **Segmentation Between Trust Domains**: Segmentation between different trust domains (DMZ, administration, etc.) should be implemented through VLANs interconnected via firewalls. The N-Tier architecture principle should be followed when supported by applications. Furthermore, each department or business unit should have a dedicated VLAN on the firewall’s DMZ for each service used.

4. **Flow Isolation and Traceability**: Flow isolation and traceability between different zones should be ensured through firewalls with intrusion protection and detection features (e.g., IPS/IDS).

5. **Confidentiality of Administration Traffic**: This can be achieved by implementing "out-of-band" administration (which avoids paralysis and enhances cyber-resilience), with administration VLANs systematically mirroring production VLANs. Additionally, protocols used for component administration should always incorporate encryption (e.g., SSH).

6. **Flow Integrity**: Integrity must be ensured through intrinsic mechanisms of the protocols used (e.g., TCP protocol, secure tunnels) as well as control functions inherent to firewalls (e.g., anti-spoofing).

7. **Back Office Server Virtualization**: Virtualizing back-office servers enables adequate segmentation for shared environments while ensuring complete isolation between different services and user flows using the same service.

8. **Separation of Filtering and Advanced Security Functions**: Whenever possible, information system filtering/isolation functions should be separated from advanced security functions (e.g., proxy, antimalware, intrusion detection, WAF) and not hosted on the same physical components.

9. **Load Testing**: Load testing should systematically be conducted for firewalls and load balancers.

---

## Operational Recommendations for Internet-Exposed Infrastructures

### Services and Procedures

10. **Configuration Management Procedures/Services**: Organizations must have procedures or services for managing technical configurations, particularly for backup and restoration in case of incidents or rollbacks.

11. **Flow Management Procedures/Services**: The management of flows between different zones must follow a procedure or service that monitors and validates exchanges. To maintain consistency, flow openings should follow uniform processes and use standardized tools.

12. **Change Management Procedures/Services**: Organizations must have procedures or services for managing changes—especially for qualifying and applying security patches to infrastructure components. Requests for upgrades (e.g., software version updates) and new community services must also be addressed.

    - Users should be notified approximately five business days before updates occur.
    - Maintenance windows should be negotiated with users (e.g., Friday at 11 PM). Notifications can be sent via mailing lists, with additional explanations provided by phone if necessary.

13. **Incident Management Services**: Organizations must establish incident management services specifically focused on detecting and handling security incidents (e.g., viral attacks, phishing, denial-of-service attacks) using dedicated ticketing tools (e.g., Cerberus).

    Incident management can follow these levels:
    - **Level 1**: Available 24/7 through an on-call system (incident detection during non-business hours can be handled by another service).
    - **Levels 2 & 3**: Managed by an expert team capable of escalating issues to vendors if necessary.

14. **Vulnerability Management Services**: Organizations should manage vulnerabilities by receiving and processing security bulletins (e.g., CERT subscriptions) and using vulnerability scanners (e.g., Qualys).

15. **Logging Administrative Operations**: All administrative operations on equipment must be logged. Logs should be stored in a database for at least six months. Additionally, technical accounts used to operate components must always be nominative.

---

### On-Call Support

16. **Remote Access During On-Call Periods**: Remote access during on-call periods must occur via an SSL VPN portal with strong authentication (e.g., token-based authentication).

---

### Maintenance Company Interventions

17. **On-Site Support in Case of Incidents**:
    - Providers must physically visit the site to handle incidents or sensitive interventions.
    - Alternatively, providers may remotely access one of the organization’s workstations (e.g., via Webex) under the supervision of an employee who monitors their actions.

---

A comprehensive approach to infrastructure security may seem daunting; however, when sensitive infrastructures containing valuable customer data—whether financial or insurance-related—are at risk, robust measures are essential to ensure their protection.