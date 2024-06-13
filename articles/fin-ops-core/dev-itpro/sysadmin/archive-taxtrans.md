---
title: Archive Dynamics 365 Finance Tax transactions data
description: Learn about how to archive Dynamics 365 Finance Tax transactions data, including prerequisites and the process of setting up archival jobs.
author: epodkolz
ms.author: epodkolzina
ms.topic: conceptual
ms.date: 4/10/2024
ms.custom:
ms.reviewer: twheeloc
---
# Archive Dynamics 365 Finance Tax transactions data

This article explains how to archive Dynamics 365 Finance Tax transactions data.

When you archive Tax transactions, data from the following tables is moved to history tables:

- TaxTrans
- TaxTrans\_BR
- TaxTrans\_IN
- TaxTrans\_IT
- TaxTrans\_RU
- TaxTrans\_W
- TaxTransExtensionTH
- TaxTransGeneralJournalAccountEntry
- TaxTransSubledgerJournalAccountEntry
- TaxTrans\_Reporting

## Prerequisites

Confirm that your environment is configured to use the archive feature. For more information, see [Set up and manage archive data](archive-setup-manage.md).

In addition, the following prerequisites must be met before you archive Tax transactions:

- All periods in the fiscal year must be either permanently closed or in an on-hold state.
- Tax transactions for the previous fiscal year for the company must be archived.
- The archive jobs for different years must be run in chronological order. For example, 2020 Tax transactions data must be archived before 2021 Tax transactions data.

## Set up an archival job

To set up an archival job, follow these steps.

1. Go to **System administration** \> **Archive with Dataverse long term retention** to open the **Archive with Dataverse long term retention** workspace.
1. Select the **Tax transactions** functional scenario.

    ![Screenshot of the tab for the Tax transactions functional scenario in the Archive with Dataverse long term retention workspace.](./media/DV_Long_term_retention_Tax%20transactions_1.png)

1. Select **Refresh** to populate the fiscal years and company dataset to archive.

    > [!NOTE]
    > After a period and year-end close is completed on the Tax transactions data for the fiscal years and the companies, run a refresh. The **Ready to archive** state must be **Ready** before you can schedule a new long term retention job.

1. Select **New long term retention job** to open a wizard that you can use to schedule a new **Tax transactions long term retention** job.

    ![Screenshot of the Configure page of the New long term retention job - Tax transactions wizard.](./media/DV_Long_term_retention_Tax%20transactions_2.png)

1. Enter a name for the job, and then select **Next**.

    New long term retention jobs can be scheduled for one or more companies at a time. Execution of these jobs is sequential.

1. On the **Define criteria** page, select the combination of fiscal years and companies to archive Tax transactions data for.

    ![Screenshot of the Define criteria page of the New long term retention job - Tax transactions wizard.](./media/DV_Long_term_retention_Tax%20transactions_3.png)

1. Select **Next**.
1. Select the type of scheduling. Two types are supported:

    - **Single run** – The long term retention and saving to history are run continuously until both processes are completed. Data is always archived in Dataverse long term retention first. Then the save to history tables occurs.
    - **Daily during allotted time** – The long term retention runs continuously until it's completed. The **Save to history** process runs only during the specified start and stop archiving time.

1. Select **Finish** to schedule the archive job for the selected fiscal years and companies.
1. Select **View progress** to view the detailed logs.

## View historical data from the history table

To view the historical transactional details, follow this step.

- Go to **Tax** \> **Inquiries and reports** \> **Voucher transactions history**.
