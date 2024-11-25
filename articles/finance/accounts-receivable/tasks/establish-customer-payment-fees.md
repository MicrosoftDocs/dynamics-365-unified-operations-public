--- 
title: Establish customer payment fees
description: Learn about how to create payment fees for customer payments, including a step-by-step process for establishing payment fees. 
author: ShivamPandeyMSFT
ms.author: shpandey
ms.topic: how-to
ms.date: 03/24/2023
ms.custom:
ms.reviewer: twheeloc
audience: Application User 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustPaymFee, CustPaymModeFee, BankAccountTableLookUp
ms.dyn365.ops.version: Version 7.0.0 
---

# Establish customer payment fees

[!include [banner](../../includes/banner.md)]

Create payment fees for customer payments.

This task uses the USMF demo company.

1. Go to **Accounts receivable** > **Payments setup** > **Payment fee**.
2. Click **New**.
3. In the **Fee ID** field, enter a **Fee ID**. The **Fee ID** displays on payment journals, it should be descriptive to understand what fee is being assessed.  
4. In the **Name** field, enter a fee name.
5. In the **Fee description** field, enter a description for the fee.
6. In the **Charge** field, select if the fee is charged to the Customer or a Ledger account. If the customer is assessed the fee, select **Customer**. If the fee is assessed to your organization as an expense, select **Ledger**. For this task, select **Customer**.  
7. In the **Journal type** field, select the type of journal that can use this payment fee. If these fees are used for customer payments, the journal type will likely be Customer payment.  
8. Click **Save**.
9. Click **Payment fee setup**. The **Payment fee setup** is used to define the criteria for when the payment fee will be assessed. For example, you can define that the fee will be calculated if the bank account is USMF OPER, and the method of payment is check.  
10. In the **Groupings** field, select either **Table**, **Group** or **All** to define which bank accounts will be assessed this fee. If you select **All**, all bank accounts could be assessed this fee. If you select **Table**, only the bank account you select is assessed this fee. If you select **Group**, only the bank accounts in the selected bank group is assessed this fee.  
11. In the **Bank relation** field, select either a bank group or a bank account. If you selected **Table**, the lookup displays bank accounts. If you selected **Group**, the lookup displays bank groups.  
12. In the list, click the link in the selected row.
13. In the **Method of payment** field, select the **Method of payment** for this fee will be assessed. For example, you may assess a fee to your customers if they send payments as a check, rather than as an electronic payment.  
14. In the list, find and select the desired record.
15. If relevant, in the **Payment currency** field, enter a payment currency. The payment currency is used as an additional criteria for whether the fee will be assessed. For example, your bank may charge an extra fee for payments received in USD currency, since they normally only transact in EUR currency.  
16. Select whether the fee will be a percent, amount or interval.
17. In the **Percentage/Amount field**, enter either percentage or amount of the fee. If the **Percentage/Amount** field is **Percent**, the value entered is a percentage. If the **Percentage/Amount** field is **Amount**, the value entered is an amount. If the **Percentage/Amount** field is **Interval**, use the **Interval** tab to define the tiers.  
18. In the **Fee currency** field, select the currency of the fee. This is the currency in which the fee will be created.  
19. Click **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
