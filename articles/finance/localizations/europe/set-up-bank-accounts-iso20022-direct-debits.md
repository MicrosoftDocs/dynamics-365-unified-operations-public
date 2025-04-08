--- 
title: Set up customers and customer bank accounts for ISO20022 direct debits
description: Learn how to set up a customer bank account and a customer direct debit mandate in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak 
ms.search.region: Global
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable, CustBankAccounts, CustDirectDebitMandate, BankAccountTableLookUp,  LogisticsAddressCityLookup
ms.dyn365.ops.version: Version 7.0.0 
---

# Set up customers and customer bank accounts for ISO20022 direct debits

[!include [banner](../../includes/banner.md)]

This article explains how to set up a customer bank account and a customer direct debit mandate, which are required to generate customer payment files like the ISO20022 direct debit. Depending on the configured customer payment formats, additional information not covered in this article might be required for a customer or a customer bank account. 

## Set up a customer bank account

To set up a customer bank account, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. Use the Quick Filter to find records. For example, enter "Account field".
1. In the list of results, select a row, and then select the link in the row.
1. On the Action Pane, select **Customer**.
1. Select **Bank accounts \> New**.
1. In the **Bank account** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Bank groups** field, enter or select a value.
1. In the **IBAN** field, enter a value.
1. In the **SWIFT code** field, enter a value. For many payment formats, SWIFT bank identifier code (BIC) codes aren't mandatory, but Microsoft recommends that you register one for a bank account.  
1. Select **Save** and then close the page.
1. Select **Edit**.
1. In the **Payment defaults** section, in the **Bank account** field, enter or select a value.

## Add a direct debit mandate

To add a direct debit mandate, follow these steps.

1. In the **Direct debit mandates** section, select **Add**.
1. In the **Creditor bank account** field, enter or select a value.
1. In the **Signature date** field, enter a date.
1. Select **Yes** to confirm the date update.
1. In the **Signature location** field, enter or select a value.
1. In the **Expected number of payments** field, enter a number.
1. Select **OK**, and then select **Save**.




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
