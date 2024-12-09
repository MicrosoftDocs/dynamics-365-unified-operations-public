---
#required metadata

title: Archive Dynamics 365 customer invoice data
description: This topic explains how to archive customer invoice data using the Dataverse long term retention. 
author: JodiChristiansen
ms.date: 12/05/2024
ms.topic: article
ms.prod: 
ms.technology: 

#optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2024-12-05
ms.dyn365.ops.version: 10.0.24
---
# Archive Dynamics 365 Finance customer invoice data

This article explains how to archive Microsoft Dynamics 365 Finance customer invoice data. 
>[!Important]
>Customer invoice archiving can only occur for fiscal periods that are on hold or closed.

## Prerequisites 
The following prerequisites must be met before you archive customer invoice transactions:
 - In Feature management enable the features **(Preview) Archive Customer invoice with long term retention** and **Archive with Dataverse long term retention**. For more information on the set up of the archive feature see [Set up and manage archive](archive-setup-manage.md).
 - The fiscal period must be On hold or closed for the date range used in the archive job

 ## Set up an archival job
 To set up an archival job follow these steps. 
  1. Go to **System administration > Workspaces > Archive with Dataverse long term retention** to open the **Archive with Dataverse long term retention** workspace.
  2. Select **Customer invoice**.
  3. Select **New long term retention** to open a wizard that you can use to schedule a new Customer invoice long term retention job.
  4. Enter a name for the job, and then select **Next**. New long term retention jobs can be scheduled for sales order invoices or free text invoices or both on the same job.
  5. On the **Define criteria** page, select to archive sales order invoices, free text invoices or both.
  6. Enter the From date and To date. The fiscal periods must have a status of On hold or Permanently closed in that date range.
  7. Select one or more legal entities. One job is created for each legal entity and each invoice type selected.
  8. Select **Next**.
  9. Select the type of scheduling. Two types are supported:
     - **Single run** - long term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long term retention first. Then the save to history tables occurs.
     - **Daily during allotted time** - The long term retention runs continuously until it is completed. The **Save to history** process runs during the specified start and stop archiving time.
 10. Select **Finish** to schedule the archive job for the selected invoice types and the companies.
 11. Select the link in the **Results** column to view the progress or detailed logs.

## View historical data from the history table
To view the historical transactional details select an archive job and then **View history data**. The **Archived invoices** page displays the invoices and lines. 

Important

## Capacity reports
The Finance application tables that are moved to Dataverse long term retention appear in the Power Platform admin center, under the database storage capacity reports. The live and history tables are available in the **Finance** section of the Power Platform admin center capacity reports. 

