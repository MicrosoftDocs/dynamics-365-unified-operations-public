---
# required metadata

title: Commerce Data Exchange implementation guidance
description: This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives an overview, implementation tips, and overall guidance that should be considered as you plan your implementation in regards to forms, setup, configuration, best practices, and more.
author: jashanno
manager: AnnBe
ms.date: 05/01/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: RetailTerminalTable, RetailDevice
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: jashanno
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: Retail July 2017 update
---

# Commerce Data Exchange implementation guidance
This topic is intended for people who implement functionality that is related to data synchronization (Commerce Data Exchange, often known as CDX) in a Commerce environment. It gives an overview, implementation tips, and overall guidance that should be considered as you plan your implementation in regards to forms, setup, configuration, best practices, and more.

## Overview
Data configuration and synchronization is crucial to a proper implementation.  Regardless of business needs, IT infrastructure, and overall preparedness, if data is not being correctly synchronized, the entire environment is effectively useless.  As such, it is top priority to understand what is required to configure, generate, synchronize, and verify data synchronization across a full implementation. From Headquarters, through the Commerce Scale Unit, to the brick and mortar stores utilizing Modern POS and other in-store components.

Before going through this document, it is important to know the concepts of a channel (Store), registers and devices, and the concept of the offline database as a part of Modern POS.  As such, it is recommended to review some of the resources at the bottom of this document such as the Devices implementation guide and the Commerce architecture documents. 

### Important Headquarters forms
The **Channel database** page is used to create, review, and edit the channel databases (Used in Commerce Scale Units (Both Cloud and Self-hosted)) and offline databases (Used with Modern POS).  Each database created here refers to a single, physical database (One to One mapping).  The channel or offline database is associated to a channel database group.  From this page, full synchronizations of a scheduler job can be created for a selected channel or offline database.
[Channel database](./media/ChannelDatabase.png)

The **Channel database group** page is used to create, review, and edit the channel database groups.  Each group is associated to one or more databases (channel or offline). The database group is responsible for gathering the relevant data (That is required by all channel and offline databases associated to the database group) necessary to be generated as part of the CDX data synchronization.
[Channel database](./media/ChannelDatabaseGroup.png)

The **Channel profile** page is used to create, review, and edit the channel profiles.  Each channel profile stores the URLs relevant to the network-based communication necessary within a channel.  A channel profile will typically have a Retail Server URL and a Cloud POS URL.  Additionally, frequently there will also be a Media Server Base URL (This URL is the internet addressable location of images used by POS, eCommerce, and other Dynamics 365 Commerce channels).  A channel profile is automatically generated for a Commerce Scale Unit (Cloud) but must be manually generated as part of the Commerce Scale Unit (Self-hosted) configuration and installation steps.
[Channel database](./media/ChannelProfile.png)

The **Offline profile** page is used to create, review, and edit the offline profiles.  Each offline profile allows a user to configure offline related settings, including configurations such as the ability to **allow manual switch to offline before sign-in**, **Enable advanced offline switching**, and **Pause offline synchronization**.  These feature configurations are discussed in this and related documents referenced at the end of this document.
[Channel database](./media/OfflineProfile.png)

The **Commerce channel schema** page is used to create, review, and edit the channel schemas.  By default, one schema is already created and available named **AX7**.  The channel schema is required to provide the means of "how" to read the Headquarters database for Commerce data.  This is also where the configuration is located to exclude customer related data from data synchronization to offline databases.  This feature will be discussed in this and other documents referenced at the end of this document.
[Channel database](./media/ChannelSchema.png)

The **Distribution schedule** page is used to create, review, and edit the distribution schedule jobs.  These schedule jobs associate which channel database groups will run the associated scheduler job (Detailed next).  A schedule job can be marked active and has a singular direction of data associated to it (Typically download, to send data down to the channels).  By default, all Commerce related jobs already exist and are prepared for use with any generated Commerce Scale unit (Cloud).  From this page, delta synchronizations can be created for a selected schedule job.
[Channel database](./media/DistributionSchedule.png)

The **Scheduler job** page is used to create, review, and edit the job selected from the schedule job.  This job has a series of associated subjobs.  This job also is associated to a channel schema (Typically the **AX7** schema originally created.  A job can be excluded from synchronization to offline databases.
[Channel database](./media/SchedulerJob.png)

The **Scheduler subjob** page is used to create, review, and edit the subjob.  A subjob is associated to one or more jobs (Seen via the scheduler job form).  A subjob is associated to a single table within the Headquarters database.  This subjob shows the channel field mapping, which lists all the related fields utilized within the database table.
[Channel database](./media/SchedulerSubjob.png)

The **Download sessions** and **Upload sessions** pages are used to review and edit download or upload sessions previously created through the data packages generated via the above described forms.  These forms showcase how many rows of data exist to be synchronized, when the data was made available and when it was synchronized, and the overall size of the data package.  These forms allow for some amount of management and troubleshooting of data packages, such as seeing what errors may have occurred and canceling or deleting jobs that are causing any issue.  This is described more in the [Best practices](CDX-Best-Practices.md) document.


### Data synchronization overview
When a job is run (Scheduler job), the channel database group (Channel database group) selects the relevant data for all channel or offline databases (Channel database) associated to itself from the fields listed in the accumulated subjobs (Scheduler subjob.  The product of this selection of data is a data package.  Data packages is a file or files zipped together containing all previously selected data (or selected delta of data, typically) required to be applied to one or more destination databases (Whether that be a Channel database or Offline database).

Data is generated and flows in a very specific way (Download or upload).  It is important to understand how the various forms are used and how this data generation occurs to be able to understand how best to configure the timing and select what data to be synchronized.  When done properly, higher performance and lower Headquarters utilization is achieved.

**Insert data configuration flow diagram (Commerce Architecture - Forms flow (PNG, Need newer one))**
[Channel database](./media/NAMENAMENAME.png)

This diagram shows the different forms in Headquarters and how the configuration flow functions together to be able to generate data... ADD MORE INFO TO DESCRIBE.

**Insert data sync flow diagram (Commerce Architecture - Data Synchronization (JPG))**
[Channel database](./media/NAMENAMENAME.png)

This diagram shows the direction and flow of data to be synchronized downward from Headquarters and the transactional data to be flowed upwards... ADD MORE INFO TO DESCRIBE.

### Overview of package management
 - Review that packages are created and showcased in Download sessions
 - Review the logic around retry and cut (Need Daniel / Yonas assistance here)
 - 

### Important CDX related features (All available in version 10.0.12 or above)
| Feature name | Feature description |
|--------------|---------------------|
| Advanced offline | A series of configurations in the **Offline profile** to enable additional offline switching scenarios, the ability to switch to offline prior to POS login, and enhanced Headquarters availability testing to return to online status more easily. |
| Advanced offline | A series of configurations in the **Offline profile** to enable additional offline switching scenarios, the ability to switch to offline prior to POS login, and enhanced Headquarters availability testing to return to online status more easily. |
| Offline data exclusion | Also called Data sizing improvements, this feature set |

**Generate a table of the features**
 - Advanced offline
 - Offline switch before login
 - Data sizing improvements (Specify the ability to flag data to not be synchronized to offline)
**Comment high level on each feature and it's reason / value**

Statement on how these features will be discussed later in the document, such as implementation considerations sub-heading (And possibly resources to other docs if decided to break apart).



## Implementation considerations
This section describes some things that you should consider as you plan to implement features that are related to data management and configuration.

**TOPICS**
 - Timing of jobs... Create a schedule
   - Specify when to use **Pause offline synchronzation**
 - When to use **Allow manual switch to offline before login** and **Enable advanced offline switching**
   - Specify how the **System health check interval (min)** works, compare against the **Reconnect attempt interval (min)**
 - How to cut away data from offline synchronization (Based on Data sizing improvements)
   - Specify job and subjob ability to cut away and when it applies to all (Subjob) and when it applies only to subset (Job)
   - Specify what can and cannot be cut from offline (OPEN QUESTION)
   - Specify the steps to remove customers completely from offline DBs
..... additional topics?

**Review implementation considerations**
 - Have at least one separate channel database group for offline DBs
 - Have a "Data Calendar", specifying when data is pushed and how it all lines up so that it does not occur:
   - When system is already loaded with calls
   - When system is already loaded with statement posting or other Headquarters workloads
   - When too much data is being generated at the same time
 - Minimize data pushed to offline DBs to minimize offline size, generate additional database groups (As required) to further cut down on data sizes
 - 



**OPEN QUESTIONS IN THIS DOC NEEDING ANSWERS**
 - Verify Working folders are no longer required with Commerce Batch Service (Azure Batch for now)
 - What data can be cut from offline DBs and it will still work correctly for sales (CREATE SEPARATE DOC FOR FEATURE)
 - Review the logic around download session retry and cut (Need Daniel / Yonas assistance here)


## Resources
[Best practices](CDX-Best-Practices.md)
[Device management implementation guidance](implementation-considerations-devices.md)
[Commerce Architecture](commerce-architecture.md)
[Select an in-store topology](dev-itpro/retail-in-store-topology.md)

*Link to MPOS installer* LINK PENDING

*Link to CSU (Self-hosted) installer* LINK PENDING


TABLE EXAMPLE
| ID | Operation | Description | Button grid | Transaction screen | Welcome screen | Available offline | Locale-specific |
|----|-----------|-------------|-------------|--------------------|----------------|-------------------|-----------------|
| 707 | Activate device | Activate the current device by allowing an authenticated user to provide connection information and assign a device and register ID. | No | No | No | No | No |
