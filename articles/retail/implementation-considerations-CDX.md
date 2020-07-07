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
The **Channel database** page is used to create, review, and edit the channel databases (Used in Commerce Scale Units (Both Cloud and Self-hosted)) and offline databases (Used with Modern POS).
Add image for this...

The **Channel database group** page is  ADD DESCRIPTION.
Add image for this...

The **Channel profile** page is  ADD DESCRIPTION.
Add image for this...

The **Offline profile** page is  ADD DESCRIPTION.
Add image for this...

The **Channel schema** page is  ADD DESCRIPTION.
Add image for this...

The **Distribution schedule** page is  ADD DESCRIPTION.
Add image for this...

The **Scheduler job** page is  ADD DESCRIPTION.
Add image for this...

The **Scheduler subjob** page is  ADD DESCRIPTION.
Add image for this...

The **Data sync interval** page is   ADD DESCRIPTION. 

Data packages are a series of files zipped together containing all data (or delta of data) required to be applied to a destination database (Whether that be Channel database or Offline database).  **More details or keep higher level?**

Additional details as required......


### Data synchronization overview
Data is generated and flows in a very specific way.  It is important to understand how this occurs to be able to understand how best to configure the timing and select what data to be synchronized. 

**Insert data sync flow diagram (Commerce Architecture - Data Synchronization (JPG))**

This diagram shows the direction and flow of data to be synchronized downward from Headquarters and the transactional data to be flowed upwards... ADD MORE INFO TO DESCRIBE.

**Insert data configuration flow diagram (Commerce Architecture - Forms flow (PNG, Need newer one))**

This diagram shows the different forms in Headquarters and how the configuration flow functions together to be able to generate data... ADD MORE INFO TO DESCRIBE.

### Overview of package management
 - Review that packages are created and showcased in Download sessions
 - Review the logic around retry and cut (Need Daniel / Yonas assistance here)
 - 

### Recent CDX related features (All available in 10.0.12 or above, some as old as 10.0.8)

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
 - What data can be cut from offline DBs and it will still work correctly for sales?
 - Review the logic around download session retry and cut (Need Daniel / Yonas assistance here)


## Resources
*Link to Devices Implementation Guide* [Device management implementation guidance](implementation-considerations-devices.md)

*Link to Commerce Architecture* [Commerce Architecture](commerce-architecture.md)

*Link to In-store Topologies* [Select an in-store topology](dev-itpro/retail-in-store-topology.md)

*Link to MPOS installer* LINK PENDING

*Link to CSU (Self-hosted) installer* LINK PENDING

