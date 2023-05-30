---
# required metadata

title: Quality management tests
description: This article describes how to create tests that can be used for quality orders in Microsoft Dynamics 365 Supply Chain Management.
author: yufeihuang
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.technology:

# optional metadata

ms.search.form: InventTestTable
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

# Quality management tests

[!include [banner](../includes/banner.md)]

This article describes how to create tests that can be used for quality orders in Microsoft Dynamics 365 Supply Chain Management.

You use the **Tests** page to define and view the individual tests that determine whether your products meet quality specifications. You can assign one or more individual tests to a test group. In this case, you also specify test-specific information, such as the acceptable measurement values. Measurement values are used for quantitative tests. For qualitative tests, test variables are used.

- For quantitative tests, the **Type** field is set to *Integer* or *Fraction*. A unit of measure is also specified. Quality specifications and test results are expressed as numbers.
- For qualitative tests, the **Type** field is set to *Option*. Qualitative tests require additional information about the test variable that is being measured and its enumerated options. Quality specifications and test results are expressed according to an outcome.

You can optionally assign a test instrument to a test. However, test instruments aren't required to create and use tests with quality orders. For more information, see [Quality management test instruments](quality-test-instruments.md).

You can also optionally specify a unit for a test, to indicate the unit of measure that test results are recorded in. For example, a test for temperature might include a unit of either degrees Fahrenheit or degrees Celsius.

## Example of a test

A manufacturing company performs two tests on purchased material: a quantitative test for material quality and a qualitative test for packaging damage. The company specifies additional information about the qualitative test to define the test variable (for example, damaged packaging) and its outcomes. The company uses the **Test groups** page to assign the two tests to a test group and to specify the test-specific information. The test group is assigned to a quality order so that the company can report test results for the two tests.

## Create a test

Follow these steps to create a test.

1. Go to **Inventory management \> Setup \> Quality control \> Tests**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Test** – Enter a unique ID or name for the test.
    - **Description** – Enter a detailed description of the test.
    - **Type** – Select the type of results that the test produces. For quantitative tests, select *Fraction* or *Integer*. For qualitative tests, select *Option*.
    - **Test instrument** – Select a [test instrument](quality-test-instruments.md) that should be used for the test.
    - **Unit** – If you selected *Fraction* or *Integer* in the **Type** field (that is, if the test is a quantitative test), select the unit of measure that test results should be recorded in.

1. Close the page.

> [!NOTE]
> After you save a test, you can no longer edit the **Type** field in the grid. If you must change the type of test results that will be recorded for a test, select **Change quality test type** on the Action Pane. In the **Change quality test type** dialog box, set the **New type** field to the desired type, and then select **OK** to close the dialog box.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management test groups](quality-test-groups.md)
- [Quality management test variables](quality-test-variables.md)
- [Quality associations](quality-associations.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
