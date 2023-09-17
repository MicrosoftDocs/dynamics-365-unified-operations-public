--- 
# required metadata 
 
title: Create a sales tax payment
description: The settle and post sales tax job procedure settles sales tax balances on the sales tax accounts and offsets them to the sales tax settlement account for a given period. 
author: twheeloc
ms.date: 01/04/2022
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Dialog   
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
# Create a sales tax payment

[!include [banner](../../includes/banner.md)]

The settle and post sales tax job procedure settles sales tax balances on the sales tax accounts, and offsets them to the sales tax settlement account for a given period.

1. Go to **Tax > Declarations > Sales tax > Settle and post sales tax**.
2. In the **Settlement period** field, select the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the **From date** field, enter a date. If you don't select the **Include corrections** option on the **General ledger parameters** page, the settlement can be processed for different versions. **Original** is the first settlement for a period interval and can be processed only once for a period interval. The latest corrections will settle sales tax transactions, which have been posted after the original version has been created.
5. In the **Transaction date** field, enter a date.
6. Select **OK**. The **Sales tax payments** report is printed to review the settled sales tax transactions in the period.

Starting in Finance version 10.0.24, you can omit the **Sales tax payments** report being generated right after the **Settle and post sales tax** periodic procedure is implemented under the **Separate sales tax payment report generation from sales tax settlement** feature in the **Feature management** workspace.

When the feature is enabled, after the settlement process is completed, no sales tax payment report is printed. Instead, you receive the following message, "The sales tax settlement and posting is completed. The voucher 'xxxx, m/d/yyyy' has been posted."

You can still manually run the sales tax payment report by going to **Tax** > **Inquiries and reports** > **Sales tax inquiries** > **Sales tax payments**.

## Performance consideration

The sales tax payment procedure can take a long time to be completed. The main factors that affect the performance of the procedure are the number of invoices in the settlement period and the number of entries that must be posted in the sales tax settlement voucher. To help improve performance, you can select to bypass some functionality that isn't required in your process.

### Enable the Sales tax payment performance improvement feature

The **Sales tax payment performance improvement** feature can help improve the performance of the sales tax payment procedure by aggregating, onto one line, the accounting currency amount and the reporting currency amount on sales tax payment voucher lines that have same main account, ledger dimension, and currency.

1. Go to **System administration** \> **Workspaces** \> **Feature management**.
2. On the **All** tab, search for and select **Sales tax payment performance improvement**.
3. Select **Enable**.

### Prevent generation of offset tax transactions

By default, the sales tax payment voucher posts offset sales tax transactions against each sales tax transaction that is settled in the sales tax payment procedure. These offset sales tax transactions are included on the **Sales tax/Ledger reconciliation** report. They show the outstanding balance of the sales tax transactions that aren't settled during the period.

However, the offset sales tax transactions can increase the burden on the sales tax payment procedure. Therefore, a flighting that is named **TaxReportGenOffsetTaxTransPerRecordSetFlighting** can be activated on demand. This flighting can help improve the performance of offset tax transaction generation for countries and regions except Thailand, Poland, Hungary, Lithuania, Malaysia, India, Italy, Russia, Czech Republic, Estonia, and Latvia.

> [!NOTE]
> If there are customized fields on the tax transaction table, the flighting can't be activated.

Because the **Sales tax/Ledger reconciliation** report is generally used only for internal control purposes and isn't required in many tax regimes, you can choose not to generate offset sales tax transactions on the sales tax payment voucher.

1. Go to **Tax** \> **Indirect taxes** \> **Sales tax** \> **Sales tax settlement periods**.
2. Select a settlement period.
3. On the **General** FastTab, set the **Prevent generating offset tax transactions** option to **Yes**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
