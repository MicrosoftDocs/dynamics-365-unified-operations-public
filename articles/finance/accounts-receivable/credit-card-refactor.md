---
# required metadata

title: Credit card payment refactoring
description: This article provides information about credit card payment refactoring.
author: sunfzam
ms.date: 02/14/2023
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: VendorInvoiceWorkspace, VendInvoiceInfoListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: ["13971", "intro-internal"]
ms.assetid: 0ec4dbc0-2eeb-423b-8592-4b5d37e559d3
ms.search.region: Global
# ms.search.industry: 
ms.author: zezhangzhao
ms.search.validFrom: 2022-09-28
ms.dyn365.ops.version: 

---

#  Credit card payment refactoring

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This article provides information about credit card payment refactoring.

Cards payment is a typical payment scenario in retail industry. In Dynamics 365 Finance, although it looks like a single step from process perspective, it is actually composed by several steps: creating customer invoice for the Sales Order, issuing cards payment (such as debit card, credit card, gift card), generate payment posting in general ledger. 

 

In old design, all the steps are done within one transaction. Since cards payment are external transactions, when failure occurs during the course, system cannot rollbackedrollback the transaction and result in inconsistent payment in system. 

 

Starting from version 10.0.32, the whole cards payment process is split into several stages: customer invoice creation and posting, credit card capture/refund, payment journal posting and remaining amount authorization.  Processing status of each stage is centrally logged and monitored per invoice and sales order. In case of failure in any steps after customer invoice is posted, from the central page, user can check failure reason and recover payment process from where it fails. 

Prerequisites:  

In the Feature management workspace, turn on feature “Improve cards payment processing flow in customer payment”.  

Go to Accounts receivable > Setup > Accounts receivable parameters. On the Credit card tab, on the Setup FastTtab, set the Cards payment status monitoring to Yes.  

## Steps to   

Go to Accounts receivable > Invoices > Open customer invoices, check menu item Incomplete cards payment under Invoice tab.  

If the invoice is selected and not related to the cards payment, the menu item cannot be clicked.  

If the invoice is selected and related to the cards payment, the menu item can be clicked and will jump to the Incomplete cards payment page with filter for the specific invoice.  

If no invoice is selected, the menu item can be clicked and will jump to the Incomplete cards payment page without filter. All incomplete cards payment process will be listed.  

  

Actions to deal with incomplete cards payment 

Resume the incomplete cards payment  

In the Incomplete cards payment page, select or highlight a line, click Resume button. The cards payment process will restart from the last failed stage.  

  

Terminate the incomplete cards payment  

In the Incomplete cards payment page, select or highlight a line, click Terminate button. The cards payment process will be manually terminated, user need to manually do the following steps in the system.  

  

View history in the incomplete cards payment  

In the Incomplete cards payment page, select or highlight a line, click View history button. Side bar viewer will pop up, list all the processed payment stage. Click the payment stage, corresponding execution log will be listed.  
