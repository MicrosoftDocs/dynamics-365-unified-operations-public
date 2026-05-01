---
title: Configure line-item workflows
description: Learn about how to configure a line-item workflow element, including outlines on naming line-item workflow elements and specifying whether workflows process all line items.
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
ms.assetid: 3237347e-71d5-4569-bc9a-0d0fc9410b78
---

# Configure line item workflows

[!include [banner](../includes/banner.md)]

This article explains how to configure a line item workflow element.

To configure a line item workflow element, in the workflow editor, right-click the element, and then select **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the line item workflow element.

## Name the line item workflow element

Follow these steps to enter a name for the line item workflow element.

1. In the left pane, select **Basic Settings**.
2. In the **Name** field, enter a unique name for the line item workflow element.

## Specify whether the same workflow processes all line items

Follow these steps to specify whether the same workflow processes all the line items on a document.

1. In the left pane, select **Basic Settings**.
1. If the same workflow should process all the line items on a document, select **Invoke a single workflow for all line-items**. Then select the workflow to use to process the line items.
1. If a specific workflow should process line items that meet a specific set of conditions, select **Invoke a workflow for each line-item**. Then follow these steps to define the set of conditions:

    1. Select **Add**.
    1. Select the condition in the table.
    1. On the **Condition name** tab, enter a name for the set of conditions that you're defining.
    1. Select **Add condition** to enter a condition.
    1. Enter any additional conditions that are required.
    1. To verify that the set of conditions that you entered is configured correctly, select **Test**. On the **Test workflow condition** page, in the **Validate condition** area, select a record, and then select **Test**. The system evaluates the record to determine whether it meets the conditions that you defined. Select **OK** or **Cancel** to return to the **Properties** page.

    On the **Workflow** tab, select the workflow to use to process line items that meet the set of conditions that you defined.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]

