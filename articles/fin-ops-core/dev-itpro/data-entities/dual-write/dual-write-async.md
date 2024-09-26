---
title: Set up and manage dual-write async in Dynamics 365 finance and operations apps
description: Learn about how to set up and manage dual-write async in Dynamics 365 finance and operations apps.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 09/26/2024
ms.custom:
ms.reviewer: twheeloc
---

# Set up and manage dual-write async in Dynamics 365 finance and operations apps

[!include [banner](../../includes/banner.md)]

This article describes how to set up and manage dual-write async in Dynamics 365 finance and operations apps.

>[Important!]
>This feature is currently in public preview and not meant to be used in production environments. 

## Overview 

Enterprise applications support complex business processes, and the real-time nature of business operations can result in long running transactions. This in turn can slow the application response times. However, 
while there are business scenarios that require to be synchronous to ensure real time consistency (example – financial transactions), there are other business scenarios which are good with eventual consistency. 
Dual-write Async supports the later business scenarios by adding a new layer of data movement that is near real-time between Dynamics 365 Finance and Operations and Dataverse applications but does not create long
running blocking transactions allowing more scale on customization. It helps avoid the real time synchronization limits, for example transaction timeouts and transaction size limits. 

 

In the era of low code no code approach, Dual-write Async makes it simple to manage your data integration, by allowing data synchronization to scale for application scenarios that support eventual consistency. 
Dual-write Async mode is recommended for entities which have sizeable peak volumes and data ingestion is driven by background processes (like batch jobs, AI agents, data import tools, offline integration systems) 
and do not need immediate feedback for any business operation. Based on the application entity, a near real time synchronization decouples any bi-directional data sync paving way for higher level of application 
customizations, without negatively impacting the live application.  

 
### Prerequisites for Async feature 

Async feature public preview, available on public clouds across all regions currently. Following are key conditions to enable the feature: 
 - Dynamics finance and operations Platform update (PU) 64 (10.0.40 with latest quality updates) and later. Verify the application foundation version greater than 7.0.7425.0
 - Minimum Dual-write Core solution version 1.0.24093.1 

### How it works 

Dual-write async feature has two key functionalities.  
Authoring: This helps define the table maps which should be part of asynchronous data movement. 

### Initial set up 

1. In the Dynamics 365 Finance and Operations home page, go to Data Management > Dual-write > Integration jobs.
2. Create a new Integration job.
3. Select “Add a table map”. A list of tables enabled for Asynch mode is available. Choose all the required tables to be set up in the asynch mode and save changes.
4. Click on Start to initiate the async mode. It could take a few minutes. The status of the job will indicate “Active” once it is ready. Select “Stop” to abort the async process.  

### Modification of the initial setup 

There are times when the admin will require to change the table groups or the sequence of execution within a table group to ensure that the integrity of the relationships is maintained. For example, the parent 
should be above the child table. 

Steps: 
1. Select the group and stop the Async job.
2. Select the table group and change the table map sequence as required.
3. Start the async job again. 


 

 	 

 
