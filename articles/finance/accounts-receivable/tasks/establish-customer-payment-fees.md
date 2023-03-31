--- 
# required metadata 
 
title: Establish customer payment fees
description: Create payment fees for customer payments. 
author: ShivamPandey-msft
ms.date: 03/24/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPaymFee, CustPaymModeFee, BankAccountTableLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: twheeloc
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Establish customer payment fees

[!include [banner](../../includes/banner.md)]

Create payment fees for customer payments.

This task uses the USMF demo company.

1. In the **Navigation pane**, go to **Modules > Accounts receivable > Payments setup > Payment fee**.
2. Click **New**.
3. In the **Fee ID** field, enter a **Fee ID**. The **Fee ID** displays on payment journals, so make it descriptive to understand what fee is being assessed.  
4. In the **Name** field, enter a fee name.
5. In the **Fee description** field, enter a description for the fee.
6. In the **Charge** field, select whether the fee will be charged to the Customer or a Ledger account. If the customer is assessed the fee, select **Customer**. If the fee will be assess to your organization as an expense, select **Ledger**. For this task, select **Customer**.  
7. In the **Journal type** field, select the type of journal that can use this payment fee. If these fees are used for customer payments, the journal type will likely be Customer payment.  
8. Click **Save**.
9. Click **Payment fee setup**. The **Payment fee setup** is used to define the criteria for when the payment fee will be assessed. For example, you can define that the fee will be calculated if the bank account is USMF OPER, and the method of payment is check.  
10. In the **Groupings** field, select either Table, Group or All to define which bank accounts will be assessed this fee. If you select **All**, all bank accounts could be assessed this fee. If you select **Table**, only the bank account you select could be assessed this fee. If you select **Group**, only the bank accounts in the selected bank group could be assessed this fee.  
11. In the **Bank relation** field, select either a bank group or a bank account. If you selected **Table**, the lookup will display bank accounts. If you selected **Group**, the lookup will display bank groups.  
12. In the list, click the link in the selected row.
13. In the **Method of payment** field, select the **Method of payment** for which this fee will be assessed. For example, you may assess a fee to your customers if they send payments as a check, rather than as an electronic payment.  
14. In the list, find and select the desired record.
15. If relevant, in the **Payment currency** field, enter a payment currency. The payment currency is used as an additional criteria for whether the fee will be assessed. For example, your bank may charge an extra fee for payments received in USD currency, since they normally only transact in EUR currency.  
16. Select whether the fee will be a percent, amount or interval.
17. In the **Percentage/Amount field**, enter either percentage or amount of the fee. If the **Percentage/Amount** field is **Percent**, then the value entered here will be a percentage. If the **Percentage/Amount** field is **Amount**, then the value you enter here will be an amount. If the **Percentage/Amount** field is **Interval**, use the **Interval** tab to define the tiers.  
18. In the **Fee currency** field, select the currency of the fee. This is the currency in which the fee will be created.  
19. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
