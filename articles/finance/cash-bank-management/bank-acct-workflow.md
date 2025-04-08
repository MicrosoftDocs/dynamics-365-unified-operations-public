---
title: Bank account lifecycle management
description: Learn how to enable an approval workflow for bank accounts in the Cash and bank management module, including prerequisites and a step-by-step process.
author: EricWangChen
ms.author: wangchen
ms.topic: article
ms.date: 12/11/2024
ms.custom:
ms.reviewer: twheeloc
audience: Application User
ms.search.region: 
ms.search.validFrom: 2024-04-29
ms.search.form: 
ms.dyn365.ops.version:  
---

# Bank account lifecycle management

[!include [banner](../../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article explains how to enable an approval workflow for bank accounts in the **Cash and bank management** module.

## Prerequisites

- In the **Feature management** workspace, turn on the **(Preview) Bank account lifecycle management** feature.
- In **Cash and bank management workflows**, make sure that there's an active **Workflow for proposed bank account change** workflow.
  
>[!NOTE]
> Beginning in Dynamics 365 Finance version 10.0.43, the **(Preview) Bank account lifecycle management** feature is available to be enabled in PROD environments. 

## Activate an approval workflow

To enable a bank account approval workflow, follow these steps.

1. Go to **Cash and bank management** \> **Setup** \> **Cash and bank master data change setup**.
1. Set the following parameters:

    - **Change approval on modification** – Select this parameter to enable an approval workflow when a bank account is modified.
    - **Change approval on creation** – Select this parameter to enable an approval workflow when a bank account is created.
    - **Change history** – Select this parameter to save and review the bank account change history.
    - **Data entity behavior** – Select the approval workflow to use when a bank account is imported through data entities.

1. If you selected the **Change approval on modification** parameter in the last step, the **Protected fields** page is available. The fields on this page correspond to fields on bank accounts. Activate the fields that should trigger an approval workflow if users update their value on a bank account.
1. Select **Save**.

## View the change history

To view the bank account change history, follow these steps.

1. Go to **Cash and bank management** \> **Bank accounts** \> **Bank accounts**.
1. Select **Changes**.
1. Select **Change history**.
