---
title: Bank account lifecycle management
description: This article explains how to enable approval workflow for bank account in cash and bank management module.
author: EricWang
ms.date: 04/18/2024
ms.topic: article
audience: Application User
ms.reviewer: twheeloc
ms.search.region: 
ms.author: wangchen
ms.search.validFrom: 2024-04-29
ms.dyn365.ops.version: 
ms.custom: 
ms.search.form: 
---

# Bank account lifecycle management 

[!include [banner](../../includes/banner.md)]

This article explains how to enable an approval workflow for bank accounts in the Cash and bank management module. 

## Prerequisites

- Turn on feature **(Preview) Bank account lifecycle management** in the **Feature management** workspace.
- There is an active **Workflow for proposed bank account change** workflow in **Cash and bank management workflows**.

## Activate approval workflow

To enable bank account approval workflow, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank master data change setup**.
2. Four parameters are available:
   - **Change approval on modification** - select this parameter to enable approval workflow when a bank account is modified.
   - **Change approval on creation** - select this parameter to enable approval workflow when a bank account is created.
   - **Change history** - select this parameter to save and review the bank account change history.
   - **Data entity behavior** - Select the approval workflow when a bank account is imported through data entity.

3. **Protected fields** page is available when the **Change approval on modification** parameter is selected. Fields that are activated in this page triggers an approval workflow if the user updates the value of any of these fields on the bank account.
4. Click **Save**.

## View change history

To view the bank account change history, follow these steps.

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**
2. Click **Changes**. 
3. Click **Change history**.
