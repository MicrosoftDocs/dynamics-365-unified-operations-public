--- 
# required metadata 
 
title: Set up Ledger posting groups for sales tax
description: Sales tax is calculated and posted to main accounts that are specified in Ledger posting groups. 
author: twheeloc
ms.date: 07/01/2019
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TaxAccountGroup   
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
# Set up Ledger posting groups for sales tax

[!include [banner](../../includes/banner.md)]

Sales tax is calculated and posted to main accounts that are specified in Ledger posting groups. Ledger posting groups are attached to each sales tax code. You can set up individual ledger posting groups for each sales tax code, use one ledger posting group for all sales tax codes or assign multiple ledger posting groups to the sales tax codes. This recording uses the DEMF demo company. 

1. Go to **Navigation pane > Modules > Tax > Setup > Sales tax > Ledger posting groups**.
2. Click **New**.
3. In the **Ledger posting group** field, type a value.
4. In the **Description** field, type a value.
5. In the **Sales tax payable** field, select the main account for outgoing sales taxes that are payable to the tax authority. Sales taxes are collected on behalf of the tax authority when you sell taxable goods and services.  
6. In the **Sales tax receivable** field, select the main account for incoming taxes that are received from the tax authority. Vendors collect taxes on behalf of the tax authority when you buy taxable goods and services. This field is not available if the Apply sales tax taxation rules option is selected in the **General ledger parameters** page. Instead, sales taxes that are paid to vendors are debited to the same account as the purchase.   
7. In the **Use tax expense** field, select  the main account for posting deductible Use taxes that are not claimed or reported to the tax authority by vendors as part of EU reverse charge GST/HST. The **Use tax** option must be selected for the **Sales tax code** in the **Sales tax group** that is used in the transaction. This field won't be available if the **Apply sales tax taxation rules** option is selected on the **General ledger parameters** page.   
8. In the **Use tax payable** field, select the main account for posting incoming Use taxes that are payable to tax authorities. The **Use tax** option must be selected in the **Sales tax code** in the **Sales tax group** to post **Use tax**. If **Apply sales tax taxation rules** option is selected in **General ledger parameters** page, the offset is posted to the transaction's expense account.   
9. In the **Settlement account** field, select the main account that the net balance of the ledger accounts specified in the **Use tax payable** and **Sales tax receivable** fields will be posted. The balance will be created when the sales taxes settle and the posting job has been run.  If the taxing authority for the settlement period is associated with a vendor account, the balance will be posted to the vendor account instead.
10. In the **Vendor cash discount** field, select the main account to post cash discount for Sales tax codes associated with this Ledger posting group. This is optional and if no account is entered,  the main account on **Cash discount codes** will be used. It can be useful to use different accounts per **Ledger posting group** if using the reverse sales tax on cash discount option on Sales tax groups.  
11. In the **Customer case discount** field, select the main account to post cash discount for **Sales tax codes** associated with this **Ledger posting group**. This is optional and if no account is entered, the main account on the **Cash discount codes** will be used. It can be useful to use different accounts per **Ledger posting group** if using the reverse sales tax on cash discount option on **Sales tax groups**.  
12. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
