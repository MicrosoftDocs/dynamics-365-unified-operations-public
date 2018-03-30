--- 
# required metadata

title: Configure a worker using the mobile job device
description: This procedure shows you how to assign the correct roles to the user account of a worker, and then enable the worker to do shop floor registrations.
author: YuyuScheller
manager: AnnBe
ms.date: 11/11/2016
ms.topic: business-process
ms.prod:  
ms.service: dynamics-ax-applications
ms.technology:  

# optional metadata

# ms.search.form:   
audience: Application User
# ms.devlang:  
ms.reviewer: yuyus
ms.search.scope: Operations
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Manufacturing
ms.author: yuyus
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Configure a worker using the mobile job device

[!include[task guide banner](../../includes/task-guide-banner.md)]

This procedure shows you how to assign the correct roles to the user account of a worker, and then enable the worker to do shop floor registrations.


## Assign roles to user account
1. Go to System administration > Users > Users.
2. Use the Quick Filter to filter on the name of a worker where the user account is associated with the machine operator role. In the sample data, the name would be Shannon.
3. Highlight the user account record.
4. In the list, click the "Name" link in the selected row to view the details of the user account.
5. In the tree, select 'Roles\Machine operator'.
6. Close the user account details page.
7. Close the page.

## Configure worker account.
1. Go to Human resources > Workers > Workers.
2. Use the Quick Filter to filter on the name of a worker where the user account is associated with the machine operator role. In the sample data, the name would be Shannon.
3. Highlight the user account record.
4. In the list, click the "Name" link in the selected row to view the details of the user account.
5. Click the Employment tab.
6. Expand the Time registration FastTab and click Activate on registration terminals.
7. Click Activate on registration terminals.
8. In the Calculation group field, enter or select a value.
9. In the Default calculation group field, enter or select a value.
10. In the Approval group field, enter or select a value.
11. In the Standard profile field, enter or select a value.
12. In the Profile group field, enter or select a value.
13. Click OK.
14. Click Edit to enter a badge number for the new time registration worker.
15. In the Badge ID field, type a value.
16. Click Save.
17. Use the SaveRecord shortcut.
18. Close the worker details page.
19. Close the page.

## Assign worker to device group.
1. Go to Production control > Setup > Manufacturing execution > Configure job card for devices.
2. Click Add.
3. In the list, mark the selected row.
4. Click OK.
5. Click Edit.
6. In the Production unit field, you can set the default filter for the worker. This will ensure that only production jobs for the selected production unit are shown when the worker logs on to the device.
7. Close the page.
