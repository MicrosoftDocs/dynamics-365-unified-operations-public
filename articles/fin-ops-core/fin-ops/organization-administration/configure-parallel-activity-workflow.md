---
title: Configure parallel activities in a workflow
description: Learn about how to configure a parallel activity, complete the following procedures in the workflow editor, including an overview on naming a parallel activity.
author: ChrisGarty
ms.author: cgarty
ms.topic: how-to
ms.date: 03/10/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 6d0656df-b5af-4001-96e6-6f0fcc44d022
---

# Configure parallel activities in a workflow

[!include [banner](../includes/banner.md)]

To configure a parallel activity, use the workflow editor.

A parallel activity consists of workflow branches that run at the same time.

## Name a parallel activity

Follow these steps to enter a name for a parallel activity.

1. Right-click the parallel activity, and then select **Properties** to open the **Properties** form.
1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the parallel activity.
1. Select **Close**.

## Configure the branches of a parallel activity

Follow these steps to add and configure the branches of this parallel activity.

1. Double-click the parallel activity to display the branches of the parallel activity.
1. To add a branch, drag the **Branch** element from the **Workflow elements** area to an insertion point on the canvas. The following figure shows an insertion point.

    :::image type="content" source="./media/workflow_insertionpoint.gif" alt-text="Screenshot of the insertion point on the workflow canvas.":::

    > [!NOTE]
    > The order of the branches doesn't matter because all the branches of a parallel activity run at the same time.

1. To configure each branch, see [Configure parallel branches in a workflow](configure-parallel-branch-workflow.md).


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
