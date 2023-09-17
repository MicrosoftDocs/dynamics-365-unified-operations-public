--- 
# required metadata 
 
title: Create payments for a customer who have direct debit mandates
description: This procedure shows how to generate an ISO20022 direct debit payment file for a customer who has direct debit configured and an invoice to be paid. 
author: mrolecki
ms.date: 08/29/2018
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, LedgerJournalTable, LedgerJournalTransCustPaym, SysQueryForm, CustPaymProposalEdit, BankAccountTableLookUp   
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
# Create payments for a customer who have direct debit mandates

[!include [banner](../../includes/banner.md)]

This procedure shows how to generate an ISO20022 direct debit payment file for a customer who has direct debit configured and an invoice to be paid. Creating and posting an invoice is optional. Instead of having an invoice to be paid you can select a mandate in a journal prior to generating a payment file, to support a customer prepayment scenario.



The demo data company used to create this procedure is DEMF.



This is the fifth of five procedures that demonstrate the customer payment process using electronic reporting configurations. Before you can complete this task, you must complete the earlier tasks. You must first import customer payment electronic reporting configurations, configure method of payments, and set up your company and customer information. 


## Post a free text invoice with direct debit information
1. Go to Accounts receivable > Invoices > All free text invoices.
2. Click New.
3. In the Customer account field, enter or select a value.
    * For example, select DE-010.  
4. In the Method of payment field, enter or select a value.
    * For example. select Electronic.  
5. In the Direct debit mandate ID field, enter or select a value.
6. Click Add line.
7. In the Description field, type a value.
8. In the Main account field, specify the desired values.
9. In the Unit price field, enter a number.
10. Click Post.
11. Click OK.

## Create a payment
1. Go to Accounts receivable > Payments > Payment journal.
2. Click New.
3. In the Name field, enter or select a value.
4. Click Lines.
5. Click Payment proposal.
6. Click Create payment proposal.
7. Expand the Records to include section.
8. Click Filter.
9. In the list, select the row for the Customer transactions table and the Method of payment field.
    * You can apply any criteria for selecting customer transactions to pay. For this example, use Electronic as a method of payment to filter transactions.  
10. In the Criteria field, enter or select a value.
11. Click OK.
12. Click OK.
13. Click Create payments.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]