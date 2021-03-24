---
# required metadata

title: Quality management test groups
description: This topic describes how you can use create test groups to combine multiple test together for use with quality orders in Dynamics 365 Supply Chain Management.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestGroup
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.custom: 94003
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: raprofit
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quality management test groups

[!include [banner](../includes/banner.md)]

This topic describes how you can create and use test groups to combine multiple test together for use with quality orders in Dynamics 365 Supply Chain Management.

Use the **Test groups** page to set up, edit, and view test groups and the individual tests that are assigned to a test group. The upper section displays test groups, and the lower section displays the tests that are assigned to a selected test group. You assign several policies to a test group, such as a sampling plan, an acceptable quality level (AQL), and the requirement for destructive testing. When you assign an individual test to a test group, you define additional information, such as the sequence, documents, and validity dates. For a quantitative test, the information that you define also includes the acceptable measurement values. For a qualitative test, the information includes the test variable and default outcome. The test group that is assigned to a quality order defines the default set of tests that must be performed on the specified item. However, you can add, delete, or change tests on the quality order. Test results are reported for each test on a quality order.

When you define the test group, you can optionally specify an Item sampling. Item samplings are used to define the amount of the product to be tested. For more information refer to [Quality management item sampling](quality-item-sampling.md).

Additionally, you can indicate if the tests in the test group are destructive. A destructive test indicates that the item sampling size will be destroyed and the quantity removed from the on-hand inventory.

## Example of a test group

A manufacturing company defines a test group for each variation of its quality guidelines. The various test groups reflect differences in the sampling plans, the sets of tests that must be performed together, the AQL, and other factors. For quantitative tests, there are also differences in the acceptable measurement values. To enforce its quality guidelines, the company assigns a test group to each rule for automatically generating quality orders on the **Quality associations** page, and also assigns a test group to quality orders that are manually created.

## Create a test group

To create a test group:

1. Go to **Inventory management > Setup > Quality control > Test groups**.
1. Select **New** on the Action Pane to add a new row to the grid in the upper section and then make the following settings for it:
    - **Test group** - Enter a unique ID or name for the test group.
    - **Description** - Enter a detailed description for the test.
    - **Acceptable quality level** - Enter the total percentage of test results that must pass to consider the group of tests as passing.
    - **Item sampling** - Select an item sampling. More information: [Quality management item sampling](quality-item-sampling.md)
    - **Destructive** - Select this check box to indicate the test group will destroy the items being tested.
1. With your new row still selected, open the **General** tab on the upper section. Some of the settings for the test group selected on the **Overview** tab are repeated here. In addition, you can set the following options for the group:
    - **Update inventory batch attribute** - When this is set to *Yes*, new tests that are added to the test group in the lower pane will automatically have this option selected for each test.
    - **Update batch disposition** - When this is set to *Yes*, if the item being tested is batch controlled, the batch disposition will be automatically updated with the value selected in the **Failed quality order batch disposition** or **Passed quality order batch disposition** field.
    - **Failed quality order batch disposition** - Select the batch disposition code that should be assigned when a quality order with this test group fails by not meeting the acceptable quality level.
    - **Passed quality order batch disposition** - Select the batch disposition code that should be assigned when a quality order with this test group passes by meeting the acceptable quality level.
    - **Update inventory status** - When this is set to *Yes*, if the item being tested has **Inventory status** enabled on the **Storage dimension group**, the status will be automatically updated with the failed or passed quality order status selected in the **Failed quality order status** or **Passed quality order status** field.
    - **Failed quality order status** - Select the inventory status that should be assigned to the item when a quality order with this test group fails by not meeting the acceptable quality level.
    - **Passed quality order status** - Select the inventory status that should be assigned to the item when a quality order with this test group passes by meeting the acceptable quality level.

## Add a qualitative test to a test group

To add a qualitative test to a test group:

1. Go to **Inventory management > Setup > Quality control > Test groups**.
1. Open the **Overview** tab in the upper section and then select the test group that you want to add a test to.
1. In the lower section, open the **Overview** tab and select **Add** from the toolbar to add a new row to the lower-section grid. Make the following settings for the new row:
    - **Sequence number** - Enter an integer to indicate the sequence that the tests should be performed. A smaller number indicates the test will be run first.
    - **Test** Select the test that you want to perform. For a qualitative test, select a test where the **Type** is *Option*.
    - **Effective** - Select the first date the test is valid. Leave blank to have no limit.
    - **Expiration** - Select the last date the test is valid. Leave blank (or set to *Never*) to have no limit.
    - **Test value determination** - This setting establishes how an acceptable quality level will be determined when multiple results are recorded for the same test. The options include *Average*, *Minimum*, *Maximum*, and *Manual*. For a qualitative test, only *Manual* can be selected&mdash;if *Average*, *Minimum*, or *Maximum* are selected, you will get an error message when you save the test group. 
    - **Attribute** - Select a batch attribute if you'd like to record test results on that attribute if you also enable the **Update inventory batch attribute** option.
    - **Update inventory batch attribute** - Select this check box to record test results on the batch attribute selected in teh **Attribute** column.

    > [!NOTE]
    > The recommended practice for numbering tests is to leave a gap between each test. For example, start with 10, and then for each additional test increment the **Sequence number** by 10. This allows for addition of new tests later on without the need to delete and create the lines to put them in the desired sequence.

1. In the lower section, open the **General** tab. Some of the settings for the test selected on the **Overview** tab are repeated here. In addition, you can set the following options for the test:

    - **Certificate of analysis report** - Set to *Yes* to indicate that the test results should print on the certificate of analysis. This report can be generated from the quality order.
    - **Action on failure** - Select either *Accept* or *Fail* to indicate if this test should pass or fail when the acceptable quality level for the test is not met.
    - **Acceptable quality level** - Enter the total percentage of test result that must pass to consider the selected test as passing.
1. In the lower section, open the **Test** tab and then make the following settings:
    - **Variable** - Select the test variable to record the qualitative test results.
    - **Default outcome** - Select the outcome that will be recorded on the test results by default.
    - **Test instrument** - Select the device to be used for the test. If a test instrument is defined, it will automatically default into the test in the test group.
1. Close the page.

## Add a quantitative test to a test group

1. Go to **Inventory management > Setup > Quality control > Test groups**.
1. Open the **Overview** tab in the upper section and then select the test group that you want to add a test to.
1. In the lower section, open the **Overview** tab and select **Add** from the toolbar to add a new row to the lower-section grid. Make the following settings for the new row:
    - **Sequence number** - Enter an integer to indicate the sequence that the tests should be performed. A smaller number indicates the test will be run first.
    - **Test** Select the test that you want to perform. For a quantitative test, select a test where the **Type** is *Fraction* or *Integer*.
    - **Effective** - Select the first date the test is valid. Leave blank to have no limit.
    - **Expiration** - Select the last date the test is valid. Leave blank (or set to *Never*) to have no limit.
    - **Test value determination** - This setting establishes how an acceptable quality level will be determined when multiple results are recorded for the same test. The options include *Average*, *Minimum*, *Maximum*, and *Manual*.  
    - **Attribute** - Select a batch attribute if you'd like to record test results on that attribute if you also enable the **Update inventory batch attribute** option.
    - **Update inventory batch attribute** - Select this check box to record test results on the batch attribute selected in teh **Attribute** column.

    > [!NOTE]
    > The recommended practice for numbering tests is to leave a gap between each test. For example, start with 10, and then for each additional test increment the **Sequence number** by 10. This allows for addition of new tests later on without the need to delete and create the lines to put them in the desired sequence.

1. In the lower section, open the **General** tab. Some of the settings for the test selected on the **Overview** tab are repeated here. In addition, you can set the following options for the test:

    - **Certificate of analysis report** - Set to *Yes* to indicate that the test results should print on the certificate of analysis. This report can be generated from the quality order.
    - **Action on failure** - Select either *Accept* or *Fail* to indicate if this test should pass or fail when the acceptable quality level for the test is not met.
    - **Acceptable quality level** - Enter the total percentage of test result that must pass to consider the selected test as passing.

1. In the lower section, open the **Test** tab and then make the following settings:
    - **Standard** - Enter the integer or fraction amount that is expected for the test results. This is the value that will default into the test result. The value entered will automatically default into the **Min** and **Max** fields.
    - **Min** - Enter the minimum allowed value for the test result. The value entered must be less than the amount set in the **Standard** field. When the **Min** field is updated, the **Min tolerance (%)** field is automatically updated. You can alternatively update this field directly, and the **Min** field will update automatically.
    - **Max** - Enter the maximum allowed value for the test result. The value entered must be more than the amount in the **Standard** field. When the **Max** field is updated, the **Max tolerance (%)** field is automatically updated. You can alternatively update this field directly, and the **Max** will update automatically.
    - **Test instrument** - Select the device to be used for the test. If a test instrument is defined, it will automatically default into the test in the test group.
1. Close the page.

## Additional resources

- [Quality management test instruments](quality-management-processes.md)
- [Quality management tests](quality-management-processes.md)
- [Quality management test variables](quality-management-processes.md)
- [Quality associations](quality-management-processes.md)
- [Batch attributes](/supply-chain/production-control/batch-attributes.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]