--- 
# required metadata 
 
title: Establish customer payment terms
description: This procedure defines a cash discount and due date setup. 
author: aprilolson
ms.date: 05/23/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: PaymDay, PaymTerm, CashDisc   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Establish customer payment terms

[!include [banner](../../includes/banner.md)]

This procedure defines a cash discount and due date setup. This task guide uses the USMF demo company.

1. Go to **Accounts receivable > Payments setup > Payment days**. The setup for the **Terms of payment** is shared for **Accounts receivable** and **Accounts payable**. If you define it in one module, it will be available in the other module also. For this task guide, all of the terms of payment under **Accounts receivable** are set up.
2. Click **New**. Create a payment day if your terms of payment require a specific day of the week (Monday, Tuesday, etc) or a specific date of the month (5th, 10th, etc). 
3. In the **Payment day** field, enter an ID.
4. In the **Description** field, enter a description of the payment day.
5. In the **Week/Month** field, select either **Week** or **Month**. If you want to enter a day of the week, such as **Monday**, select **Week**. If you want to enter a date in the month, such as the 10th, select **Month**. Select **Month** for this example. 
6. In the **Day of month** field, enter a date. The date should be entered as a number, such as '10', and not as '10th'. 
7. Click **Save**.
8. Close the page.
9. Go to **Accounts receivable > Payments setup > Terms of payment**. 

>[!NOTE] 
>If the **Terms of payment** is **Cash**, the **Cash payment** field on the **Terms of payment** page must be **No**.

10. Click **New**. **Terms of payment** is used to define how the due dates will be calculated. The cash discount date setup is defined in a separate page. 
11. In the **Terms of payment field**, enter an ID.
12. In the **Description** field, enter a description.
13. Select a **Payment method** such as **COD**, **Net**, **Current month**, etc. The **Payment method** is used to define the start of how the due will be calculated. For example, **Net** is used if the due date is always a set number of months or days after the invoice date. **COD** can be used to when payment is required upon invoice, so a due date wouldn't be calculated. Select **Current month** for this task guide.  
14. Select a **Payment day** if a specific day of the  week or date are included in the calculation. Depending on your terms of payment, you may enter a quantity in **Months** or **Days**. Or you can use the **Payment schedule** or **Payment day** to 'add' to the end of the **Payment method**. If the due date will always be the 10th of the next month, select a **Payment day** of the 10th. If you are using a **Payment calendar**, you can define how the due date is determined when the calculated date lands on a non-workday. The initial due date is calculated using calendar days. If the calculated date lands on a non-workday, you can adjust the calculated due date to either the next working date or earlier working day.
15. Click **Save**.
16. Close the page.
17. Go to **Accounts receivable > Payments setup > Cash discounts**.
18. Click **New**. This page is used to define how the cash discount date will be calculated. 
19. In the **Cash discount** field, enter an ID.
20. In the **Description** field, enter a description.
21. If a tiered cash discount is available, select the **Next discount code** that is relevant after this new cash discount.
22. In the **Days** field, enter the number of days used to calculate the cash dicount date. If **Net** principle is selected, the number of days will be added to the invoice date to calculate the cash discount date.  
23. In the **Discount percentage** field, enter the percentage of the cash discount.
24. In the **Main account for customer discounts**, enter the main account to which the cash discount will post for customer invoices.
25. In the **Discount offset accounts** field, select an option. If you select **Accounts on the invoice lines**, the cash discount will post to the same asset/expense main account on the lines of the vendor invoice. If you select **Use main account for vendor invoices**, the cash discount will post to the main account you define in the **Main account for vendor invoices**. For this example, select **Use main account for vendor invoices**. 
26. In the **Main account for vendor discounts** field, enter the main account to which the cash discount will post for vendor invoices.
27. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
