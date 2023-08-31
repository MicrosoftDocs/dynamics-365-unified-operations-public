---
# required metadata

title: Configure line-item workflows
description: This article explains how to configure a line-item workflow element.
author: ChrisGarty
ms.date: 11/03/2017
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
ms.custom: 195833
ms.assetid: 3237347e-71d5-4569-bc9a-0d0fc9410b78
ms.search.region: Global
# ms.search.industry: 
ms.author: cgarty
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure line-item workflows

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

This article explains how to configure a line-item workflow element.

To configure a line-item workflow element, in the workflow editor, right-click the element, and then click **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the line-item workflow element.

## Name the line-item workflow element

Follow these steps to enter a name for the line-item workflow element.

1. In the left pane, click **Basic Settings**.
2. In the **Name** field, enter a unique name for the line-item workflow element.

## Specify whether the same workflow is used to process all line items

Follow these steps to specify whether the same workflow is used to process all the line items on a document.

1. In the left pane, click **Basic Settings**.
2. If the same workflow should process all the line items on a document, click **Invoke a single workflow for all line-items**. Then select the workflow to use to process the line items.
3. If a specific workflow should process line items that meet a specific set of conditions, click **Invoke a workflow for each line-item**. Then follow these steps to define the set of conditions:

    1. Click **Add**.
    2. Select the condition in the table.
    3. On the **Condition name** tab, enter a name for the set of conditions that you're defining.
    4. Click **Add condition** to enter a condition.
    5. Enter any additional conditions that are required.
    6. To verify that the set of conditions that you entered is configured correctly, click **Test**. On the **Test workflow condition** page, in the **Validate condition** area, select a record, and then click **Test**. The system evaluates the record to determine whether it meets the conditions that you defined. Click **OK** or **Cancel** to return to the **Properties** page.

    On the **Workflow** tab, select the workflow select the workflow to use to process line items that meet the set of conditions that you defined.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
