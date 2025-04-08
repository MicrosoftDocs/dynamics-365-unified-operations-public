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

- **Customer-specific COAs** – This feature supports the setup and application of customer certificate of analysis (COA) requirements. The specific customer will drive details such as whether a specific test should be included, if minimum/maximum values should be suppressed, if customer-specific batch attribute ranges should be used instead of the standard range and if results (pass and/or fail) should be replaced with standard verbiage. In addition, customer-specific COA's can be generated automatically from the sales order packing slip posting process. Learn more in [Customer specific certificate of analysis (COA)](quality-customer-specific-coa.md)

- **Production dispensing** – This feature enables users to segregate the dispensing area and activities from the picking activities. Learn more in [Production dispensing](../production-control/quality-production-dispensing.md).

- **Quick test results entry** – This feature enables users to very quickly and easily enter test results on a quality order from a consolidated view which includes visibility to test minimum, maximum and target values. Learn more in [Quick Results Entry](quality-quick-results-entry.md).

## Quality Order Usability Improvements

Advanced quality management adds several usability improvements to the quality order process. The option to skip a quality order test has been added. When a decision is made not to perform a test on a given quality order, that can now be noted on the quality order without losing visibility to the original test. When a test is skipped, all validations on the test is by-passed and the test is changed to not be included in results so that AQL calculations are still performed on the remaining tests. Quality order "Priority" Level and "Assigned to" tester are new data elements on the quality order that can be used to sort and filter on the quality work that needs to be completed. Result notes can now also be recorded for a given test result line. Finally, test instrument tags are always checked to see if the selected tag is already on an open quality order. This validation is not important to all businesses so now there is a parameter that drives this functionality, and the validation can be skipped if not required.

### Skip Test Option has been Added

It is a common business process to create a test group that has a certain number of tests but when executing that test group within a Quality order, some tests are purposefully skipped. Prior to this feature, the user would need to delete those tests if they did not want to enter in test results. Some businesses would prefer to mark the test as Skipped instead of deleting it so that it can be logged as an audit trail that it was decided to skip it. When a test is skipped, all results data is cleared and becomes uneditable and no validation needs to be done on its associated test result data such as tag numbers and test result values. Also, the skipped test is excluded from Acceptable Quality Level (AQL) calculations. Additionally, a test can be unskipped which basically returns the test back to its original state and test results can be entered as usual.

### Using Skip from Quality Order Test Line

To mark a Test as Skipped, you need to select the desired test line(s) and select the Skip ribbon action from the line. If test results have already been entered, the user will receive a warning message. If OK is selected from the warning message, then all results data is removed. The test result icon, order line result, and batch attribute values are cleared. The Update inventory batch attribute and Include results checkboxes are both unchecked and the Skip test checkbox is checked. No editing can be done on the test while it is in this Skip state. To Unskip a test that was previously skipped, you merely need to select the line and choose the Skip option again. This will put the line back into its original state. Note: When using the Unskip, it is always wise to confirm all values on the test line are correct before validating the quality order.

### Using Skip from Quick Results Entry

Using the Skip option from Quick Results Entry works the same way with a few minor exceptions. Multi-select is not allowed from Quick Results Entry and if there are multiple rows of result data for the same test, the Skip option collapses them back to their original quantities before updating the data and making the line not editable.

### Quality Order Priority and Assigned To Tester has been Added

The effort to perform quality order testing can be extensive. Often, the work needs to be prioritized and assigned out to appropriate testing resources. To improve this process, we have added the following fields to the Quality Order Header: "Priority" and "Assigned To". These data elements by default are found on the General tab within the Assignment group box but can be personalized to the grid if sorting and filtering is desired. The Priority field is free-format and can be user defined based on business requirements. For example, a business might choose numbers between 0-100 where 100 are the most important. The Assigned to field needs to be assigned to a valid worker. Both fields are optional. Additionally, we added a Test Outcome Description field and a Result Note to the Quality Order Line Test Results to improve usability.

### Option to Not Validate Test Instrument Tag Assigned to Open Quality Order

Currently, if a Quality order test is set up with a Test Instrument that uses Tags, the system will always check to see if a selected test instrument tag is already on an open quality order. If the selected test instrument tag is found on an open quality order, a warning message is always displayed to the user. Some businesses don't need this validation so a parameter is added in Inventory Management to indicate that this validation can be skipped. This parameter on Inventory and warehouse management parameters from the Quality management tab will default to all new test instrument tags. This parameter can also be modified on a test instrument tag basis. When validating a quality order, if this flag is selected on a chosen test instrument tag and that tag is currently assigned to an open quality order, then no warning message will be triggered on validation.

| **Path: Inventory management** \> **Setup** \> **Inventory and Warehouse Management Parameters** |  |  |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
| **Quality management tab** |  |  |
| Skip check for test instrument on open quality order | Select this option if you want the system to skip the validation related to if the selected test instrument tag is already assigned to an open quality order. If selected, that validation is bypassed, and no warning message is triggered. If not selected, then the validation is performed, and a warning message may be triggered. This value will default from the parameters for new test instrument tags but can be changed on an individual tag. | Selected or deselected. Prior releases, the system functioned as if this flag was never selected. Used as a default to test instrument tags. To skip the validation, this field must be selected on the test instrument tag. |

| **Path: Inventory management** \> **Setup** \> **Quality Control** \> **Test instrument tags** |  |  |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
|  |  |  |
| Skip check for test instrument on open quality order | Select this option if you want the system to skip the validation related to if the selected test instrument tag is already assigned to an open quality order. If selected, that validation is bypassed, and no warning message is triggered. If not selected, then the validation is performed, and a warning message may be triggered. This value will default from the parameters for new test instrument tags but can be changed on an individual tag. | Selected or deselected. Prior releases, the system functioned as if this flag was never selected. |

| **Path: Inventory management** \> **Periodic** \> **Quality management** \> **Quality orders and Quick Result Entry** |  |  |
|--|--|--|
| **Label Name** | **Description** | **Examples/Hints** |
|  |  |  |
| Skip test | This is a not-editable field that is updated by the Skip ribbon action. If selected, then the test has been skipped, no test results will be entered, and this test line will not go through standard quality order test line validations. | The default value for this field is NOT Selected. |
| Priority | Assign a priority to the Quality order for testing | Is user defined. For example, you might decide that the lower the number, the higher the priority. |
| Assigned to | Use to assign the user responsible for the Quality order testing. | Must be a valid worker. |
| Outcome description | Is the associated description of the chosen Test Outcome. |  |
| Result note | Enter any additional notes for the test results. |  |
