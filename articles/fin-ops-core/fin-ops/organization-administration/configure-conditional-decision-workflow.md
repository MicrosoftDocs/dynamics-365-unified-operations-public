---
title: Configure conditional decisions in a workflow
description: Learn about how to configure conditional decisions in a workflow, including outlines on naming decisions and setting conditions.
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
ms.assetid: cd5554a4-210c-4c20-a7d3-4b1563c2b5df
---

# Configure conditional decisions in a workflow

[!include [banner](../includes/banner.md)]


Use the following procedure to configure the properties of a conditional decision.

A conditional decision is a point where a workflow divides into two branches. To configure a conditional decision, right-click the conditional decision in the workflow editor, and then select **Properties** to open the **Properties** form.

## Name a decision

Follow these steps to enter a name for a conditional decision.

1. In the left pane, select **Basic Settings**.
1. In the **Name** field, enter a unique name for the conditional decision.

## Set conditions

The system determines which branch to use by evaluating the submitted document to see if it meets specific conditions.

1. In the left pane, select **Basic Settings**.
1. Select **Add condition**.
1. Enter a condition.
1. Enter additional conditions, if needed.
1. To verify that the conditions you entered are configured correctly, complete the following steps:

    1. Select **Test** to open the **Test workflow condition** form.
    1. Select a record in the **Validate condition** area of the form.
    1. Select **Test**. The system evaluates the record to see if it meets the conditions you defined.
    1. Select **OK** or **Cancel** to return to the **Properties** form.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
