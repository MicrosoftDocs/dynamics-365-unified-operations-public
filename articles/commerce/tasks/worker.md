---
title: Configure a worker
description: This procedure demonstrates how to configure a worker as a sales representative who is eligible for commission on sales in POS.
author: josaw1
ms.date: 08/29/2018
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.industry: Retail
ms.search.form: CommissionSalesGroup, CommissionSalesMember, DirPartyLookup, HcmWorker
---
# Configure a worker

[!include [banner](../includes/banner.md)]

This procedure demonstrates how to configure a worker as a sales representative who is eligible for commission on sales in POS. This procedure uses the USRT demo data company.


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
1. Go to Retail and Commerce > Employees > Workers.
2. In the list, find and select the desired record.
3. In the list, click the link in the selected row.
4. Click the Commerce tab.
    * A worker can be assigned to a default sales group. The default sales group will be automatically added to sales lines in POS if the option is enabled in the functionality profile for the store.  
5. Click Edit.
6. In the Default group field, enter or select a value.
7. Click Save.



[!INCLUDE[footer-include](../../includes/footer-banner.md)]
