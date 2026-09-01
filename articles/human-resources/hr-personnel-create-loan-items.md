--- 
# required metadata 
 
title: Create loan items
description: Loan items are records that help you track physical items, such as phones or computers, that your company lends to workers. 
author: twheeloc
ms.date: 08/06/2026
ms.topic: how-to 
 
# optional metadata 
 
ms.search.form: HcmLoanType, DefaultDashboard, HcmLoanItem, HcmWorkerLookUp, HcmPersonnelManagementWorkspace  
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: ajitchandran
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create loan items

[!INCLUDE [banner](../includes/banner.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

Loan items are records that help you track physical items, such as phones or computers, that your company lends to workers. Each physical item must have a corresponding loan item. Each loan item record should describe what is being loaned, who is responsible for the loan, and the number of days the item can be on loan. You can create multiple loan items, such as keys, access cards, or uniforms, at the same time. The demo data company used to create this procedure is USMF.

## Create Loan types

1. Go to **Human resources** > **Workers** > **Loan items** > **Loan types**.
1. Select **New**.
1. In the **Loan type** field, enter a value.
1. In the **Description** field, enter a value.
1. Enter the number of days that items assigned to this loan type can be overdue.
1. Select **Save**.
1. Close the page.
1. Refresh the page.

## Create loan items

1. Go to **Human resources** > **Workers** > **Loan items** > **Loan items**.
1. Select **Create loan items**.
1. In the **Qty.** field, enter a number.
1. In the **Description** field, enter a value.
1. In the **Loan type** field, select the dropdown button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Enter the number of days the item can be on loan.
    * The default value for the **Planned return** field on the **Loaned equipment** page is calculated as the current date plus this number.  
1. In the **Person in charge** field, select the dropdown button to open the lookup.
1. Select **Select**.
1. In the **Starting value** field, enter a number.
1. In the **Interval** field, enter a number.
1. In the **Format** field, type a value.
    * For example, if the starting number for a loan item is 10, enter two number symbols in the **Format** field.  
1. Select **OK**.
1. Refresh the page.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
