---
title: One-time customers
description: Learn how to manage one-time customers for Spain in Microsoft Dynamics 365 Finance.
author: AdamTrukawka
ms.author: atrukawk
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 07/11/2025
ms.reviewer: johnmichalak
ms.search.region: Spain
ms.search.validFrom: 2016-11-30
ms.search.form: CustTable
---

# One-time customers

[!include [banner](../../includes/banner.md)]

This article explains how to manage one-time customers for Spain in Microsoft Dynamics 365 Finance.

A one-time customer is a customer who does not have a long-term relationship with your company. For one-time customers, you typically don't need to save information like address, contact, or tax exempt details. 

To indicate that a customer is a one-time customer, follow these steps.

1. In Dynamics 365 Finance, go to the **All customers** page.
1. Select a customer name to open the customer's record.
1. On the **Miscellaneous details** FastTab, set the **One-time customer** option to **Yes**.
1. Select **Save**.

> [!NOTE]
> Before you can post transactions for a one-time customer, you must specify an account to use for one-time customers in the **One-time customer account** field on the **Accounts receivable parameters** page. For Spain, you can restrict users from creating project contracts for one-time customers. 

To restrict users from creating project contracts for one-time customers, follow these steps.

1. In Dynamics 365 Finance, go to the **Project management and accounting parameters** page.
1. Set the **No one-time customer for project contracts** parameter to **True**.
1. Select **Save**.






[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
