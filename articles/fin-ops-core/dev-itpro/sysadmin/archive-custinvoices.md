---
title: Archive Dynamics 365 customer invoice data
description: This article explains how to archive customer invoice data using the Microsoft Dataverse long term retention. 
author: JodiChristiansen
ms.date: 12/05/2024
ms.topic: how-to
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: jchrist
ms.search.validFrom: 2024-12-05
ms.dyn365.ops.version: 10.0.24
---

# Archive Dynamics 365 Finance customer invoice data

[!INCLUDE[banner](../includes/banner.md)]

This article explains how to archive Microsoft Dynamics 365 Finance customer invoice data. 

> [!IMPORTANT]
> Customer invoice archiving can only occur for fiscal periods that are on hold or closed.

## Prerequisites 

The following prerequisites must be met before you archive customer invoice transactions:
- In Feature management, enable the features **(Preview) Archive Customer invoice with long term retention** and **Archive with Dataverse long term retention**. For more information on how to set up the archive feature, see [Set up and manage archive](archive-setup-manage.md).
- The fiscal period must be **On hold** or **Closed** for the date range used in the archive job.

## Set up an archival job

To set up an archival job, follow these steps. 

1. Go to **System administration \> Workspaces \> Archive with Dataverse long term retention**.
1. Open the **Archive with Dataverse long term retention** workspace.
1. Select **Customer invoice**.
1. Select **New long term retention** to open a wizard that you can use to schedule a new Customer invoice long term retention job.
1. Enter a name for the job, and then select **Next**. New long term retention jobs can be scheduled for sales order invoices or free text invoices or both on the same job.
1. On the **Define criteria** page, select to archive sales order invoices, free text invoices or both.
1. Enter the **From date** and **To date**. The fiscal periods must have a status of On hold or Permanently closed in that date range.
1. Select one or more legal entities. One job is created for each legal entity and each invoice type selected.
1. Select **Next**.
1. Select the type of scheduling. Two types are supported:
   - **Single run** - long term retention and saving to history run continuously until both processes are completed. Data is always archived in Dataverse long term retention first. Then the save to history tables occurs.
   - **Daily during allotted time** - The long term retention runs continuously until it's complete. The **Save to history** process runs during the specified start and stop archiving time.
1. Select **Finish** to schedule the archive job for the selected invoice types and the companies.
1. Select the link in the **Results** column to view the progress or detailed logs.

## View historical data from the history table

To view the historical transactional details, select an archive job and then **View history data**. The **Archived invoices** page displays the invoices and lines. 

Important

## Capacity reports
The Finance application tables that are moved to Dataverse long term retention appear in the Power Platform admin center, under the database storage capacity reports. The live and history tables are available in the **Finance** section of the Power Platform admin center capacity reports. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
