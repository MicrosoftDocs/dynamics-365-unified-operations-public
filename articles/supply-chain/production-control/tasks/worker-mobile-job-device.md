--- 
# required metadata 
 
title: Configure a worker using the mobile job device
description: This topic explains how to assign the correct roles to the user account of a worker, and then enable the worker to do shop floor registrations. 
author: ShylaThompson
manager: AnnBe 
ms.date: 07/09/2019
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: SysUserManagement, HcmWorker, JmgRegistrationSetupTouch, JmgRegistrationSetupAssignUsers   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: shylaw
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Configure a worker using the mobile job device

[!include [banner](../../includes/banner.md)]

This topic explains how to assign the correct roles to the user account of a worker, and then enable the worker to do shop floor registrations.

## Verify that a worker is assigned a certain role

For this example, verify that user "SHANNON" is assigned the machine operator role before you configure the worker account.

1. Go to **Navigation pane > Modules > System administration > Users > Users**.
2. Search for a user in the quick filter. For this example, enter `shannon`.
3. Select the link in the **User ID** column of the user account that appears.
4. In the **User's roles** tree, select **Roles > Machine operator**.
5. Close the **user details** and **users** pages to return to the home page.

## Configure worker account
1. Go to **Navigation pane > Modules > Human resources > Workers > Workers**.
2. Search for a user in the quick filter. For this example, enter `shannon`.
3. Select the link in the **Name** column of the user account that appears.
4. Select the **Time registration** tab.
5. Select **Activate on registration terminals**.
6. Enter or select values in the following fields:  

    - **Calculation group**  
    - **Default calculation group**  
    - **Approval group**  
    - **Standard profile**  
    - **Profile group**  

7. Select **OK**.
8. Select **Edit** to enter a badge number for the new time registration worker. Enter a value in the **Badge ID** field.
9. Select **Save**.
10. Close the **Worker details** and **Workers** pages.

## Assign worker to device group
1. Go to **Production control > Setup > Manufacturing execution > Configure job card for devices**.
2. Select **Add**.
3. In the list, select the desired worker. For this example, select **SHANNON**.
4. Select **OK**.
5. Select **Edit**.
6. In the **Production unit** field, you can set the default filter for the worker. This will ensure that only production jobs for the selected production unit are shown when the worker logs on to the device. Enter the desired value.
7. Close the page.

