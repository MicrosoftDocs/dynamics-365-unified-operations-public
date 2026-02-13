--- 
title: Create payments for a customer who have direct debit mandates
description: This article describes how to generate an ISO20022 direct debit payment file for a customer who has direct debit configured and an invoice to be paid in Microsoft Dynamics 365 Finance. 
author: kailiang
ms.author: kailiang
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/27/2025
ms.reviewer: johnmichalak
ms.search.region: Global 
ms.search.validFrom: 2016-06-30
ms.search.form: CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, LedgerJournalTable, LedgerJournalTransCustPaym, SysQueryForm, CustPaymProposalEdit, BankAccountTableLookUp
---

# Create payments for a customer who have direct debit mandates

[!include [banner](../../includes/banner.md)]

This article describes how to generate an ISO20022 direct debit payment file for a customer who has direct debit configured and an invoice to be paid in Microsoft Dynamics 365 Finance. 

The following procedures show how to generate an ISO20022 direct debit payment file for a customer who has direct debit configured and an invoice to be paid. Creating and posting an invoice is optional. Instead of having an invoice to be paid, you can select a mandate in a journal prior to generating a payment file to support a customer prepayment scenario.

Before completing these procedures, you must first import customer payment electronic reporting configurations, configure method of payments, and set up your company and customer information. 

The following procedures use the DEMF demo company.

## Post a free text invoice with direct debit information

To post a free text invoice with direct debit information, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value. For example, select **DE-010**.  
1. In the **Method of payment** field, enter or select a value. For example. select **Electronic**.  
1. In the **Direct debit mandate ID** field, enter or select a value.
1. Select **Add line**.
1. In the **Description** field, enter a value.
1. In the **Main account** field, enter a value.
1. In the **Unit price** field, enter a price.
1. Select **Post**.
1. Select **OK**.

## Create a payment

To create a payment, follow these steps:

1. In Dynamics 365 Finance, go to **Accounts receivable \> Payments \> Payment journal**.
1. Select **New**.
1. In the **Name** field, enter or select a value.
1. Select **Lines**.
1. Select **Payment proposal**.
1. Select **Create payment proposal**.
1. Expand the **Records to include** section.
1. Select **Filter**.
1. In the list, select the row for the **Customer transactions** table and the **Method of payment** field. You can apply any criteria for selecting customer transactions to pay. For this example, use **Electronic** as a method of payment to filter transactions.  
1. In the **Criteria** field, enter or select a value.
1. Select **OK**.
1. Select **Create payments.**


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
