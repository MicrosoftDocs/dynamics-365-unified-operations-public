--- 
# required metadata 
 
title: Create a sales tax payment
description: The settle and post sales tax job procedure settles sales tax balances on the sales tax accounts and offsets them to the sales tax settlement account for a given period. 
author: twheeloc
ms.date: 08/29/2018
ms.topic: business-process 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: Dialog   
audience: Application User 
# ms.devlang:  
ms.reviewer: roschlom
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: roschlom
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Create a sales tax payment

[!include [banner](../../includes/banner.md)]

The settle and post sales tax job procedure settles sales tax balances on the sales tax accounts, and offsets them to the sales tax settlement account for a given period.

1. Go to **Tax > Declarations > Sales tax > Settle and post sales tax**.
2. In the **Settlement period** field, click the drop-down button to open the lookup.
3. In the list, click the link in the selected row.
4. In the **From date** field, enter a date.
    * If you don't select the **Include corrections** option on the **General ledger parameters** page, the settlement can be processed for different versions. Original is the first settlement for a period interval and can be processed only once for a period interval. The latest corrections will settle sales tax transactions which have been posted after the original version has been created.   
5. In the **Transaction date** field, enter a date.
6. Click **OK**.

## Performance consideration

Sales tax payment procedure might spend a long time to complete. The number of the invoices in the settlement period as well as the number of the entries to be posted in the sales tax settlement voucher are the key factors which impact the performance of the sales tax payment procedure significantly. You can choose to bypass some functionalities which are not mandate in your process to improve the performance.

### Enable the Sales tax payment performance improvement

This feature can improve sales tax payment performance by aggregating accounting currency amount and reporting currency amount on sales tax payment voucher lines with same main account, ledger dimension, currency into one single line.

1. Go to **System administration > Workspaces > Feature management > all**.
2. Search for **Sales tax payment performance improvement**.
3. Click **Enable** now.

### Prevent generating offset tax transactions

By default, the sales tax payment voucher will post offset sales tax transactions against each sales tax transaction settled in the procedure. These offset sales tax transactions will be included in the **Sales tax/Ledger reconciliation** report to reveal the outstanding balance of the sales tax transactions which have not been settled in the given period.

However, the offset sales tax transactions can increase the burden on the sales tax payment procedure. A flighting **TaxReportGenOffsetTaxTransPerRecordSetFlighting** can be activated on demand to increase the performance of generating offset tax transactions for countries/regions other than Thailand, Poland, Hungary, Lithuania, Malaysia, India, Italy, Russia, Czech Republic, Estonia and Latvian.

> [!Note]
>
> There shall be no customized fields on the tax transaction table. Otherwise, the flighting can't be activated.

On the other hand, as the **Sales tax/Ledger reconciliation** report is generally only for internal control purpose and is not mandate in many tax regimes, you can choose to prevent generating offset sales tax transactions on the sales tax payment voucher.

1. Go to **Tax > Indirect taxes > Sales tax > Sales tax settlement periods**.
2. Select a settlement period.
3. In the **General** FastTab, switch the **Prevent generating offset tax transactions** option to **Yes**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
