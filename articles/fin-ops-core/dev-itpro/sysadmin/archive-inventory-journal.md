---
title: Archive inventory journal data in Dynamics 365 Supply Chain Management (preview)
description: This article explains how to archive data in Microsoft Dynamics 365 Finance Tax transactions.
author: epodkolz
ms.author: epodkolzina
ms.reviewer: twheeloc
ms.topic: conceptual
ms.date: 3/20/2024
ms.custom:

---
# Archive inventory journal data in Dynamics 365 Supply Chain Management (preview)

[!INCLUDE [preview-banner](../../../supply-chain/includes/preview-banner.md)]

[This article is prerelease documentation and is subject to change.] 

This article explains how to archive data for inventory journal with Dataverse long term retention. 

Prerequisites 

The ledger period of inventory journal which need be archived must be closed. 

The period must be at least one year before the from-period date of the archive. 

Turn on the features in Supply Chain Management  

If your system doesn't already enable the features, follow these steps. 

Go to Feature management. 

Enable following feature 

Archive with Dataverse long term retention – This feature moves inventory journal to Dataverse long term retention and replicates the data to the history table. 

. 

Schedule the long term retention job 

To move inventory journal records to the Dataverse long term retention, follow these steps. 

Go to Workspaces > Archive with Dataverse long term retention. 

Select Inventory journal. 

Select New long term retention job to open a wizard that you can use to schedule a new Inventory Journal archival job with Dataverse long-term retention. 

Enter a name for the job, and then select Next. 

Select the period of inventory journal which needs to be purged, and then select Next. 

Enter the start date and time of the job, and then select Next. 

Select Finish to schedule the archive job. 

 

You receive a message that the long term retention job has been created.   

 

View the status of the long term retention job 

To view the results of the long term retention job, follow these steps. 

Go to Workspaces > Archive with Dataverse long term retention > Inventory journal. 

A list of long term retention jobs is shown. Select the job which the Job status field was set to Completed. 

Under Results, select the link. 

View the Inventory journal archive progress information. 

Select View detailed logs to view the Archive job message log. This log describes the steps of the long term retention job in detail. 

View historical data from the history table@ 

When the Inventory Journal data is archived with Dataverse long term retention, the archived data is also replicated to a history table within the Dynamics 365 Finance and Operations live application database. 
This allows users to view the archived data using an inquiry form. 

the long term retention job moves archived inventory journal to the Dataverse long term retention, the same data is replicated to the history table.  

To view the historical data, follow these steps. 

Go to Workspaces > Archive with Dataverse long term retention > Inventory journal. 

A list of long term retention jobs is shown. Select the job where the Job status field is set to Completed. 

Select View historical data to view the data in the history table. 

 

 

Capacity reports 

The capacity consumed by the Inventory Journal tables that are archived with Dataverse long term retention appear in the Power Platform admin center, under the database storage capacity reports. The capacity consumed by the live and history tables in the Dynamics 365 Finance and Operations tables are available in the Finance section of the Power Platform admin center capacity reports. 
