---
title: Archive sales orders
description: This article describes how to archive sales orders to help improve database performance while keeping the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 05/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

<!--KFM: Add form codes to metadata -^  -->

# Archive sales orders

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until further notice. -->

Over time, your company will probably generate and store a large volume of sales orders and sales order lines. Although these records aren't required for day-to-day operations, they may still be needed for purposes such as historical reporting, auditing, machine learning, legal claims, and so on. Keeping a large volume of historical sales orders and lines in your day-to-day working environment not only results in increased storage costs, but also impacts system performance and usability.

To solve these issues, you can use the archival framework for finance and operations apps to implement rules-based archiving of historical sales orders and order lines. During archiving, the system starts by moving records from the sales orders headers database table (`SalesTable`) and the related sales order lines table (`SalesLine`) to the `SalesTableHistory` and `SalesLineHistory` tables, respectively. Administrators and other users can then view and validate the archived sales order records. Once approved, the administrator then schedules the process to move the verified records from the `SalesTableHistory` and `SalesLineHistory` tables to the Dataverse managed data lake for long-term storage. <!--KFM: Please verify my edit of this paragraph. -->

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.34 or later. <!--KFM: Correct version? -->
- The data archive micro-service must be installed on your system from Lifecycle Services (LCS). <!--KFM: Link to more info? What is the service called? Maybe a short mention of what configuration is needed (with link). -->
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *(Preview) Archive*
    - *(Preview) Archive data to Dataverse managed data lake and purge*
    - *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge*
    - *(Preview) Archive sales orders to history tables*
    - *(Preview) Archive sales orders to history tables using archive service*

The purpose of each of these features is summarized in the following table

| Feature | Description |
|---|---|
| *(Preview) Archive* | This feature lets you execute data archive for select high volume areas of the product. |
| *(Preview) Archive data to Dataverse managed data lake and purge* | Provides the basic archival framework for performing rules-based archiving of historical data. It makes it possible to remove archived records from your local history tables and store them in your Dataverse managed data lake. |
| *(Preview) Archive sales orders to history tables* | Performs the first step in the archival process, which is archiving from day-to-day transaction tables to local history tables. Once archived to history tables, the data from the day-to-day transaction tables will be purged. <!--KFM: FM contains identical description of these two features. How is this one different? --> |
| *(Preview) Archive sales orders to history tables using archive service* | Performs the first step in the archival process, which is archiving from day-to-day transaction tables to history tables. Once archived to history tables, the data from the day-to-day transaction tables will be purged. <!--KFM: FM contains identical description of these two features. How is this one different? --> |
| *(Preview) Archive sales order from history tables to Dataverse managed data lake and purge* | Performs the final step in the archival process, which is to remove archived orders from your local history tables and store them in your Dataverse managed data lake. |

## Which sales orders can be archived and when

Sales orders can be archived when the following conditions are met:

- The sales orders to be archived must be fully invoiced.
- The ledger period must be closed or on hold. <!--KFM: Which period? Current period? -->
- Inventory closing must be run on or after the to-period date of the archive. <!--KFM: Is our point that the closing must already be set to run, or that it must not be run before the to-period? -->
- The period must be at least one year before the from-period date of the archive. <!--KFM: Which period? -->

## Set up a batch job to archive sales orders

To set up sales order archiving, follow these steps:

1. Navigate to the **Archive** workspace. <!--KFM: How do we get here? Give full nav path. -->
1. On the Action Pane, select **Archive** to open a drop-down dialog box, and then make the following settings:
    - **Name** – select *Sales order archive automation*.
    - **Company** – select the legal entity (company) for which you want to archive sales orders.
1. Select **Archive** to apply your settings and close the drop-down dialog box.
1. The **Create new process automation** page opens, open to the **General** tab. Make the following settings:
    - **Schedule type** – <!-- KFM: Description needed -->
    - **Name** – Enter a name for the archive job.
    - **Description** – Enter a short description for the archive job.
    - **Scheduling** field group – Use the settings in this field group to define ... <!-- KFM: Description needed. -->
    - **Occurrence run times** field group – Use the settings in this field group to define ... <!-- KFM: Description needed -->
    - **Occurrence pattern** field group – Use the settings in this field group to define how often the archive job should run. When you're setting up a sales archive job, you have more options here than you do for most other types of process automation jobs.<!-- KFM: Description needed -->
    - **Alerts** and **Other alerts** field groups – Choose which kinds of events should trigger an alert (**Ended**, **Canceled**, and/or **Error**) and how you want to be notified (**Email** and/or **Show pop-ups**). <!-- KFM: Confirm these guesses. -->
1. Select **Next** to continue to the **Sales order archive automation** tab. Make the following settings:
    - **Archive from date** – Enter the date of the oldest sales orders that you want to archive.
    - **Archive to date** – Enter the date of the newest sales orders that you want to archive.

    > [!NOTE]
    > Only dates that meet the [prerequisites](#prerequisites) will be available for selection.

1. Select **Finish**.

## Review archived sales orders

The **Archive** workspace shows your full archiving history. Each row in the grid shows information such as the date when the archive was created, the user who created it, and its status. The orders listed here haven't yet been moved to your Dataverse managed data lake. They're now available for review and can be moved to your Dataverse managed data lake at any time, as described in the next section.

1. To open the **Archive** workspace, go to <!--KFM: How do we get here? Give full nav path. -->
1. On the **Section** FastTab, open the **Sales order archive** tab.
1. Your sales order archives are listed in the grid. To view details about the sales orders included in any archive, select an archive and then select **Archived Sales order** on the toolbar. <!--KFM: We should document the purpose of each other toolbar button somewhere ... -->
1. The **Archived sales orders** page opens, showing a list of each sales order included in the archive.
    - To view an order, including its header and all of its order lines, select it in the grid. <!-- KFM: Please confirm this guess. -->
    - To view related information about an order, select the order, open the **Inquiry** menu on the Action Pane and then choose the entry for the type of records you'd like to inspect (**Sent sales quotations**, **Sales order confirmations**, **Picking list**, **Packing slip** or **Invoice journal**).

## Schedule long-term data retention in Dataverse managed data lake

After you have reviewed a sales order archive and are sure you're ready to move it to your Dataverse managed data lake, follow these steps:

1. Return to the **Sales order archive** tab of the **Archive** workspace.
1. Select the archive you want to move to your Dataverse managed data lake.
1. On the toolbar, select **Schedule purge**.
1. The **Schedule purge** dialog opens. Select the date and time at which to start copying data from the `SalesTableHistory` and `SalesLineHistory` tables to Dataverse managed data lake.
1. Select **OK** to schedule the purge and close the dialog.
1. You can view information about previous purges and/or modify a purge in progress by selecting a listed archive and the selecting one of the following buttons on the toolbar:
    - **Cancel scheduled purge** – Cancel a purge that has been scheduled but not yet started. <!-- KFM: Please confirm this guess. -->
    - **View purge history** – View information about previous purges and/or view the progress of a purge that is currently in progress. <!-- KFM: Please confirm this guess. -->
    - **Refresh purge state fo...** – <!-- KFM: Description needed. -->
    - <!-- KFM: Others? -->

<!--KFM: Maybe add a section about how to search/review the records in the data lake. Can we do this within SCM somehow? -->