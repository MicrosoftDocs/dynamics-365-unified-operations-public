---
# required metadata

title: Quality management test groups
description: This article describes how to create test groups, so that multiple tests can be used with quality orders in Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestGroup
# ROBOTS:
audience: Application User
# ms.devlang:
ms.reviewer: kamaybac
# ms.tgt_pltfrm:
ms.assetid: a1d9417b-268f-4334-8ab6-8499d6c3acf0
ms.search.region: Global
ms.search.industry: Distribution
ms.author: yufeihuang
ms.search.validFrom: 2020-06-17
ms.dyn365.ops.version: AX 7.0.0

---

# Quality management test groups

[!include [banner](../includes/banner.md)]

This article describes how to create test groups, so that multiple tests can be used with quality orders in Microsoft Dynamics 365 Supply Chain Management.

You use the **Test groups** page to set up, edit, and view test groups and the individual tests that are assigned to them. The upper part of the page shows the test groups, and the lower part shows the tests that are assigned to a selected test group.

You assign several policies to a test group, such as a sampling plan, an acceptable quality level (AQL), and the requirement for destructive testing. Then, when you assign an individual test to a test group, you define additional information, such as the sequence, documents, and validity dates. For a quantitative test, the information that you define also includes the acceptable measurement values. For a qualitative test, the information includes the test variable and default outcome.

The test group that is assigned to a quality order defines the default set of tests that must be performed on the specified item. However, you can add, delete, or change tests for the quality order. Test results are reported for each test on a quality order.

When you define a test group, you can optionally specify an item sampling. Item samplings are used to define the amount of the product that must be tested. For more information, see [Quality management item sampling](quality-item-sampling.md). You can also indicate whether the tests in a test group are destructive. In a destructive test, the item sampling is destroyed, and the quantity is removed from the on-hand inventory.

## Example of a test group

A manufacturing company defines a test group for each variation of its quality guidelines. The various test groups reflect differences in the sampling plans, the sets of tests that must be performed together, the AQL, and other factors. For quantitative tests, there are also differences in the acceptable measurement values. To enforce its quality guidelines, the company assigns a test group to each rule that is used to automatically generate quality orders on the **Quality associations** page. It also assigns a test group to quality orders that are manually created.

## Create a test group

To create a test group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Test groups**.
1. On the Action Pane, select **New** to add a row to the grid in the upper part of the page. Then set the following fields for the new row:

    - **Test group** – Enter a unique ID or name for the test group.
    - **Description** – Enter a detailed description of the test group.
    - **Acceptable quality level** – Enter the total percentage of test results that must pass for the group of tests to be considered passed.
    - **Item sampling** – Select an item sampling. For more information, see [Quality management item sampling](quality-item-sampling.md).
    - **Destructive** – Select this check box to indicate that the test group will destroy the items that are tested.

1. While the new row is still selected, select the **General** tab in the upper part of the page. Some of the settings for the test group that is selected on the **Overview** tab are repeated here. In addition, you can set the following fields for the group:

    - **Update inventory batch attribute** – When you set this option to *Yes* here, it will automatically be set to *Yes* for every new test that is added to the test group in the lower part of the page.
    - **Update batch disposition** – When you set this option to *Yes*, if the item that is being tested is batch controlled, the batch disposition will automatically be updated with the value that is selected in the **Failed quality order batch disposition** or **Passed quality order batch disposition** field.
    - **Failed quality order batch disposition** – Select the batch disposition code that should be assigned when a quality order that includes this test group fails because it doesn't meet the AQL.
    - **Passed quality order batch disposition** – Select the batch disposition code that should be assigned when a quality order that includes this test group passes because it meets the AQL.
    - **Update inventory status** – When you set this option to *Yes*, if **Inventory status** is enabled on the storage dimension group for the item that is being tested, the status will automatically be updated with the status that is selected in the **Failed quality order status** or **Passed quality order status** field.
    - **Failed quality order status** – Select the inventory status that should be assigned to the item when a quality order that includes this test group fails because it doesn't meet the AQL.
    - **Passed quality order status** – Select the inventory status that should be assigned to the item when a quality order that includes this test group passes because it meets the AQL.

## Add a qualitative test to a test group

To add a qualitative test to a test group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Test groups**.
1. On the **Overview** tab in the upper part of the page, select the test group that you want to add a test to.
1. In the lower part of the page, on the **Overview** tab, select **Add** on the toolbar to add a row to the grid. Then set the following fields for the new row:

    - **Sequence number** – Enter an integer to specify the order that the tests should be performed in. Tests that have smaller sequence numbers will be run before tests that have larger sequence numbers.

        > [!NOTE]
        > We recommend that you leave a gap between sequence numbers. For example, set the **Sequence number** field to *10* for your first test, and then increment the value by 10 for each additional test. In this way, you can add new tests later without having to delete and re-create the lines to put them in the desired order.

    - **Test** – Select the test that you want to perform. For a qualitative test, select a test where the **Type** field is set to *Option*.
    - **Effective** – Select the first date when the test is valid. If you leave this field blank, there is no limit.
    - **Expiration** – Select the last date when the test is valid. If you leave this field blank or set it to *Never*, there is no limit.
    - **Test value determination** – Select how an AQL should be determined when multiple results are recorded for the same test. For a qualitative test, only *Manual* can be selected. If you select one of the other values (*Average*, *Minimum*, or *Maximum*), you will receive an error message when you save the test group.
    - **Attribute** – If you want to record test results on a batch attribute, select the attribute here, and select the **Update inventory batch attribute** check box.
    - **Update inventory batch attribute** – Select this check box to record test results for the batch attribute that is selected in the **Attribute** field.

1. In the lower part of the page, select the **General** tab. Some of the settings for the test that is selected on the **Overview** tab are repeated here. In addition, you can set the following fields for the test:

    - **Certificate of analysis report** – Set this option to *Yes* to indicate that the test results should be printed on the certificate of analysis (CoA). This report can be generated from the quality order.
    - **Action on failure** – Select either *Accept* or *Fail* to indicate whether the test should pass or fail if the AQL for it isn't met.
    - **Acceptable quality level** – Enter the total percentage of test results that must pass for the test to be considered passed.

1. In the lower part of the page, on the **Test** tab, set the following fields:

    - **Variable** – Select the test variable to record the qualitative test results for.
    - **Default outcome** – Select the default outcome that should be recorded for the test results.
    - **Test instrument** – Select the device that should be used for the test. If a test instrument is defined, it's automatically entered for the test in the test group.

1. Close the page.

## Add a quantitative test to a test group

To add a quantitative test to a test group, follow these steps.

1. Go to **Inventory management \> Setup \> Quality control \> Test groups**.
1. On the **Overview** tab in the upper part of the page, select the test group that you want to add a test to.
1. In the lower part of the page, on the **Overview** tab, select **Add** on the toolbar to add a row to the grid. Then set the following fields for the new row:

    - **Sequence number** – Enter an integer to specify the order that the tests should be performed in. Tests that have smaller sequence numbers will be run before tests that have larger sequence numbers.

        > [!NOTE]
        > We recommend that you leave a gap between sequence numbers. For example, set the **Sequence number** field to *10* for your first test, and then increment the value by 10 for each additional test. In this way, you can add new tests later without having to delete and re-create the lines to put them in the desired order.

    - **Test** – Select the test that you want to perform. For a quantitative test, select a test where the **Type** field is set to *Fraction* or *Integer*.
    - **Effective** – Select the first date when the test is valid. If you leave this field blank, there is no limit.
    - **Expiration** – Select the last date when the test is valid. If you leave this field blank or set it to *Never*, there is no limit.
    - **Test value determination** – Select how an AQL should be determined when multiple results are recorded for the same test. The available options are *Average*, *Minimum*, *Maximum*, and *Manual*.
    - **Attribute** – If you want to record test results on a batch attribute, select the attribute here, and select the **Update inventory batch attribute** check box.
    - **Update inventory batch attribute** – Select this check box to record test results for the batch attribute that is selected in the **Attribute** field.

1. In the lower part of the page, select the **General** tab. Some of the settings for the test that is selected on the **Overview** tab are repeated here. In addition, you can set the following fields for the test:

    - **Certificate of analysis report** – Set this option to *Yes* to indicate that the test results should be printed on the CoA. This report can be generated from the quality order.
    - **Action on failure** – Select either *Accept* or *Fail* to indicate whether the test should pass or fail if the AQL for it isn't met.
    - **Acceptable quality level** – Enter the total percentage of test results that must pass for the test to be considered passed.

1. In the lower part of the page, on the **Test** tab, set the following fields:

    - **Standard** – Enter the amount (integer or fraction) that is expected for the test results. The value that you enter will be entered by default in the test results. Additionally, it will automatically be entered as a default value in the **Min** and **Max** fields.
    - **Min** – Enter the minimum allowed value for the test results. The value that you enter must be less than the amount that is set in the **Standard** field. When you update the **Min** field, the **Min tolerance (%)** field is automatically updated. Likewise, when you update the **Min tolerance (%)** field, the **Min** field is automatically updated.
    - **Max** – Enter the maximum allowed value for the test results. The value that you enter must be more than the amount that is set in the **Standard** field. When you update the **Max** field, the **Max tolerance (%)** field is automatically updated. Likewise, when you update the **Max tolerance (%)** field, the **Max** field is automatically updated.
    - **Test instrument** – Select the device that should be used for the test. If a test instrument is defined, it's automatically entered for the test in the test group.

1. Close the page.

## Additional resources

- [Quality management test instruments](quality-management-processes.md)
- [Quality management tests](quality-management-processes.md)
- [Quality management test variables](quality-management-processes.md)
- [Quality associations](quality-management-processes.md)
- [Batch attributes](../production-control/batch-attributes.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
