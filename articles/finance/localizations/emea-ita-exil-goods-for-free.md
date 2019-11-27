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

## Set up 
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

Define...

## Use...

### Post

When you post...

> [!NOTE]
> Warning...
