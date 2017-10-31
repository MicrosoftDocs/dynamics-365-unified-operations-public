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
The Microsoft Service Engineering team will take your environment offline, complete the refresh, and then bring the environment back online. You can expect the downtime period to be less than two hours. The period after you enter your request and before our Service Engineers take action will be longer than your environment downtime. In the future, we will provide a self-service method that you can use to perform your own point-in-time restores.

1.  Click the hamburger icon in the upper left of the Microsoft Dynamics Lifecycle Services (LCS) window, and then select **Work items** in the list. [![Work items](./media/selectworkitems.png)](./media/selectworkitems.png)
2.  On the **Work items** page, click **Add** on the toolbar, and then click **Database point-in-time restore request**. [![Database point-in-time restore request](./media/createrequest.png)](./media/createrequest.png)
3.  In the **Request for database point-in-time restore** dialog box, follow these steps:
    1.  In the **Environment name** field, select the environment to restore. **Note:** Only Azure SQL Database environments can be restored. Therefore, you can't select one-box environments that are based on Microsoft SQL Server.
    2.  In the **Database** field, the database to restore is always Microsoft Dynamics AX or Microsoft Dynamics 365 for Finance and Operations. Other databases, such as Entity store or Financial reporting, aren't currently supported for point-in-time restores.
    3.  Enter information in the **Restore point time** fields. Azure SQL Database lets you restore a database to a point in time that is up to 35 days before the date when you make the request. If the environment is less than 35 days old, or if it has previously been restored, the maximum amount of time will be less.
    4.  Enter information in the **Preferred downtime start date** and the **Preferred downtime end date** fields. The end date must be at least one hour after the start date. Requests must be submitted least 24 hours before the preferred downtime window, to help guarantee that resources are available to complete the request.
    5.  Carefully read and acknowledge the three statements that have check boxes next to them.

    [![Request for database point-in-time restore dialog box](./media/requestform.png)](./media/requestform.png)
4.  After you submit your request, you will be redirected to the list of work items. Here, you can view the status of the request, or reschedule or cancel the request.
5.  When the Microsoft Service Engineering team has acknowledged that it can complete your request, the status of the request changes to **Request accepted**. At this point, you can follow any of these steps:
    -   Wait for the Service Engineering team to complete the restore. When restore is completed, the status changes to **Succeeded**.
    -   Reschedule the request by clicking the ID, or by selecting the request and then clicking **Reschedule** on the toolbar. You can then change the downtime windows dates and times, and the point in time to restore to.
    -   Cancel the request by selecting the request and then clicking **Cancel** on the toolbar.

## Conditions of a point-in-time restore
Here is the list of requirements and conditions of operation for a point-in-time restore:

-   Requests must be submitted 24 hours before the desired downtime window, to help guarantee that resources will be available to complete the request.
-   A point-in-time restore erases the existing database in the target environment. The existing database can't be recovered after the restore is completed.
-   The target environment will be unavailable until the refresh process is completed.
-   The point-in-time restore will affect only the Dynamics 365 for Finance and Operations database.
    -   Document handling documents that are stored in Azure blob storage won't be changed and will remain in their current state. The same rule applies to any documents that are stored in Azure blob storage through X++ customization.
    -   The Financial reporting database will also remain in the current state and must be reset after the restore is completed.
-   The Dynamics 365 for Finance and Operations database will be left at the precise state that it was in at the requested point in time. We do **not** withhold batches or restrict access to the restored database.
-   LCS users who have a role of **Project Owner** or **Environment Manager** in LCS will have access to the Azure SQL Database and machine credentials for all non-production environments. To help guarantee security of the data that is copied to non-production environments, restrict membership in these roles.
