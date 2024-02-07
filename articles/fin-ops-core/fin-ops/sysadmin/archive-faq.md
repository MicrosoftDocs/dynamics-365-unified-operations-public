---
title: Dynamics 365 finance and operations archive with dataverse longterm retention FAQ (preview)
description: This article answers some FAQ about archiving data in Dynamics 365 finance and operations with dataverse. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---

# Dynamics 365 finance and operations archive with dataverse longterm retention FAQ 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

## After archiving data, can I access the live data and archived data from Dataverse long term retention? 
Yes, you can use Microsoft Fabric (with PowerBI option) to query live and archived data. Dataverse makes it simple to set up Fabric. 

### Can I view archived data from my Dynamics 365 finance and operations application? 
Yes, application specific inquiry page are available within the application to view this data. After data is permanently purged from history tables, this isn't an option. You can still use Microsoft Fabric (with PowerBI option) to query data from Dataverse long term retention. 

### Can I restore data from history tables to live tables? 
Not currently. This is planned to be supported in the future. 

### Can I restore data from Dataverse long term retention back to live tables?
No, this isn't supported.  

### Will I save the maximum database capacity if I purge data from the history table? 
Yes, for full savings, consider purging the data from the history table, especially when you will no longer be accessing the historical data from the application inqueiry form. 

### Does this feature archive related tables? 
For example If Supply Chain Management Inventory Transactions are archived, and there are related data in Supply Chain management Sales tables and Lines? 
No. The data from only the live application tables which are in the archive scenario will be archived. Dependent transactions outside the supported archive scenario will not be archived.  For example, archiving Inventory Transaction does not archive its original transactions, and vice versa. Admin will be required to set up the archival of SalesOrder separately.  

### I have linked my Dynamics 365 finance and operations environment with a Dataverse environment and run a successful archival job from my workspace. Can I make a change to relink the Dynamics finance and operations environment to a new PowerApps/CE environment?
No, this will result in data loss and should not be done.  

### I have run a successful archival job from my Dynamics 365 finance and operations archival workspace. When I refresh the Dynamics 365 finance and operations database with new production data, will my archived data be also refreshed with the same production Dataverse backup?  
No. Currently, the Dynamics 365 finance and operations database refresh will not automatically refresh the Dataverse. You will be required to separately refresh Dataverse from production. 

### There's no inventory closing for **Moving average transactions**. Does this mean we can't archive these transactions? The same also applies to "Standard Costing". Would these not be archived too? 
No, Inventory transactions archival scenario is not limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory. 

### What if I don't want to use long term retention? I just need to delete data from Dynamics 365 finance and operations database? 
Purge is on the roadmap.  Dynamics 365 finance and operations will support purge from history first. 
