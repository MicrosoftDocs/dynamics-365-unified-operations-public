---
# required metadata

title: Configure conditional decisions in a workflow
description: Use the following procedure to configure the properties of a conditional decision.
author: ChrisGarty
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 195703
ms.assetid: cd5554a4-210c-4c20-a7d3-4b1563c2b5df
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure conditional decisions in a workflow

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

Use the following procedure to configure the properties of a conditional decision.

A conditional decision is a point at which a workflow divides into two branches. To configure a conditional decision, in the workflow editor, right-click the conditional decision, and then click **Properties** to open the **Properties** form.

## Name a decision

Follow these steps to enter a name for a conditional decision.

1. In the left pane, click **Basic Settings**.
2. In the **Name** field, enter a unique name for the conditional decision.

## Set conditions

The system determines which branch is used by evaluating the submitted document to determine whether it meets specific conditions.

1. In the left pane, click **Basic Settings**.
2. Click **Add condition**.
3. Enter a condition.
4. Enter additional conditions, if they are required.
5. To verify that the conditions that you entered are configured correctly, complete the following steps:

    1. Click **Test** to open the **Test workflow condition** form.
    2. Select a record in the **Validate condition** area of the form.
    3. Click **Test**. The system evaluates the record to determine whether it meets the conditions that you defined.
    4. Click **OK** or **Cancel** to return to the **Properties** form.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
