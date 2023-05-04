--- 
# required metadata 
 
title: Create loan items
description: Loan items are records that help you track physical items, such as phones or computers, that your company lends to workers. 
author: twheeloc
ms.date: 10/28/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HcmLoanType, DefaultDashboard, HcmLoanItem, HcmWorkerLookUp, HcmPersonnelManagementWorkspace  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create loan items


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]



Loan items are records that help you track physical items, such as phones or computers, that your company lends to workers. Each physical item must have a corresponding loan item. Each loan item record should describe what is being loaned, who is responsible for the loan, and the number of days the item can be on loan. You can create multiple loan items, such as keys, access cards, or uniforms, at the same time. The demo data company used to create this procedure is USMF.


## Create Loan types
1. Go to **Human resources** > **Workers** > **Loan items** > **Loan types**.
2. Click **New**.
3. In the **Loan type** field, type a value.
4. In the **Description** field, type a value.
5. Enter the number of days that items assigned to this loan type can be overdue. 
6. Click **Save**.
7. Close the page.
8. Refresh the page.

## Create Loan items
1. Go to **Human resources** > **Workers** > **Loan items** > **Loan items**.
2. Click **Create loan items**.
3. In the **Qty.** field, enter a number.
4. In the **Description** field, type a value.
5. In the **Loan type** field, click the drop-down button to open the lookup.
6. In the list, find and select the desired record.
7. In the list, click the link in the selected row.
8. Enter the number of days the item can be on loan.
    * The default value for the Planned return field on the Loaned equipment page is calculated as the current date plus this number.  
9. In the **Person in charge** field, click the drop-down button to open the lookup.
10. Click **Select**.
11. In the **Starting value** field, enter a number.
12. In the **Interval** field, enter a number.
13. In the **Format** field, type a value.
    * For example, if the starting number for a loan item is 10, enter two number symbols symbols in the **Format** field.  
14. Click **OK**.
15. Refresh the page.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
