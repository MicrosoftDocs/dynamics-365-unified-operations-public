---
title: Bank account lifecycle management
description: This article explains how to enable approval workflow for bank account in cash and bank management module.
author: EricWang
ms.date: 04/18/2024
ms.topic: article
ms.prod: 
ms.technology: 
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

This article explains how to enable approval workflow for bank account in cash and bank management module. 

## Prerequisites

- Turn on feature **(Preview) Bank account lifecycle management** in Feature management workspace.
- There is an active version of workflow type **Workflow for proposed bank account change** in **Cash and bank management workflows setup**.

## Activate approval workflow

To enable bank account approval workflow, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank master data change setup**.
2. Four parameters are available:
   - **Change approval on modification**: Turn on this parameter if you want to enable approval workflow when the bank account is modified.
   - **Change approval on creation**: Turn on this parameter if you want to enable approval workflow when the bank account is created.
   - **Change history**: Turn on this parameter if you want to save and review the bank account change history.
   - **Data entity behavior**: Select the approval workflow behavior you want when the bank account is imported through data entity.

3. **Protected fields** form will be available if you turn on parameter **Change approval on modification**. Fields that are activated in this form will trigger an approval workflow if the user updates the value of any of these fields on the bank account.
4. **Save** the setup.

## View change history

To view the bank account change history, follow these steps.

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**
2. Click **Changes** on the navigation bar
3. Click **Chang history**