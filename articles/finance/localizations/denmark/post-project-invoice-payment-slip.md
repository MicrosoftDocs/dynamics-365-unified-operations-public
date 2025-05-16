--- 
title: Post a project invoice with a payment slip
description: This article describes how to post a project invoice with a payment slip in a specified format in Denmark with Microsoft Dynamics 365 Finance. 
author: EvgenyPopovMBS
ms.author: evgenypopov
ms.topic: how-to
ms.date: 03/11/2025
ms.reviewer: johnmichalak 
ms.search.region: Denmark
ms.search.validFrom: 2016-06-30
ms.search.form: CustTable, ProjProjectContractsListPage, ProjInvoiceTableCreate, ProjInvoiceTable, ProjProjectsListPage, ProjTableCreate, ProjGroupLookUp, ProjTable,  ProjTransOnAcc, ProjInvoiceProposalListPage, ProjInvoiceProposalCreateLines, ProjInvoiceProposalDetail, ProjInvoiceEditLines  
ms.custom: 
  - bap-template
---

# Post a project invoice with a payment slip

[!include [banner](../../includes/banner.md)]

This article describes how to post a project invoice with a payment slip in a specified format in Denmark with Microsoft Dynamics 365 Finance. 

You can post a project invoice with a payment slip attachment in a specified format. The payment slip is printed with the creditor identification number and invoice number to identify the payment. This functionality is available for legal entities whose primary address is in Denmark.

Before you can complete this procedure, you must first set up a payment slip format and set up payment slips for customer invoices. This procedure was created using the demo data company DEMF.

To post a project invoice with a payment slip, follow these steps. 

1. In Dynamics 365 Finance, go to **Accounts receivable \> Customers \> All customers**.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Expand or collapse the **Invoice and delivery** section.
1. Select **Edit**.
1. In the On a project invoice field, select an option. Select the **None – Do not print a payment slip** option if the payment amount is in a currency other than Danish kroner (DKK). Print an FIK 751 payment slip if you intend to write the payment amount and due date on the payment slip manually. Print an FIK 752 payment slip if you intend to use a computer-generated payment slip with a preprinted payment amount and due date.     
1. Select **Save**.
1. Select the **TabPageGrid** tab.
1. Close the page.
1. Go to **Project management and accounting \> Projects \> Project contracts**.
1. Select **New**.
1. In the **Name** field, enter a value.
1. In the **Funding source** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Sales currency** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. In the **Sales currency** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record. The payment slip can be printed only for a project invoice with the currency Danish kroner (DKK).  
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Select **Save**.
1. Go to **Project management and accounting \> Projects \> All projects**.
1. Select **New**.
1. In the **Project type** field, select an option.
1. In the **Project name** field, enter a value.
1. In the **Project group** field, select the drop-down button to open the lookup.
1. In the list, select the link in the selected row.
1. In the **Project contract ID** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **Create project**.
1. On the Action Pane, select **Project**.
1. Select **Project stage**.
1. Select **In process**.
1. Select **OK**.
1. Select **Save**.
1. On the Action Pane, select **Manage**.
1. Select **On-account transactions**.
1. Select **New**.
1. In the list, mark the selected row.
1. In the **Sales price** field, enter a number.
1. Select **Save**.
1. Close the page.
1. On the Action Pane, select **Manage**.
1. Select **Project invoice** proposals.
1. Select **New**.
1. Select **Invoice proposal**.
1. In the **Project** field, select the drop-down button to open the lookup.
1. Close the page.
1. In the **Project contract** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the selected row.
1. Select **OK**.
1. Select **Post**.
1. Select **OK**.
1. Select **OK**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
