# Splunk: Zero to Power User
 
## Overview
 
This repository documents my practical learning and hands-on work while completing the **Splunk: Zero to Power User** Udemy course.
 
The course covers Splunk fundamentals, data ingestion, searching, Search Processing Language (SPL), data analysis, visualisation, dashboards, alerts, data models and the Common Information Model (CIM).

---

## Table of Contents

- [Overview](#overview)
- [Practical Learning](#practical-learning)
  - [1. Splunk Installation](#1-splunk-installation)
  - [2. Practice Data](#2-practice-data)
  - [3. Verifying the Data](#3-verifying-the-data)
  - [4. Searching and Basic Navigation](#4-searching-and-basic-navigation)
  - [5. Knowledge Objects](#5-knowledge-objects)
  - [6. Fields](#6-fields)
  - [7. Search Processing Language (SPL)](#7-search-processing-language-spl)
  - [8. Transforming Searches and Commands](#8-transforming-searches-and-commands)
  - [9. Transactions and Event Analysis](#9-transactions-and-event-analysis)
  - [10. Manipulating Data with SPL](#10-manipulating-data-with-spl)
  - [11. Lookups](#11-lookups)
  - [12. Dashboards](#12-dashboards)
  - [13. Reports and Drilldowns](#13-reports-and-drilldowns)
  - [14. Alerts](#14-alerts)
  - [15. Tags and Event Types](#15-tags-and-event-types)
  - [16. Macros](#16-macros)
  - [17. Data Models](#17-data-models)
  - [18. Common Information Model (CIM)](#18-common-information-model-cim)
- [Conclusion](#conclusion)
 
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

After uploading the practice data, I used the **Splunk Search & Reporting** interface to verify that the data had been successfully ingested.

I used the following search:

```
index=*
```

This allowed me to view the available data and confirm that the uploaded practice dataset was accessible within Splunk.

The screenshot below shows the **Search & Reporting interface, the search query, and the resulting events** returned from the practice dataset:

![Splunk Search & Reporting showing ingested practice data](https://github.com/user-attachments/assets/c229c43b-3f2f-4cee-9e2d-2d0fbcdc150c)

The search results showed the different data sources that had been ingested, including:

* `web1`
* `web2`
* `web3`
* `cisco`

This confirmed that the practice data had been successfully uploaded and was available to work with in Splunk.

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
---

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

    index=* error

This searches the indexed data for events containing the keyword `error`.

#### Basic SPL Structure

SPL searches can be built by combining a search with additional commands.

The **pipe character (`|`)** passes the results of one command into another command.

For example:

    index=* | stats count

This searches the indexed data and then uses the `stats` command to count the number of events returned.

Commands can be chained together to perform more detailed analysis:

    index=* | stats count by host | sort -count

This counts the events associated with each host and then sorts the results from highest to lowest.

#### Common SPL Commands

Some of the basic commands used when working with SPL include:

| Command | Purpose | Example |
| :--- | :--- | :--- |
| `search` | Searches or filters events | `search status=404` |
| `stats` | Calculates statistics | `stats count by host` |
| `sort` | Sorts results | `sort -count` |
| `table` | Displays selected fields | `table host, user, status` |
| `dedup` | Removes duplicate results | `dedup src_ip` |
| `top` | Shows the most common values | `top src_ip` |

These commands can be combined to search and analyse data more efficiently.

#### Practical SPL Example

Using the practice data that has been ingested into Splunk, SPL can be used to investigate the available events.

For example:

    index=* | stats count by host

This groups the events by host and shows how many events are associated with each one.

A more focused search can then be built as I progress through the practical work and learn additional SPL commands.

#### SPL in Security Analysis

SPL is particularly useful in a **Security Operations Centre (SOC)** because analysts often need to investigate large volumes of security and system events.

It can be used to investigate:

- Failed login attempts
- Suspicious IP addresses
- Unusual user activity
- Network activity
- System errors
- Potential indicators of compromise
- Patterns of suspicious behaviour

This makes SPL an important skill for security monitoring, incident investigation and threat hunting.

---

### 8. Transforming Searches and Commands

Transforming searches are used to take raw Splunk events and turn them into more useful summaries, statistics and results.

Instead of simply viewing individual events, transforming commands allow users to analyse the data and identify patterns, trends and relationships within it.

Transforming searches are useful when working with large amounts of data because they can summarise thousands of events into information that is easier to understand.

#### What Are Transforming Commands Used For?

Transforming commands can be used to:

- Calculate statistics
- Count events
- Group results by fields
- Compare values
- Identify the most common activity
- Analyse activity over time
- Create tables and charts
- Summarise large amounts of data

Some commonly used transforming commands include:

| Command | Purpose | Example |
| :--- | :--- | :--- |
| `stats` | Calculates statistics and groups results | `stats count by host` |
| `chart` | Creates a table of results for reporting and visualisation | `chart count by host` |
| `timechart` | Analyses data over time | `timechart count` |
| `top` | Shows the most common values | `top src_ip` |

For example:

    index=* | stats count by host

This counts the number of events associated with each host.

The results can then be used to identify which hosts are generating the most activity.

#### Why Transforming Searches Are Useful

Transforming searches are particularly useful for security and IT analysis because analysts often need to understand patterns across large datasets rather than examine individual events.

For example, an analyst could use a transforming search to identify:

- The hosts generating the most events
- The most active source IP addresses
- Changes in activity over time
- The frequency of specific events
- Unusual increases in activity

---

### 9. Transactions and Event Analysis

Splunk events can sometimes represent individual parts of a larger activity or sequence.

The **`transaction`** command can be used to group related events together into a single transaction based on specified fields or conditions.

This can make it easier to understand a sequence of activity rather than analysing each event individually.

#### What Is the Transaction Command Used For?

The `transaction` command can be useful when multiple events belong to the same logical activity.

For example, a user's activity might involve:

    Login Attempt
        ↓
    Authentication
        ↓
    Session Activity
        ↓
    Logout

Looking at these events individually may not provide the full context. Grouping related events can help an analyst understand the overall sequence.

For example:

    index=* | transaction user

This can group related events based on the `user` field.

Transactions can be useful for:

- Investigating user activity
- Following sessions
- Understanding sequences of events
- Investigating authentication activity
- Correlating related events
- Supporting security investigations

The `transaction` command should be used carefully, particularly with large datasets, as grouping large numbers of events can require significant resources.

---

### 10. Manipulating Data with SPL

SPL can also be used to manipulate and filter search results so that the data becomes more useful for analysis.

Commands such as **`eval`**, **`where`** and **`search`** can be used to modify fields, apply conditions and narrow down results.

#### `eval`

The `eval` command can be used to create new fields or perform calculations using existing fields.

For example:

    index=* | eval total=bytes_in+bytes_out

This creates a new field called `total` by adding the values of `bytes_in` and `bytes_out`.

`eval` can also be used to apply conditional logic.

For example:

    index=* | eval severity=if(status=404,"Warning","Normal")

This creates a new `severity` field based on the value of the `status` field.

#### `where`

The `where` command is used to filter search results based on a condition.

For example:

    index=* | stats count by host | where count > 10

This first counts events by host and then returns only hosts with more than 10 events.

This can be useful when looking for activity that exceeds a particular threshold.

#### `search`

The `search` command can be used to search for or filter specific events.

For example:

    index=* | search status=404

This filters the results to events where the `status` field has a value of `404`.

A keyword can also be searched for:

    index=* | search error

This searches for events containing the keyword `error`.

#### Using These Commands Together

These commands can be combined to progressively analyse data.

For example:

    index=* | search status=404 | stats count by host | where count > 10

This search:

1. Searches the indexed data for events with a `404` status.
2. Counts the matching events for each host.
3. Filters the results to hosts with more than 10 matching events.

Combining commands in this way allows an analyst to move from a large set of raw events towards a smaller set of results that may require further investigation.

#### Security Analysis

These commands are useful in security monitoring and investigation because they allow analysts to:

- Filter relevant security events
- Identify activity above a defined threshold
- Create additional fields for analysis
- Compare values
- Investigate suspicious patterns
- Reduce large datasets to more manageable results

For example, repeated failed authentication attempts could be filtered and counted by source IP address to identify potentially suspicious activity.

---

### 11. Lookups

A **lookup** in Splunk allows additional information stored outside of the original event data to be matched with Splunk events. This can add useful context to existing data and make searches and investigations more informative.

For example, a lookup could contain information such as usernames, departments, asset details, IP addresses or other reference data. This information can then be matched against fields in Splunk events.

#### Why Are Lookups Useful?

Lookups can be used to:

- Add additional context to events
- Enrich existing Splunk data
- Associate information with existing fields
- Filter and search reference data
- Identify users or systems using additional information
- Make search results easier to understand
- Support security investigations

#### Practical Lookup Exercise

As part of the practical work, I used a provided `mockdata.csv` file to create and use a lookup in Splunk.

The CSV contained a list of people and associated information, including fields such as:

- First name
- Last name
- IP address
- Latitude
- Longitude
- State

The file was uploaded through the Splunk administration interface under:

**Settings → Lookups**

It was then configured as a lookup table so that the information could be accessed and used within Splunk searches.

The lookup data could then be searched and filtered using its available fields.

For example, I used the **State** field to filter the lookup data for:

    State = New York

This returned the people in the lookup data associated with New York and demonstrated how specific information could be retrieved from the lookup table.

![Splunk Lookup CSV](https://github.com/user-attachments/assets/7fd9547b-9707-440f-b272-59209bb74fc4)


#### Lookup Definition

The lookup was then configured through the **Lookup Definitions** settings in Splunk.

The definition was configured using the administrative settings, including the appropriate **owner** and lookup configuration. This made the uploaded CSV available as a defined lookup within Splunk.

#### Searching and Filtering Splunk Data

I then used the **Search & Reporting** interface to work with the indexed `web` data.

The following search was used:

    index=web
    | table productId
    | dedup productId

This searches the `web` index, displays the `productId` field and removes duplicate product IDs.

The search returned a list of unique product IDs, including:

![Splunk Search & Reporting](https://github.com/user-attachments/assets/2fd97e9f-212c-4def-aa64-333737d4fdd8)

This demonstrated how SPL can be used to select specific fields and remove duplicate values from indexed data.

Overall, the practical exercise provided experience with uploading external CSV data, filtering lookup information, configuring a lookup definition and working with indexed Splunk data through the Search & Reporting interface.

Lookups are particularly useful in security operations because reference data can provide additional context when investigating events, users, IP addresses or other indicators.

---


### 13. Dashboards

A **Splunk dashboard** is a collection of panels containing searches, tables, charts and other visualisations. Dashboards bring related information together in one place, making it easier to monitor and analyse activity.

#### Why Are Dashboards Useful?

Dashboards can be used to:

- Monitor systems and applications
- Track security and operational activity
- Display important metrics
- Identify trends and unusual activity
- Provide a central view of related information
- Support security monitoring and investigations

For example, a SOC dashboard could display event activity, failed login attempts, top source IP addresses and other security-related information in one place.

#### Practical Dashboard Exercise

I created a dashboard to monitor **total event activity over the previous three days** using Splunk's internal data.

![Splunk Dashboard - Total Events](https://github.com/user-attachments/assets/a2dcaa88-5087-4bdc-bc77-22715992a267)

---

The dashboard was based on the following SPL search:

```spl

index="_internal" sourcetype=splunkd
| timechart count
| trendline sma5(count) as "Our Moving Average of Total Events"


```

---
The search uses Splunk's internal _internal index and the splunkd sourcetype to work with events generated by Splunk itself.

The timechart count command counts the events over time, allowing the total event activity to be displayed across the selected three-day period.

The trendline sma5(count) command calculates a 5-period simple moving average of the event count. This helps smooth short-term fluctuations and makes the overall trend in event activity easier to identify.

I then used the results to create a dashboard visualisation showing the total number of events over the previous three days, together with the moving-average trend.

Dashboard Visualisation

The completed dashboard provided a graphical view of the total event activity and the moving-average trend, making it easier to monitor changes in activity over time.

This practical exercise demonstrated how SPL searches can be converted into visualisations and added to dashboards to make Splunk data easier to monitor, analyse and interpret.

---
### 14. Reports and Drilldowns

**Reports** in Splunk are saved searches that can be run again when the same information is needed. They are useful for regularly monitoring activity, analysing data and sharing useful search results with other users.

**Drilldowns** allow users to investigate a specific result in more detail. For example, a user could select a value, chart or table entry from a dashboard and use a drilldown to open a more detailed search related to that result.

#### Why Are Reports and Drilldowns Useful?

Reports and drilldowns can be used to:

- Save frequently used searches
- Reuse searches for regular analysis
- Monitor important activity
- Present search results in a structured way
- Investigate specific results in more detail
- Move from high-level information to the underlying events
- Support security investigations and troubleshooting

For example, a SOC analyst could have a report showing failed login attempts. A drilldown could then allow the analyst to select a particular user or IP address and investigate the related events in more detail.

#### Practical Exercise

I explored how searches can be saved as reports and how drilldowns can be used to investigate specific results.

This demonstrated how Splunk can be used to move from a saved search or high-level visualisation into more detailed event information, making it easier to investigate activity without having to manually create a new search each time.

Reports and drilldowns are particularly useful when working with dashboards and security monitoring because they allow analysts to quickly move from an overview of activity to more detailed investigation.

---

### 15. Alerts

A **Splunk alert** is a saved search that runs automatically based on defined conditions. When the conditions are met, Splunk can trigger an action to notify users or record the alert for further investigation.

Alerts are commonly used to detect events that may require attention, such as repeated failed login attempts, unusual activity, system errors or other potentially suspicious behaviour.

#### Why Are Alerts Useful?

Alerts can be used to:

- Detect suspicious or unusual activity
- Monitor security events
- Identify repeated failed login attempts
- Detect system or application errors
- Notify analysts when specific conditions occur
- Support incident detection and response
- Automate monitoring instead of relying on manual searches

For example, a SOC analyst could create an alert that looks for multiple failed login attempts within a specific time period. If the search meets the defined condition, the alert can notify the analyst so the activity can be investigated.

#### Practical Alert Exercise

I created and enabled a scheduled **Web Event Alert** using the practice `web` data.

The alert was configured to run on a scheduled basis using a cron expression and to check the **last 15 minutes** of data. The trigger condition was set to **Number of Results greater than 0**, meaning the alert will trigger when the search returns one or more matching events.

The alert was also configured with **Medium** severity and the **Add to Triggered Alerts** action, allowing triggered alert activity to be recorded within Splunk.

![Splunk Web Event Alert](https://github.com/user-attachments/assets/2a325d77-1dff-4a0b-ac92-fd232b1f5c95)

At the time of testing, the alert had been successfully created and enabled, although no triggered events had been recorded yet.

This practical exercise demonstrated how a Splunk search can be converted into an automated alert with defined scheduling, trigger conditions and actions.

Alerts are particularly useful in a **Security Operations Centre (SOC)** because analysts cannot manually monitor every event generated by an organisation. Automated alerts help bring potentially important activity to the analyst's attention for further investigation.

---

### 16. Tags and Event Types

**Tags** in Splunk are labels that can be applied to specific field-value combinations. They provide an easier way to identify and search for related information without having to remember the exact underlying field and value.

For example, a tag could be used to associate a specific IP address, host or user with a meaningful label.

**Event Types** are saved definitions that identify events matching a particular search. They can be used to categorise related events and make commonly used searches easier to reference.

#### Why Are Tags and Event Types Useful?

They can be used to:

- Categorise related events
- Make searches easier to understand
- Add context to existing data
- Identify important users, hosts or IP addresses
- Create reusable event categories
- Support security investigations
- Standardise how related activity is identified

For example, a SOC analyst could create an event type for failed authentication activity and use it to identify related events consistently across searches.

#### Practical Exercise

I explored how tags and event types can be used to organise and categorise Splunk data.

This demonstrated how Knowledge Objects can add meaning and context to existing events, making related activity easier to identify and search for.

Tags and event types can be particularly useful in security operations when analysts need to consistently categorise users, systems, network activity or other security-related events.

---

### 17. Macros

A **Splunk macro** is a reusable piece of SPL that can be inserted into searches. Macros are useful for simplifying complex or repetitive search logic and making searches easier to maintain.

Instead of repeatedly writing the same SPL, a macro can store the search logic and be called whenever it is needed.

#### Why Are Macros Useful?

Macros can be used to:

- Reuse common SPL search logic
- Reduce repetition in searches
- Simplify complex searches
- Make searches easier to read
- Standardise commonly used search logic
- Make changes easier to maintain

For example, if the same search filter is used across multiple searches, the filter can be stored in a macro and then referenced whenever required.

#### Practical Exercise

I explored how macros can be created and used within Splunk searches.

Macros can be created through **Settings → Advanced Search → Search Macros**, where the search logic, name and other settings can be configured.

Once created, the macro can be called from an SPL search using the macro's name, allowing the saved search logic to be reused without having to manually enter it each time.

This demonstrated how macros can make SPL searches more efficient, reusable and easier to maintain, particularly when the same search logic is required across multiple searches.

---

### 17. Macros

A **Splunk macro** is a reusable piece of SPL that can be inserted into searches. Macros are useful for simplifying complex or repetitive search logic and making searches easier to maintain.

Instead of repeatedly writing the same SPL, a macro can store the search logic and be called whenever it is needed.

#### Why Are Macros Useful?

Macros can be used to:

- Reuse common SPL search logic
- Reduce repetition in searches
- Simplify complex searches
- Make searches easier to read
- Standardise commonly used search logic
- Make changes easier to maintain

For example, if the same search and analysis is used across multiple searches, the search logic can be stored in a macro and then referenced whenever required.

#### Practical Macro Exercise

I created a macro called **`salesmade`** to store a reusable SPL search for purchase activity in the practice `web` data.

The macro definition was:

```spl
index=web action=purchase
| stats count by host
| addtotals col=t row=f fieldname="Total" labelfield=host count
```

---
The search looks for events where the action field is set to purchase, counts the purchase events by host and adds a total to the results.

After creating the macro, I tested it directly in the Search & Reporting interface by entering:

`salesmade`

The macro successfully expanded and executed the saved SPL, returning the number of purchase events for each web server.

The results showed:

![Splunk Salesmade Macro Results](https://github.com/user-attachments/assets/a5bb25fe-4ea5-4a55-bc0f-8dd22237e35e)

web1 — 2,041 purchase events
web2 — 1,887 purchase events
web3 — 1,809 purchase events

This practical exercise demonstrated how macros can store reusable SPL logic and allow the same search functionality to be called without manually entering the complete search each time.

Macros can be particularly useful in larger Splunk environments where analysts regularly use the same search logic across different searches, reports, dashboards and investigations.

---
### 18. Datamodels

A **Splunk data model** is a structured representation of data that organises related events and fields into a consistent format. Data models make it easier to search and analyse specific types of activity without having to work directly with the raw event structure every time.

Data models can contain datasets that represent different types of activity, such as authentication, network traffic, web activity or other security-related events.

#### Why Are Datamodels Useful?

Datamodels can be used to:

- Organise related events and fields
- Provide a consistent structure for searching data
- Simplify searches across different data sources
- Improve the way security data is analysed
- Support faster searches using accelerated data models
- Support dashboards, reports and security investigations
- Provide structured data for other Splunk features

#### Searching Datamodels

Splunk provides the `datamodel` command to search and explore data models.

A datamodel search can be used to retrieve structured information from a particular dataset rather than searching raw events directly.

For example:

```spl
| datamodel Web Web search
```

---
The exact datamodel and dataset available will depend on the data and applications configured in the Splunk environment.

Practical Datamodel Exercise

I explored how datamodels can be searched in Splunk and how structured datasets can be used to analyse related activity.

This demonstrated how datamodels can provide a more structured approach to searching and analysing Splunk data, particularly when working with large amounts of security-related information.

Datamodels are particularly useful in security operations because they provide a consistent structure for analysing different types of activity and can be used as a foundation for more advanced security searches.

---

### 19. Common Information Model (CIM)

The **Common Information Model (CIM)** is a standard used by Splunk to provide a consistent structure for data from different sources.

Different systems and applications can use different field names for the same type of information. CIM helps normalise these fields into a common structure so that searches and security applications can work more consistently across different data sources.

For example, different data sources might record information about a source IP address using different field names. CIM provides standardised fields that allow the same type of information to be searched consistently.

#### Why Is CIM Useful?

CIM can be used to:

- Standardise fields across different data sources
- Normalise security-related event data
- Make searches more consistent
- Support cross-source analysis
- Improve compatibility with Splunk security applications
- Support Splunk Enterprise Security
- Make dashboards and reports more consistent
- Simplify searches across different technologies

#### CIM and Data Normalization

CIM works closely with **data normalization**. Raw data from different systems may have different structures and field names, so the data needs to be mapped to the appropriate CIM fields.

This allows events from different sources to be analysed using common field names and structures.

For example:

**Different data sources → Normalized fields → CIM data model → Consistent searches**

#### CIM Add-on

Splunk provides CIM-compatible add-ons and tools that help map incoming data to the appropriate CIM fields.

The **CIM Add-on Builder** can also be used to create or customise mappings for data sources that do not already have suitable CIM mappings.

For this project, the main focus is understanding how CIM standardises data and why this is useful for security monitoring rather than building a custom CIM add-on.

#### CIM in Security Analysis

CIM is particularly important in a **Security Operations Centre (SOC)** because security analysts may need to investigate data from many different technologies and vendors.

Using a common data structure allows analysts to perform more consistent searches across areas such as:

- Authentication
- Network traffic
- Web activity
- Endpoint activity
- DNS activity
- Firewall activity
- Intrusion detection

This makes CIM an important concept when working with Splunk security monitoring and **Splunk Enterprise Security**.

---

## Conclusion

This Course and Project provided practical experience with **Splunk**, **Search Processing Language (SPL)**, data analysis and core Security Operations Centre (SOC) concepts.

The practical work covered searching and analysing indexed data, using SPL commands, enriching events with lookups, creating dashboards, configuring alerts and working with reusable search macros. It also introduced more advanced Splunk concepts including datamodels, data normalization and the Common Information Model (CIM).

Through the practical exercises, I developed a better understanding of how Splunk can be used to collect, search, analyse and visualise machine-generated data and support security monitoring and investigation.

The project also provided hands-on experience working with Splunk's interface, configuration settings and Knowledge Objects, helping to build a foundation for further development in **SOC analysis, SIEM technologies, incident investigation and threat detection**.

---

