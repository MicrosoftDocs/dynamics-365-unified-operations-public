---
title: Import a database
description: Learn how to import a database for finance and operations apps, including prerequisites, and overviews of long-running operations.
author: LaneSwenka
ms.author: laswenka
ms.date: 04/03/2026
ms.topic: article
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form: 
ms.dyn365.ops.version: 8.1.3
---

# Import a database

[!include [banner](../includes/banner.md)]

Use Microsoft Dynamics Lifecycle Services to import a golden configuration database into a sandbox user acceptance testing (UAT) environment.

## Prerequisites

Database import isn't applicable to Lifecycle Services projects that are configured for a Dynamics AX 2012 upgrade. Therefore, import is blocked if the **Legacy system** field at **Project Onboarding** > **Project overview** is set to **AX2012 Upgrade**.

## Self-service import database

[!include [dbmovement-import](../includes/dbmovement-import.md)]

### Long running operations

The import operation can take several hours and, in extreme cases, days to complete. This duration is due to the schema complexity of finance and operations apps, and limitations of Azure SQL provided tools to convert a cloud database to a flat file for use by traditional SQL Server. When the import operation takes too long and you want to stop the process, select **Cancel** from the environment details page.

### Import operation failure

If the import operation isn't successful, it automatically *rolls back*. The process restores your target sandbox environment to the state it was in before the import began. The Microsoft Azure SQL Database point-in-time restore capability provides the rollback operation for restoring the database. Rollback is required if a customization that is present in the target sandbox can't complete a database synchronization with the newly imported data.

To cancel an ongoing import operation, use the **Cancel** button.

To determine the root cause of the failure, use the **Environment change history** page to download the logs for the failed operation.

### Data elements that require attention after import

Specific activities must be completed when you import a database backup into a sandbox UAT environment. Here are some examples:

- Make sure that the source database contains only a single record in the Partitions table.
- Make sure that email capabilities are correctly reconfigured or turned off, according to your requirements.
- Make sure that integration settings are turned on or off, according to your requirements.
- Make sure that Application Object Server (AOS) servers are added back to required batch groups.
- Make sure that system Help and task guides are reconnected.
- Make sure that batch jobs are set to a status of **Waiting**.
- Make sure that users are re-enabled.
- Make sure that dual-write is relinked if necessary.
- Make sure that dual-write is relinked if necessary.  To set up a new link on the target environment after this operation is successful, see [Enable Power Platform Integration](../../dev-itpro/power-platform/enable-power-platform-integration.md).

### Environment admin

The system admin account in the target environment (**Admin** user ID) is reset to the value that is found in the web.config file in that environment. This account should be the same as the admin account from Lifecycle Services. To preview which account this account is, visit the **Environment details** page for your target sandbox in Lifecycle Services. The value that was selected in the **Environment Administrator** field when the environment was first deployed is updated to the system admin in the transactional database. Therefore, the tenant of the environment is the tenant of the environment admin.

If you've used the Admin User Provisioning Tool on your environment to change the web.config file, the value might not match the value in Lifecycle Services. If you require that a different account is used, you must deallocate and delete the target sandbox, redeploy, and select another account. You can then do another database refresh action to restore the data.

## Steps to complete after a database import for environments that use Commerce functionality

[!include [environment-reprovision](../includes/environment-reprovision.md)]

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
