--- 
# required metadata 
 
title: Set up sales tax groups and item sales tax groups
description: This task recording walks you through the setup of Sales tax and Item sales tax groups. 
author: twheeloc
ms.date: 05/23/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxGroup,  TaxItemGroup   
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
# Set up sales tax groups and item sales tax groups

[!include [banner](../../includes/banner.md)]

This task recording walks you through the setup of Sales tax and Item sales tax groups. Sales tax groups are groups of sales tax codes that are attached to customers and vendors. They are also attached to ledger accounts for transactions that are not posted to a particular vendor or customer. Item sales tax groups are groups of sales tax codes that are attached to resources like products. The sales taxes that apply to a particular transaction are determined by the sales tax codes that are included both in the sales tax group and in the item sales tax group of the transaction. Sales tax can be calculated only if a sales tax group and an item sales tax group are selected for each transaction for which sales tax must be calculated or recorded.  

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax groups**.
2. Click **New**.
3. In the **Sales tax group** field, type a value.
4. In the **Description** field, type a value.
5. Expand the **Setup** section.
6. Click **Add**.
7. In the list, mark the selected row.
8. In the **Sales tax code** field, click the drop-down button to open the lookup.
9. In the list, click the link in the selected row.
10. Click **Save**.
11. Close the page.
12. Go to **Tax > Indirect taxes > Sales tax > Item sales tax groups**.
13. Click **New**.
14. In the **Item sales tax group** field, type a value.
15. In the **Description** field, type a value.
16. Click **Add**.
17. In the list, mark the selected row.
18. In the **Sales tax code** field, click the drop-down button to open the lookup.
19. In the list, click the link in the selected row.
20. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
