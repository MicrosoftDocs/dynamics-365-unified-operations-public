--- 
# required metadata 
 
title: Set up customers and customer bank accounts for ISO20022 direct debits
description: This article explains how to set up a customer bank account and a customer direct debit mandate which are required to generate customer payment files like the ISO20022 direct debit. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustTable, CustBankAccounts, CustDirectDebitMandate, BankAccountTableLookUp,  LogisticsAddressCityLookup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# Set up customers and customer bank accounts for ISO20022 direct debits

[!include [banner](../../includes/banner.md)]

This article explains how to set up a customer bank account and a customer direct debit mandate which are required to generate customer payment files like the ISO20022 direct debit. Depending on the customer payment formats that are set up, additional information, not covered in this article, might be required for a customer or a customer bank account. 

## Set up a customer bank account
1. Go to **Accounts receivable** > **Customers** > **All customers**.
2. Use the **Quick Filter** to find records. For example, filter on the **Account field**.
3. In the list of results, select a row, and then select the link in the row.
4. On the Action Pane, select **Customer**.
5. Select **Bank accounts** > **New**.
7. In the **Bank account** field, enter a value.
8. In the **Name** field, enter a value.
9. In the **Bank groups** field, enter or select a value.
10. In the **IBAN** field, enter a value.
11. In the **SWIFT code** field, type a value. For many payment formats, SWIFT\BIC isn't mandatory. However we recommend that it be registered for a bank account.  
12. Select **Save** and then close the page.
13. Select **Edit**.
15. In the **Payment defaults** section, in the **Bank account** field, enter or select a value.

## Add a direct debit mandate
1. In the **Direct debit mandates** section, select **Add**.
2. In the **Creditor bank account** field, enter or select a value.
3. In the **Signature date** field, enter a date.
4. Select **Yes** to confirm the date update.
5. In the **Signature location** field, enter or select a value.
6. In the **Expected number of payments** field, enter a number.
7. Select **OK** and then select **Save**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
