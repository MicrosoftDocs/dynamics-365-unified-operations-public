---
# required metadata

title: Configure a parallel activity in a workflow
description: To configure a parallel activity, complete the following procedures in the workflow editor.
author: sericks007
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 195753
ms.assetid: 6d0656df-b5af-4001-96e6-6f0fcc44d022
ms.search.region: Global
# ms.search.industry: 
ms.author: donaldc
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure a parallel activity in a workflow

[!include[banner](../includes/banner.md)]


To configure a parallel activity, complete the following procedures in the workflow editor.

A parallel activity consists of workflow branches that run at the same time.

## Name a parallel activity
Follow these steps to enter a name for a parallel activity.
1.  Right-click the parallel activity, and then click **Properties** to open the **Properties** form.
2.  In the left pane, click **Basic Settings**.
3.  In the **Name** field, enter a unique name for the parallel activity.
4.  Click **Close**.

## Configure the branches of a parallel activity
Follow these steps to add and configure the branches of this parallel activity.
1.  Double-click the parallel activity to display the branches of the parallel activity.
2.  To add a branch, drag the **Branch** element from the **Workflow elements** area to an insertion point on the canvas. The following figure shows an insertion point.![Insertion point](./media/workflow_insertionpoint.gif)
    | **Note**                                                                                                         |
    |------------------------------------------------------------------------------------------------------------------|
    | The order of the branches is not important because all the branches of a parallel activity run at the same time. |

3.  To configure each branch, see [Configure a parallel branch](configure-parallel-branch-workflow.md).





