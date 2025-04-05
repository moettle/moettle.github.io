---
title: "The Heart of every Incident: Incident Coordination"
description: Without effective coordination, major incidents cannot be resolved efficiently. This article explains why incident coordination is critical and outlines its key responsibilities.
slug: incident-coordination
date: 2025-04-05 15:30:00+0000
image: cover.jpg
categories:
    - Overview
tags:
    - Incident Response
    - Incident Coordination
    - Incident Management
---

# Introduction
Surprised? Let me guess—you thought forensics was the heart of every incident response. While forensics is a crucial part of Incident response, it is definitely not its heart. The following article makes it clear why.

Too often, I’m thrown into an ongoing incident where an "Incident Response Provider" is already involved. So why would the customer bring in a second incident response provider if one is already on board?

The first thing I do, when I get thrown in such an incident, is test the waters with a few simple questions:
* What are the ongoing tasks and who is responsible for them?
* Where is the current situational overview, and who is updating it?
* Are there established working streams?
* Where are the results of the different working streams documented?

When I’m met with blank stares, I immediately know what’s happening: the so-called "Incident Response Provider" is just another forensics provider. They are selling forensic analysis as incident response while neglecting the most critical part—incident coordination.

Before diving into what incident coordination entails, let’s first discuss the fundamental building blocks of incident response.

# The Building Blocks of Incident Response
Every incident response effort consists of several key building blocks, also often called working streams. Basically teams working a specific part of the IR assessment:
* **Incident Coordination**
  * The glue that holds everything together, ensuring all aspects of the response function smoothly. That's why I called in the heart of every incident.
  * Assigning responsibilities
  * Assigning and tracking tasks
  * Keeping all teams aligned
  * More details in the next section
* **Digital forensics**
  * Evidence Acquisition
  * Performing forensic analysis
  * Assessing the extent of the attack
  * Identifying attacker tactics, techniques, and procedures (TTPs) and indicators of compromise (IOCs)
  * Determining the impact of the attack
* **Monitoring and Threat Hunting**
  * Watching for new attacker activity using TTPs and IOCs from forensics
  * Proactively hunting for additional compromised assets (systems, identities, etc.)
* **Remediation**
  * This building block is the reason why we perform all the other building blocks. In the end we want to get rid of the attacker and establish a clean base-line 
  * In this building block we need to implement a set of measures to achieve that
  * The results from digital forensics (especially the extent of the attack) comes in very handy here
* **Lessons Learned** (usually not a working stream but something you do after the remediation)
  * After remediation is done and successful, it's time to learn your lessons 
  * How can we avoid such incidents in the future?
  * How can we improve our prevention, detection, and response?


# The Role of Incident Coordination
As an incident coordinator you are effectively leading the whole incident and it's your responsibility the resolve the incident. Therefore a multitude of tasks must be performed in the coordination building block. These tasks involve
* Setting up and moderating regular status calls with all stakeholders
* Documenting and tracking status updates
* Assigning and tracking ongoing tasks
* Collecting results of all fulfilled tasks
* Ensuring critical decisions are made and documented
* Gathering and consolidating findings from all workstreams to maintain a situational overview
* Translating technical findings for management
* Communicating management decisions effectively to technical teams
* Ensuring all workstreams receive the necessary information
    
Note that some of tasks can be delegated or supported by others, but responsibility ultimately falls back to you as an Incident Coordinator.

# Why Incident Coordination Is Rare
The reason why there are so many providers not able to offer incident coordination is because high-quality incident coordinators are very rare. The role requires a unique combination of skills:
* **Highly organized**
  * Incidents are chaotic, especially in the beginning
  * An Incident Coordinator must keep track of numerous moving parts
  * Every little thing that gets overlooked might cause huge damage later on in the incident (e.g. you forgot to turn of one compromised system --> Your containment was incomplete and the attacker persists)
* **High-level view**
  * While forensic analysis like to get lost in technical details, someone needs to keep a high-level view of everything happening. This task goes to the incident coordinator
* **Excellent communication skills**
  * Since you have to communicate with forensic analysts as well as high-level management, you better work on your situational communication skills. Otherwise the analysts won't respect you and management won't understand you
  * Your moderation skills should also be strong since you often have to moderated chaotic calls and it's on you to direct everyone in a productive direction
* **Sufficient technical know-how**
  * First of all you need sufficient know-how about how incidents, incident response, and cyber attacks work
  * Next you need to know typical measures of containment, evidence acquisition, forensics and remediation
  * To be able to communicate and direct the Digital Forensics block, you should have forensic experience yourself
* **Incident Response Experience**
  * It takes years of hands-on Incident response experience until you are able to lead major incidents like APTs, Ransomware or Bad Insiders
* **Ability to Stay Calm Under Pressure**
  * If the incident coordinator starts to panic, everbody is going to panic
  * If you have all the skills described above, keeping calm shouldn't be a problem :)

# Conclusion
Now you know why Incident coordinators are rare. If you happen to find one, keep them and never let them go…

If you happen to be in the DACH region, we are training Incident Coordinators and Managers. So feel free to reach out.

One final piece of advice: if you're selecting an Incident Response provider, always ask how they manage and coordinate an incident. If they don’t have a clear answer, you’re usually dealing with a forensics provider, not a true Incident Responsed. If you are looking for a forensics provider, this is fine. If you are looking for an Incident Response provider, you should keep looking.


> Cover Image by [Freepik](https://www.freepik.com/free-photo/multi-colored-psychedelic-background_11761213.htm#from_element=detail_alsolike)

