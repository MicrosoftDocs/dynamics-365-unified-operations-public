---
title: Flexible sampling plans (preview)
description: 
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
<!-- KFM: Preview until further notice -->

A flexible sampling plan defines the criteria for inspecting units of items that are randomly picked from a lot to determine if the entire lot passes or fails based on the results of the inspected samplings. Typically, the number of units chosen for inspection is proportional to the total size of the lot based on rational criterion. The quality association defined for a plan identifies the activity to be inspected. For example, the activity might be a quality order to inspect a product before it is released to a customer in a sales order, or it could be a quality order to inspect a manufactured product upon completion of production.

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

Flexible sampling plans offer other features that allow you to modify your criteria over time based on prior testing results.

- **Sampling size variations** – Flexible sampling provides the ability to vary your item sampling over time based on test findings. For example, for the first five rounds of testing, you inspect 50% of the receipt. Assuming no quality failures were found in those rounds, you may decide to reduce the inspection sampling size to only 10% of the receipt for subsequent rounds. Rounds identify the number of times that a test is performed at a specific level before moving to the next level in the testing plan. For example, if a level requires 5 rounds of testing, then the assigned item sampling should be used for all 5 rounds before moving to the next level, which may use a different item sampling.

- **Test group flexibility** – Using a flexible sampling plan, you can change a plan's current test group, which identifies the individual tests performed, to a different test group based on inspection results. For example, if prior testing results show minimal problems in the quality of receipts, you might choose to change the test group to a less stringent set of tests. You can also specify different test groups for different levels in a flexible sampling plan.

- **Skip lot inspections** – Skip lot inspections, which are an alternative to lot-by-lot inspections, allow you to skip a set number of goods during testing. For example, a Quality manager may set up a flexible sampling plan for a long-time supplier to inspect a quantity of 10 units and then skip the next 10 units. This decision was made based on the vendor having demonstrated that the quality of their receipts is very good. Receipts that do not require inspection are put away and a quality order is not generated. With the flexibility to perform lot-by-lot inspections instead of unit-by-unit inspections, as well as the use of other features such as sampling size variations, skip lot inspections, and test group flexibility, this type of inspection plan helps to minimize time, costs, handling damage, and inspection errors for your company.

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The feature that is named *(Preview) Advanced quality management* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Setting up flexible sampling plans

To set up your flexible sampling plans, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality control** \> **Flexible sampling plans**

1. For your new or selected sampling plan, make the following settings in the header:

    - **Flexible sampling plan code** - Enter a name for the sampling plan.
    - **Name**  – Enter a short description of the sampling plan.
    - **Alert role** - Select a security role to be notified when a specified number of failures for a level is reached.
    - **Last level** - Select the level number for the last activity to be performed in this flexible sampling plan process.
    - **Approved** - Set the plan in the approved state.

1. On the Action Pane you have following option.
    - **Add** Add a new sampling plan.
    - **Delete** Remove an existing plan. (You can't delete a plan if quality orders are using the plan or if activities are being tracked against it.)
    - **Copy plan** - Copy content from another plan to the selected plan.
    - **View activities** - Opens the **Flexible sampling plan activities** page where you can can get summaries and detailed information about the plan activities.

1. Use the grid on the **Details** FastTab to set up the plan. Use the buttons on the Action Pane to add and remove lines in the grid. For new or selected lines make the following settings:

    - **Level** – Select or view the level number assigned to this activity. The plan will be procssed in the desending order of the levels.
    - **Item sampling** – Select or view the **Item sampling** that determines the sampling size of the quality order for the activity, for example a 10 percent sampling or a 50-unit quantity sampling.
    - **Test group** – Select or view the **Test group** that determines the set of tests of the quality order for the activity.
    - **Rounds** – Set or view the number of testing rounds for the specific flexible sampling plan level that must pass quality order validation to advance to the next level. Once you select a level for the **Last level** field, any **Rounds** value you entered for that level is removed from the plan. It is removed from the plan intentionally to allow the last level to continue indefinitely until several failures regress the plan to a prior level. **Note:** The last level in the testing plan does not allow rounds because all future tests would then remain at this level indefinitely until the appropriate number of fails is met to revert the plan to a prior level. Assume a quality association has been set up to test purchase order registrations for a certain vendor. The vendor's flexible sampling plan requires that 10% of every registration be tested for 5 rounds. So if I receive 100 units, then a quality order is generated to test 10 of those units. The quality order for the first registration passes. However, the second quality order fails, but the next three pass. If round 6 passes, then the first level in the plan is accomplished as the number of passed rounds required has been met.
    - **Time span (days)** – Enter or view the number of days by which the specified number of rounds must be completed. This field is optional. **Note:** This field works in conjunction with the **Rounds** field. If a time span is defined, then the specified number of rounds must pass inspection within this time frame to advance testing to the next level. For example, if you set the time span to 60 days and the rounds to 10, then ten quality orders for this quality association must pass within 60 days to advance to the next level in the plan.
    - **Skip** – Select this check box to enable skip lot sampling, which allows for only a fraction of the submitted lots to be inspected. When you select this check box, you must enter the skip range in the **Frequency** fields.
    - **Test frequency** – If the **Skip** field is selected, enter the first number in the Skip range.
    - **Out of frequency** – If the **Skip** field is selected, enter the last number in the Skip range. Assume the quality association is set for Production order registrations. The flexible sampling plan associated with this reference type uses the Skip feature where the **Test frequency** field is set to **1** and **out of frequency** is set to **5**. Based on these settings, a quality order is generated to test 1 out of every 5 registrations. The determination as to which registrations of the 5 are tested and which ones are skipped is randomly made.
    - **Number of fails** – Enter or view the number of failed tests allowed before the flexible sampling plan reverts to a previous testing level, which may be more or less restrictive than the current test based on prior testing results. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails before the plan reverts to a prior level. A vendor might initially define a plan to test 10 out of 40 receipts to minimize costs associated with testing. However, because recent testing results support a notable increase in failures, the current level ends and a different level to test 20 out of 40 receipts replaces it. To the contrary, if the vendor's testing quality is consistent with no failures, then the level may be replaced by a level that requires a lower number of fails.
    - **Consecutive** – Select this check box if the number of fails specified in the **Number of fails** field must be consecutive failures. If selected and the number of consecutive fails is reached, then the appropriate action based on the fail action level and code is initiated. If the number of fails allowed is set to **2** and this check box is selected, then two consecutive fails generate a predefined fail action, such as issuing an alert notification to the Quality manager.
    - **Fail action level** – Enter or view the level of action that is initiated when the quantity in the **Number of fails** field is reached. This action indicates that more testing is required. If the **Consecutive** check box is also selected, then the number of fails must be consecutive fails to initiate the action. For example, if two consecutive quality orders fail at Level 3, then the action defined may require that testing start over at Level 1. You can assign any prior level that is currently defined in the flexible sampling plan that is at least equal to or less than the current level.
    - **Fail action code** – Select the action code that defines the action to take when the failure criteria is met or exceeded for the flexible sampling plan. All of the actions return the test sampling process to the fail action level.

## Set up the quality association for the flexible sampling plan

Quality orders using flexible sampling plans are set up to be automatically generated using a quality association.

Learn more about managing quality associations in [Quality associations](quality-associations.md)

## View flexible sampling plan activities

Open the **Flexible sampling plan activities** page by selecting the **View activities** button in the action pane on the **Flexible sampling plan** page. This page provides and overview of in which quality associations flexible sampling plans are used.

The following buttons are provided on the **Flexible sampling plan activities** page

- **Flexible sampling plan activity summary** – View a summary of activity for the selected flexible sampling plan.
- **Flexible sampling plan activity details** – View the specific details of the flexible sampling plan you select. In this page you can view how the activities in the plan has been progressing through the levels of the plan. For each activity the quality order used for the activity is indicated. A color codes a related text is describing the pass and fail criteria for each levels. As an example, if a quality order has failed, this is indicated with a read color, and you can also see if the test is reverted to a previous level that requires more testing of in case of a failed quality order. From this page you can also open pages with summaries and details about activities, and view charts with statistics about quality order testing performance.
- **Flexible sampling plans** – View the specific activity details for the flexible sampling plan you select. You can also create a new flexible sampling plan from this page.
