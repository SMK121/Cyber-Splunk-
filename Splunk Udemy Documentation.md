# Splunk: Zero to Power User
 
## Overview
 
This repository documents my practical learning and hands-on work while completing the **Splunk: Zero to Power User** Udemy course.
 
The course covers Splunk fundamentals, data ingestion, searching, Search Processing Language (SPL), data analysis, visualisation, dashboards, alerts, data models and the Common Information Model (CIM).
 
---
 
## Practical Learning
 
### 1. Splunk Installation
 
I began by downloading and installing Splunk as part of the course.
 
This provided a local Splunk environment to use for the practical exercises throughout the course.
 
---
 
### 2. Practice Data
 
The course provides a practice dataset to use for the practical exercises.
 
I downloaded the practice data and uploaded it into my local Splunk environment.
 
The practice dataset contains logs from **three web servers**, with each web server containing its own **access logs and security logs**. This provides different types of web and security-related events to work with in Splunk.
 
The data sources consist of:
- **web1** — Access and security logs
- **web2** — Access and security logs
- **web3** — Access and security logs
The final log uploaded during this stage was:
 
```text
cisco_ironport_web.log
```
 
This contains web-related log data from a Cisco IronPort device, providing an additional source of network and security-related data for analysis.
 
The data was successfully ingested and made available for searching and analysis.
 
---
 
### 3. Verifying the Data
 
After uploading the practice data, I used the Splunk Search & Reporting interface to verify that the data had been successfully ingested.
 
I used the following search:
 
```text
index=*
```
 
This allowed me to view the available data and confirm that the uploaded practice dataset was accessible within Splunk.
 
The search results showed the different data sources that had been ingested, including:
 
- web1
- web2
- web3
- cisco
This confirmed that the practice data had been successfully uploaded and was available to work with in Splunk.


---

---

### 4. Searching and Basic Navigation

Searching is one of the fundamental functions of Splunk. Once data has been ingested and indexed, searches allow users to find, investigate and analyse events within that data.

The **Search & Reporting** interface is the main area used to search and analyse data in Splunk. It provides the search bar, time range controls, search results, event details and field information.

Searching is useful because Splunk can store and process very large volumes of machine-generated data. Instead of manually reviewing individual log files, users can query the data and quickly identify events that match specific criteria.

#### What Is Searching Used For?

Splunk searches can be used for many different purposes, including:

- Finding specific events
- Investigating security incidents
- Troubleshooting systems and applications
- Monitoring user activity
- Investigating network activity
- Identifying errors and failures
- Searching for suspicious behaviour
- Supporting incident response
- Analysing trends and patterns
- Monitoring operational activity

For example, a security analyst could search for failed authentication attempts and then investigate whether multiple failures came from the same user or IP address.

An IT support or infrastructure team could search application or system logs to identify errors occurring during a particular period.

---


### 5. Knowledge Objects

**Knowledge Objects (KOs)** are reusable configurations in Splunk that help users organise, search, analyse, enrich and present data.

They are created from information or search logic that users want to save and reuse. Instead of repeatedly creating the same search or configuration from scratch, a Knowledge Object can preserve it for future use.

Knowledge Objects are particularly useful in environments where multiple analysts or teams work with the same Splunk data because they can provide a consistent way of searching, categorising and presenting information.

#### What Are Knowledge Objects Used For?

Knowledge Objects can be used to:

- Save frequently used searches
- Create reports
- Build dashboards
- Create alerts
- Categorise events
- Add context to existing data
- Create reusable search components
- Enrich events with additional information
- Standardise how teams work with data

For example, if a SOC analyst regularly searches for failed authentication attempts, the search can be saved as a report or used as part of an alert rather than being recreated every time.

#### Common Knowledge Objects

Splunk provides several types of Knowledge Objects.

Some of the main examples include:

- **Reports** — Saved searches that can be run again and reused for reporting or other Splunk features.
- **Dashboards** — Collections of panels and visualisations used to present information in an easily understandable format.
- **Alerts** — Searches that run based on defined conditions and can trigger actions when those conditions are met.
- **Lookups** — Additional data that can be combined with Splunk events to provide more context.
- **Calculated Fields** — Fields created from existing data using expressions or calculations.
- **Event Types** — Saved definitions used to categorise related events.
- **Tags** — Labels applied to specific field-value combinations to make them easier to identify and search.
- **Macros** — Reusable pieces of SPL that can simplify searches and reduce repetition.

---

#### Practical Example: Login Failure Alert

As part of working with Knowledge Objects, I created and tested an alert based on password/login failures.

The purpose of the alert was to identify repeated failed login activity that could indicate:

- Incorrect or repeated password attempts
- Brute-force activity
- Potential account compromise
- Suspicious authentication behaviour

The alert uses a search to identify relevant login failure events and can be configured to trigger when the defined conditions are met.

This demonstrates how Knowledge Objects can be used to move from simply searching data to **actively monitoring for potentially suspicious activity**.

Alerts are particularly useful in a SOC because analysts do not need to continuously run the same search manually. Splunk can monitor the search conditions and notify or trigger an action when the defined criteria are met.


---

### 6. Fields

Fields are named pieces of information extracted from Splunk events. They allow specific information within an event to be searched, filtered and analysed.

Examples of commonly used fields include:

- `host` — Identifies the host associated with an event
- `source` — Identifies where the event originated
- `sourcetype` — Identifies the type or format of the data
- `src_ip` — Source IP address
- `user` — Username
- `status` — Status or result of an activity

Fields are important because they allow searches to target specific information rather than searching through entire raw events.

For example:

```spl
index=* status=404
```

### 7. Search Processing Language (SPL)

**Search Processing Language (SPL)** is Splunk's search language used to search, filter, transform and analyse machine-generated data.

SPL allows users to work with large amounts of indexed data and turn raw events into useful information. Instead of manually reviewing individual log entries, SPL can be used to identify specific events, filter results, calculate statistics, group related activity and identify patterns.

SPL is one of the core skills required to use Splunk effectively, particularly when working with security monitoring, incident investigation, threat hunting and operational troubleshooting.

#### What Is SPL Used For?

SPL can be used to:

- Search indexed data
- Filter events
- Search specific fields
- Extract information from events
- Create calculated fields
- Perform statistical calculations
- Group events together
- Sort results
- Remove duplicate results
- Rename fields
- Identify patterns and trends
- Investigate security incidents
- Build reports and dashboards
- Create searches for alerts
- Support threat hunting

For example:

```spl
index=* error

```


