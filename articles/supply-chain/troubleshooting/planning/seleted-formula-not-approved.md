---
title: The selected formula number is not approved for a batch order.
description: "When you try to firm a planned order, you get the following error message: 'The selected formula number is not approved for a batch order'"
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

# The selected formula number is not approved for a batch order.

Error code: PRO2614

## Symptoms

When you try to firm a planned order, you get the following error message:
> The selected formula number is not approved for a batch order.

## Cause

The system validates the firming operation to make sure an approved formula is available for the active item. You probably need to approve the formula.

## Resolution

To approve a formula:

1. Go to **Product information management \> Bills of materials and formulas \> Formulas**.
1. Select the relevant formula.
1. On the Action Pane, open the **Formula** tab and, in the **Maintain** group, and select **Approve formula**.
1. The **Approve BOM or formula** dialog opens. Select an approver and then select **OK**.
