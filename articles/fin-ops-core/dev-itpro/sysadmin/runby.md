---
title: Batch manager security role
description: Learn about the batch manager security role that is used to manage batch job, including an overview on assigning batch manager roles to users.
author: hasaid
ms.author: hasaid
ms.topic: how-to
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-08-15
ms.search.form: 
ms.dyn365.ops.version: Platform update 20
ms.assetid: 6135bcf7-bf8f-42ae-b2c6-458f6538e6a4
ms.custom: sfi-image-nochange
---

# Batch manager security role

[!include [banner](../includes/banner.md)]

Before Platform update 20, users needed to be assigned to the system admin or IT admin security role to manage batch jobs. With the release of Platform update 20, there's a more targeted role: Batch manager. By using this security role, a user has permissions to copy batch jobs, change who executes jobs, and specify the time ranges during which jobs can execute. The Batch maintain security privilege is part of the Batch manager security role, and it grants a user the ability to create an ad hoc batch job and grant privileges to other users.

> [!NOTE]
> This feature is available as of Platform update 20.

## Assign the Batch manager role to a user

Complete the following steps to assign the Batch manager security role to a specific user.

1. Select **System administration** > **Security** > **Assign users to roles**.

   :::image type="content" source="./media/assign-batchmanager-role.png" alt-text="Screenshot of the Assign Users to Roles page.":::

1. Select **Batch Job Manager**. In the left pane, select **Manually assign/exclude user**.

   :::image type="content" source="./media/assign-batchmanager-role-2.png" alt-text="Screenshot of the Batch Job Manager role selection with Manually assign/exclude user option.":::

1. Select a user from the list, and then select **Assign to role**.
1. Close the page.

## Run by user

By using the **run by user** functionality, Batch managers can specify a user to run the batch job. This functionality is useful when you want to change the user who currently runs the job or when you want to quickly set a user while copying the batch jobs from one company to another. You can also use this functionality to copy batch jobs.

:::image type="content" source="./media/runby-user.png" alt-text="Screenshot of the Run by user functionality in batch job settings.":::  

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
