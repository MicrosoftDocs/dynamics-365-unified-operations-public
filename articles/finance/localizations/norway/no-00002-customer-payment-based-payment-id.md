--- 
title: NO-00002 Customer payment based on payment ID
description: Learn how to set up and maintain customer payment based on payment IDs for Norway in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: kfend
ms.topic: how-to
ms.date: 06/12/2025
ms.reviewer: johnmichalak  
ms.search.region: Norway
ms.search.validFrom: 2016-06-30
ms.search.form: BankCustPaymIdTable, LogisticsCountryRegionPaymentIdType_NO, CustTable, CustPaymMode, CustGroup,  CustInvoiceJournal
ms.custom: 
  - bap-template
---

# NO-00002 Customer payment based on payment ID

[!include [banner](../../includes/banner.md)]

This article explains how to set up and maintain Norwegian payment IDs in Microsoft Dynamics 365 Finance.

A payment identification (ID) is a unique identifier for customer payments that are settled electronically. The payment ID can be divided into different parts, such as the customer account number, invoice number, prefix, suffix, and external reference. When you receive a payment from a customer, the payment ID identifies the payment transaction for a sales invoice that is received from a bank.

## Set up a payment ID

To set up a payment ID, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Payments setup** \> **Payment ID** and select **New**.
1. Enter values in the following fields:

   - **Payment ID type**
   - **Name**
   - **Payment ID length**
   - **Account from position**
   - **Account to position**
   - **Invoice from position**
   - **Invoice to position** 

1. In the **Modulo** field, select the modulo check method to calculate the check number. The last digit of a payment ID is reserved for the check number to verify that the payment ID is valid. The following options are available:

   - **Modulo 10** – The total length of the payment ID is divided by 1. The remainder is the check number.
   - **Modulo 11** – The total length of the payment ID is divided by 1. The remainder is the check number.
   - **(None)** – No check number is calculated.
   - **Modulo 731** - The check number is calculated using the 7-3-1 method specified by the Estonian Bank Association for reference numbers.

1. Select **Save**. After the record is saved, you can preview the selected payment ID in the **Payment ID test** field.
1. Go to **Accounts receivable** \> **Payments setup** \> **Payment ID per country/region** and select **New**.
1. In the **Country/region** field, enter or select a value.
1. In the **Payment ID type** field, enter or select a value.
1. Select **Save**.

## Attach a payment ID to a customer

To attach a payment ID to a customer, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Customers** \> **All customers**.
1. Use the **Quick Filter** to filter on the **Account** field with a value of **DE-010**.
1. In the list, select the link in the selected row.
1. Expand the **Payment defaults** section and select **Edit**.
1. In the **Payment ID type** field, enter or select a value and then select **Save**.
1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Payments setup** \> **Methods of payment**.
1. Use the **Quick Filter** to find records. For example, filter on the **Method of payment** field with a value of **ELECTRONIC**.
1. Select **Edit**.
1. Expand the **Payment control** section and in the **Payment ID type** field, enter or select a value.
1. Select **Save**.
1. Go to **Accounts receivable** \> **Setup** \> **Customer groups** and select **Edit**.
1. In the **Payment ID type** field, enter or select a value and then select **Save**.

## Update the payment ID

To update the payment ID, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Periodic tasks** \> **Update invoice payment ID**.
1. Select the **Delete payment ID** check box to delete the payment ID information from all documents.

    > [!NOTE]
    > This option should only be used only to remove or update Payment IDs for documents that have a Payment ID assigned. You'll have the option to delete the Payment ID from specific type of documents.  

1. In the Update invoice payment ID field, select **Yes**.
1. Select **OK**.
1. Select **Yes**.
1. Select **Yes**.
1. Select **Yes**.
1. Select **Yes**.

## View the payment ID

To view the payment ID, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable** \> **Inquiries and reports** \> **Invoices** \> **Invoice journal**.
1. Select **Show filters**.
1. Apply the following filters: Enter a filter value of **""** on the **Payment ID** field using the **is not** filter operator.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
