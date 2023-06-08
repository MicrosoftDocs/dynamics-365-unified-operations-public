---
title: Archive general ledger data
description: This article describes how to archive general ledger data to help improve database performance while keeping the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: rcarlson
ms.author: rcarlson
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: how-to
ms.date: 06/01/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive general ledger data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->
<!--KFM: Add form codes to metadata -->

General ledger data is often one of the highest volume sets of data in your Dynamics 365 Finance and Operations environment. Your ability to manage this data while staying compliant with your data storage retention policies is paramount. This data is needed for auditing, historical reporting and analysis, but keeping historical data in your day-to-day working environment not only results in increased storage costs, but also impacts system performance and usability.

To solve these issues, you can use the archive workspace to manage archiving of historical years of general ledger data. During the archive process, the system moves records from General ledger voucher header and lines: ('GeneralJournalEntry') and ('GeneralJournalAccountEntry') and related child tables.

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Finance and Operations 10.0.34 or later.
- The data archive micro-service must be installed on your system from Lifecycle Services (LCS). See also [Set up record archiving](archive-setup.md).
- The following features must be turned on in [feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). See also [Set up record archiving](archive-setup.md).
    - *(Preview) Archive*
    - *(Preview) Ledger archive automation*

## <a name="archival-requirements"></a>Which general ledger data can be archived and when

General ledger data can be moved to history when the following conditions are met:

- The year end close process has been completed for the year.
- All periods are *on hold* or *permanently closed*.
- The prior year has already moved to history or long-term retention.

Once these conditions are met, the fiscal year will change to *Ready* status and will be available for archiving.

## Schedule archiving of general ledger data

To schedule a general ledger archive job, follow these steps:

1. Open the **Archive** workspace.
1. On the Action Pane, select **Archive** to open a drop-down dialog box. Then set **Name** to *LedgerArchiveAutomation* and select **Archive**.
1. The **Create new process automation** page opens, open to the **General** tab. Use the settings on this page to establish the archive **Name** (required), when the archive job should start running, how often it should run, and when it should stop running (if you set up multiple occurrences). If you choose to set up multiple occurrences, then you can also set a **Duration**, which sets a limit on the amount of time an archive job runs in a day; if an archive job does not finish running within this limit, the job will be paused and picked up at the next execution occurrence. <!--KFM: Confirm this about the **Duration** setting. --> You can also set up alerts as needed.
1. Select **Next** to continue to the **Ledger archive automation selection** tab. This page shows a list record collections that meet the [archival requirements](#archival-requirements) (grouped by company and fiscal year). Select the record collection you want to archive, and then select **Finish**.
1. You return to the **Active** workspace, which now shows the archive job you just created (with an **Archive status** of *Scheduled*). The job will run at the scheduled time.

<!--KFM: What is the "Fiscal calendar" drop-down list for? -->
<!-- RCC: The fiscal calendar is the base pivot of data - meaning you have to pick that, then you can see all the companies and the the years in use for that given fiscal calendar. --> 

## Review the progress and log of an archive job

To review the progress and log of an archive job, follow these steps:

1. Open the **Archive** workspace.
1. Open the **General ledger archive** tab.
1. In the grid, select the archive job you want to inspect.
1. On the toolbar, select **View results**.
1. The **General ledger archive progress** dialog box opens, showing the archive progress of each table that is being archived. To see more details, select the **View detailed logs** button.
1. Select **Close** to return to the **Archive** workspace.

## Review general ledger historical data

To view the historical general ledger data, go to **General ledger \> Inquiries and reports \> Voucher transactions history**.

<!-- KFM: This section isn't clear. Is that really the right navigation path to see this?  Are we reviewing a history of archive jobs, or looking at the archived records themselves? Is it possible to view the archived data, as with SO? Confirm with UI. RCC - view the history records themselves -->

## Reverse an archive

When you reverse an archive, the system moves records from the selected archive from the history tables back to the live tables. This operation is useful if you need to edit an archived transaction because you cannot edit records in the history tables. To reverse an archive, follow these steps:

1. Open the **Archive** workspace.
1. Open the **General ledger archive** tab.
1. Your existing archives are listed in the grid. Select the archive you want to reverse and then select **Reverse** on the toolbar.
1. The **Reverse** dialog opens. Schedule the reverse job by entering a **Reversal start time** and select **OK**.
1. A message appears asking you to confirm the operation. Select **OK** to confirm. <!-- KFM: Confirm this step - RCC correct -->
