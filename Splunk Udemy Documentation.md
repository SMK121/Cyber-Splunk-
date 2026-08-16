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