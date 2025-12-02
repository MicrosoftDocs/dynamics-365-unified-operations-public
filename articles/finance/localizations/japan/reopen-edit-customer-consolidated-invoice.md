---
title: Reopen and edit a customer consolidated invoice
description: Learn how to reopen and modify a confirmed customer consolidated invoice for Japan in Microsoft Dynamics 365 Finance.
author: kfend
ms.author: johnmichalak
ms.topic: how-to
ms.date: 05/02/2025
ms.reviewer: johnmichalak
ms.search.region: Japan
ms.search.validFrom: 2016-06-30
ms.search.form: CustConsInvoice_JP, SysQueryForm
ms.custom: 
  - bap-template
---

# Reopen and edit a customer consolidated invoice

[!include [banner](../../includes/banner.md)]

This article explains how to reopen and modify a confirmed customer consolidated invoice for Japan in Microsoft Dynamics 365 Finance.

In Japan, when you miss an invoice during the consolidation process, you must reopen the consolidated invoice to add the missed invoice. 

The following procedures walk you through how to reopen a confirmed consolidated invoice and modify it. Before you can complete procedures, you must have a confirmed consolidated invoice.

The procedures use the demo data company JPMF.

## Reopen a consolidated invoice

To reopen a consolidated invoice, follow these steps.

1. In Dynamics 365 Finance, go to **Accounts receivable \> Periodic tasks \> Consolidated invoice**.
1. In the list, find and select an invoice that is already confirmed.  
1. Select **Reopen**.

## Remove a sales order from a consolidated invoice

To remove a sales order from a consolidated invoice, follow these steps.

1. In the list, select the link in the selected row.
1. Select **Edit**.
1. In the list, mark the selected row.
1. Select **Remove**.

## Add sales orders and confirm the consolidated invoice

To add sales orders and confirm the consolidated invoice, follow these steps.

1. Select **Query invoice**.
1. Select **OK**.
1. Confirm that sales orders that were invoiced before the consolidation date are included.  
1. Select **Confirm**.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
