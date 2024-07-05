--- 
title: Set up sales tax settlement periods
description: This article explains how to set up sales tax settlement periods in Dynamics 365 Finance.
author: liza-golub
ms.author: egolub
ms.date: 06/27/2024
ms.topic: how-to 
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak

---

# Set up sales tax settlement periods

[!include [banner](../../includes/banner.md)]

This article explains how to set up sales tax settlement periods. Sales tax settlement periods contain information about the period intervals for which sales tax needs to be reported and paid. A settlement process can be run for a settlement period for a specific date interval. All tax codes associated with the settlement period will be settled. Depending on the setup of the related Sales tax authority, the tax liability is posted either to a vendor or a General ledger account.

This task uses the USMF demo company.

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax settlement periods**.
2. Select **New**.
3. In the **Settlement period** field, type a value.
4. In the **Description** field, type a value.
5. In the **Authority** field, select the sales tax authority that receives the reports and the payments that are created for the settlement period.
6. In the list, find and select the desired record.
7. In the **Terms of payment** field, select the desired record in the dropdown menu. The related Sales tax authority can be set up as a vendor and the Sales tax settlement will create an open vendor invoice. The Terms of payment defines the Due date for the open vendor invoice.  
8. Select a type for the settlement period intervals.
9. Enter the number of Period interval units per period. For example, a quarter has three months.
10. Select or clear the **Use batch processing for sales tax settlement** checkbox. The settlement process for the settlement period can be processed as batch job in the background. This is recommended for a large number of tax transactions within a period interval.
11. Select or clear the **Prevent generating offset tax transactions** checkbox. By default, the system generates offset tax transactions during the settlement process, which can cause performance issues if there is a large number of tax transactions within a period interval. Select this checkbox to prevent the generation of offset tax transactions.
12. Select or clear the **Include corrections** checkbox. By default, the value is copied from the **Sales tax** tab on the **General ledger parameters** page. You can make this option available by enabling the **Enable "Include corrections" option on Sales tax settlement periods** feature in the **Feature management** workspace. The **Include corrections** option affects the sales tax settlement process and periodic sales tax reporting. It lets you control the **Include corrections** option for each sales tax settlement period instead of the whole legal entity.
13. On the **Period intervals** tab, select **Add**.
14. On the new row, in the **From date** field, enter a date.
15. In the **To date** field, enter a date.
16. Select **New period interval**. After you enter the first period interval, new periods can be created automatically. You can come back and add new period intervals as required.
17. Close the page.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
