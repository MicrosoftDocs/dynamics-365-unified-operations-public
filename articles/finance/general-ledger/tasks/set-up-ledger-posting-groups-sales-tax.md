--- 
title: Set up Ledger posting groups for sales tax
description: Sales tax is calculated and posted to main accounts that are specified in Ledger posting groups. Learn about setting up ledger posting groups for sales tax.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/05/2026
ms.custom:
ms.reviewer: twheeloc   
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: TaxAccountGroup 
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up Ledger posting groups for sales tax

[!INCLUDE [banner](../../includes/banner.md)]

Sales tax is calculated and posted to main accounts that you specify in ledger posting groups. Attach ledger posting groups to each sales tax code. You can set up individual ledger posting groups for each sales tax code, use one ledger posting group for all sales tax codes, or assign multiple ledger posting groups to the sales tax codes. This recording uses the DEMF demo company.

1. Go to **Navigation pane > Modules > Tax > Setup > Sales tax > Ledger posting groups**.
1. Select **New**.
1. In the **Ledger posting group** field, enter a value.
1. In the **Description** field, enter a value.
1. In the **Sales tax payable** field, select the main account for outgoing sales taxes that are payable to the tax authority. Collect sales taxes on behalf of the tax authority when you sell taxable goods and services.  
1. In the **Sales tax receivable** field, select the main account for incoming taxes that the tax authority sends. Vendors collect taxes on behalf of the tax authority when you buy taxable goods and services. This field isn't available if the **Apply sales tax taxation rules** option is selected in the **General ledger parameters** page. Instead, sales taxes that are paid to vendors are debited to the same account as the purchase.
1. In the **Use tax expense** field, select the main account for posting deductible use taxes that vendors don't claim or report to the tax authority as part of EU reverse charge GST/HST. Select the **Use tax** option for the **Sales tax code** in the **Sales tax group** that you use in the transaction. This field isn't available if the **Apply sales tax taxation rules** option is selected on the **General ledger parameters** page.
1. In the **Use tax payable** field, select the main account for posting incoming use taxes that are payable to tax authorities. Select the **Use tax** option in the **Sales tax code** in the **Sales tax group** to post **Use tax**. If the **Apply sales tax taxation rules** option is selected in **General ledger parameters** page, the offset is posted to the transaction's expense account.
1. In the **Settlement account** field, select the main account where the net balance of the ledger accounts specified in the **Use tax payable** and **Sales tax receivable** fields is posted. The balance is created when the sales taxes settle and the posting job runs. If the taxing authority for the settlement period is associated with a vendor account, the balance is posted to the vendor account instead.
1. In the **Vendor cash discount** field, select the main account to post cash discount for sales tax codes associated with this ledger posting group. This step is optional. If you don't enter an account, the main account on **Cash discount codes** is used. It can be useful to use different accounts per **Ledger posting group** if you're using the reverse sales tax on cash discount option on **Sales tax groups**.  
1. In the **Customer case discount** field, select the main account to post cash discount for **Sales tax codes** associated with this **Ledger posting group**. This step is optional. If you don't enter an account, the main account on the **Cash discount codes** is used. It can be useful to use different accounts per **Ledger posting group** if you're using the reverse sales tax on cash discount option on **Sales tax groups**.  
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
