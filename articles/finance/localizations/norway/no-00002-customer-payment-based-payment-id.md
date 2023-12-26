--- 
# required metadata 
 
title: NO-00002 Customer payment based on payment ID
description: This article explains how to set up and maintain Norwegian payment IDs. 
author: kfend
ms.date: 08/01/2023
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: BankCustPaymIdTable, LogisticsCountryRegionPaymentIdType_NO, CustTable, CustPaymMode, CustGroup,  CustInvoiceJournal   
audience: Application User 
# ms.devlang:  
ms.reviewer: kfend
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Norway
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# NO-00002 Customer payment based on payment ID

[!include [banner](../../includes/banner.md)]

Complete the steps in this article to set up and maintain Norwegian payment IDs. 

A payment identification (ID) is a unique identifier for customer payments that are settled electronically. The payment ID can be divided into different parts, such as the customer account number, invoice number, prefix, suffix, and external reference. When you receive a payment from a customer, the payment ID identifies the payment transaction for a sales invoice that is received from a bank.

## Set up a payment ID
1. Go to **Accounts receivable** > **Payments setup** > **Payment ID** and select **New**.
2. Enter values in the following fields:

   - **Payment ID type**
   - **Name**
   - **Payment ID length**
   - **Account from position**
   - **Account to position**
   - **Invoice from position**
   - **Invoice to position** 

3. In the **Modulo** field, select the modulo check method to calculate the check number. The last digit of a payment ID is reserved for the check number to verify that the payment ID is valid. The following options are available:

   - **Modulo 10** – The total length of the payment ID is divided by 10. The remainder is the check number.
   - **Modulo 11** – The total length of the payment ID is divided by 11. The remainder is the check number.
   - **(None)** – No check number is calculated.  

4. Select **Save**. After the record is saved, you can preview the selected payment ID in the **Payment ID test** field.
5. Go to **Accounts receivable** > **Payments setup** > **Payment ID per country/region** and select **New**.
6. In the **Country/region** field, enter or select a value.
7. In the **Payment ID type** field, enter or select a value.
8. Select **Save**.

## Attach a payment ID to a customer
1. Go to **Accounts receivable** >** Customers** > **All customers**.
2. Use the **Quick Filter** to filter on the **Account** field with a value of **DE-010**.
3. In the list, select the link in the selected row.
4. Expand the **Payment defaults** section and select **Edit**.
5. In the **Payment ID type** field, enter or select a value and then select **Save**.
6. Go to **Accounts receivable** > **Payments setup** > **Methods of payment**.
7. Use the **Quick Filter** to find records. For example, filter on the **Method of payment** field with a value of **ELECTRONIC**.
8. Select **Edit**.
9. Expand the **Payment control** section and in the **Payment ID type** field, enter or select a value.
10. Select **Save**.
11. Go to **Accounts receivable** > **Setup** > **Customer groups** and select **Edit**.
12. In the **Payment ID type** field, enter or select a value and then select **Save**.

## Update the payment ID
1. Go to **Accounts receivable** > **Periodic tasks** > **Update invoice payment ID**.
2. Select the **Delete payment ID** check box to delete the payment ID information from all documents.

    > [!NOTE]
    > This option should only be used only to remove or update Payment IDs for documents that have a Payment ID assigned. You'll have the option to delete the Payment ID from specific type of documents.  

3. In the Update invoice payment ID field, select **Yes**.
4. Select **OK**.
5. Select **Yes**.
6. Select **Yes**.
7. Select **Yes**.
8. Select **Yes**.

## View the payment ID
1. Go to **Accounts receivable** > **Inquiries and reports** > **Invoices** > **Invoice journal**.
2. Select **Show filters**.
3. Apply the following filters: Enter a filter value of **""** on the **Payment ID** field using the **is not** filter operator.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
