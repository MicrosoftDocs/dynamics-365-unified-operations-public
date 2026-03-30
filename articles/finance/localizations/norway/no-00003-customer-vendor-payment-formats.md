---
title: NO-00003 Customer and vendor payment formats
description: Learn how to set up and maintain customer and vendor payment formats for Norway in Microsoft Dynamics 365 Finance.
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/12/2025
ms.reviewer: johnmichalak
ms.search.region: Norway
ms.search.validFrom: 2016-06-30
ms.search.form: 
  - BankCustPaymIdTable, LogisticsCountryRegionPaymentIdType_NO, CustTable, CustPaymMode, CustGroup
  - CustInvoiceJournal
---
# NO-00003 Customer and vendor payment formats

[!include [banner](../../includes/banner.md)]

This article explains how to set up and maintain Norwegian payment IDs in Microsoft Dynamics 365 Finance.

A payment identification (ID) is a unique identifier for customer payments that are settled electronically. It can be divided into different parts, such as the customer account number, invoice number, prefix, suffix, and external reference. When you receive a payment from a customer, the payment ID identifies the payment transaction for a sales invoice that is received from a bank.

The following procedures walk you through how to set up and maintaining Norwegian payment IDs, and were created using the demo data company DEMF with the country/region of legal entity primary address updated to be Norway.

## Set up payment IDs

To set up payment IDs, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments setup \> Payment ID**.
1. Select **New**.
1. In the **Payment ID type** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Payment ID length** field, enter a number.
1. In the **Account from position** field, enter a number.
1. In the **Account to position** field, enter a number.
1. In the **Invoice from position** field, enter a number.
1. In the **Invoice to position** field, enter a number.
1. In the **Modulo** field, select **Modulo 10**.
    Select the modulo check method to calculate the check number. The last digit of a payment ID is reserved for the check number to verify that the payment ID is valid. The following options are available:     -     - **Modulo 10** – The total length of the payment ID is divided by 1. The remainder is the check number.
    - **Modulo 11** – The total length of the payment ID is divided by 1. The remainder is the check number.
    - (None) – No check number is calculated.  
1. Select **Save**. After saving the record, you can preview the selected payment ID in the Payment ID test field.  
1. Go to **Accounts receivable \> Payments setup \> Payment ID per country/region**.
1. Select **New**.
1. In the **Country/region** field, enter or select a value.
1. In the **Payment ID type** field, enter or select a value.
1. Select **Save**.

## Attach the payment ID

To attach the payment ID, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. Use the Quick Filter to find records. For example, filter on the Account field with a value of "DE-010".
1. In the list, select the link in the selected row.
1. Expand the **Payment defaults** section.
1. Select **Edit**.
1. In the **Payment ID type** field, enter or select a value.
1. Select **Save**.
1. Go to **Accounts receivable \> Payments setup \> Methods of payment**.
1. Use the Quick Filter to find records. For example, filter on the Method of payment field with a value of "ELECTRONIC".
1. Select **Edit**.
1. Expand the **Payment control** section.
1. In the **Payment ID type** field, enter or select a value.
1. Select **Save**.
1. Go to **Accounts receivable \> Setup \> Customer groups**.
1. Select **Edit**.
1. In the **Payment ID type** field, enter or select a value.
1. Select **Save**.

## Update the payment ID

To update the payment ID, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Update invoice payment ID**.
1. To delete the payment ID information from all documents, select the **Delete payment ID** checkbox. This option should be used only when you want to remove or update payment IDs for documents that have payment IDs assigned. You're offered a dialog to delete payment IDs from specific type of documents.  
1. In the **Update invoice payment ID** field, select **Yes**.
1. Select **OK**.
1. Select **Yes**.
1. Select **Yes**.
1. Select **Yes**.
1. Select **Yes**.

## View the payment ID

To view the payment ID, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Inquiries and reports \> Invoices \> Invoice journal**.
1. Select **Show filters**.
1. In the **Payment ID** field, enter a filter value of **""** using the **is not** filter operator.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
