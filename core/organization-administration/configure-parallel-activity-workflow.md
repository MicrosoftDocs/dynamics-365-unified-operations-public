---
# required metadata

title: Configure a parallel activity in a workflow
description: To configure a parallel activity, complete the following procedures in the workflow editor.
author: sericks007
manager: AnnBe
ms.date: 2016-09-30 15 - 56 - 21
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
# ms.reviewer: 71
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 195753
ms.assetid: e397823b-5bac-44aa-8e00-4bce790b5899
ms.search.region: Global
# ms.search.industry: 
ms.author: donaldc
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Configure a parallel activity in a workflow

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

3.  To configure each branch, see [Configure a parallel branch](http://axhelp.dynamics.com/en/wiki/configure-a-parallel-branch/).



