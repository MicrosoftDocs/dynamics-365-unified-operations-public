---
title: Archive general ledger data
description: This article describes how to archive general ledger data. In this way, you help improve database performance but also keep the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: rcarlson
ms.author: rcarlson
ms.reviewer: kamaybac
ms.search.form: ArchiveWorkspace, ProcessScheduleSeriesWizard, LedgerArchiveAutomationCriteriaForm, TimelineDialog, ArchiveMessageLogDialog, ArchiveReversalDialog, LedgerTransHistoryVoucher
ms.topic: how-to
ms.date: 06/13/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive general ledger data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->

General ledger data is typically one of the highest-volume sets of data in your finance and operations environment. You must be able to manage this data but also remain compliant with your data storage retention policies. This data is required for auditing, historical reporting, and analysis. However, historical data that's kept in your day-to-day working environment not only increases storage costs but also affects system performance and usability.

To address these issues, you can use the archive solution to manage the archiving of historical years of general ledger data. During the archive process, the system moves records from general ledger voucher header and lines (the `GeneralJournalEntry` and `GeneralJournalAccountEntry` tables, and related child tables).

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running version 10.0.34 or later of finance and operations apps.
- The data archive micro-service must be installed on your system from Microsoft Dynamics Lifecycle Services. For more information, see [Install the Archive add-in from Lifecycle Services](archive-setup.md#install-addin).
- The following features must be turned on in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Enable the features that you need](archive-setup.md#enable-features).

    - *(Preview) Archive*
    - *(Preview) Ledger archive automation*

## <a name="archival-requirements"></a>Which general ledger data can be archived and when

General ledger data can be moved to history if all the following conditions are met:

- The year-end close process has been completed for the year.
- All periods are either *on hold* or *permanently closed*.
- The previous year has already been moved to history or long-term retention.

After these conditions are met, the status of the fiscal year is changed to *Ready*, and the fiscal year is available for archiving.

## Schedule archiving of general ledger data

To schedule archiving of general ledger data, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, on the Action Pane, select **Archive**.
1. In the drop-down dialog box that appears, set the **Name** field to *LedgerArchiveAutomation*, and then select **Archive** to apply your setting and close the drop-down dialog box.
1. On the **Create new process automation** page, on the **General** tab, you must set the **Name** field to define the name of the archive and the **Schedule time** field to define when the archive job should start to run. You can also specify how often the archive job should run. If you decide to set up multiple occurrences, you can set the **End time** field to limit the amount of time that an archive job runs during a day. Any archive job doesn't finish running within that time limit is paused and picked up during the next occurrence. You can also set up alerts as required.
1. Select **Next** to continue.
1. The **Ledger archive automation selection** tab shows a list of record collections that meet the [archival requirements](#archival-requirements). The collections are grouped by company and fiscal year. Select the record collection that you want to archive, and then select **Finish**.

   You're returned to the **Archive** workspace, which now shows the archive job that you just created. The **Archive status** field of this job is set to *Scheduled*. The job will run at the scheduled time.

## Review the progress and log of an archive job

To review the progress and log of an archive job, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, on the **General ledger archive** tab, set the **Fiscal calendar** field to the fiscal calendar that you want to inspect.
1. In the grid, select the archive job that you want to inspect.
1. On the toolbar, select **View results**.
1. The **General ledger archive progress** dialog box that appears shows the archive progress of each table that's being archived. To view more details, select **View detailed logs**.
1. Select **Close** to return to the **Archive** workspace.

## Review historical general ledger data

To review the historical general ledger data, go to **General ledger \> Inquiries and reports \> Voucher transactions history**.

## Reverse an archive

When you reverse an archive, the system moves records of that archive from the history tables back to the live tables. This operation is useful if you must edit an archived transaction, because you can't edit records in the history tables. To reverse an archive, follow these steps.

1. Go to **System administration \> Workspaces \> Archive**.
1. In the **Archive** workspace, on the **General ledger archive** tab, the grid lists your existing archives. Select the archive that you want to reverse, and then select **Reverse** on the toolbar.
1. In the **Reverse** dialog box, schedule the reversal job by setting the **Reversal start time** field and then selecting **OK**.
1. A message box prompts you to confirm the operation. Select **OK** to confirm it.
