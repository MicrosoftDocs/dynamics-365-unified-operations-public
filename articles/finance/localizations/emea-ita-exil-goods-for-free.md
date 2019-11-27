---
# required metadata

title: Tax invoice for goods delivered for free
description: Tax invoice for goods delivered for free
author: ilkond
manager: AnnBe
ms.date: 10/29/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: mrolecki
ms.search.validFrom: 2019-11-01
ms.dyn365.ops.version: 10.0.8

---

# Tax invoice for goods delivered for free

[!include [banner](../includes/banner.md)]

This topic describes how to manage goods delivered for free. Functionality makes possible to generate invoices with the words "free invoice" and the total of invoice to be equal to the tax amount only. Operation requires setup of delivery reasons to be used in the sales order. There are two cases depending on who pays taxes on these items:
- your company pays the sales tax, the system will generate a self-invoice and will also generate accounting entries for payment
- customer pays the sales tax
Delivery reason setup determines which case you use.



## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Tax invoice for goods delivered for free** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up Summary update parameters
To do this, delivery reason must be available for both the packing slip and the invoice.
1.	Go to **Accounts receivable > Setup > Accounts receivable parameters**
2.	In the tab **Summary update** click on **Summary update parameters**
3.	The  **Delivery reason** summary update parameter must be selected for “Packing slip” and “Invoice” documents. To do this, select the "Invoice” tab and use the right-arrow to move  "Delivery reason" to Selected. Repeat the same in the "Packing slip" tab.

## Set up Sales for free account
To set up the accounting account for sales for free:
1. Go to **Inventory management > Setup > Posting > Posting**
2. Select  **Sales for free** radio button
3. Set up **Main account** selecting required relations and account codes.

## Set up Miscellaneous charges

Miscellaneous charges are not always desired when issuing free sales invoices, to exclude them when they are generated automatically enable the flag “Exclude charge in free invoice” in the charge codes.
To do this:
1. Go to **Accounts receivable> Charges setup > Charges code**
2. Create or select **Charges code**
2. Enable **Exclude charge in free invoices** parameter

## Set up Delivery reasons
1. Go to **Sales and marketing > Setup > Distribution > Reasons for delivery**
2. Enable **Goods for free** flag
3. Select the customer account representing your company, in the **Invoice account** field 
4. Set the cash term of payment in the **Term of payment** field 

> [!NOTE]
> The company issues a self-invoice to account required taxes for goods delivered for free. In addition to the invoice posting, the accounting entries for payment must be also generated. To enable that process you must have a customer account that represents your company. In this case, the invoice account on a sales order will be defaulted to the company customer account, and conseqently the issued invoice will be a self-invoice. When you specify cash term of payments the payment occurs, in addition to the self-invoice. Finally the customer transaction is closed and the amount is posted to the cash account specified in the term of payment. This field will be also defaulted in a sales order header. When your customer pays taxes, then it is necessary to leave **Invoice account** and **Term of payment** empty.

## Posting Tax invoice for goods delivered for free

When you create a sales order for goods delivery for free, the specified delivery reason  will determine creation of the self-invoice for your company or your customer. If you use cash payment term, the payment accounting entries will also be created when you post the sales invoice.

