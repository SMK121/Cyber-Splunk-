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


