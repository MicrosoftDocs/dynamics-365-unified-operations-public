--- 
# required metadata 
 
title: Configure a worker
description: This procedure demonstrates how to configure a retail worker as a sales representative who is eligible for commission on sales in POS. 
author: jblucher
manager: AnnBe 
ms.date: 02/22/2017
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: josaw
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Retail
ms.author: jeffbl
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Configure a worker

[!include[task guide banner](../includes/task-guide-banner.md)]

This procedure demonstrates how to configure a retail worker as a sales representative who is eligible for commission on sales in POS. This procedure uses the USRT demo data company.


## Create a commission sales group for the worker
1. Go to Sales and marketing > Commissions > Sales groups.
    * Workers can be assigned to one or more sales groups. In POS, you can choose any sales group that contains workers from the store's address book.  
2. Click New.
3. In the Group field, type a value.
4. In the Name field, type a value.
5. Click Save.
6. On the Action Pane, click General.
7. Click Sales rep.
    * A sales group can contain more than one worker. Commissions can be split between workers based on how you define the commission share.  
8. In the Name field, enter or select a value.
9. In the Commission share field, enter a number.
10. Click Save.
11. Close the page.
12. Close the page.

## Assign the workers default sales group
1. Go to Retail and commerce > Employees > Workers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click the Retail tab.
    * A worker can be assigned to a default sales group. The default sales group will be automatically added to sales lines in POS if the option is enabled in the functionality profile for the store.  
5. Click Edit.
6. In the Default group field, enter or select a value.
7. Click Save.

