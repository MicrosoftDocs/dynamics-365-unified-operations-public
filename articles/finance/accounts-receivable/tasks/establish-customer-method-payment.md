--- 
# required metadata 
 
title: Establish customer method of payment
description: This article explains how to create a method of payment for customer payments. 
author: ShivamPandey-msft
ms.date: 03/23/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustPaymMode, BankAccountTableLookUp   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: shpandey
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Establish customer method of payment

[!include [banner](../../includes/banner.md)]

This article explains how to create a method of payment for customer payments. This task uses the USMF demo company.

1. In the navigation pane, go to **Modules > Accounts receivable > Payments setup > Methods of payment**.
2. Select **New**.
3. In the **Method of payment** field, enter an ID for the method of payment. The **Method of payment ID** is shown on invoices and payments, so make it descriptive enough to understand what type of payment is being recorded, and for what bank account.  
4. In the **Description** field, enter a description.
5. Select what payment status is required in order for payments to be posted. When creating a customer payment, it can only be posted when the payment status matches the payment status you define here.  
6. Select how customers payments should be created for invoices. This option is only used when running a payment proposal. A payment proposal could be used for customer payments when doing direct debits, and pulling the funds from the customers' bank accounts.  
7. Select the type of payment. The payment type will help determine whether some validation will occur or not on the payment.  
8. Select what account type payments will post to. Typically, Bank would be selected for this option.  
9. Select the bank account into which this payment will be recorded.
10. Enter the **Bank transaction type** to identify the type of payment used by your bank. The bank transaction type is used during the bank reconciliation process, and can make reconciliation easier.  
11. Select whether this payment will temporarily post to a bridging account. If you want to try the float time for a payment to clear the bank, use the Bridging functionality. The payment will temporarily post to a Ledger account until it clears the bank, at which time the payment will move to the bank account you defined here.  
12. Enter the main account used for the bridging posting. This is the main account to which the payment will temporarily post if using bridging.  
13. Use the **File format** tab to define setting for electronic payments.
14. Use the **Payment control** tab to define fields that are mandatory. For example, if you require all payments with this method of payment to be deposited, you can choose that option on this tab.  
15. Use the **Payment attributes** tab to define which payment attributes you want to use for this method of payment.
16. Select **Save**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
