---
title: Create checks that have Blank status 
description: Learn about how to create blank checks for a bank account, including a step-by-step process that details creating a blank check, which can't be deleted or reused.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 03/24/2023
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2019-09-17
ms.search.form: BankChequeTable
ms.dyn365.ops.version: AX 10.0.5
ms.assetid: d7e22bd8-fd0d-47e1-843f-45ab0193ff8d
---

# Create checks that have Blank status

[!include [banner](../includes/banner.md)]

This article explains how to create blank checks. For example, you might create a blank check to record a check that has been damaged and can't be used for payment.

On the **Checks** page, you perform maintenance tasks for checks. For example, you can create new check numbers and delete checks. You can also create checks that have a status of **Blank**. After blank checks are created, they can't be deleted or reused in the system.

> [!NOTE]
> This feature is available on the **Checks** page only if you turn on the **Create checks with a blank status on the Checks page** feature on the **Feature management** page. If the feature isn't turned on, checks that have **Blank** status can be created only from the **Payment by check** dialog box during the payment generation process in Accounts payable.

1. Go to **Cash and bank management \> Bank accounts \> Bank accounts**. 
2. On the Action Pane, on the **Manage payments** tab, in the **Related information** group, select **Checks**. Alternatively, go to **Cash and bank management \> Inquiries and reports \> Checks**.
3. To create checks that have **Blank** status, on the Action pane, select **Create blank checks**. While the blank checks are created, the associated bank account is temporarily deactivated. This behavior reduces the risk that payments will be generated at the same time that blank checks are created. When the processing is completed, the associated bank account is reactivated.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
