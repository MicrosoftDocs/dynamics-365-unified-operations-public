---
title: One-time customers
description: Learn about one-time customers, including a step-by-step process for indicating that a customer is a one-time customer.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2024
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: CustTable
ms.dyn365.ops.version: Version 1611
---

# One-time customers

[!include [banner](../../includes/banner.md)]

This article provides information about one-time customers.  

A one-time customer is a customer who does not have a long-term relationship with your company. For one-time customers, you typically don't need to save information like address, contact, or tax exempt details. To indicate that a customer is a one-time customer, complete the following steps:

1.  Open the **All customers** page.
2.  Select a customer name to open the customer's record.
3.  On the **Miscellaneous details** FastTab, set the **One-time customer** option to **Yes**.
4.  Click **Save**.

**Note:** Before you can post transactions for a one-time customer, you must specify an account to use for one-time customers in the **One-time customer account** field on the **Accounts receivable parameters** page. For Spain, you can restrict users from creating project contracts for one-time customers. To do this, complete the following steps:

1.  Open the **Project management and accounting parameters** page.
2.  Set the **No one-time customer for project contracts** parameter to **True**.
3.  Click **Save**.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
