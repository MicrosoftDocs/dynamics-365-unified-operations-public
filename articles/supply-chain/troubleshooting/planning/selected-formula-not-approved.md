---
title: Selected formula number isn't approved for a batch order
description: When you try to firm a planned order, you receive an error message that states that the selected formula number isn't approved for a batch order.
author: ankubik
ms.date: 06/10/2021
ms.topic: troubleshooting
ms.search.form: ReqTransPo
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: ankubik
ms.search.validFrom: 2021-06-10
ms.dyn365.ops.version: 10.0.20
---

# Selected formula number isn't approved for a batch order

Error code: PRO2614

## Symptoms

When you try to firm a planned order, you receive the following error message:

> The selected formula number is not approved for a batch order.

## Cause

The system validates the firming operation to make sure that an approved formula is available for the active item. You must probably approve the formula.

## Resolution

To approve a formula, follow these steps.

1. Go to **Product information management \> Bills of materials and formulas \> Formulas**.
1. Select the relevant formula.
1. On the Action Pane, on the **Formula** tab, in the **Maintain** group, select **Approve formula**.
1. In the **Approve BOM or formula** dialog box, select an approver, and then select **OK**.
