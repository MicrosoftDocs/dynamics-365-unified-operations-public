--- 
# required metadata 
 
title: NO-00002 Customer payment based on payment ID
description: This article explains how to set up and maintain Norwegian payment IDs. 
author: EvgenyPopovMBS
ms.date: 08/29/2018
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
ms.author: epopov
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 
---
# NO-00002 Customer payment based on payment ID

[!include [banner](../../includes/banner.md)]

This task walks you through setting up and maintaining Norwegian payment IDs. 

A payment identification (ID) is a unique identifier for customer payments that are settled electronically. It can be divided into different parts, such as the customer account number, invoice number, prefix, suffix, and external reference. When you receive a payment from a customer, the payment ID identifies the payment transaction for a sales invoice that is received from a bank.

This task was created using the demo data company DEMF with the country/region of legal entity primary address updated to be Norway. This procedure is for a feature that was added in Dynamics 365 for Operations version 1611.


## Set up a payment ID
1. Go to Accounts receivable > Payments setup > Payment ID.
2. Click New.
3. In the Payment ID type field, type a value.
4. In the Name field, type a value.
5. In the Payment ID length field, enter a number.
6. In the Account from position field, enter a number.
7. In the Account to position field, enter a number.
8. In the Invoice from position field, enter a number.
9. In the Invoice to position field, enter a number.
10. In the Modulo field, select 'Modulo 10'.
    * Select the modulo check method to calculate the check number. The last digit of a payment ID is reserved for the check number to verify that the payment ID is valid. The following options are available:     Modulo 10 – The total length of the payment ID is divided by 10. The remainder is the check number.   Modulo 11 – The total length of the payment ID is divided by 11. The remainder is the check number.   - (None) – No check number is calculated.  
11. Click Save.
    * After saving the record, you can preview the selected payment ID in the Payment ID test field.  
12. Go to Accounts receivable > Payments setup > Payment ID per country/region.
13. Click New.
14. In the Country/region field, enter or select a value.
15. In the Payment ID type field, enter or select a value.
16. Click Save.

## Attach a payment ID to a customer
1. Go to Accounts receivable > Customers > All customers.
2. Use the Quick Filter to filter on the Account field with a value of 'DE-010'.
3. In the list, click the link in the selected row.
4. Expand the Payment defaults section.
5. Click Edit.
6. In the Payment ID type field, enter or select a value.
7. Click Save.
8. Go to Accounts receivable > Payments setup > Methods of payment.
9. Use the Quick Filter to find records. For example, filter on the Method of payment field with a value of 'ELECTRONIC'.
10. Click Edit.
11. Expand the Payment control section.
12. In the Payment ID type field, enter or select a value.
13. Click Save.
14. Go to Accounts receivable > Setup > Customer groups.
15. Click Edit.
16. In the Payment ID type field, enter or select a value.
17. Click Save.

## Update the payment ID
1. Go to Accounts receivable > Periodic tasks > Update invoice payment ID.
2. Select the Delete payment ID check box to delete the payment ID information from all documents
    * This option should be used only when you want to remove or update Payment IDs for documents that got Payment IDs assigned. You will be offered a dialog to delete Payment ID from specific type of documents.  
3. Select Yes in the Update invoice payment ID field.
4. Click OK.
5. Click Yes.
6. Click Yes.
7. Click Yes.
8. Click Yes.

## View the payment ID
1. Go to Accounts receivable > Inquiries and reports > Invoices > Invoice journal.
2. Click Show filters.
3. Apply the following filters: Enter a filter value of "" on the "Payment ID" field using the "is not" filter operator.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
