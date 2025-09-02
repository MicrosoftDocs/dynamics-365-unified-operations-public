---
title: Flexible sampling plans (preview)
description: Learn how to use flexible sampling plans to inspect randomly selected units of items from a lot. The results from the inspected sample determine whether the whole lot passes or fails testing.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: QMSInventFlexSamplingPlan, QMSInventFlexSamplingTrackingListPage
ms.topic: how-to
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Flexible sampling plans (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until 10.0.45 GA -->

A *flexible sampling plan* defines the criteria for inspecting randomly selected units of items from a lot. The results from the inspected sample determine whether the whole lot passes or fails testing. Typically, the number of units that are selected for inspection is proportional to the total size of the lot. The quality association that is defined for a plan identifies the activity for the inspection. For example, the activity might be a quality order to inspect a product before it's released to a customer on a sales order. Alternatively, it might be a quality order to inspect a manufactured product after production is completed.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Flexible sampling plans offer other features that you can use to modify your criteria over time, based on previous testing results.

- **Sampling size variations** – Flexible sampling lets you vary your item sampling over time, based on test findings. For example, for the first five rounds of testing, you inspect 50% of the receipt. If no quality failures are found in those rounds, you might decide to reduce the inspection sampling size for subsequent rounds to 10% of the receipt. Rounds identify the number of times that a test is performed at a specific level before testing moves to the next level in the testing plan. For example, if a level requires five rounds of testing, the assigned item sampling should be used for all five rounds before the testing moves to the next level. The next level might use a different item sampling.
- **Test group flexibility** – By using a flexible sampling plan, you can change a plan's current test group based on inspection results. The test group identifies the individual tests that are performed. For example, if previous testing results show minimal issues with the quality of receipts, you might change the test group to one that has a less stringent set of tests. You can also specify different test groups for different levels in a flexible sampling plan.
- **Skip lot inspections** – Skip lot inspections are an alternative to lot-by-lot inspections. They let you skip a set number of goods during testing. For example, a long-time supplier has demonstrated that the quality of their receipts is very good. Therefore, a quality manager might set up a flexible sampling plan to inspect a quantity of 10 units from this supplier and then skip the next 10 units. Receipts that don't require inspection are put away, and no quality order is generated.

Because flexible sampling plans give you the flexibility to perform lot-by-lot inspections instead of unit-by-unit inspections, and to use features such as sampling size variations, test group flexibility, and skip lot inspections, they help your company minimize time, costs, handling damage, and inspection errors.

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *Advanced quality management* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Set up flexible sampling plans

To set up flexible sampling plans, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Flexible sampling plans**.
1. On the Action Pane, use the following buttons as required:

    - **Add** – Add a new sampling plan.
    - **Delete** – Remove an existing plan. (You can't delete a plan if quality orders use it or activities are tracked against it.)
    - **Copy plan** – Copy content from another plan to the selected plan.
    - **View activities** – Open the **Flexible sampling plan activities** page, where you can view summaries and detailed information about the plan activities.

1. On the header of the new or selected sampling plan, set the following fields:

    - **Flexible sampling plan code** – Enter a name for the sampling plan.
    - **Name** – Enter a short description of the sampling plan.
    - **Alert role** – Select the security role that should be notified if a specified number of failures for a level is reached.
    - **Last level** – Select the level number for the last activity that is performed in this flexible sampling plan process.
    - **Approved** – Set the plan to the *Approved* state.

1. On the **Details** FastTab, use the grid to set up the plan. Use the buttons on the toolbar to add and remove lines in the grid. For new or selected lines, set the following fields:

    - **Level** – Select or review the level number that is assigned to the activity. The plan is processed in descending order of levels.
    - **Item sampling** – Select or review the item sampling. The item sampling determines the sampling size of the quality order for the activity. Examples include a 10% sampling or a 50-unit quantity sampling.
    - **Test group** – Select or review the test group. The test group determines the set of tests for the quality order for the activity.
    - **Rounds** – Set or review the number of testing rounds for the specific flexible sampling plan level that must pass quality order validation before testing can move to the next level. After you select a level in the **Last level** field, any **Rounds** value that you entered for that level is removed from the plan. In this way, the last level can continue indefinitely until several failures cause the plan to revert to a previous level.

        > [!NOTE]
        > Unless rounds are removed from the last level in the testing plan, all future tests remain at that level indefinitely, until the enough failures occurred so that the plan can revert to a previous level.

        For example, a quality association is set up to test purchase order registrations for a specific vendor. The vendor's flexible sampling plan requires that 10% of every registration is tested for five rounds. If you receive 100 units, a quality order is generated to test 10 of them. The quality order for the first registration passes. The second quality order then fails, but the next three quality orders pass. If round six passes, the first level in the plan is accomplished, because the number of passed rounds met the requirement.

    - **Time span (days)** – Enter or review the number of days within which the specified number of rounds must be completed. This field is optional. It works together with the **Rounds** field. If this field is set, testing can move to the next level only if the specified number of rounds pass inspection within the defined time span. For example, if you set the time span to 60 days and specify 10 rounds, testing can move to the next level in the plan only if 10 quality orders for the quality association pass within 60 days.
    - **Skip** – Select this checkbox to enable skip lot sampling, where only a fraction of the submitted lots is inspected. If you select this checkbox, you must enter the skip range in the **Test frequency** and **Out of frequency** fields.
    - **Test frequency** – If the **Skip** checkbox is selected, enter the first number in the skip range.
    - **Out of frequency** – If the **Skip** checkbox is selected, enter the last number in the skip range. 

        For example, the quality association is set for production order registrations. The flexible sampling plan that is associated with this reference type uses skip lot sampling. The **Test frequency** field is set to *1*, and the **Out of frequency** field is set to *5*. In this case, a quality order is generated to test one out of every five registrations. The system randomly selects one of the five registrations for testing, and the other four registrations are skipped.

    - **Number of fails** – Enter or review the number times that tests can fail before the flexible sampling plan reverts to a previous testing level. That level might be more or less restrictive than the current test, based on previous testing results. If the **Consecutive** checkbox is selected, the plan reverts to a previous level only if the failures are consecutive. For example, a vendor might initially define a plan to test 10 out of 40 receipts, to minimize the costs that are associated with testing. However, if recent testing results show a notable increase in failures, the current level might be replaced by a level that tests 20 out of 40 receipts. On the other hand, if the vendor's testing results show consistent quality and no failures, the current level might be replaced by a level that requires fewer failures.
    - **Consecutive** – Select this checkbox if the number of failures that is specified in the **Number of fails** field must be consecutive. If this checkbox is selected, and the number of consecutive failures is reached, the appropriate action is initiated, based on the specified fail action level and fail action code. For example, if the **Number of fails** field is set to *2*, and this checkbox is selected, two consecutive failures generate a predefined fail action, such as issuing an alert notification to the quality manager.
    - **Fail action level** – Enter or review the level of action that is initiated when the number that is specified in the **Number of fails** field is reached. This action indicates that more testing is required. If the **Consecutive** checkbox is also selected, the action is initiated only if the failures are consecutive. For example, if two consecutive quality orders fail at level 3, the defined action might require that testing starts over at level 1. You can assign any level that is currently defined in the flexible sampling plan, provided that it's equal to or lower than the current level.
    - **Fail action code** – Select the action code that defines the action that should be taken when the failure criteria are met or exceeded for the flexible sampling plan. All the actions return the test sampling process to the fail action level.

## Set up the quality association for the flexible sampling plan

Quality orders that use flexible sampling plans are set up so that they are automatically generated by using a quality association.

Learn more about how to manage quality associations in [Quality associations](quality-associations.md).

## View flexible sampling plan activities

To open the **Flexible sampling plan activities** page, select the **View activities** button on the Action Pane of the **Flexible sampling plan** page. The **Flexible sampling plan activities** page provides an overview of the quality associations where flexible sampling plans are used.

The following buttons are available on the **Flexible sampling plan activities** page:

- **Flexible sampling plan activity summary** – View a summary of activity for the selected flexible sampling plan.
- **Flexible sampling plan activity details** – View the specific details of the flexible sampling plan that you select. On this page, you can view how the activities in the plan are progressing through the levels of the plan. For each activity, the page indicates the quality order that is used. Color-coded related text describes the pass and fail criteria for each level. For example, a red color indicates that a quality order failed. If a quality order fails, the page also indicates whether the test reverted to a previous level that requires more testing. From this page, you can also open pages that include summaries and details about activities, and view charts that show statistics about the performance of quality order testing.
- **Flexible sampling plans** – View the specific activity details for the flexible sampling plan that you select. You can also create a new flexible sampling plan from this page.
