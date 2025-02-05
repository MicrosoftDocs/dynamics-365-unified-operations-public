---
title: 
description: 
ms.date: 04/25/2025
ms.topic: how-to
ms.service: 
author: johanhoffmann
ms.author: johanho
manager: 
---

# Quality Order Usability Improvements

## Skip Test Option has been Added

It is a common business process to create a test group that has a certain number of tests but when executing that test group within a Quality order, some tests are purposefully skipped. Prior to this feature, the user would need to delete those tests if they did not want to enter in test results. Some businesses would prefer to mark the test as Skipped instead of deleting it so that it can be logged as an audit trail that it was decided to skip it. When a test is skipped, all results data is cleared and becomes uneditable and no validation needs to be done on its associated test result data such as tag numbers and test result values. Also, the skipped test is excluded from Acceptable Quality Level (AQL) calculations. Additionally, a test can be unskipped which basically returns the test back to its original state and test results can be entered as usual.

## Using Skip from Quality Order Test Line

To mark a Test as Skipped, you need to select the desired test line(s) and select the Skip ribbon action from the line. If test results have already been entered, the user will receive a warning message. If OK is selected from the warning message, then all results data is removed. The test result icon, order line result, and batch attribute values are cleared. The Update inventory batch attribute and Include results checkboxes are both unchecked and the Skip test checkbox is checked. No editing can be done on the test while it is in this Skip state. To Unskip a test that was previously skipped, you merely need to select the line and choose the Skip option again. This will put the line back into its original state. Note: When using the Unskip, it is always wise to confirm all values on the test line are correct before validating the quality order.

## Using Skip from Quick Results Entry

Using the Skip option from Quick Results Entry works the same way with a few minor exceptions. Multi-select is not allowed from Quick Results Entry and if there are multiple rows of result data for the same test, the Skip option collapses them back to their original quantities before updating the data and making the line not editable.

## Quality Order Priority and Assigned To Tester has been Added

The effort to perform quality order testing can be extensive. Often, the work needs to be prioritized and assigned out to appropriate testing resources. To improve this process, we have added the following fields to the Quality Order Header: "Priority" and "Assigned To". These data elements by default are found on the General tab within the Assignment group box but can be personalized to the grid if sorting and filtering is desired. The Priority field is free-format and can be user defined based on business requirements. For example, a business might choose numbers between 0-100 where 100 are the most important. The Assigned to field needs to be assigned to a valid worker. Both fields are optional. Additionally, we added a Test Outcome Description field and a Result Note to the Quality Order Line Test Results to improve usability.

## Option to Not Validate Test Instrument Tag Assigned to Open Quality Order

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

