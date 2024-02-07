---
title: Dynamics 365 finance and operations archive with dataverse long term retention FAQ (preview)
description: This article answers FAQ about archiving data in Dynamics 365 finance and operations with dataverse. 
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---

# Dynamics 365 finance and operations archive with dataverse long term retention FAQ 

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

## After archiving data, can I access the live data and archived data from Dataverse long term retention? 
Yes, you can use Microsoft Fabric (with PowerBI option) to query live and archived data. Dataverse makes it simple to set up Fabric. 

### Can I view archived data from my Dynamics 365 finance and operations application? 
Yes, an application specific inquiry page is available to view archived data. After data is permanently purged from history tables, the data isn't available for viewing. You can still use Microsoft Fabric (with PowerBI option) to query data from Dataverse long term retention. 

### Can I restore data from history tables to live tables? 
Not currently and is planned for a future release. 

### Can I restore data from Dataverse long term retention back to live tables?
No, restoring data isn't supported.  

### Will I save the maximum database capacity if I purge data from the history table? 
For full savings, users can purge data from the history table. 

### Does this feature archive related tables? 
No. The data from only the live application tables that are in the archive scenario are archived. Dependent transactions outside the supported archive scenario aren't archived. For example, archiving Inventory Transaction doesn't archive its original transactions. Administrators are required to set up the archival of SalesOrder separately.  

### I linked my Dynamics 365 finance and operations environment with a Dataverse environment and run a successful archival job from my workspace. Can I make a change to relink the Dynamics finance and operations environment to a new PowerApps/CE environment?
No, relinking will cause data loss and shouldn't be done.  

### I have run a successful archival job from my Dynamics 365 finance and operations archival workspace. When I refresh the Dynamics 365 finance and operations database with new production data, will my archived data be refreshed with the same production Dataverse backup?  
No. Currently, the Dynamics 365 finance and operations database refresh don't automatically refresh the Dataverse. You're required to refresh Dataverse separately from production. 

### There's no inventory closing for **Moving average transactions**. Does this mean we can't archive these transactions? 
No, Inventory transactions archival scenario isn't limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory. 

### What if I don't want to use long term retention? I just need to delete data from Dynamics 365 finance and operations database? 
Purge history is planned for a future release. 
