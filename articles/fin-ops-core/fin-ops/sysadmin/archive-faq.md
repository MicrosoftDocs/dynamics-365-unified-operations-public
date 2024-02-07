---
title: FAQ for Finance and Operations archival with DV LTR
description: This article describes FAQ for Finance and Operations archival with DV LTR
author: pnghub
ms.author: gned
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 2/06/2024
ms.custom:

---
# FAQ for Finance and Operations archival with DV LTR

Post archival, can I access the live data and archived data from Dataverse long term retention? 

Yes, you can use Microsoft Fabric (with PowerBI option) to query live and archived data. Dataverse makes it simple to set up Fabric. 

Can I view archived data from my FnO application? 

Yes, app specific inquiry forms are available within the application to view this data. Once data is permanently purged from history tables, this will not be an option. You can still use Microsoft Fabric (with PowerBI option) to query data from Dataverse long term retention. 

Can I restore data from history tables to live tables. 

Not currently. This is planned to be supported in the future. 

Can I restore data from Dataverse long term retention back to live tables. 

No, this is not planned to be supported.  

Will I save the maximum database capacity if I purge data from the history table? 

Yes, for full savings, consider purging the data from the history table, especially when you will no longer be accessing the historical data from the application inqueiry form. 

 

Does this feature archive related tables - For example If Supply Chain Management Inventory Transactions are archived, and there are related data in Supply Chain management Sales tables and Lines? 

No. The data from only the live application tables which are in the archive scenario will be archived. Dependent transactions outside the supported archive scenario will not be archived.  For example, archiving Inventory Transaction does not archive its original transactions, and vice versa. Admin will be required to set up the archival of SalesOrder separately.  

 

I have linked my FnO environment with a Dataverse environment and run a successful archival job from my FnO archival workspace. Can I now make a change to relink the FnO environment to a new PowerApps/CE environment.  

No, this will result in data loss and should not be done.  

I have run a successful archival job from my FnO archival workspace. When I refresh the Finance and Operations database with new production data, will my archived data be also refreshed with the same production Dataverse backup.  

No. Currently, the Finance and Operations database refresh will not automatically refresh the Dataverse. You will be required to separately refresh Dataverse from production. 

 

Inventory Trans: There is no inventory closing for "moving average transactions". Does this mean we cannot archive these transactions? The same also applies to "Standard Costing". Would these not be archived too? 

No, Inventory transactions archival scenario is not limited for transactions. Moving average transactions and standard cost transactions can be archived if they have closed inventory. 

 

What if I do not want to use LTR? I just need to delete data from F&O database?" 

Purge is on the roadmap however FnO will support purge from history first. 
