---
title: Archive sales orders
description: This article describes how to archive sales orders to help improve database performance while keeping the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: XXXX
ms.author: XXXX
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: MM/DD/YYYY
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive sales orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until further notice. -->

Over time, your company will probably generate and store a large volume of sales orders and sales order lines. Although these records aren't required for day-to-day operations, they may still be needed for purposes such as historical reporting, auditing, machine learning, legal claims, and so on. Keeping a large volume of historical sales orders and lines in your day-to-day working environment not only results in increased storage costs, but also impacts system performance and usability.

To solve these issues, you can leverage the archival framework for finance and operations apps to implement rules-based archiving of historical sales orders and order lines. The archived records are removed from your day-to-day working environment and stored in your Dataverse managed data lake, thereby improving system performance and lowering operating costs while keeping your historical sales records available as read-only data for when you need them.

During archiving, the system starts by moving records from the sales orders headers database table (`SalesTable`) and the related sales order lines table (`SalesLine`) to the `SalesTableHistory` and `SalesLineHistory` tables, respectively. Administrators and other suers can then view and validate the archived sales order records. Once approved, the administrator then schedules long-term data retention to move records from the `SalesTableHistory` and `SalesLineHistory` tables to the Dataverse managed Data Lake. <!--KFM: Please verify my edit of this paragraph. -->

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later. <!--KFM: Correct version? -->
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *(Preview) Archive*
    - *(Preview) Archive data to Dataverse managed data lake and purge*
    - *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge*
    - *(Preview) Archive sales orders to history tables*
    - *(Preview) Archive sales orders to history tables using archive service*

The purpose of each of these features is summarized in the following table

| Feature | Description |
|---|---|
| *(Preview) Archive* | This feature lets you execute data archive for select high volume areas of the product. The data archive is performed by a micro-service. You must first install the service from Lifecycle Services (LCS). <!--KFM: Link to this? What is the service called? Add to system requirements list? --> |
| *(Preview) Archive data to Dataverse managed data lake and purge* | Provides the archival framework to perform rules-based archiving of historical data. It removes archived records from your day-to-day working environment and stores them in your Dataverse managed data lake. |
| *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge* | Performs the last step in the archival process, which is archiving from the history tables to your Dataverse managed data lake. |
| *(Preview) Archive sales orders to history tables* | Performs the first step in the archival process, which is archiving from day-to-day transaction tables to history tables. Once archived to history tables, the data from the day-to-day transaction tables will be purged. <!--KFM: FM contains identical description of these two features. How is this one different? --> |
| *(Preview) Archive sales orders to history tables using archive service* | Performs the first step in the archival process, which is archiving from day-to-day transaction tables to history tables. Once archived to history tables, the data from the day-to-day transaction tables will be purged. <!--KFM: FM contains identical description of these two features. How is this one different? --> |

## Which sales orders can be archived and when

Sales orders can be archived when the following conditions are met:

- The sales orders must be fully invoiced.
- The ledger period must be closed or on hold.
- Inventory closing must be run on or after the to-period date of the archive.
- The period must be at least one year before the from-period date of the archive. <!--KFM: Which period? Ledger period? -->

## Set up a batch job to archive sales orders

To set up sales order archiving, follow these steps:

1. Navigate to **Archive** workspace. <!--KFM: How do we get here? Give full nav path. -->
1. From the top-left Archive dropdown button, select **Sales order archive automation**  
1. Then select company (legal entity) and click on the Archive button  
1. Then enter name and description (optional)and set schedule time to run. NOTE: For the Sales order archive automation, the repeats option has additional options available that other process automations do not. In the screenshot below the archive automation will run daily and run 13 hours each day, and will continue daily run until it completes, no matter how long it takes to complete.  
1. Then click on **Next** to setup Archive from date and archive to date,  

    Note: Only periods that meet the prerequisites will be available for selection.

1. Select **Finish**

## View archives Sales orders

The Archive workspace page shows full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status.

1. To view further details on the sales orders, click on the "**Archived Sales order**" button.  
1. Users can further view details for a given sales order. For example, inquire sales order confirmation, picking list, packing slip and Invoice journal.  

## Schedule Long-term data retention in Dataverse managed Data Lake

To move the archived sales orders to Dataverse managed Data Lake, follow the following steps:

1. Click on the Schedule purge button  
1. Then enter the Start date and time. This is the date time to start copy of data from the SalesTableHistory and SalesLineHistory tables to Dataverse managed Data Lake.  
1. User can then view the progress by clicking on the View purge history button.
