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

## 1. Security Dashboard

### What is a Dashboard?

A Splunk dashboard is a collection of visualisations and panels that presents search results in an easy-to-understand format.

Dashboards are useful for monitoring because they bring relevant information together in one place. Instead of manually running searches, a stakeholder can use the dashboard to quickly identify important activity, trends and potential security concerns.

### Purpose of This Dashboard

The **Website Security Concerns** dashboard provides an overview of security-related authentication activity within the web-server environment.

The dashboard focuses on SSH authentication activity and helps a stakeholder identify potentially concerning authentication patterns that may require further investigation.

### Dashboard Component

The dashboard contains a visualisation showing the different SSH authentication actions recorded within the security logs:

- Blocked authentication
- Failed authentication
- Started authentication sessions
- Successful authentication

### Dashboard Screenshot

![Website Security Concerns dashboard showing SSH Authentication Activity](https://github.com/user-attachments/assets/99f97c78-1385-4716-ae96-04c8cf541511)

### SPL Search

    index=security eventtype=sshd_authentication
    | stats count BY action
    | sort -count

### Results

The search returned the following authentication activity:

- **Blocked:** 25,099
- **Failure:** 24,958
- **Started:** 1,219
- **Success:** 1,219

### Findings

The results show a significantly higher volume of **blocked and failed authentication activity** compared with successful authentication activity.

This makes authentication activity an important area to monitor for potential security concerns. However, failed or blocked authentication events do not automatically indicate malicious activity and would require further investigation and contextual analysis.
---

## 2. Security Report


# What is a Report?

A Splunk report is a saved search that can be run automatically according to a defined schedule.

Reports are useful when stakeholders need regular information without having to manually open Splunk and run the search themselves. A report can provide a consistent summary of specific activity that a stakeholder wants to monitor.

### Purpose of This Report

The **Failed SSH User Logins** report monitors failed SSH user authentication attempts within the security logs.

The report provides a simple count of failed authentication attempts, allowing a stakeholder to regularly monitor authentication activity and identify potentially concerning levels of failed login activity.

Unlike the dashboard, which is designed for interactive monitoring and visualisation, the report is designed to **automatically run the saved search on a scheduled basis**.

### SPL

    index=security eventtype=sshd_authentication action=failure
    | stats count AS "Failed Login Attempts"

### Results

The search returned **24,958 failed SSH user authentication attempts** using the **All time** time range.

![Failed SSH User Login Report](https://github.com/user-attachments/assets/e1bdaf7e-74ab-44ef-ac14-5faf937c71cf)

### Schedule

The search was saved as the **Failed SSH User Logins** report and configured to run **daily at 09:00**.

The **All time** range is used because the dataset contains historical security events rather than current-day activity.


---

## 3. Security Alert

# Potentially Suspicious Web Activity

## What is an Alert?

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


