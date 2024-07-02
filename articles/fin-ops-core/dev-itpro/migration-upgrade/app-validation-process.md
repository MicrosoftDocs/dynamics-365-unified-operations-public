---
title: Upgrade from AX 2012 - Post-upgrade tasks
description: Learn about the tasks that you might have to perform after you complete a code and data upgrade from Microsoft Dynamics AX 2012.
author: LaneSwenka
ms.author: laswenka
ms.topic: article
ms.date: 11/12/2019
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

This article describes the tasks that you might have to perform in finance and operations apps, like Dynamics 365 Finance and Dynamics 365 Supply Chain Management, after you complete a code and data upgrade from Microsoft Dynamics AX 2012. A process data package (PDP) that is available in Microsoft Dynamics Lifecycle Services (LCS) includes links to the following menu items. This PDP will fill in the **Data validation checklist** workspace. The **Data validation checklist** workspace lets users track a project and monitor the tasks that are required in order to complete it.

## Document management

If you use document management, existing documents or attachments that are stored in the database should be migrated to Microsoft Azure Blob storage. To complete this migration, use the **Migrate files** button on the **Migrate files** tab on the **Document management parameters** page. This operation is not critical as document management can still access file stored in the database, but the files can take considerable database storage and the retrieval is less efficient. The file migration process will migrate all possible database files to Microsoft Azure Blob storage, reporting on any failures and continuing. If any errors are reported, attempt running the file migration process again.

If the file migration process isn’t able to complete without failure, this may be that the files stored in the database are corrupt, which Microsoft is unable to repair. If this is the case, you can request a non-business critical support case be opened to enable conversion of the attachments into note records, which will retain any previous notes as well as the names of the files that were stored in the database. Note that the files themselves cannot be recovered.

## Print management

If you use Print management, the references to network printers from AX 2012 won’t be valid. You must set up and reference network printers on the **Document routing** page. For more information, see [Install the Document Routing Agent to enable network printing](../analytics/install-document-routing-agent.md).

## Commerce

After you complete the upgrade from AX 2012, you must configure registers and devices.

To configure a register, click **Retail and Commerce** > **Channels** > **Stores**. Select the row for the channel, and then expand the **Registers** FactBox. Click **More**, click **New**, and complete the setup of the register.

To configure a device, click **Retail and Commerce** > **Channel setup** > **POS Setup**, and then click **New**.

Additionally, you must run all jobs (9999) for the channel database. Click **Retail and Commerce** > **Headquarters setup** > **Commerce scheduler** > **Channel database**. Select the row for the appropriate channel database, and then click **Full data sync**. Select the **9999** (**All jobs**) distribution schedule, and then click **OK**. Click **OK** again to run the job.

## Service industries

After you complete the upgrade from AX 2012, you must set up resource capacity roll-up and project ledger intercompany posting.

To run the Resource capacity roll-up batch job, click **Project management and accounting** > **Inquiries and reports** > **Capacity synchronization**. You must run this batch job to set up the resource and resource calendar reservation data. This data will be required if you use project resource scheduling. For more information, see [Project resourcing](/dynamics365/project-operations/prod-pma/project-resourcing).

To enable project ledger intercompany posting, click **Project management and accounting** > **Setup** > **Posting** > **Ledger posting setup**. On the **Cost accounts** tab, in the **Ledger account types** field, select **Intercompany cost**, and then enter the details of the lending legal entity. On the **Revenue accounts** tab, in the **Ledger account types** field, select **Intercompany revenue**, and then enter details of the borrowing legal entity.

## Budget planning

After you complete the upgrade from AX 2012, you must set up Budget planning columns and layouts. To complete this setup, click **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**.

Additionally, you must update Budget planning processes so that they use the appropriate layout for each budget stage. To update Budget planning processes, click **Budgeting** > **Setup** > **Budget planning** > **Budget planning process**.

For more information about Budget planning upgrade, see [Upgrade budget planning](../../fin-ops/migration/upgrade-budget-planning.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
