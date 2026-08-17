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

### 4. Searching and Basic Navigation

The next stage of the course introduces the **Search & Reporting** interface and the basics of searching and navigating within Splunk.

This section focuses on understanding how to:

- Navigate the Splunk Search & Reporting interface
- Perform basic searches across ingested data
- Use time ranges to control which events are returned
- View and examine individual events
- Identify and work with fields within events
- Review search results and refine searches
- Understand basic Splunk data concepts such as **host**, **source** and **sourcetype**

Basic searching is an important part of working with Splunk because it provides the foundation for investigating and analysing machine-generated data.

The course will build on these fundamentals later by introducing **Search Processing Language (SPL)** and more advanced methods of searching, filtering and analysing data.


---

### 5. Knowledge Objects

**Knowledge Objects (KOs)** are reusable configurations in Splunk that help users organise, search, analyse and present data more efficiently.

They allow information or search logic to be saved and reused rather than having to recreate the same configuration each time.

Examples of Knowledge Objects include:

- **Reports** — Saved searches that can be run again or used as the basis for other Splunk features.
- **Dashboards** — Collections of visualisations and panels used to present and monitor data.
- **Alerts** — Configured searches that can trigger an action when specific conditions are met.
- **Lookups** — External data that can be used to enrich or add context to Splunk events.
- **Calculated fields** — Fields created using expressions to derive additional information from existing data.
- **Event types** — Saved search definitions used to categorise events.
- **Tags** — Labels applied to specific field-value pairs to make data easier to identify and search.

Knowledge Objects are useful because they allow searches, classifications, enrichments and visualisations to be **saved, reused and shared** within Splunk.

The course introduces Knowledge Objects and then demonstrates how they can be created and used within the Splunk environment.
