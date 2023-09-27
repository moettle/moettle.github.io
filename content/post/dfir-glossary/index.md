---
title: DFIR Glossary
description: Collection of terms and abbreviations in the field of DFIR
slug: dfir-glossary
date: 2023-09-27 16:00:00+0000
image: cover.jpg
categories:
    - Introduction
tags:
    - Incident Response
    - Forensics
    - Glossary
---

Personally, I dislike it when people use abbreviations as if they are universally understood. More often than not, half of the people in a meeting won't even know what an abbreviation means, but nobody would dare to ask. Furthermore, it is nearly impossible for newcomers to grasp a topic when people consistently use abbreviations without explaining them. You can ask any employee of a company with more than 50,000 employees how much they appreciate abbreviations. Every department tends to have its own set of abbreviations, and company-wide, most abbreviations aren't even unique. Okay, enough complaining about abbreviations; I think you've got the idea.

While I've expressed my frustration with abbreviations, this article aims to provide an introduction to the most commonly used terms in Digital Forensics and Incident Response (DFIR). Oh wow, it's not that difficult to write out an abbreviation, is it? The article also serves the purpose of defining terms that might have multiple meanings in different companies, countries, vendors, etc.

| Term                                             | Explanation |
|--------------------------------------------------|-------------|
| Active Directory (AD)                            | Microsoft's solution for managing an on-premises Microsoft enterprise environment. |
| Advanced Persistent Threat (APT)                 | A sophisticated threat actor, often state-sponsored, performing elaborate attacks on selected targets with the goal of espionage, financial gain, or sabotage / destruction. These attacks are often carried out stealthily over an extended period (months to years). Due to the substantial financial and personnel resources of these threat actors, they are highly dangerous and challenging to defend against.|
| Alternate Data Stream (ADS)                      | A file attribute in the NTFS file system, often used to hide data from detection.|
| Antivirus (AV)                                   | A program designed to detect and prevent malware on endpoints. |
| Azure Active Directory (AAD)                     | Microsoft's solution for managing a Microsoft cloud environment, now renamed to Microsoft Entra ID. |
| Blue Team                                        | The team responsible for defending an organization. The term is also used during simulations, where a red team simulates an attack, and a blue team defends against it. |
| Command and Control (C2, C&C)                    | A method for threat actors to remotely control a compromised system over the network. C2 typically involves a compromised system and a C2 server for control, often using simple HTTP or HTTPS channels to evade detection among an organization's usual network traffic. |
| Computer Emergency Response Team (CERT)          | A team of security experts specialized in handling cyberattacks and security incidents, which may not be limited to organizations; some countries have their own CERTs, and even the EU has one. |
| Computer Security Incident Response Team (CSIRT) | Sometimes used as a synonym for CERT, but also refers to a dedicated team that exists primarily during major incidents, whereas CERTs are active in daily operations. Definitions may vary among organizations.|
| Confidentiality, Integrity, Availability (CIA)   | Protective goals originating from Information Security. |
| Containment                                      | The act of slowing down or stopping an attacker to limit further impact and damage, typically initiated early after detecting an attack or when attackers become active again during Incident Response. The range of containment measures will be covered in a future post. |
| Cyber Threat Intelligence (CTI)                  | See TI (Threat Intelligence). |
| Domain Controller (DC)                           | A server responsible for processing authentication requests within an Active Directory (AD). |
| Deception                                        | A category of security solutions aimed at detecting attackers by deceiving them, such as internal honeypots. |
| Denial-of-Service (DOS)                          | An attack with the goal of disrupting the availability of a system or service, often achieved by flooding the server with requests. |
| Digital Forensics (DF)                           | The act of analyzing digital evidence to reach investigative goals, which can range from presenting results in court to understanding a cyberattack. |
| Digital Forensics and Incident Response (DFIR)   | A broad term used to describe the field encompassing digital forensic analysis and Incident Response. |
| Distributed Denial-of-Service (DDOS)             | A DOS attack where the flooding comes from multiple systems, commonly achieved through request amplification or bot networks. |
| Endpoint Detection & Response (EDR)              |A security tool that detects threats and unusual behavior on endpoints and enables a company to respond effectively to alerts. EDR collects all endpoint events centrally and offers response features like isolation, containment, live response, and more, surpassing traditional antivirus solutions. |
| Entra ID                                         | See Azure Active Directory (AAD) |
| Evidence Acquisition                             | The process of collecting evidence for later forensic analysis, including disk images, memory images, triage packages, log files, single artifacts, malware samples, and more. |
| Extended Detection and Response (XDR)            | A marketing term for EDR (Endpoint Detection & Response). |
| Honeypot (internal)                              | An internal honeypot acts as an enticing target for attackers to deceive them. Access to such a honeypot is monitored, and the security team is alerted when access occurs. Examples include systems with vulnerabilities or open file shares. |
| Incident Response (IR)                           | The act of responding to cyber security incidents. |
| Indicator of Compromise (IOC)                    | Indicators used for detecting a compromise, typically specific to a single attack or attacker group. IOCs can include filenames, hashes, URLs, domains, IPs, command lines, registry keys, and more. |
| Information Security (IS)                        | Focused on protecting information related to CIA (Confidentiality, Integrity, Availability) within an organization. |
| Information Security Management System (ISMS)    | A framework for managing an organization's sensitive data related to CIA, using a set of policies and procedures. |
| Information Security Operations Center (ISOC)    | See SOC (Security Operation Center). |
| Intrusion Detection System (IDS)                 | A system monitoring the network for malicious activity and triggering alerts. |
| Intrusion Prevention System (IPS)                | An IDS that also attempts to block detected malicious activity. |
| KAPE                                             | A valuable tool for creating triage packages from Windows systems. |
| Malware Analysis                                 | The process of analyzing a malware sample to understand its functionality. |
| Network Detection and Response (NDR)             | A solution continuously monitoring the network for threats and offering network-level response actions. |
| Network Operation Center (NOC)                   | A team that monitors the network traffic of an organization. Many organizations don't have a NOC anymore but rather a monitoring team in general or a SIEM team, which also covers network monitoring. Since network monitoring is only a part of a complete monitoring strategy, it often resolves in a large monitoring team. |
| Network Security Monitoring (NSM)                | The continuous monitoring of network traffic to detect malicious activity. |
| NT File System (NTFS)                            | A proprietary file system used by Windows. |
| Privileged Access Workstation (PAW)              | A dedicated workstation for administrative tasks, with added hardening to make it more resistant to admin account takeovers and lateral movement by attackers. |
| Purple Team                                      | A collaboration between a blue team (defense) and a red team (offense) working together in a coordinated manner. |
| Red Team                                         | A team responsible for offensive work, often involved in security assessments or attack simulations to test an organization's existing defense and detection mechanisms. |
| Remediation                                      | TThe act of mitigating an attack after it has occurred, aiming to regain control over the infrastructure, remove attackers from systems, and return to normal operations. Forensics analysis is essential for defining effective remediation measures, which may include reinstalling compromised systems, changing passwords on abused accounts, or enhancing security to prevent the same incident in the future. |
| Reverse Engineering (RE)                         | Part of malware analysis, involving reconstructing the original source code of a compiled malware sample to understand its functionality. |
| Security Incident Management Process (SIMP)      | A process defining the handling and management of security incidents within an organization, with templates available in ISO 27035, SANS, and NIST standards. |
| Security Information and Event Management (SIEM) | A solution helping companies detect and analyze security incidents by centrally collecting various logs, standardizing them, and generating alerts based on predefined signatures. |
| Security Operation Center (SOC)                  | In larger organizations, a SOC is often the first level to handle incoming security alerts, often managed by a higher entity like a CERT. |
| SIGMA                                            | An excellent GitHub project providing SIEM signatures in a generic format. |
| Tactics, Techniques, and Procedures (TTP)        | Behaviors of threat actors during an attack, defined by MITRE ATT&CK®, a database cataloging tactics and techniques used by attackers. |
| Thor                                             | An IOC scanner specialized in detecting traces of attacks on endpoints, offering over 10,000 signatures and various modules for system scanning. A free variant, Thor-lite, is also available.|
| Threat Intelligence (TI)                         | The process of gathering information about current cyber threats and risks, utilized for prevention, detection, or response to incidents within an organization. |
| Threat Hunting                                   | The proactive search for traces of attacks within an organization, often initiated by new reports, ideas for identifying attackers, or management concerns. Threat hunting is commonly performed in EDR or SIEM systems. |
| Traffic Light Protocol (TLP)               | TLP is a tagging system for shared information specifying sharing options for recipients. It includes four labels: TLP:RED (For recipient only), TLP:AMBER (Limited disclosure, e.g., within the organization), TLP:GREEN (Limited disclosure, e.g., within a community), and TLP:CLEAR (No limitations, shared information can be published).  |
| Windows Event Forwarding (WEF)                   | The forwarding of Windows Event logs to a central server, which is supported by Windows by default and is for free, making it an excellent way to collect all Windows Event Logs in one place, simplifying log management. |
| YARA (Yet Another Ridiculous Acronym)            | YARA provides a standard for writing detection signatures and offers a scanner to apply them to files or directories, serving as the de-facto standard for signature writing for files.|

> Cover Image by [Freepik](https://www.freepik.com/free-photo/multi-colored-psychedelic-background_11761198.htm#&position=37&from_view=collections)