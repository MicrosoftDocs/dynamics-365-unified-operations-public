--- 
# required metadata 
 
title: Set up sales tax settlement periods
description: This article explains how to set up sales tax settlement periods in Dynamics 365 Finance.
author: twheeloc
ms.date: 08/05/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxPeriod   
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
# Set up sales tax settlement periods

[!include [banner](../../includes/banner.md)]

This article explains how to set up sales tax settlement periods. Sales tax settlement periods contain information about the period intervals for which sales tax needs to be reported and paid. A settlement process can be run for a settlement period for a specific date interval. All tax codes associated with the settlement period will be settled. Depending on the set up of the related Sales tax authority, the tax liability is posted either to a vendor or a General ledger account.

This task uses the USMF demo company.

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax settlement periods**.
2. Select **New**.
3. In the **Settlement period** field, type a value.
4. In the **Description** field, type a value.
5. In the **Authority** field, select the sales tax authority that receives the reports and the payments that are created for the settlement period.
6. In the list, find and select the desired record.
7. In the **Terms of payment** field, select the desired record in the drop-down menu. The related Sales tax authority can be set up as a vendor and the Sales tax settlement will create an open vendor invoice. The Terms of payment defines the Due date for the open vendor invoice.  
8. Select a type for the settlement period intervals.
9. Enter the number of Period interval units per period. For example, a quarter has 3 months.
10. Select or clear the **Use batch processing for sales tax settlement** check box. The settlement process for the settlement period can be processed as batch job in the background. This is recommended for a large number of tax transactions within a period interval.
11. Select or clear the **Prevent generating offset tax transactions** check box. By default, the system generates offset tax transactions during the settlement process, which cause can performance issue if there are a large number of tax transactions within a period interval. Select this check box to prevent generating offset tax transactions.
12. Expand the **Period intervals** tab.
13. Select **Add**.
14. In the **From date** field in the new row, enter a date.
15. In the **To date** field, enter a date.
16. Select **New period interval**. Once the first period interval has been entered, new periods can be created automatically. You can come back and add new period intervals as required.  
17. Close the page.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
