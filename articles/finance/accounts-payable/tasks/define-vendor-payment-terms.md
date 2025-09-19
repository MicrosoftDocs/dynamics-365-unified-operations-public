--- 
title: Define vendor payment terms
description: Learn how to set up payment terms for vendor invoices.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/04/2025
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: PaymTerm, CashDisc   
ms.dyn365.ops.version: Version 7.0.0 
---

# Define vendor payment terms

[!include [banner](../../includes/banner.md)]

This article explains how to set up payment terms for vendor invoices. This task uses the USMF demo company.

1. Go to **Accounts payable > Payment setup > Terms of payment**.
2. Select **New**. The **Terms of payment** page defines how the due date is calculated. It's not used to define how the cash discount date is calculated.  
3. In the **Terms of payment** field, type a value.
4. In the **Description field**, type a value.
5. In the **Days** field, enter a number. The number entered here is added to the due date, or to the end of the period identified in the **Payment method**. For example, if you select **Net**, the number is added to the due date. If you select **Current month**, it's added to the last day of the current month to calculate the due date.  
6. Select **Save**.
7. Close the page.
8. Go to **Accounts payable > Payment setup > Cash discounts**.
9. Select **New**.
10. In the **Cash discount** field, enter an ID.
11. In the **Description** field, type a value.
12. If the vendor offers a tiered discount, select the next cash discount after the current one is expired.
13. Close the page.
14. In the **Days** field, enter a number. The quantity entered in the **Days** field is used to calculate the **Cash discount date**, based on what option is selected in the **Net/Current** field. If **Net** was selected, the quantity is added to the invoice date to determine the cash discount date. If **Current month** was selected, the quantity is added to the end of the currency month to determine the cash discount date.  
15. Enter the percentage of the cash discount in the **Discount** field. 
16. Enter the main account to which the cash discount is posted for customer invoices, then enter the main account to which the cash discount is posted for vendor invoices. If **Discount offset accounts** is set to **Use main account for vendor discount**, then the Main account is used. If the option is set to **Accounts on the invoice lines**, the cash discount is posted to the asset/expense accounts on the invoice's lines.  
17. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
