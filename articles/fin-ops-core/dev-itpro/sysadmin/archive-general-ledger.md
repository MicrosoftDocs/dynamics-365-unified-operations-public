---
title: Archive general ledger
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

# Archive general ledger

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.34 GA -->
<!--KFM: Add form codes to metadata -->

General ledger data is often one of the highest volume sets of data in your Dynamics 365 Finance and Operations environment. Your ability to manage this data while staying compliant with your data storage retention policies is paramount. This data is needed for auditing, historical reporting and analysis, but keeping historical data in your day-to-day working environment not only results in increased storage costs, but also impacts system performance and usablity. 

To solve these issues, you can use the archive workspace to manage archiving of historical years of general ledger data. During the archive process, the system moves records from General ledger voucher header and lines: ('GeneralJournalEntry') and ('GeneralJournalAccountEntry') and related child tables. 

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Finance and Operations 10.0.34 or later.
- The data archive micro-service must be installed on your system from Lifecycle Services (LCS). See also [Set up record archiving](archive-setup.md).
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). See also [Set up record archiving](archive-setup.md).
    - *(Preview) Archive*
    - *(Preview) Ledger archive automation*

## General ledger move to history

General ledger data can be moved to history when the following conditions are met:

- The year end close process has been completed for the year. 
- All periods are **on hold** or **permanently closed**. 
- The prior year has already moved to history or long-term retention.

## Schedule archive of general ledger

To schedule a general ledger archive job, follow these steps:

1. Open the **Archive** workspace.
1. On the Action Pane, select **Archive** to open a drop-down dialog box, and then select **LedgerArchiveAutomation**. 
1. The **Create new process automation** page opens, open to the **General** tab. Use the settings on this page to establish the name and when the archive job should start running, how often it should run, and when it should stop running (if you set up multiple occurrences). You can also set up alerts as needed.
1. Select **Next** to continue to the **Ledger archive automation selection**

    > [!NOTE]
    > Only fiscal years that are in the **Ready** state are shown in this list. 

1. Select **Finish**.

## Review general ledger historical data
To view the historical general ledger data use the provided form found in the menu at:
*General ledger - inquiries and reports - Voucher transactions history.*

## Dataverse Long term retention
Future releases will enable the movement of data from Finance and Operations history tables to Dataverse long term rentention.  This moves data from the existing database to a Microsoft managed data lake storage location, completely removing this data from your Finance and Operations database. 
