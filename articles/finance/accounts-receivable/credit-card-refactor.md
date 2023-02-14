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

Cards payment is a typical payment scenario in retail industry. In Dynamics 365 Finance, although it looks like a single step, it is composed of several steps: 
1. Create customer invoice for the Sales Order 
2. Issue cards payment (such as debit card, credit card, gift card) 
3. Post payment in general ledger 

In releases prior to Dynamics 365 Finance 10.0.32, all of the steps are done within one transaction. Cards payment are external transactions and when an error occurs, the transaction can't be rolled back and result in inconsistent payments. 

 

Beginning in version 10.0.32, the cards payment process is split into several stages: 
 - Create and post the customer invoice 
 - Credit card capture/refund 
 - Post the payment journal  
 - Remaining payment amount authorization  
 
The status of each stage is logged and monitored per invoice and sales order. In case of an error in any steps after the customer invoice is posted, users can check the failure reason and recover the payment process from the point it fails. 

## Prerequisites  

1. In **Feature management** workspace, turn on feature **Improve cards payment processing flow in customer payment**.  
2. Go to **Accounts receivable > Setup > Accounts receivable parameters**. 
3. On the **Credit card** tab, on the **Setup** FastTtab, set the **Cards payment status monitoring** to **Yes**.  

## View incomplete cards payments  

1. Go to **Accounts receivable > Invoices > Open customer invoices**, select **Incomplete cards payment** on the **Invoice** tab.
2. If the selected invoice is not related to the cards payment, the item can't be clicked. 
3. If the selected invoice is related to the cards payment, the menu item can be clicked and will go to the **Incomplete cards payment** page.
4. If no invoice is selected, the menu item can be clicked and the **Incomplete cards payment page** will open. All incomplete cards payments will be listed.  

  

## Resume incomplete cards payment
1. Go to **Incomplete cards payment**, select or highlight a line, click **Resume**. 
2. The cards payment process will restart from the last failed stage.  

## Terminate the incomplete cards payment 
1. Go to **Incomplete cards payment**, select or highlight a line, click **Terminate**. 
2. The cards payment process will be manually terminated. 


The user will need to manually follow these steps:   
1. Go to **Incomplete cards payment**, select or highlight a line, click **View history**. 
2. Side bar viewer will pop up and lists all of the processed payment stages. 
3. Click **Payment stage** and corresponding execution log will display.  
