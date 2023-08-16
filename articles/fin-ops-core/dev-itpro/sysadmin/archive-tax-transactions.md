---
title: Archive tax transactions data
description: This article describes how to archive tax transactions data. In this way, you help improve database performance but also keep the records available for historical reporting, auditing, machine learning, legal claims, and other purposes.
author: epodkolzina
ms.author: epodkolzina
ms.reviewer:
ms.search.form: ArchiveWorkspace, ProcessScheduleSeriesWizard, TimelineDialog, ArchiveMessageLogDialog, ArchiveReversalDialog, TaxTransHistory
ms.topic:
ms.date: 08/16/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Archive tax transactions data

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- Preview until further notice -->

With time, tax transaction data expands, it occupies more database space, gradually slowing down queries. This article explains utilizing the tax transactions archive to enhance system performance.
When you archive tax transactions, data from the following tables will be moved to history tables:
 - `TaxTrans`
 - `TaxTrans_BR`
 - `TaxTrans_IN`
 - `TaxTrans_IT`
 - `TaxTrans_RU`
 - `TaxTrans_W`
 - `TaxTransExtensionTH`
 - `TaxTransGeneralJournalAccountEntry`
 - `TaxTransSubledgerJournalAccountEntry`
 - `TaxTrans_Reporting`

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running version 10.0.35 or later of finance and operations apps.
- The data archive micro-service must be installed on your system from Microsoft Dynamics Lifecycle Services. For more information, see [Install the Archive add-in from Lifecycle Services](archive-setup.md#install-addin).
- The following features must be turned on in [Feature management](../../fin-ops/get-started/feature-management/feature-management-overview.md). For more information, see [Enable the features that you need](archive-setup.md#enable-features).

    - *(Preview) Archive*
    - *(Preview) Tax archive automation*

## Schedule archiving of tax transactions

To schedule archiving of tax transactions, follow these steps.

1.	Go to **System administration > Workspaces > Archive**.
2.	In the **Archive** workspace, on the Action Pane, select **Archive**.
3.	In the drop-down dialog box that appears, set the **Name** field to _TaxArchiveAutomation_, and then select **Archive** to apply your setting and close the drop-down dialog box.
4.	On the **Create new process automation** page, on the **General** tab, you must set the **Name** field to define the name of the archive and the **Schedule time** field to define when the archive job should start to run. You can also specify how often the archive job should run. If you decide to set up multiple occurrences, you can set the **End time** field to limit the amount of time that an archive job runs during a day. Any archive job that doesn't finish running within that time limit is paused and picked up during the next occurrence. You can also set up alerts as required.
5.	Select **Next** to continue.
6.	On the **Tax archive automation parameters** you can see a list of record collections that are ready for archiving. 

> [!NOTE]
> Tax archive automation utilizes the same conditions of data readiness for archiving as described in [Archive general ledger data](archive-general-ledger.md#archival-requirements). 

7.	Select the record collection that you want to archive, and then select **Finish**.
   
You're returned to the **Archive** workspace, which now shows the archive job that you just created. The **Archive status** field of this job is set to _Scheduled_. The job will run at the scheduled time

## Review the progress and log of an archive job

To review the progress and log of an archive job, follow these steps.

1.	Go to **System administration > Workspaces > Archive**.
2.	In the **Archive** workspace, on the **Tax transactions archive** tab, set the **Fiscal calendar** field to the fiscal calendar that you want to inspect.
3.	In the grid, select the archive job that you want to inspect.
4.	On the toolbar, select **View results**.

## Review historical tax transactions data

To review the historical tax transactions data, go to **Tax > Inquiries and reports > Sales tax inquiries > Posted sales tax history**.

## Reverse tax transactions archive

When you reverse an archive, the system moves records of that archive from the history tables back to the live tables. This operation is useful if you must edit an archived transaction, because you can't edit records in the history tables. To reverse an archive, follow these steps.

1.	Go to **System administration > Workspaces > Archive**.
2.	In the **Archive** workspace, on the **Tax transactions archive** tab, the grid lists your existing archives. Select the archive that you want to reverse, and then select **Reverse** on the toolbar.
3.	In the **Reverse** dialog box, schedule the reversal job by setting the **Reversal start time** field and then selecting **OK**.
4.	A message box prompts you to confirm the operation. Select **OK** to confirm it.


