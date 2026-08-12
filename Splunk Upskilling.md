# Splunk Upskilling

> A collection of notes, practical exercises and learning resources covering Security Operations Centres (SOC), Security Information and Event Management (SIEM), Splunk fundamentals and Search Processing Language (SPL).

---

## Table of Contents

- [Introduction](#introduction)
  - [How Everything Connects](#how-everything-connects)
  - [Where Splunk Fits](#where-splunk-fits)
  - [The Security Monitoring Pipeline](#the-security-monitoring-pipeline)
  - [Security Monitoring Pipeline Explained](#security-monitoring-pipeline-explained)
  - [Learning Objectives](#learning-objectives)

- [Security Operations Centre (SOC)](#security-operations-centre-soc)
  - [What is a SOC?](#what-is-a-soc)
  - [Key Functions of a SOC](#key-functions-of-a-soc)

- [Common SOC Technologies](#common-soc-technologies)

- [SOC Processes](#soc-processes)

- [Common SOC Challenges](#common-soc-challenges)

- [SOC Best Practices](#soc-best-practices)

- [SOC Roles](#soc-roles)

- [Threat Hunting](#threat-hunting)
  - [What is Threat Hunting?](#what-is-threat-hunting)
  - [Examples of Threat Hunting Activities](#examples-of-threat-hunting-activities)

- [Common Security Event Types to Monitor](#common-security-event-types-to-monitor)

- [Security Information and Event Management (SIEM)](#security-information-and-event-management-siem)
  - [What is SIEM?](#what-is-siem)
  - [SIEM Analogy](#siem-analogy)
  - [Examples of SIEM Software (2026)](#examples-of-siem-software-2026)

- [What is Splunk?](#what-is-splunk)

- [What can Splunk be used for?](#what-can-splunk-be-used-for)

- [Why use Splunk?](#why-use-splunk)

- [What is a Splunk/SOC Analyst?](#what-is-a-splunksoc-analyst)

- [Splunk Versions](#splunk-versions)


---
# Introduction

As organisations become increasingly reliant on digital systems, they also become more vulnerable to cyber attacks such as ransomware, phishing, insider threats and data breaches. Every day, thousands or even millions of security events are generated across servers, applications, cloud platforms, endpoints and network devices.

Monitoring this enormous volume of data manually is impossible. Organisations therefore use a **Security Operations Centre (SOC)** supported by a **Security Information and Event Management (SIEM)** platform such as **Splunk** to detect, investigate and respond to cyber threats.

Splunk enables security teams to collect logs from multiple sources, search and analyse large volumes of machine data, generate alerts for suspicious activity and provide dashboards that improve visibility across an organisation's IT environment.

This repository documents my learning journey through SOC operations, SIEM concepts, Splunk architecture, Search Processing Language (SPL), and practical security monitoring techniques.

---

## How Everything Connects

```text
                Cyber Security
                      │
                      ▼
       Protect Organisation's Systems
                      │
                      ▼
      Security Operations Centre (SOC)
        Monitors & Responds to Threats
                      │
                      ▼
    SIEM Platform (e.g. Splunk Enterprise)
 Collects • Correlates • Detects • Investigates
                      │
                      ▼
          Dashboards • Alerts • Reports
                      │
                      ▼
          Security Analysts Respond
```

---

## Where Splunk Fits

| Layer | Purpose | Example |
|--------|---------|----------|
| Cyber Security | Protect systems, networks and data | Security policies, firewalls |
| SOC | Monitors security incidents | Tier 1, Tier 2 Analysts |
| SIEM | Collects and analyses security logs | Splunk Enterprise Security |
| Splunk | Searches, visualises and investigates machine data | Dashboards, alerts, reports |

---

## The Security Monitoring Pipeline

```text
Servers
Applications
Firewalls
Cloud
Endpoints
Network Devices

        │
        ▼

Generate Logs & Events

        │
        ▼

SIEM (Splunk)

        │
        ├── Collect Data
        ├── Index Data
        ├── Search Events
        ├── Detect Threats
        └── Generate Alerts

        │
        ▼

SOC Analysts

        │
        ▼

Investigate → Contain → Recover → Improve
```
## Security Monitoring Pipeline Explained

The security monitoring pipeline shows how security data moves through an organisation. Systems such as servers, applications, firewalls, cloud platforms and endpoints generate logs and events, which are collected by a SIEM platform such as Splunk.

Splunk processes this data by collecting, indexing and analysing events to identify suspicious activity and generate alerts. SOC analysts then investigate these alerts, respond to confirmed threats, contain the impact, recover affected systems and improve security controls to prevent future incidents.

---

## Learning Objectives

This repository covers:

- Understanding the purpose of a Security Operations Centre (SOC)
- Understanding how SIEM platforms improve cyber defence
- Learning how Splunk collects and analyses machine data
- Understanding Splunk architecture and deployment options
- Learning Search Processing Language (SPL)
- Creating searches, reports and dashboards
- Investigating security events using Splunk
- Building practical SOC knowledge for entry-level Cyber Security and SOC Analyst roles

---

# Security Operations Centre (SOC)

## What is a SOC?

A **Security Operations Centre (SOC)** is a dedicated team responsible for monitoring, detecting, investigating and responding to cybersecurity threats within an organisation.

The main purpose of a SOC is to provide continuous visibility over an organisation's IT environment and reduce the impact of security incidents.

A SOC combines:

- Security analysts
- Security tools
- Processes
- Threat intelligence
- Incident response procedures

Together, these allow organisations to identify suspicious activity before it becomes a major security incident.

---

## Key Functions of a SOC

| Function | Description |
|----------|-------------|
| Security Monitoring | Continuously monitors systems, networks and applications for suspicious activity |
| Threat Detection | Identifies potential threats using alerts, rules and analytics |
| Incident Response | Investigates and responds to security incidents |
| Threat Intelligence | Uses information about current threats, attackers and vulnerabilities |
| Threat Hunting | Proactively searches for hidden threats that bypass security controls |
| Vulnerability Management | Identifies weaknesses and helps reduce security risks |
| Digital Forensics | Analyses evidence from compromised systems |
| Reporting | Creates security reports and metrics for stakeholders |

---

# Common SOC Technologies

A SOC uses multiple security technologies to provide visibility and protection.

| Technology | Purpose | Example |
|------------|---------|---------|
| SIEM | Collects and analyses security logs | Splunk, Microsoft Sentinel |
| EDR | Detects threats on endpoints | CrowdStrike Falcon, Microsoft Defender |
| XDR | Combines security data across multiple areas | Palo Alto Cortex XDR |
| IDS/IPS | Detects and blocks suspicious network traffic | Snort, Suricata |
| Firewalls | Controls network access | Palo Alto, Fortinet |
| Vulnerability Scanners | Finds weaknesses in systems | Nessus, Qualys |
| SOAR | Automates security response actions | Splunk SOAR |
| Threat Intelligence Platforms | Provides information about attackers and threats | MISP |

---

# SOC Processes

SOC teams usually follow an incident response lifecycle:

    Monitoring
         │
         ▼
    Detection
         │
         ▼
   Investigation
         │
         ▼
   Containment
         │
         ▼
   Eradication
         │
         ▼
    Recovery
         │
         ▼
 Lessons Learned

### Example:

A user receives a phishing email:

1. Email security detects suspicious attachment
2. SIEM creates an alert
3. SOC analyst investigates the event
4. Malware is identified
5. Account access is removed
6. Endpoint is cleaned
7. Detection rules are improved

---

# Common SOC Challenges

| Challenge | Description |
|-----------|-------------|
| Alert Fatigue | Large numbers of alerts can overwhelm analysts |
| False Positives | Legitimate activity may trigger security alerts |
| Data Volume | Organisations generate millions of logs daily |
| Limited Resources | Security teams may have limited staff and time |
| Advanced Threats | Attackers continuously change techniques |
| Cloud Complexity | Hybrid and cloud environments increase visibility challenges |
| Skills Shortage | Demand for cybersecurity professionals continues to grow |

---

# SOC Best Practices

Effective SOC teams follow several best practices:

- Centralise logs using a SIEM platform
- Prioritise critical alerts
- Regularly update detection rules
- Automate repetitive tasks
- Maintain incident response playbooks
- Use threat intelligence
- Conduct regular threat hunting
- Follow least privilege principles
- Monitor critical assets first
- Review previous incidents to improve processes

---

# SOC Roles

| Role | Responsibilities |
|------|------------------|
| Tier 1 SOC Analyst | Reviews alerts, performs basic investigation and escalation |
| Tier 2 SOC Analyst | Performs deeper investigations and handles incidents |
| Tier 3 SOC Analyst | Conducts advanced investigations and malware analysis |
| Incident Responder | Coordinates containment and recovery |
| Threat Hunter | Searches proactively for threats |
| Detection Engineer | Creates and improves detection rules |
| Security Engineer | Designs and maintains security solutions |
| SOC Manager | Manages SOC operations and reporting |

---

# Threat Hunting

## What is Threat Hunting?

Threat hunting is a proactive security activity where analysts search for threats that may have avoided existing security controls.

Unlike normal alert monitoring, threat hunting does not wait for an alert. Analysts investigate suspicious patterns and attacker behaviour.

---

## Examples of Threat Hunting Activities

| Investigation | Example |
|-|-|
| Suspicious Authentication | Multiple failed logins followed by success |
| Privilege Escalation | User gaining unexpected administrator privileges |
| Malware Behaviour | Unknown processes running on endpoints |
| Network Activity | Unusual outbound connections |
| PowerShell Usage | Suspicious commands being executed |
| Persistence | Unexpected scheduled tasks or services |

Threat hunters commonly use frameworks such as:

- MITRE ATT&CK
- Cyber Kill Chain

---

# Common Security Event Types to Monitor

SOC analysts commonly investigate:

| Event Type | Example |
|------------|---------|
| Authentication Events | Successful and failed logins |
| Account Changes | New users or privilege changes |
| Endpoint Events | Process creation and malware detection |
| Network Events | Firewall traffic and suspicious connections |
| DNS Events | Requests to malicious domains |
| Email Events | Phishing attempts |
| VPN Events | Remote access activity |
| Cloud Events | AWS, Azure and Google Cloud activity |
| File Events | File creation, modification or deletion |
| Application Logs | Errors and suspicious behaviour |

---

# Security Information and Event Management (SIEM)

## What is SIEM?

A **Security Information and Event Management (SIEM)** platform is a technology used to collect, store, analyse and monitor security data from multiple sources.

SIEM solutions allow organisations to:

- Collect logs from different systems
- Detect suspicious activity
- Correlate related events
- Generate alerts
- Support investigations
- Create security dashboards

---

# SIEM Analogy

A SIEM can be compared to a **security control room in a large building**.

A building has:

- CCTV cameras
- Door access systems
- Alarm systems
- Security guards

Each system produces information.

The control room collects everything together, analyses activity and alerts security staff when something suspicious happens.

A SIEM works in the same way by collecting information from:

- Servers
- Applications
- Endpoints
- Firewalls
- Cloud services

and presenting it to security analysts.

---

# Examples of SIEM Software (2026)

| SIEM Platform | Company |
|--------------|---------|
| Splunk Enterprise Security | Cisco Splunk |
| Microsoft Sentinel | Microsoft |
| IBM QRadar | IBM |
| Google Security Operations | Google |
| Elastic Security | Elastic |
| Securonix | Securonix |
| LogRhythm | LogRhythm |

---

# What is Splunk?

Splunk is a data analytics platform used to collect, search, analyse and visualise machine-generated data.

Although Splunk is widely used in cybersecurity, it can also support:

- IT monitoring
- Application performance monitoring
- Business analytics
- Compliance reporting
- Infrastructure monitoring

Splunk turns large amounts of raw machine data into useful information that analysts can investigate.

---

# What can Splunk be used for?

| Area | Example Use |
|-|-|
| Cyber Security | Detect suspicious login activity |
| SOC Operations | Investigate security alerts |
| IT Operations | Monitor server health |
| DevOps | Analyse application logs |
| Business Analytics | Understand customer behaviour |
| Compliance | Produce audit reports |

---

# Why use Splunk?

Organisations use Splunk because it provides:

- Centralised log management
- Fast searching across large datasets
- Real-time monitoring
- Security alerts
- Dashboards and reports
- Historical investigation capability
- Integration with many security tools

---

# What is a Splunk/SOC Analyst?

A Splunk or SOC Analyst uses Splunk to monitor security events, investigate alerts and identify potential threats.

Typical responsibilities include:

- Reviewing SIEM alerts
- Searching logs using SPL
- Investigating suspicious activity
- Creating dashboards
- Building reports
- Improving detection rules
- Supporting incident response

---

# Splunk Versions

| Version | Description |
|-|-|
| Splunk Enterprise | Self-hosted Splunk deployment managed by an organisation |
| Splunk Cloud Platform | Cloud-hosted Splunk solution managed by Splunk |
| Splunk Enterprise Security | Security-focused application built on Splunk |
| Splunk SOAR | Automates security response workflows |

---

# Splunk Architecture

Splunk uses a distributed architecture to collect, process, store and search machine-generated data. The main components covered in this section are the **Search Head, Universal Forwarder and Indexer**.

-
                         DATA SOURCES
       ┌──────────┬──────────┬──────────┬──────────┐
       │          │          │          │          │
    Servers   Firewalls   Cloud     Endpoints   Network
       │          │          │          │        Devices
       └──────────┴──────────┴──────────┴──────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │ Universal         │
                    │ Forwarder         │
                    │ Collects Data     │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │     Indexer(s)    │
                    │ Process & Store    │
                    │      Events       │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │    Search Head    │
                    │ Search & Analyse  │
                    │ Dashboards/Alerts │
                    └─────────┬─────────┘
                              │
                              ▼
                         SOC Analyst
Search Head

The Search Head is the Splunk component used to search, analyse and visualise data.

It provides the interface that users and analysts interact with when working with Splunk.

Common activities include:

Running SPL searches
Investigating security events
Creating dashboards
Creating reports
Configuring alerts
Analysing search results
Managing knowledge objects

In a distributed Splunk environment, a Search Head can send searches to one or more Indexers and combine the results.

Universal Forwarder

The Universal Forwarder (UF) is a lightweight Splunk component used primarily to collect and forward data to another Splunk component, such as an Indexer.

For example, a Universal Forwarder could be installed on a Windows server and configured to collect Windows Event Logs.

Its main functions include:

Collecting log data
Monitoring files and directories
Forwarding events
Using relatively few system resources
Sending data to Splunk Indexers or other receiving components

The Universal Forwarder is designed for data collection and forwarding, rather than searching and analysing data.

Indexers

Indexers receive incoming data, process it and store it so that it can later be searched.

Their main responsibilities include:

Receiving data
Processing incoming events
Indexing data
Storing indexed events
Making data available for searches

Large Splunk environments can use multiple Indexers to distribute data and search workloads, improving scalability and availability.

Splunk Deployment Options

Splunk can be deployed in different ways depending on the organisation's size, requirements and infrastructure.

Deployment	Description	Typical Use
Standalone	Search and indexing functions can operate on one system	Learning, testing and smaller environments
Distributed Deployment	Search Heads and Indexers operate on separate systems	Larger environments
Search Head Cluster	Multiple Search Heads work together	Scalability and high availability
Splunk Cloud Platform	Splunk is provided as a cloud service	Organisations wanting a managed Splunk environment
Standalone Deployment

A standalone deployment can be useful for learning and smaller environments because multiple Splunk functions can operate on a single instance.

Distributed Deployment

In a distributed deployment, Splunk components are separated across multiple systems.

Data Sources
     │
     ▼
Forwarders
     │
     ▼
Indexers
     │
     ▼
Search Head
     │
     ▼
Analysts

This approach allows organisations to scale their Splunk environment as the volume of data increases.

Search Head Cluster

A Search Head Cluster (SHC) consists of multiple Search Heads working together.

This can provide:

Improved availability
Scalability
Shared configuration and knowledge
Better support for multiple users
Splunk Cloud Platform

Splunk Cloud Platform provides Splunk as a cloud-based service. This can reduce the amount of infrastructure an organisation needs to manage itself.

Basic Splunk Terms

Understanding common Splunk terminology is important when learning how to search and analyse data.

Term	Meaning
Event	An individual record of activity indexed by Splunk
Index	A location where Splunk stores indexed events
Host	The system that generated the event
Source	The original source of the data
Sourcetype	Identifies the type or format of incoming data
Field	A named piece of information extracted from an event
SPL	Splunk Search Processing Language
Search Head	Component used to search and analyse data
Indexer	Component responsible for processing and storing data
Forwarder	Component used to collect and forward data
Dashboard	Collection of panels displaying search results
Alert	A notification generated when search conditions are met
Report	A saved search that can be run or scheduled
Timestamp	Records when an event occurred
What Type of Data Does Splunk Ingest?

Splunk is designed to collect and analyse machine-generated data from a wide range of systems.

Common sources include:

Data Source	Example Data
Windows	Windows Event Logs
Linux	Syslog and authentication logs
Firewalls	Allowed and blocked connections
Network Devices	Network traffic and authentication events
Web Servers	HTTP requests and errors
Applications	Application activity and errors
DNS	DNS queries and responses
VPN	Remote access activity
Cloud Platforms	API calls and authentication activity
Endpoints	Process, file and security events

Splunk can also ingest different data formats, including:

Plain text
CSV
JSON
XML
Syslog
Application logs
System logs

The type of data collected depends on the organisation's environment and monitoring requirements.

---
