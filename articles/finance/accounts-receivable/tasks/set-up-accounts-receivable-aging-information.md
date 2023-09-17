--- 
# required metadata 
 
title: Set up and generate accounts receivable aging information
description: This guide will help you set up an aging period definition, age customer balances, and view balances in the Aged balance list and the Collections page. 
author: abruer
ms.date: 03/28/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustVendReportInterval, CustAgingSnapshot, CustCollectionsPoolsListPage, CustCollections   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up and generate accounts receivable aging information

[!include [banner](../../includes/banner.md)]

This guide will help you set up an aging period definition, age customer balances, and view balances in the **Aged balance** list and the **Collections** page. This recording uses the USMF demo company.


## Create an aging period definition
1. Go to **Credit and collections > Setup > Aging period definitions**.
2. Click **New**.
3. In the **Aging period definition** field, type a value.
4. In the **Description** field, type a value.
5. Click **Add below** to insert a new aging period.
6. In the **Period** field, enter the description to show on aging reports.
7. In the **Unit** field, enter a number.
8. In the **Interval** field, select an option. Ledger period matches the period to your ledger calendar. Day, week, month, quarter and years define the size of the interval by date type. Unlimited selects all transactions before or after the previous period, depending on whether it is the first or last period.  
9. In the **Aging indicator** field, select an option.
10. Select the period at the top of the grid. Update the description to describe the oldest period in the aging period definition
11. In the **Period** field, enter the new description of the aging period.
12. Close the page.

## Age the balances
1. Go to **Credit and collections > Periodic tasks > Age customer balances**.
2. In the **Aging period definition** field, select the aging period definition that you created.
    + You can have one active snapshot for each aging period definition.  
    + All customers are processed by default. You can use this selection to calculate a single collections pool of customers.  
    + Select the date from the transaction that you will use for the aging.  
    + Select an "as of" date for aging. The default is today but, if you change this field to **Selected date**, you will be able to pick the date that you want. For batch processing, use **Today's date**.  
3. Expand the **Company** range. You can select the companies that will be included in the snapshot. The current company is selected by default.
4. Click **Ok** to process the snapshot. It will take some time, wait for the slider to disappear and check the message center for a message.

## View the balances on the Aged balances list and on the Collection page
1. Go to **Credit and collections > Collections > Aged balances**. The list page shows the balances for the customer. The aging icon shows the aging period for the oldest transaction.  
2. Select a customer with a balance.
3. Expand the **Aging** FactBox area to view the aged balances. The aging period definition for the factbox is taken from the default aging period definition specified in the parameters. You can change it using the **Collect** menu.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
