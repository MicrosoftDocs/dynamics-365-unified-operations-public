---
# required metadata

title: Request a database refresh
description:
author: Robadawy
manager: AnnBe
ms.date: 10/31/2017
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
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 257614
ms.assetid: 558598db-937e-4bfe-80c7-a861be021db1
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Restore a database on a non-production environment

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 for Finance and Operations lets you request that a database be refreshed. This topic describes how to request a database refresh.

## Database refresh process
The Microsoft Service Engineering team will take your environment offline, complete the refresh, and then bring the environment back online. You can expect the downtime period to be less than two hours. The period after you enter your request and before our Service Engineers take action will be longer than your environment downtime. In the future, we will provide a self-service method that you can use to perform your database refreshes.

1.  Click the hamburger icon in the upper left of the Microsoft Dynamics Lifecycle Services (LCS) window, and then select **Work items** in the list. 
2.  On the **Work items** page, click **Add** on the toolbar, and then click **Database refresh**. 
3.  In the **Request for database refresh** dialog box, follow these steps:
    1.  In the **Environment name** field, select the environment to refresh. 
    2.  In the **Database** field, the database to refresh is always Microsoft Dynamics AX or Microsoft Dynamics 365 for Finance and Operations. Other databases, such as Entity store or Financial reporting, aren't currently supported for point-in-time restores.
    3.  Carefully read and acknowledge the statements that have check boxes next to them.
4.  After you submit your request, you will be redirected to the list of work items. Here, you can view the status of the request, or reschedule or cancel the request.
5.  When the Microsoft Service Engineering team has acknowledged that it can complete your request, the status of the request changes to **Request accepted**. At this point, you can follow any of these steps:
    -   Wait for the Service Engineering team to complete the refresh. When restore is completed, the status changes to **Succeeded**.
    -   Reschedule the request by clicking the ID, or by selecting the request and then clicking **Reschedule** on the toolbar. You can then change the downtime windows dates and times, and the point in time to restore to.
    -   Cancel the request by selecting the request and then clicking **Cancel** on the toolbar.

## Conditions of a database refresh
Here is the list of requirements and conditions of operation for a point-in-time restore:

-   Requests must be submitted 24 hours before the desired downtime window, to help guarantee that resources will be available to complete the request.
-   A refresh erases the existing database in the target environment. The existing database can't be recovered after the refresh is completed.
-   The target environment will be unavailable until the refresh process is completed.
-   The point-in-time restore will affect only the Dynamics 365 for Finance and Operations database.
    -   Document handling documents that are stored in Azure blob storage won't be changed and will remain in their current state. The same rule applies to any documents that are stored in Azure blob storage through X++ customization.
    -   The Financial reporting database will also remain in the current state and must be reset after the refresh is completed.

## Steps to complete after a database refresh for environments using retail functionality
When refreshing a database, you will need to run the environment re-provisioning tool before the copied database is fully functional, to ensure that all Retail components are up-to-date.

> [!IMPORTANT]
> We recommend that you run this procedure whether you are using Retail components or not, because Retail functionality is included in all environments. 

Before you continue, you must make sure that the following prerequisites are met:

1. If your target enviornment is running the July 2017 release or later, apply KB 4035399. 
2. If your target environment is running the November release (version 1611), apply the following hotfixes:
  -   KB 4025631
  -   KB 4035355
  -   KB 4035492
  -   KB 4010947
3. The default channel database and the default channel data group must be named **Default**. If you've renamed them, you must change the names back.

Follow these steps to run the Environment reprovisioning tool.

1. In the Shared asset library, select **Software deployable package**.
2. Download the Environment reprovisioning tool.
3. In the asset library for your project, select **Software deployable package**.
4. Select **New** to create a new package.
5. Enter a name and description for the package. You can use **Environment reprovisioning tool** as the package name.
6. Upload the package that you downloaded earlier.
7. On the **Environment details** page for your target environment, select **Maintain** > **Apply updates**.
8. Select the Environment reprovisioning tool that you uploaded earlier, and then select **Apply** to apply the package.
9. Monitor the progress of the package deployment. 

For more information about how to apply a deployable package, see [Apply a deployable package](../deployment/create-apply-deployable-package.md). For more information about how to manually apply a deployable package, see [Install a deployable package](../deployment/install-deployable-package.md).
