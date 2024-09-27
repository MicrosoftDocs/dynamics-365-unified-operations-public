---
title: Set up and manage dual-write async in Dynamics 365 finance and operations apps (preview)
description: Learn about how to set up and manage dual-write async in Dynamics 365 finance and operations apps.
author: pnghub
ms.author: gned
ms.topic: conceptual
ms.date: 09/26/2024
ms.custom:
ms.reviewer: twheeloc
---

# Set up and manage dual-write async in Dynamics 365 finance and operations apps (preview)

[This article is prerelease documentation and is subject to change.]

[!include [banner](../../includes/banner.md)]

This article describes how to set up and manage dual-write async in Dynamics 365 finance and operations apps.

>[Important!]
> This is a preview feature.
> Preview features aren't meant for production use and might have restricted functionality. These features are available before an official release so that customers can get early access and provide feedback.

## Overview 

Enterprise applications support complex business processes, and the real-time nature of business operations can result in long running transactions. This can slow the application response times. However, 
there are business scenarios that require to be synchronous to ensure real time consistency, there are other business scenarios that work with eventual consistency. 
Dual-write Async supports the later business scenarios by adding a new layer of data movement that is near real-time between Dynamics 365 finance and operations and Dataverse applications.
 - Doesn't create long running blocking transactions allowing more scale on customization
 - Avoids the real time synchronization limits. For example, transaction timeouts and transaction size limits. 

 
In the era of low code no code approach, Dual-write Async makes it simple to manage data integration by allowing data synchronization to scale for application scenarios that support eventual consistency. 
Dual-write Async mode is recommended for entities that have sizeable peak volumes and data ingestion is driven by background processes, and don't need immediate feedback for any business operation. Based on the application entity, a near real time synchronization decouples any bi-directional data sync. This paves the way for higher level of application customizations, without negatively impacting the live application.  


Dual-write async feature has two key functionalities:  
Authoring - Define the table maps which should be part of asynchronous data movement. 
Error management - Manage and troubleshoot failures encountered during data sync.

 
### Prerequisites for Async feature 
The Async feature public preview is available on public clouds across all regions currently. To enable the feature, the following are needed:  
 - Dynamics 365 finance and operations platform update (PU) 64 (10.0.40 with latest quality updates) and later. The application foundation version greater than version 7.0.7425.0.
 - Minimum Dual-write Core solution version 1.0.24093.1. 

Dual-write async feature has two key functionalities.  
Authoring - Helps define the table maps which should be part of asynchronous data movement. 
Error management - 



### Initial setup 

1. In Dynamics 365 finance and operations, go to **Data Management** > **Dual-write** > **Integration jobs**.
2. Create a new integration job.
3. Select **Add a table map**. A list of tables enabled for Asynch mode is available.
4. Select all the required tables needed to set up in the asynch mode and save changes.
5. Click **Start** to initiate the async mode. It could take a few minutes. The status of the job indicates **Active** when it's ready.
6. Select **Stop** to stop the async process.  

### Modification of the initial setup 
There are times when the table groups need to be changed or the sequence of execution need to be updated within a table group to maintain the integrity of the relationships. For example, the parent should be above the child table. 

To modify the initial setup, follow these steps: 
1. Select the group and stop the Async job.
2. Select the table group.
3. Update the table map sequence as required.
4. Start the async job again. 


 

 	 

 
