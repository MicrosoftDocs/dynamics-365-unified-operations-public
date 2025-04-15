---
title: Advanced quality management overview (preview)
description: Learn about the advanced quality management features in Supply Chain Management.
author: johanhoffmann
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form: 
ms.topic: overview
ms.date: 04/25/2025
ms.custom: 
  - bap-template
---

# Advanced quality management overview (preview)

[!include [banner](../../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]
<!-- KFM: Preview until further notice -->

Advanced quality management is a suite of quality-management features introduced in Supply Chain Management version 10.0.44. It enhances the quality management features that were already available by adding many new tools that address core issues that manufacturers face to meet the U.S. Food and Drug Administration's (FDA) Quality System Regulation 21 CFR Part 11, cGMP and other various regulatory and international standards such as ISO and Six Sigma. <!-- KFM: is this too narrow a description? Should we describe this has having broader applications? Mention here (and/or in Prerequisites) that these features mostly require the Inventory module (not WMS)? -->

:::image type="content" source="media/advanced-quality-management-overview.png" alt-text="Overview of advanced quality management features." lightbox="media/advanced-quality-management-overview.png":::

[!INCLUDE [preview-note](~/../shared-content/shared/preview-includes/preview-note-d365.md)]

## Prerequisites

To use the features described in this article, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.44 or later.
- The following features must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
    - *(Preview) Approved customer list* – Allows administrators to set up rules that restrict the sale of specific products to specific customers. The feature applies to sales orders, sales quotations, and sales agreements.
    - *(Preview) Dispense management* – Allows users to separate dispensing activities from picking activities, ensuring effective management of controlled and regulated products. It supports over-picking with residual products returned to inventory, identifies items needing dispensing control, and requires authorized personnel for dispensing. Additionally, it captures electronic signatures for dispensing postings, establishes dispensing tolerance parameters, generates pick lists/dispensing tickets at production release, and allows issuing more than the proposed quantity.
    - *(Preview) Electronic signature improvements* – Introduces new electronic signature requirements for various management tasks, including dispense management, CAPA management, instrument calibration, and validation of quality orders. It also defines pass-key expiration and passphrase constraints for electronic signatures.
    - *(Preview) Advanced quality management* – Integrates advanced quality capabilities throughout the Supply Chain Management solution. Key features include: optimized testing strategies (flexible sampling plans, skip-lot testing, new quality order triggers, and instrument calibration), regulatory compliance (customer-specific certificates of analysis (COA), and enhancements to electronic signatures), digitized manufacturing for precision and compliance (electronic batch record), continuous improvement and risk mitigation (corrective and preventive actions (CAPA) management and enhancements to non-conformance), and enhanced user experience (simplified entry of quality test results and new workspaces for quality management).

## Key features of advanced quality management

Some of the key industry-specific capabilities of the solution are:

- **Corrective Actions/Preventive Actions (CAPA)** – This feature allows users to automate processes to manage, track, and correct root causes of issues and to implement action plans to prevent the same and similar issues going forward. Learn more in [Corrective and preventive action (CAPA) management overview (preview)](capa-overview.md).

- **Electronic signature requirement for CAPA case closure** – This feature allows users to establish CAPA case closure and cancellation as a trigger for an electronic signature sign-off. Learn more in [CAPA management administration (preview)](capa-admin.md)

- **Flexible sampling plans** – This feature enables companies to inspect a fraction of a lot, or to skip lots altogether, to realize reduced quality and material handling costs, faster material throughput, and less redundant and destructive testing. Learn more in [Flexible sampling plans (preview)](quality-flexible-sampling-plans.md)

- **Approved customer lists (ACL)** – This feature provides greater control over what products a given customer can buy and when they can buy them, which is especially important with a product line that involves controlled substances and branded products. Learn more in [Approved customer lists (preview)](../sales-marketing/approved-customer-lists.md)

- **Electronic signature** – This feature enhancement provides greater security of the digital signatures to meet the latest government requirements and regulations.

- **Electronic Batch Record (EBR)** – This feature enables users to view all the versions, methods, and characteristics for consumed BOM and Formula items. This is referred to as a Master Manufacturing Record that maintains all the methods that could be utilized to produce the item. This feature also allows users to view and print reports of the actual versions, test values, attribute values, quality order results of all the items produced and the ingredients consumed. This is referred to as a Batch Production Record that captures the actual version and methods used to produce the item. Learn more in [Electronic Batch Records (EBR)](../production-control/quality-electronic-batch-record.md).

- **Instrument calibration** – This new feature adds capability around tracking individual test instrument tags, supports an on-going calibration process for the instrument tag and tracks usage of given tags against the quality order tests. Learn more in [Test instrument calibration (preview)](quality-instrument-calibration.md).

- **Quality associations for return and transfer orders** – This feature enhances the capability of quality associations by offering the ability to automatically create quality orders triggered from a sales return or a transfer order. Learn more in [Quality associations](quality-associations.md).

- **Customer-specific COAs** – This feature supports the setup and application of customer certificate of analysis (COA) requirements. The specific customer will drive details such as whether a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results (pass and/or fail) should be replaced with standard verbiage. In addition, customer-specific COA's can be generated automatically from the sales order packing slip posting process. Learn more in [Customer specific certificate of analysis (COA) (preview)](quality-customer-specific-coa.md)

- **Production dispensing** – This feature enables users to segregate the dispensing area and activities from the picking activities. Learn more in [Production dispensing (preview)](../production-control/quality-production-dispensing.md).

- **Quick test results entry** – This feature enables users to very quickly and easily enter test results on a quality order from a consolidated view which includes visibility to test minimum, maximum and target values. Learn more in [Quick Results Entry (preview)](quality-quick-results-entry.md).

## Quality order usability improvements

Advanced quality management adds several usability improvements to the quality order process. The option to skip a quality order test has been added. When a decision is made not to perform a test on a given quality order, that can now be noted on the quality order without losing visibility to the original test. When a test is skipped, all validations on the test is by-passed and the test is changed to not be included in results so that acceptable quality level (AQL) calculations are still performed on the remaining tests. Quality order **Priority** Level and **Assigned to** tester are new data elements on the quality order that can be used to sort and filter on the quality work that needs to be completed. Result notes can now also be recorded for a given test result line. Finally, test instrument tags are always checked to see if the selected tag is already on an open quality order. This validation isn't important to all businesses so now there is a parameter that drives this functionality, and the validation can be skipped if not required.

### Skip tests when needed

It is a common business process to create a test group that has a certain number of tests but when executing that test group within a quality order, some tests are purposefully skipped. Prior to this feature, you were required to delete tests you didn't want to enter results for. Some businesses prefer to mark the test as *Skipped* instead of deleting it so that it can be logged as an audit trail that it was decided to skip it. When a test is skipped, all results data is cleared and becomes uneditable and no validation needs to be done on its associated test result data such as tag numbers and test result values. Also, the skipped test is excluded from AQL calculations. Tests can be un-skipped if needed, which returns the test back to its original state and test results can be entered as usual.

#### Skip tests from a quality order test line

To mark a test as *Skipped*, select the desired test line(s) and select the **Skip** on the Action Pane. If test results have already been entered, you receive a warning message. The test result icon, order line result, and batch attribute values are cleared. The **Update inventory batch attribute** and **Include results** checkboxes are both cleared and the **Skip test** checkbox is selected. No editing can be done on the test while it is in the *Skip* state. To un-skip a test that was previously skipped, select the line and choose the **Skip** option again. This will put the line back into its original state.

#### Skip tests during quick results entry

When you use the skip option from quick results entry, multi-select is not allowed from and if there are multiple rows of result data for the same test, the skip option collapses them back to their original quantities before updating the data and making the line not editable.

### Quality order priority and tester assignment

Quality orders now include the following fields on the **General** tab: **Quality order priority** and **Worker**. The **Quality order priority** field is free-format and can be user-defined based on business requirements. For example, a business might choose numbers between 0-100 where 100 are the most important. The **Worker** field needs to be assigned to a valid worker. Both fields are optional. 

Quality orders also now include fields for entering a test outcome description and result notes for each test line.

### Skip test instrument tags validation

Previously, the system always checked whether all test instrument tags selected for use on a new quality order were already assigned to an existing open quality order. If the selected test instrument tag was found on an open quality order, a warning message was always displayed. This check is now optional. The setting to skip the validation is made on a per-tag basis, but you can also set a default value, which applies for all new tags.

To set the validation option for each tag, go to **Inventory management** \> **Setup** \> **Quality Control** \> **Test instrument tags** and make the following setting for each tag:

- **Skip check for test instrument on open quality order** – Set to *Yes* to skip the validation that checks whether the selected tag is already assigned to an open quality order (no warning message is triggered). Set to *No* if the system should run the check and display a warning message if the tag is already assigned to an open quality order. 

To set the default validation setting for all new tags, go to **Path: Inventory management** \> **Setup** \> **Inventory and Warehouse Management Parameters**. Open the **Quality management** tab and make the following setting:

- **Skip check for test instrument on open quality order** – Choose whether all new test instrument tags should be set to skip the validation by default. You can still change this setting for individual tags.

Learn more in [Test instrument calibration (preview)](quality-instrument-calibration.md).
