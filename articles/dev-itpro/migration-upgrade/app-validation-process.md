---
# required metadata

title: Dynamics AX 2012 upgrade - Tasks to complete after upgrade
description: This topic describes the tasks that you might have to perform in Microsoft Dynamics 365 for Operation after you complete a code and data upgrade from Microsoft Dynamics AX 2012.
author: tariqbell
manager: AnnBe
ms.date: 01/31/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 106163
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: tabell
ms.search.validFrom: 2017-06-16
ms.dyn365.ops.version: Platform update 8

---

# Dynamics AX 2012 upgrade - Tasks to complete after upgrade

[!include[banner](../includes/banner.md)]

[!include[upgrade banner](../includes/upgrade-banner.md)]

This topic describes the tasks that you might have to perform in Microsoft Dynamics 365 for Operation after you complete a code and data upgrade from Microsoft Dynamics AX 2012. A process data package (PDP) that is available in Microsoft Dynamics Lifecycle Services (LCS) includes links to the following menu items. This PDP will fill in the **Data validation checklist** workspace. The **Data validation checklist** workspace lets users track a project and monitor the tasks that are required in order to complete it.

## Document management

If you use Document management, existing documents or attachments that are stored in the database must be migrated to Microsoft Azure Blob storage. To complete this migration, use the **Migrate files** button on the **Migrate files** tab on the **Document management parameters** page.

## Print management

If you use Print management, the references to network printers from AX 2012 won’t be valid. You must set up and reference network printers on the **Document routing** page. For more information, see [Install the Document Routing Agent to enable network printer devices](../analytics/install-document-routing-agent.md).

## Retail

After you complete the upgrade from AX 2012, you must configure registers and devices.

To configure a register, click **Retail** > **Channels** > **Retail stores**. Select the row for the retail channel, and then expand the **Registers** FactBox. Click **More**, click **New**, and complete the setup of the register.

To configure a device, click **Retail** > **Channel setup** > **POS Setup**, and then click **New**.

Additionally, you must run all jobs (9999) for the channel database. Click **Retail** > **Headquarters setup** > **Retail scheduler** > **Channel database**. Select the row for the appropriate channel database, and then click **Full data sync**. Select the **9999** (**All jobs**) distribution schedule, and then click **OK**. Click **OK** again to run the job.

## Service industries

After you complete the upgrade from AX 2012, you must set up resource capacity roll-up and project ledger intercompany posting.

To run the Resource capacity roll-up batch job, click **Project management and accounting** > **Inquiries and reports** > **Capacity synchronization**. You must run this batch job to set up the resource and resource calendar reservation data. This data will be required if you use project resource scheduling. For more information, see [Project resourcing](../../financials/project-management/project-resourcing.md).

To enable project ledger intercompany posting, click **Project management and accounting** > **Setup** > **Posting** > **Ledger posting setup**. On the **Cost accounts** tab, in the **Ledger account types** field, select **Intercompany cost**, and then enter the details of the lending legal entity. On the **Revenue accounts** tab, in the **Ledger account types** field, select **Intercompany revenue**, and then enter details of the borrowing legal entity.

## Budget planning

After you complete the upgrade from AX 2012, you must set up Budget planning columns and layouts. To complete this setup, click **Budgeting** > **Setup** > **Budget planning** > **Budget planning configuration**.

Additionally, you must update Budget planning processes so that they use the appropriate layout for each budget stage. To update Budget planning processes, click **Budgeting** > **Setup** > **Budget planning** > **Budget planning process**.

For more information about Budget planning upgrade, see [Upgrading to Budget planning from Microsoft Dynamics AX 2012](upgrade-budget-planning.md).
