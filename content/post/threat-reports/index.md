---
title: Threat Reports
description: How to read and write Threat Reports
slug: threat-reports
date: 2023-10-04 16:30:00+0000
image: cover.jpg
categories:
    - Advanced
tags:
    - Incident Response
    - Forensics
    - Documentation
    - Threat Intelligence
    - Best Practice
toc:
    false
---
Frequently, I come across poor threat / incident response reports that seem to prioritize self-promotion over delivering valuable and actionable information. Such reports often lack crucial parts to help others in defending themselves against these threats. After finding another bad threat recently, I decided to write a constructive blog post on how to read and write threat reports.

# TL;DR

* Include an actionable management summary
* Provide a comprehensive technical timeline
* Utilize the [MITRE ATT&CK® framework](https://attack.mitre.org/)
* Provide IOCs and use a standardized way to share them. For example via a [MISP](https://www.misp-project.org/)
* Write Yara signatures
* Write SIGMA signatures
* Reference other reports about the same threat
* Use a consistent Timezone, ideally UTC+0. In any case, specify the timezone you are using.

# What is a threat report even?
A threat report is a document or publication that provides detailed information about a specific (current) cyber threats. These reports are typically authored by  cybersecurity organizations, government agencies, or security vendors with the primary objective of keeping organizations and individuals well-informed about the latest threats in the cyber space. Most often these reports are published after an IR engagement. Hence, the report usually covers a single attack, or a set of attacks performed by the same threat actor. A threat report should not be confused with a report about a threat landscape, which has a bigger picture in mind.  In this article, we will delve into the specifics of threat / incident response reports.

# Contents of a threat report

## Management Summary

To kick things off, let's address one of the often-overlooked but crucial elements missing in most threat reports: the management summary. Typically, these reports are tailored for a niche audience – those engaged in Digital Forensics and Incident Response (DFIR). Undoubtedly, the information contained therein is immensely valuable for this specific group, aiding them in fine-tuning their detection strategies for this specific attack. However, what if the incident responder reads the report and wants to prevent the attack in the future, for example by disabling Office macros or by rolling out a new security tool. The incident responder runs to the management, presents the report and urges them to action. Management looks at the report and the first sentence they see is something like:
```{linenos=false}
"<fancy name> (aka <more fancy names>) attacker group managed to infiltrate company XYZ by abusing 
<fancy vulnerability name> and deploying <fancy malware name>"
```
In such cases, the management may find it challenging to immediately grasp the gravity of the situation, given the technical jargon and intricacies presented upfront. This is precisely where an effective management summary comes into play, providing a concise yet comprehensive overview that bridges the gap between the technical details and the need for strategic decisions at a higher level within the organization. Instead of sounding all fancy and technically sophisticated in the first section, it should rather sound something like this:
```{linenos=false}
"Company XYZ was hacked by an attacker due to bad patch management. The impact from the attack resulted in a halt 
of production for several days, which caused X million in damage for the company. The attack could have been 
prevented through fast emergency patches."
```
Now management actually has a chance to understand what the report is trying to convey and what potential consequences could arise from the described threat.

A rule of thumb here: **If is sounds cool to you as an incident responder, management won't understand it. If is sounds straightforward and plain, there is a higher chance that management will understand.**

What should be included in a management summary:

1. **Clarity and Simplicity**: Write in a non-technical and easily comprehensible manner.
2. **Impact Assessment**: Explain the impact or damage caused by the attack, and if possible, quantify it.
3. **Incident Overview**: Provide a concise description of what occurred.
4. **Preventive Measures**: Offer recommendations on how to prevent a similar incident in other organizations.
5. **Visualization**: Include any necessary visual aids to illustrate the attack, making it more accessible to non-technical readers.
6. **Timeline**: Optionally, include a high-level timeline to demonstrate how rapidly an attack can disrupt a company.

In 2022 I co-authored a threat report[[1]](https://www.hvs-consulting.de/public/ThreatReport-EmissaryPanda.pdf) on a threat actor called Emissary Panda, which was harvesting major vulnerabilities like ProxyLogon at that time and engaging in industrial espionage. Since we received a lot of positive feedback from Incident Responders and managers, I would like to show you some highlights of the report, starting with the management summary. The first page after the table of contents contains an abstract, which serves as a management summary. It adheres to the tips given above and contains a summary written in non-technical terms as well as easy to understand recommendations:

![Threat Report Emissary Panda: Recommendations [1]](Threat_Report_Emissary_panda.png)

As you can see, the report even contains a link to a separate summary targeting management[[2]](https://www.hvs-consulting.de/en/threat-intelligence-report-emissary-panda-apt27/). Furthermore, it contains easy to understand recommendations.



## Technical Timeline

Now that we've covered the management aspect in depth, let's delve into the technical aspects of a threat report. Before we go into executed commands, used malware, and attacker infrastructure, the reader needs to gain an understanding of the attack. The report should provide that in form of visualization of the attack and technical timelines.

One publisher that often combines visualization and timeline in a single, beautiful image is [The DFIR Report](https://thedfirreport.com). The following timeline was taken from one of their latest reports[[3]](https://thedfirreport.com/2023/02/06/collect-exfiltrate-sleep-repeat/). I love these timelines because they offer a quick overview as well as the most critical technical details of an attack.

![Threat Report "Collect, Exfiltrate, Sleep, Repeat" from The DFIR Report [3]](Threat_Report_TheDFIRReport.png)

Another approach to presenting a technical timeline is to separate the visualization from the actual timeline by placing it in a dedicated table. This is what we did in our report[[1]](https://www.hvs-consulting.de/public/ThreatReport-EmissaryPanda.pdf).

![Threat Report Emissary Panda - Timeline [1]](Threat_Report_Emissary_panda_Timeline_1.png)

![Threat Report Emissary Panda - Timeline [1]](Threat_Report_Emissary_panda_Timeline_2.png)

![Threat Report Emissary Panda - Timeline [1]](Threat_Report_Emissary_panda_Timeline_3.png)

## Mapping the attack to MITRE ATT&CK®

The next section delves deeper into the technical aspects of the attack by leveraging the [MITRE ATT&CK® framework](https://attack.mitre.org/). By aligning the analyzed attack with MITRE's tactics and procedures, defenders can swiftly grasp the attack and determine how to detect or mitigate it within their environment. The report should include a MITRE map created with the [MITRE ATT&CK® Navigator](https://mitre-attack.github.io/attack-navigator/) as well as a detailed and technical description of each used technique.

![Threat Report Emissary Panda - Mitre [1]](Threat_Report_Emissary_panda_Mitre.png)

The descriptions of the used techniques should have the highest level of technical details, including the tools used, command-lines, and more. Why? Let me illustrate that with an example from another threat report we released in 2021 about Lazarus[[4]](https://www.hvs-consulting.de/public/ThreatReport-Lazarus.pdf), a North Korean threat actor:

![Threat Report Lazarus - Mitre Technique Description [4]](Threat_Report_Emissary_panda_Mitre_technique.png)

In that report, we disclosed the entire command-line, including the password used to decrypt the embedded payload. Approximately 1.5 years later, an incident responder from ESET encountered another attack from Lazarus, still employing the same malware. Although, the ESET researchers were not able to catch the password live from the command-line, they found our report and were able to decrypt the payload with the contained password used in the command-line [[5]](https://www.welivesecurity.com/2022/09/30/amazon-themed-campaigns-lazarus-netherlands-belgium/).

## Detection

A threat report should empower others to detect the same attack in their environment. This is typically accomplished by sharing Indicators of Compromise (IOCs) or detection signatures.

### Indicators of Compromise

IOCs, as described in my [Glossary](https://dfir-delight.de/glossary), encompass indicators such as filenames, hashes, URLs, domains, IPs, command lines, registry keys, and more. These indicators are crucial for detecting compromises or attacks.

However, sharing IOCs comes with several challenges, some of which I intend to explore in a dedicated blog post. For now, let me highlight the main issues associated with sharing IOCs:

* IOC types are only semi-standardized. The closest thing to a standardized format for IOCs can be found in the [MISP Project](https://www.misp-project.org/). Since most people are still sharing indicators like its 1982, defenders still have to deal with poorly formatted tables in PDF and Excel sheets, and self-defined type names. You wouldn't believe how many ways there are to title an IPv4 address: IP, IP4, IP-v4, IPv4, etc. An IPv4 address is still one of the easy types to title, now think about how you would title registry keys, command-lines or even scheduled tasks.
* Many organization lack a way of automatically applying IOCs to their monitoring and detection tools.
* IOCs that are true positives today may become obsolete tomorrow. IP addresses are reused, domains are taken down, and hashes of the same malware can change due to one changed byte in the malware.
* Often, IOCs are shared without context or information about their relevance in a specific attack.
* Some IOCs, although they might be used by an attacker as described, have a high false-positive rate. Especially when Windows filenames are used as a means of defense evasion.

Many of these challenges are addressed, at least partially, by the [MISP Project](https://www.misp-project.org/). A MISP provides predefined IOC types, the option to tag IOCs to enhance them with additional information, and a standardized format for sharing with others. You can connect a MISP with other instances globally or simply export MISP events as a file for publication. This enables defenders to easily import the event, ensuring that the information is presented in a semi-standardized format that can be utilized within their organization via APIs.

Here are some key guidelines for sharing IOCs:

* If your IOCs are a picture, you are doing it wrong.
* If some of your IOCs are spread over multiple lines, you are doing it wrong.
* If your IOCs are only found in a PDF file, you are also doing it wrong.
* At a minimum, you have to share the IOCs in a CSV with consistent type naming.
* Even better is the creation and export of a MISP event.
* Enrich your IOCs with metadata. Explain how, where, and when you discovered the IOC, its relevance in the attacker's tactics, and whether it has a high false-positive rate.
* Classify your IOCs with Traffic Light Protocol (TLP) markings so that others understand how to handle them.

As a defender, it's essential to have a MISP system in place and established processes for automatically incorporating new IOCs into your detection tools.

### Signatures

The most common format for sharing **detection signatures** for **files** is YARA. YARA offers a standard for writing detection rules along with a scanner that can apply these signatures to a file system. If you have detected malware samples or other suspicious files during your incident investigation, you should bundle that knowledge in YARA signatures and share it with the community. If you're new to YARA, Florian Roth has provided excellent tutorials on how to write effective YARA signatures[[6]](https://www.nextron-systems.com/2015/02/16/write-simple-sound-yara-rules/) [[7]](https://www.nextron-systems.com/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/) [[8]](https://cyb3rops.medium.com/how-to-post-process-yara-rules-generated-by-yargen-121d29322282).

For sharing detection signatures specific to logs, [SIGMA](https://github.com/SigmaHQ/sigma) is the way to go.  It serves as a generic signature format for SIEM systems. To quote the SIGMA description from their repository:
```{linenos=false}
"Sigma is for log files what Snort is for network traffic and YARA is for files."
```
The repository already provides a wide array of open-source signatures for common attacker techniques, along with a converter for various SIEM systems.

Other signatures might include:

* Network-based signatures: [Snort](https://www.snort.org/) or [Surricata](https://suricata.io/)
* EDR-specific hunting queries (e.g. Defender for Endpoint hunting queries written in KQL)

## Other Possible Contents of the report

In addition to the previously mentioned content, which should ideally be included in every threat report, there are several other valuable components that can enhance a threat report:

* **Malware analysis**: This involves the thorough dissection and analysis of a malware sample to gain a deeper understanding of its functionality. Such analysis can provide insights into elements like Command and Control (C2) endpoints.
* **Comparison to Previous Attacks by the Same Threat Actor**: By comparing the current attack to past incidents attributed to the same threat actor, it becomes possible to identify changes in their techniques or tactics over time. This historical perspective can be invaluable for anticipating their future actions.
* **Investigative Research**: Conducting further research to uncover additional tools, infrastructure, malware samples, and other resources employed by the threat actor. This extended investigation helps in building a more comprehensive profile of the adversary's capabilities and activities.

# Resources

* [[1]](https://www.hvs-consulting.de/public/ThreatReport-EmissaryPanda.pdf) https://www.hvs-consulting.de/public/ThreatReport-EmissaryPanda.pdf
* [[2]](https://www.hvs-consulting.de/en/threat-intelligence-report-emissary-panda-apt27/) https://www.hvs-consulting.de/en/threat-intelligence-report-emissary-panda-apt27/
* [[3]](https://thedfirreport.com/2023/02/06/collect-exfiltrate-sleep-repeat/) https://thedfirreport.com/2023/02/06/collect-exfiltrate-sleep-repeat/
* [[4]](https://www.hvs-consulting.de/public/ThreatReport-Lazarus.pdf) https://www.hvs-consulting.de/public/ThreatReport-Lazarus.pdf
* [[5]](https://www.welivesecurity.com/2022/09/30/amazon-themed-campaigns-lazarus-netherlands-belgium/) https://www.welivesecurity.com/2022/09/30/amazon-themed-campaigns-lazarus-netherlands-belgium/
* [[6]](https://www.nextron-systems.com/2015/02/16/write-simple-sound-yara-rules/) https://www.nextron-systems.com/2015/02/16/write-simple-sound-yara-rules/
* [[7]](https://www.nextron-systems.com/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/) https://www.nextron-systems.com/2015/10/17/how-to-write-simple-but-sound-yara-rules-part-2/
* [[8]](https://cyb3rops.medium.com/how-to-post-process-yara-rules-generated-by-yargen-121d29322282) https://cyb3rops.medium.com/how-to-post-process-yara-rules-generated-by-yargen-121d29322282

> Cover Image by [Freepik](https://www.freepik.com/free-photo/multi-colored-psychedelic-background_11761297.htm#page=2&query=psychedelic%20pattern&position=1&from_view=keyword&track=ais)