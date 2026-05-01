---
title: Upgrade from AX 2012 - Post-upgrade tasks
description: Learn about the tasks that you might have to perform after you complete a code and data upgrade from Microsoft Dynamics AX 2012.
author: LaneSwenka
ms.author: laswenka
ms.topic: upgrade-and-migration-article
ms.date: 03/17/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-06-16
ms.search.form:
ms.dyn365.ops.version: Platform update 8
---

# Upgrade from AX 2012 - Post-upgrade tasks

[!include [banner](../includes/banner.md)]

[!include [upgrade banner](../includes/upgrade-banner.md)]

This article describes the tasks that you might need to perform in finance and operations apps, like Dynamics 365 Finance and Dynamics 365 Supply Chain Management, after you complete a code and data upgrade from Microsoft Dynamics AX 2012. A process data package (PDP) that's available in Microsoft Dynamics Lifecycle Services includes links to the following menu items. This PDP fills in the **Data validation checklist** workspace. The **Data validation checklist** workspace lets users track a project and monitor the tasks that are required to complete it.

## Document management

If you use document management, migrate existing documents or attachments that are stored in the database to Microsoft Azure Blob storage. To complete this migration, use the **Migrate files** button on the **Migrate files** tab on the **Document management parameters** page. This operation isn't critical as document management can still access files stored in the database, but the files can take up considerable database storage and retrieval is less efficient. The file migration process migrates all possible database files to Microsoft Azure Blob storage, reports on any failures, and continues. If any errors are reported, try running the file migration process again.

If the file migration process can't complete without failure, the files stored in the database might be corrupt. Microsoft can't repair corrupt files. If this condition occurs, you can request to open a non-business critical support case to enable conversion of the attachments into note records. This conversion retains any previous notes as well as the names of the files that were stored in the database. The files themselves can't be recovered.

## Print management

If you use Print management, the references to network printers from AX 2012 aren't valid. You must set up and reference network printers on the **Document routing** page. For more information, see [Install the Document Routing Agent to enable network printing](../analytics/install-document-routing-agent.md).

## Commerce

After you complete the upgrade from AX 2012, you must configure registers and devices.

To configure a register, select **Retail and Commerce** > **Channels** > **Stores**. Select the row for the channel, and then expand the **Registers** FactBox. Select **More**, select **New**, and complete the setup of the register.

To configure a device, select **Retail and Commerce** > **Channel setup** > **POS Setup**, and then select **New**.

Additionally, you must run all jobs (9999) for the channel database. Select **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Channel database**. Select the row for the appropriate channel database, and then select **Full data sync**. Select the **9999** (**All jobs**) distribution schedule, and then select **OK**. Select **OK** again to run the job.

## Service industries

After you upgrade from AX 2012, set up resource capacity roll-up and project ledger intercompany posting.

To run the Resource capacity roll-up batch job, select **Project management and accounting** > **Inquiries and reports** > **Capacity synchronization**. Run this batch job to set up the resource and resource calendar reservation data. You need this data if you use project resource scheduling. For more information, see [Project resourcing](/dynamics365/project-operations/prod-pma/project-resourcing).

To enable project ledger intercompany posting, select **Project management and accounting** > **Setup** > **Posting** > **Ledger posting setup**. On the **Cost accounts** tab, in the **Ledger account types** field, select **Intercompany cost**, and then enter the details of the lending legal entity. On the **Revenue accounts** tab, in the **Ledger account types** field, select **Intercompany revenue**, and then enter details of the borrowing legal entity.

## Budget planning

After you upgrade from AX 2012, set up Budget planning columns and layouts. To complete this setup, select **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**.

Also, update Budget planning processes so that they use the appropriate layout for each budget stage. To update Budget planning processes, select **Budgeting** > **Setup** > **Budget planning** > **Budget planning process**.

For more information about Budget planning upgrade, see [Upgrade budget planning](../../fin-ops/migration/upgrade-budget-planning.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
