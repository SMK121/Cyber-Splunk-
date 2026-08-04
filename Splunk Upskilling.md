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
