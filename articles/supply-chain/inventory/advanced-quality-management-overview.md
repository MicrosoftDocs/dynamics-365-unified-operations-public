---
title: Advanced quality management overview
description: Learn about the advanced quality management features in Microsoft Dynamics 365 Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Advanced quality management overview

[!include [banner](../../includes/banner.md)]

Advanced quality management is a suite of quality management features that was introduced in Microsoft Dynamics 365 Supply Chain Management version 10.0.44. It enhances the quality management features that were already available by adding many new tools. These tools address core issues that manufacturers face as they try to meet the United States Food and Drug Administration's (FDA's) Quality System Regulation (QSR), part 11 of Title 21 of the Code of Federal Regulations (21 CFR Part 11), current Good Manufacturing Practice (cGMP), and other regulatory and international standards, such as the International Organization for Standardization (ISO) and Six Sigma.

:::image type="content" source="media/advanced-quality-management-overview.png" alt-text="Diagram that provides an overview of advanced quality management features, organized into continuous improvement, optimized testing, digitized manufacturing, regulatory compliance, and user productivity areas." lightbox="media/advanced-quality-management-overview.png":::

## Prerequisites

Before you can use the features that are described in this article, your system must meet the following requirements:

- You must be running Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

    - *Approved customer list* – This feature lets administrators set up rules that limit the sale of specific products to specific customers. The feature applies to sales orders, sales quotations, and sales agreements.
    - *Dispense management* – This feature lets users separate dispensing activities from picking activities. In this way, it ensures effective management of controlled and regulated products. The feature supports over-picking where residual products are returned to inventory, identifies items that require dispensing control, and requires authorized personnel for dispensing. Additionally, it captures electronic signatures for dispensing postings, establishes dispensing tolerance parameters, generates pick lists and dispensing tickets at production release, and enables the quantity that is issued to exceed the proposed quantity.
    - *Electronic signature improvements* – This feature introduces new electronic signature requirements for various management tasks, including dispense management, corrective and preventive actions (CAPA) management, instrument calibration, and validation of quality orders. The feature also defines passkey expiration and passphrase constraints for electronic signatures.
    - *Advanced quality management* – This feature integrates advanced quality capabilities throughout the Supply Chain Management solution. Key capabilities include optimized testing strategies (flexible sampling plans, skip lot testing, new quality order triggers, and instrument calibration), regulatory compliance (customer-specific certificates of analysis \[COAs\] and enhancements to electronic signatures), digitized manufacturing for precision and compliance (electronic batch records), continuous improvement, risk mitigation (CAPA management and enhancements to nonconformance), and an enhanced user experience (simplified entry of quality test results and new workspaces for quality management).

## Key features of advanced quality management

This section describes some of the key industry-specific capabilities of the solution.

- **Corrective and preventive actions (CAPA)** – Users can automate processes for managing, tracking, and correcting root causes of issues. They can also implement action plans to prevent the same issues and similar issues from occurring in the future. Learn more in [Corrective and preventive action (CAPA) management overview (preview)](capa-overview.md).
- **Electronic signature requirement for CAPA case closure** – Users can establish CAPA case closure and cancellation as a trigger for electronic signature sign-off. Learn more in [CAPA management administration (preview)](capa-admin.md).
- **Flexible sampling plans** – Companies can inspect a fraction of a lot, or skip lots completely, to reduce quality and material handling costs, accelerate material throughput, and make testing less redundant and destructive. Learn more in [Flexible sampling plans (preview)](quality-flexible-sampling-plans.md).
- **Approved customer lists (ACLs)** – This feature provides more control over what products specific customers can buy and when they can buy those products. This capability is especially important for a product line that involves controlled substances and branded products. Learn more in [Approved customer lists (preview)](../sales-marketing/approved-customer-lists.md).
- **Electronic signature** – This feature enhancement improves the security of digital signatures to meet the latest government requirements and regulations.
- **Electronic batch records (EBRs)** – Users can view all the versions, methods, and characteristics for consumed bill of materials (BOM) and formula items. This view is referred to as a *master manufacturing record* (MMR). It maintains all the methods that can be used to produce an item. Users can also view and print reports of the actual versions, test values, attribute values, and quality order results of all the items that are produced and the ingredients that are consumed. This view is referred to as a *batch production record* (BPR). It captures the actual version and methods that are used to produce an item. Learn more in [Electronic batch records (EBRs)](../production-control/quality-electronic-batch-record.md).
- **Instrument calibration** – This new feature adds a capability for tracking individual test instrument tags. It also supports an ongoing calibration process for instrument tags and tracks the use of tags against quality order tests. Learn more in [Test instrument calibration (preview)](quality-instrument-calibration.md).
- **Quality associations for return and transfer orders** – This feature enhances the capability of quality associations by enabling automatic creation of quality orders that are triggered from a sales return or a transfer order. Learn more in [Quality associations](quality-associations.md).
- **Customer-specific certificates of analysis (COAs)** – This feature supports the setup and application of customer-specific COA requirements. Each customer drives details such as whether a specific test should be included, whether minimum/maximum values should be suppressed, whether customer-specific batch attribute ranges should be used instead of the standard range, and whether pass and fail results should be replaced with standard text. In addition, customer-specific COAs can be automatically generated from the sales order packing slip posting process. Learn more in [Customer specific certificate of analysis (COA) (preview)](quality-customer-specific-coa.md).
- **Production dispensing** – Users can segregate the dispensing area and activities from the picking activities. Learn more in [Production dispensing (preview)](../production-control/quality-production-dispensing.md).
- **Quick test results entry** – Users can quickly and easily enter test results on a quality order from a consolidated view that provides visibility into minimum, maximum, and target values for a test. Learn more in [Enter quality test results quickly (preview)](quality-quick-results-entry.md).

## Quality order usability improvements

Advanced quality management adds several usability improvements to the quality order process. Quality order tests can now be skipped. A user who decides not to perform a test on a given quality order can make a note of that decision on the quality order without losing visibility into the original test. When a test is skipped, all validations on the test are bypassed, and the test is excluded from the results. Acceptable quality level (AQL) calculations are then performed on the remaining tests.

The priority level of the quality order and the tester that the quality order is assigned to are new data elements on the quality order. They can be used to sort and filter on the quality work that must be completed. Additionally, result notes can now be recorded for a given test result line. Finally, a parameter now controls the validation that determines whether a selected test instrument tag is already used on an open quality order. Previously, this validation always ran. However, it can now be skipped if it isn't important to a business.

### Skip tests as required

A common business process is to create a test group that has several tests, but to intentionally skip some tests when the test group runs within a quality order. Previously, you had to delete tests that you didn't want to enter results for. However, some businesses prefer to mark the test as *Skipped* instead of deleting it, so that the decision to skip it can be logged in an audit trail.

When a test is skipped, all result data is cleared and can no longer be edited. In addition, no validation has to be done on associated test result data, such as tag numbers and test result values. The skipped test is also excluded from AQL calculations.

The decision to skip a test can be reversed as required. In this case, the test returns to its original state, and test results can be entered as usual.

#### Skip tests from a quality order test line

To mark a test as *Skipped*, select the desired test lines, and then, on the Action Pane, select **Skip**. The test result symbol, order line result, and batch attribute values are cleared. The **Update inventory batch attribute** and **Include results** checkboxes are cleared, and the **Skip test** checkbox is selected. The test can't be edited while it is in the *Skipped* state.

If test results were already entered, you receive a warning message when you try to skip the test.

If you no longer want to skip a test that was previously skipped, select the line, and then select **Skip** again. The line returns to its original state.

#### Skip tests during quick results entry

When you use the **Skip** option from quick results entry, you can't select multiple test lines at a time. If there are multiple rows of result data for the same test, the **Skip** option collapses them to their original quantities before it updates the data and makes the line uneditable.

### Quality order priority and tester assignment

Quality orders now include **Quality order priority** and **Worker** fields on the **General** tab. Both fields are optional.

- **Quality order priority** – This free-form field can be user-defined based on business requirements. For example, a business might express priority as a number between 0 (zero) and 100, where 100 represents the highest priority.
- **Worker** – This field must be set to a valid worker.

Additionally, quality orders now include fields for entering a test outcome description and result notes for each test line.

### Skip test instrument tags validation

Previously, the system always ran a validation to determine whether the test instrument tags that were selected for use on a new quality order were already used on an existing open quality order. If a selected test instrument tag was found on an open quality order, the system showed a warning message.

This validation is now optional, and a parameter lets you control whether it's run or skipped. You can configure this parameter for each tag individually. You can also set a default value that applies to all new tags.

To set the validation option for individual tags, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Quality Control** \> **Test instrument tags**.
1. For each tag, set the **Skip check for test instrument on open quality order** option to one of the following values:

    - *Yes* – Skip the validation that determines whether the tag is already assigned to an open quality order. If the tag is already assigned to an open quality order, no warning message is shown.
    - *No* – The system should run the validation and show a warning message if the tag is already assigned to an open quality order.

To set the default validation setting for all new tags, follow these steps.

1. Go to **Inventory management** \> **Setup** \> **Inventory and Warehouse Management parameters**.
1. On the **Quality management** tab, in the **Skip check for test instrument on open quality order** field, specify whether the validation should be skipped for all new test instrument tags by default. You can change the setting for individual tags.

Learn more in [Test instrument calibration (preview)](quality-instrument-calibration.md).
