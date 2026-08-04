# Splunk Upskilling

> A collection of notes, practical exercises and learning resources covering Security Operations Centres (SOC), Security Information and Event Management (SIEM), Splunk fundamentals and Search Processing Language (SPL).

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

---
