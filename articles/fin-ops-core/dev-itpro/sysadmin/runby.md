---
# required metadata

title: Batch manager security role
description: This article provides information about the batch manager security role that is used to manage batch job.
author: hasaid
ms.date: 10/25/2018
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.search.region: Global
# ms.search.industry: 
ms.author: hasaid
ms.search.validFrom: 2018-08-15
ms.dyn365.ops.version: Platform update 20

---

# Batch manager security role

[!include [banner](../includes/banner.md)]

Before Platform update 20, users needed to be assigned to the system admin or IT admin security role to manage batch jobs. With the release of Platform update 20, there is a more targeted role, Batch manager. With this security role, a user now has permissions to copy batch jobs, change who will execute jobs, and specify the time ranges during which jobs can execute. The Batch maintain security privilege is part of the Batch manager security role and it allows a user to create an ad hoc batch job and grant privileges to other users.

> [!NOTE]
> This feature is available as of Platform update 20.

## Assign the Batch manager role to a user

Complete the following steps to assign the Batch manager security role to a specific user.

1. Select **System administration** > **Security** > **Assign users to roles**.

![Assign User To Roles.](./media/assign-batchmanager-role.png) 

2. Select **Batch Job Manager**, and on the left pane, select **Manually assign/exclude user**.

![Batch Manager Role.](./media/assign-batchmanager-role-2.png) 

3. Select a user from the list, and then select **Assign to role**.
4. Close the page. 

## Run by user

The **run by user** functionality allows Batch managers to specify a user to run the batch job. This functionality is useful when you want to change the user who is currently assigned to run the job or if you want to quickly set a user while copying the batch jobs from one company to another. You can also use this functionality to copy batch jobs.

![RunBy User.](./media/runby-user.png)  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]