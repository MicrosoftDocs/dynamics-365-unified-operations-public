--- 
title: MY-00011 02 Generate Customer Debit Note for Project sales (November 2016)
description: Learn how to create and print a project debit note for GST in Malaysia with Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak   
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: ProjProjectsListPage, SalesCreateOrder, SalesTable, CustInvoiceJourLookup_MY, TaxGroupLookup, ProjJournalTable, ProjJournalTransEmpl, ResourceLookup, ProjInvoiceProposalCreateLines, ProjInvoiceProposalTransTypeLookup, ProjInvoiceProposalDetail, ProjInvoiceEditLines 
ms.custom: 
  - bap-template
---

# MY-00011 02 Generate Customer Debit Note for Project sales (November 2016)

[!include [banner](../../includes/banner.md)]

This article explains how to create and print a project debit note for GST in Malaysia with Microsoft Dynamics 365 Finance. 

To complete the following procedures, you must select **GST invoice** invoice type in Dynamics 365 Finance at **General ledger \> Ledger setup \> General ledger parameters**, and you must be in the project accountant role.

The procedures use the demo data company MYMF.

## Create a project sales debit note

To create a project sales debit note, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting \> Projects \> All projects**.
1. On the Action Pane, select **Manage**.
1. In the **New** group on the Action Pane, select **Item task**.
1. Select **Sales order**.
1. Expand the **General** section.
1. In the **Site** field, enter or select a value.
1. In the **Warehouse** field, enter or select a value.
1. Select **OK**.
1. On the Action Pane, select **Options**.
1. Select **Change view**.
1. Select **Header view**.
1. In the **Reason code** field, enter or select a value.
1. Select **Save**.
1. Select **Change view**.
1. Select **Line view**.
1. In the **Item number** field, enter or select a value.
1. In the **Quantity** field, enter a number.
1. In the **Unit price** field, enter a number.
1. In the list, mark the selected row.
1. In the **Original invoice number** field, enter or select a value.
1. Expand the **Line details** section.
1. Select the **Setup** tab.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Save**.
1. Close the page.

## Create and post an hour journal

To create and post an hour journal, follow these steps.

1. On the Action Pane, select **Project**.
1. Select **Hour**.
1. Select **New**.
1. Select **Lines**.
1. Select **New**.
1. In the **Resource** field, enter or select a value.
1. In the **Hours** field, enter a number.
1. Select the **General** tab.
1. In the Cost price field, enter a number.
1. In the **Sales price** field, enter a number.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Save**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.

## Create and post invoice proposal

To create and post invoice proposal, follow these steps.

1. On the Action Pane, select **Manage**.
1. Select **Invoice proposa**.
1. In the **End date** field, enter a date.
1. In the **Transaction types** field, enter or select a value.
1. Select **Search**.
1. Select **Select all**.
1. Select **OK**.
1. In the **Reason code** field, enter or select a value.
1. Expand the **Invoice proposal transactions** section.
1. Select the **Hour** tab.
1. In the list, mark the selected row.
1. In the **Original invoice number** field, enter or select a value.
1. Select **Save**.
1. Select **Post**.
1. In the **Print invoice** field, select **Yes**.
1. Select **OK**.
1. Select **OK**.
1. Validate the debit note report.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
