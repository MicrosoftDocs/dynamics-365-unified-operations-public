---
# required metadata

title: Request sandbox database refreshes
description: This topic explains how to request a refresh of the database for Microsoft Dynamics 365 for Finance and Operations, in a sandbox user acceptance testing (UAT) environment.
author: LaneSwenka
manager: AnnBe
ms.date: 10/16/2018
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
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry: 
ms.author: laneswenka
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Request sandbox database refreshes

[!include [banner](../includes/banner.md)]

You can use Microsoft Dynamics Lifecycle Services (LCS) to request a refresh of the database for Microsoft Dynamics 365 for Finance and Operations, in a sandbox user acceptance testing (UAT) environment. A database refresh lets you copy the database of your production environment (and the Financial Reporting database) into the target sandbox UAT environment. If you have another UAT environment, you can also copy the databases from that environment.

This functionality lets you use production data to test upcoming code changes in a UAT environment. You can also copy a production database into a UAT environment for debugging purposes.

## Database refresh process

> [!NOTE]
> As of October 8, 2018, Database Refresh requests must be signed off before another refresh of the same environment can be requested.  This is to support future automation of database movement operations.

The Microsoft Service Engineering team will take your environment offline, complete the refresh, and then bring the environment back online. You can expect the downtime period to be approximately two hours. The period after you enter your request and before our Service Engineers take action will be longer than your environment's downtime. In the future, we will provide a self-service method that you can use to perform your database refreshes.

1. In LCS, select the hamburger icon in the upper left, and then select **Work items**.
2. On the **Work items** page, select **Add** on the toolbar, and then select **Database refresh**.
3. In the **Request for database refresh** dialog box, follow these steps:

    1. In the **Environment name** field, select the environment to refresh.
    2. In the **Database** field, the database to refresh is always the Microsoft Dynamics AX database or the Finance and Operations database. Other databases, such as Entity store aren't currently supported for database refresh.
    3. Carefully read and acknowledge the statements that have check boxes next to them.

4. After you submit your request, you are returned to the list of work items. Here, you can view the status of the request, or reschedule or cancel the request.
5. When the Service Engineering team has acknowledged that it can complete your request, the status of the request is changed to **Request accepted**. At this point, you can follow any of these steps:

    - Wait for the Service Engineering team to complete the refresh. When the restore is completed, the status is changed to **Succeeded**.
    - Reschedule the request by selecting the ID, or by selecting the request and then selecting **Reschedule** on the toolbar. You can then change the dates and times for the downtime window.
    - Cancel the request by selecting the request and then selecting **Cancel** on the toolbar.

## Conditions of a database refresh
Here is the list of requirements and conditions of operation for a database refresh:

- All previous Database Refresh requests for the environment are marked either *Succeeded*, *Failed*, or *Cancelled*.
- Requests must be submitted 24 hours before the desired downtime window, to help guarantee that resources will be available to complete the request.
- A refresh erases the existing database in the target environment. The existing database can't be recovered after the refresh is completed.
- The target environment will be unavailable until the refresh process is completed.
- The refresh will affect only the Finance and Operations and Financial Reporting databases.
- Documents in Azure blob storage are not copied from one environment to another. This means that attached document handling documents and teamplates won't be changed and will remain in their current state.
- All users except the Admin user and other internal service user accounts will be disabled. This process allows the Admin user to delete or obfuscate data before allowing others users back into the system.
- The Admin user must make required configuration changes, such as reconnecting integration endpoints to specific services or URLs.
- All data management framework recurring import and export jobs must be fully processed and stopped in the target system prior to initiating the restore. In addition, we recommend that you select the database from the source after all recurring import and export jobs have been fully processed. This will ensure there are no orphaned files in Azure storage from either system. This is important because orphaned files cannot be processed after the database is restored in the target environment. After the restore, the integration jobs can be resumed.
- All batches that were set to run are set to **Withhold** status, to stop batches from running before the environment has been reconfigured.
- The SMTP server configuration, all email addresses, and all **Print management** settings, including network printers are removed.
- Any user with a role of Project owner or Environment manager in LCS will have acccess to the SQL and machine credentials for all non-production environments.

## Steps to complete after a database refresh for environments that use Retail functionality
[!include [environment-reprovision](../includes/environment-reprovision.md)]
