--- 
title: MY-00011 03 Generate Customer Credit note for Project sales
description: Learn how to create and print a project credit note for GST in Malaysia with Microsoft Dynamics 365 Finance.
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 05/29/2025
ms.reviewer: johnmichalak
ms.search.region: Malaysia
ms.search.validFrom: 2016-06-30
ms.search.form: ProjProjectsListPage, ProjJournalTable, ProjJournalTransEmpl, ResourceLookup, TaxGroupLookup, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, CustInvoiceJourLookup_MY, TaxTmpWorkTrans, ProjInvoiceEditLines,  SysOperationSandboxForm
ms.custom: 
  - bap-template
---

# MY-00011 03 Generate Customer Credit note for Project sales

[!include [banner](../../includes/banner.md)]

This article explains how to create and print a project credit note for GST in Malaysia with Microsoft Dynamics 365 Finance.

To complete the following procedures, you must select **GST invoice** invoice type in Dynamics 365 Finance at **General ledger \> Ledger setup \> General ledger parameters**, and you must be in the project accountant role.

The procedures use the demo data company MYMF.

## Create a project credit note

To create a project credit note, follow these steps.

1. In Dynamics 365 Finance, go to **Project management and accounting \> Projects \> All projects**.
1. On the Action Pane, select **Project**.
1. Select **Hour**.
1. Select **New**.
1. Select **Lines**.
1. Select **New**.
1. In the **Resource** field, enter or select a value.
1. In the **Hours** field, enter a number.
1. Select **Save**.
1. Select the **General** FastTab.
1. In the **Cost price** field, enter a number.
1. In the **Sales price** field, enter a number.
1. In the **Sales tax group** field, enter or select a value.
1. In the **Item sales tax group** field, enter or select a value.
1. Select **Save**.
1. Select **Post**.
1. Select **OK**.
1. Close the page.

## Create and post an invoice proposal

To create and post an invoice proposal, follow these steps.

1. On the Action Pane, select **Manage**.
1. Select **Invoice proposal**.
1. In the **End date** field, enter a date.
1. Select **Search**.
1. Select **Select all**.
1. Select **OK**.
1. In the **Reason code** field, enter or select a value.
1. In the **Original invoice number** field, enter or select a value.
1. Select **Sales tax**.
1. Validate the calculated negative tax amount for the tax code "SR".
1. Select **OK**.
1. Select **Post**.
1. In the **Print invoice** field, select **Yes**.
1. Select **OK**.
1. Select **OK**.
1. Verify that the information on credit note report is correct.  



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
