# Splunk Security Monitoring Mini Project

## Introduction

This project demonstrates how Splunk can be used to monitor and investigate potential security concerns within a website environment.

The project uses existing web-server data ingested into Splunk and focuses on analysing activity that could indicate unusual, suspicious or potentially malicious behaviour.

The project consists of three main Splunk features:

- **Dashboard** – Used to visualise and monitor security activity.
- **Report** – Used to summarise and distribute security information on a scheduled basis.
- **Alert** – Used to automatically detect activity that meets a defined security condition and notify the relevant user or team.

The overall aim is to demonstrate how raw web-server logs can be turned into useful security information for monitoring, analysis and investigation.

---

# 1. Security Dashboard

## Website Security Concerns

### What is a Dashboard?

A Splunk dashboard is a collection of visualisations and panels that presents search results in an easy-to-understand format.

Dashboards are useful for monitoring because they bring multiple pieces of information together in one place. Instead of manually running several searches, a stakeholder can use the dashboard to quickly see important trends, unusual activity and potential areas of concern.

### Purpose of This Dashboard

The **Website Security Concerns** dashboard will provide an overview of security-related activity within the website environment.

It will be designed to help a stakeholder answer questions such as:

- Is there an unusual increase in security-related activity?
- Which IP addresses are generating the most activity?
- Are there high levels of HTTP errors?
- Are there requests or patterns that may require further investigation?

The dashboard will use multiple visualisations to provide both a high-level overview and more detailed information about potentially concerning activity.

### Dashboard Components

The dashboard will include visualisations covering areas such as:

- Security-related activity over time
- HTTP status codes and errors
- Top source IP addresses
- Potentially suspicious web activity

### Dashboard Screenshot

*Screenshot to be added.*

### SPL Searches

*Searches to be added as the dashboard is created.*

### Findings

*Findings and observations to be added after analysing the dashboard data.*

---

# 2. Security Report

## Daily Website Security Activity Report

### What is a Report?

A Splunk report is a saved search that can be run automatically according to a defined schedule.

Reports are useful when stakeholders need regular information without having to manually open Splunk and run the search themselves.

For example, a security team could receive a daily report summarising the previous day's security-related activity.

### Purpose of This Report

The **Daily Website Security Activity Report** will provide a scheduled summary of relevant security activity identified within the web-server logs.

The report will allow a stakeholder to regularly review security-related events and identify anything that may require further investigation.

Unlike the dashboard, which is designed for interactive monitoring, the report is focused on **regularly delivering a summary of the data**.

### Schedule

**Frequency:** Daily

**Time:** To be configured

**Time Range:** To be configured

### Report Screenshot

*Screenshot to be added.*

### SPL Search

*Search to be added.*

### Findings

*Findings and observations to be added after the report has been created and reviewed.*

---

# 3. Security Alert

## Potentially Suspicious Web Activity

### What is an Alert?

A Splunk alert monitors search results and automatically triggers when a predefined condition is met.

Alerts are particularly useful for security monitoring because they can identify potentially concerning activity without requiring an analyst to continuously monitor the logs themselves.

For example, an alert could be configured to trigger when an IP address generates an unusually high number of requests within a specific period.

### Purpose of This Alert

The **Potentially Suspicious Web Activity** alert will monitor the web-server data for an activity pattern that could indicate a security concern.

When the defined condition is met, the alert will trigger and provide an opportunity for the activity to be investigated.

The alert does **not automatically confirm that an attack or vulnerability exists**. Instead, it acts as an indicator that something unusual has occurred and may require further investigation.

### Alert Configuration

**Alert Type:** To be configured

**Schedule:** To be configured

**Trigger Condition:** To be configured

**Threshold:** To be configured

### Alert Screenshot

*Screenshot to be added.*

### SPL Search

*Search to be added.*

### Investigation

If the alert triggers, the activity can be investigated by examining information such as:

- Source IP address
- Requested URLs
- HTTP status codes
- Request volume
- Timestamps
- Other relevant event fields

### Findings

*Findings and observations to be added after testing the alert.*

---

# Project Summary

The three components provide different ways of using Splunk for security monitoring:

| Feature | Main Purpose |
|---|---|
| **Dashboard** | Provides a visual overview of security activity and trends. |
| **Report** | Provides a scheduled summary of security information. |
| **Alert** | Automatically identifies activity that meets a defined security condition. |

Together, they demonstrate a basic security monitoring workflow:

**Monitor → Analyse → Report → Alert → Investigate**
