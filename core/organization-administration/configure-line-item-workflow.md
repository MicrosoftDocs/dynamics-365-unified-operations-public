---
# required metadata

title: Configure a line-item workflow
description: This topic explains how to configure a line-item workflow element.
author: sericks007
manager: AnnBe
ms.date: 2016-09-30 15 - 59 - 28
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
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 195833
ms.assetid: 3237347e-71d5-4569-bc9a-0d0fc9410b78
ms.search.region: Global
# ms.search.industry: 
ms.author: donaldc
ms.dyn365.ops.intro: 01-02-2016
ms.dyn365.ops.version: AX 7.0.0

---

# Configure a line-item workflow

This topic explains how to configure a line-item workflow element.

To configure a line-item workflow element, in the workflow editor, right-click the element, and then click **Properties** to open the **Properties** page. Then use the following procedures to configure the properties of the line-item workflow element.

## Name the lineitem workflow element
Follow these steps to enter a name for the line-item workflow element.

1.  In the left pane, click **Basic Settings**.
2.  In the **Name** field, enter a unique name for the line-item workflow element.

## Specify whether the same workflow is used to process all line items
Follow these steps to specify whether the same workflow is used to process all the line items on a document.

1.  In the left pane, click **Basic Settings**.
2.  If the same workflow should process all the line items on a document, click **Invoke a single workflow for all line-items**. Then select the workflow to use to process the line items.
3.  If a specific workflow should process line items that meet a specific set of conditions, click **Invoke a workflow for each line-item**. Then follow these steps to define the set of conditions:
    1.  Click **Add**.
    2.  Select the condition in the table.
    3.  On the **Condition name** tab, enter a name for the set of conditions that you're defining.
    4.  Click **Add condition** to enter a condition.
    5.  Enter any additional conditions that are required.
    6.  To verify that the set of conditions that you entered is configured correctly, click **Test**. On the **Test workflow condition** page, in the **Validate condition** area, select a record, and then click **Test**. The system evaluates the record to determine whether it meets the conditions that you defined. Click **OK** or **Cancel** to return to the **Properties** page.

    On the **Workflow** tab, select the workflow select the workflow to use to process line items that meet the set of conditions that you defined.


