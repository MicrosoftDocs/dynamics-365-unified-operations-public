--- 
title: MY-00003 Manage customer debit and credit notes for GST
description: Learn how to print a Malaysian goods and services tax (GST) invoice for a credit note or debit note in Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak    
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: SalesTableListPage, SalesCreateOrder, SalesTable, PCProductLookup, CustInvoiceJourLookup_MY, TaxGroupLookup, TaxTmpWorkTrans, SalesEditLines,  CustFreeInvoice, CustTableLookup, CustPostInvoiceJob, SRSPrintDestinationSettingsForm
---

# MY-00003 Manage customer debit and credit notes for GST

[!include [banner](../../includes/banner.md)]

This article explains how to print a Malaysian goods and services tax (GST) invoice for a credit or debit notes in Microsoft Dynamics 365 Finance.

The following procedures walk you through how to print a Malaysian goods and services tax (GST) invoice for a credit note or debit note. You can print a GST invoice for a credit note or debit note from a sales order, free text invoice, purchase order, or project proposal but these procedures only shows how to print from a sales order and a free text invoice.

Before you can complete this procedure, you must select the **GST invoice** invoice type in general ledger parameters. You must be in the accounting receivable clerk role to complete the procedures.

The procedures use the demo data company MYMF.

## Create a debit note from a sales order

To create a debit note from a sales order, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Orders \> All sales orders**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Expand the **General** section.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. Select **OK**.
1. Select **Header**.
1. In the **Reason code** field, enter or select a value.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Lines**.
1. In the list, mark the selected row.
1. In the Item number field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the **Original invoice number** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Save**.
1. On the Action Pane, select **Sell**.
1. Select **Sales tax**.
1. Validate the calculated tax amount for the selected tax code.  
1. Select **OK**.
1. On the Action Pane, select **Invoice**.
1. Expand the **Parameters** section.
1. In the **Quantity** field, select an option.
1. In the **Print invoice** field, select **Yes**.
1. Select **OK**.
1. Select **Yes**.

## Create a credit note from a free text invoice

To create a credit note from a free text invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Invoices \> All free text invoices**.
1. Select **New**.
1. In the **Customer account** field, enter or select a value.
1. Select **Header**.
1. In the **Reason code** field, enter or select a value.
1. Select **Lines**.
1. In the **Description** field, enter a value.
1. In the list, mark the selected row.
1. In the **Main account** field, enter a value.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the **Original invoice** number field, enter or select a value.
1. Select **Save**.
1. Select **Sales tax**.
1. Validate the calculated negative tax amount for the tax code "AJS".  
1. Select **OK**.
1. Select **Post**.
1. In the **Print invoice** field, select **Yes**.
1. Select **OK**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
