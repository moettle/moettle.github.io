---
title: Black Basta - Insights from a Ransomware Response Assessment
description: The ransomware group Black Basta disclosed part of their C2 infrastructure during a recent attack
slug: black-basta-iocs
date: 2024-04-14 11:30:00+0000
image: cover.jpg
categories:
    - Advanced
tags:
    - Incident Response
    - Forensics
    - Threat Intelligence
toc:
    false
---

# Black Basta's clumsy attack

In a recent incident response assessment, our encounter with the ransomware group Black Basta shed light on their tactics. Although they were able to get initial access to a server system an early detection enabled us to contain and remediate the incident shortly after. What's interesting are the activities performed by Black Basta during their brief presence on the compromised system. Forensic analysis provided us with invaluable insights, including high quality IOCs, which we recently published [[1]](https://github.com/hvs-consulting/ioc_signatures/tree/main/BlackBasta). Besides the forensics findings, this article shows once again that established ransomware groups  often lack sophistication and can be protected against.

After gaining initial access, Black Basta attempted to deploy a beacon calling back to their C2 infrastructure. Since the server did not have direct access to the internet (outgoing traffic was very limited), the operator started to panic. In the following hour, the Black Basta operator tried various ways to reach their C2 infrastructure, thereby disclosing executed commands, IPs, as well as domains belonging to the C2 infrastructure. The attack showed similarities to the attack observed by TrendMicro [[2]](https://www.trendmicro.com/de_de/research/24/b/threat-actor-groups-including-black-basta-are-exploiting-recent-.html)

# IOCs
You can find our published IOCs on our Github repository [[1]](https://github.com/hvs-consulting/ioc_signatures/tree/main/BlackBasta), which also includes an export of our MISP event with more detailed descriptions and tagging. Since our observed attack and the attack observed by TrendMicro showed various parallels, we included TrendMicro's IOCs to provide a more comprehensive collection of Black Basta IOCs.

The following list of IPs and Domains have a very high certainty, since all of them were pinged while the operator was trying to get a connection to their C2 infrastructure. Since outgoing ICMP traffic was not allowed (unknown to the operator), they started to try out every C2 endpoint know to them. Very clumsly indeed but very fruitful for us :)
```{linenos=false}
45.11.183.110
198.244.135.245
91.134.207.30
37.10.71.143
170.130.165.44
15.204.170.49
79.132.135.149
170.130.165.132
79.132.130.60
91.134.187.17
144.202.38.240
198.27.121.195
151.80.52.32
webnubee.com
startupbuss.com
artspathgroup.net
buyblocknow.com
trailcosolutions.com
```

We strongly recommend to block these IOCs and to implement appropriate detections based on our IOCs.

To receive our HvS IOCs automatically in the future, I recommend to subscribe to our unrestricted [MISP Feed](https://misp.ir.hvs-consulting.de/feed/unrestricted/). This feed allows you to integrate our tagged IOCs in your MISP and enables you to automatically process and integrate these IOCs for detection and mitigation in your security solutions.

# Resources

* [[1]](https://github.com/hvs-consulting/ioc_signatures/tree/main/BlackBasta)https://github.com/hvs-consulting/ioc_signatures/tree/main/BlackBasta
* [[2]](https://www.trendmicro.com/de_de/research/24/b/threat-actor-groups-including-black-basta-are-exploiting-recent-.html) https://www.trendmicro.com/de_de/research/24/b/threat-actor-groups-including-black-basta-are-exploiting-recent-.html

> Cover Image by [Freepik](https://www.freepik.com/free-photo/multi-colored-psychedelic-background_11761208.htm#&position=46&from_view=collections&uuid=dcbe476a-37f5-4321-baca-55efaff2416d)