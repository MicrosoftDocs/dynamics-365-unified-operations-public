---
# required metadata

title: Database Movement Operations - Import Database Quickstart
description: This topic explains how to perform an import of a database for Microsoft Dynamics 365 for Finance and Operations.
author: LaneSwenka
manager: AnnBe
ms.date: 1/22/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro, Developer
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2019-01-22
ms.dyn365.ops.version: AX 7.0.0

---

# Import database quickstart

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to perform the import of a database for Microsoft Dynamics 365 for Finance and Operations to a sandbox user acceptance testing (UAT) environment. 

## Self-service import database
[!include [dbmovement-import](../includes/dbmovement-import.md)]

### Import operation failed
In case of failure, the option to perform a **Rollback** is available.  By clicking the rollback option after the operation has initially failed, your target sandbox environment will be restored to the state it was before the import began. This is made possible by the Azure SQL Point-in-time restore capability to restore the database. This is often required if a customization is present in the target sandbox that cannot complete a database synchronization with the newly imported data.  

To determine the root cause of the failure, download the runbook logs using the available buttons before starting the rollback operation.

### Data elements that need attention after import
When importing a database backup in to a sandbox UAT environment, there are certain activities which must be performed.  These include:
* Ensure email capabilities are properly reconfigured or disabled, per your requirements.
* Integration settings are enabled or disabled, per your requirements.
* AOS servers are added back to required batch groups.
* System Help and Task guides are reconnected.
* Batch jobs are set to Waiting status.
* Users are re-enabled.

### Environment administrator
The System Administrator account in the target environment (UserId of 'Admin') is reset to the value found in the web.config on the target.  This should be the same value as that of the Administrator from Lifecycle Services.  To preview which account this will be, visit your target sandbox **Environment Details** page in LCS.  The value of the **Environment Administrator** field that was selected when the environment was first deployed is updated to be the System Administrator in the transactional database. This also means that the tenant of the environment will be that of the Environment Administrator.  

If you have used the Admin User Provisioning Tool on your environment to change the web.config to a different value, it may not match what is in Lifecycle Services.  If you require a different account to be used, you will need to deallocate and delete the target sandbox, and redeploy selecting another account. After this, you can perform another refresh database action to restore the data.

## Steps to complete after a database import for environments that use Retail functionality
[!include [environment-reprovision](../includes/environment-reprovision.md)]

## Known issues

### Import is denied for environments running Platform Update 3 or earlier
The import database process cannot be completed if the environment is running PU3 or earlier.  Please see the list of currently supported Platform Updates.
