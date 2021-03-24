---
# required metadata

title: Quality management tests
description: This topic describes how you can use create tests for use with quality orders in Dynamics 365 Supply Chain Management.
author: rachel-profitt
manager: tfehr
ms.date: 03/23/2021
ms.topic: article
ms.prod:
ms.service: dynamics-ax-applications
ms.technology:

# optional metadata

ms.search.form: InventTestTable
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

# Quality management tests

[!include [banner](../includes/banner.md)]

This topic describes how you can create and use tests for use with quality orders in Dynamics 365 Supply Chain Management.

Use the **Tests** page to define and view the individual tests that determine whether your products meet quality specifications. You can assign one or more individual tests to a test group. In this case, you also specify test-specific information, such as the acceptable measurement values. Measurement values are used for quantitative tests, and test variables are used for qualitative tests.

- A quantitative test has a test **Type** of *Integer* or *Fraction*, and also has a designated unit of measure. Quality specifications and test results are expressed as numbers.
- A qualitative test has a test **Type** of *Option*. Qualitative tests require additional information about the test variable that is being measured and its enumerated options. Quality specifications and test results are expressed according to an outcome.

You can optionally assign a test instrument to a test; however, test instruments are not required to create and use tests with Quality orders. For more information, refer to [Quality management test instruments](quality-test-instruments.md).

You can also optionally specify a unit for a test. When a unit is specified this indicated the unit of measurement that results are recorded in for this test. For example, a test for the temperature might include a unit of either centigrade or fahrenheit.

## Example of a test

A manufacturing company performs two tests on purchased material: a quantitative test about material quality and a qualitative test about packaging damage. The company defines additional information about the qualitative test to identify the test variable such as damaged packaging, and its outcomes. The company uses the **Test groups** page to assign the two tests to a test group and to specify the test-specific information. The test group is assigned to a quality order, so that the company can report test results for the two tests.

## Create a test

To create a test:

1. Go to **Inventory management > Setup > Quality control > Tests**.
1. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Test** - Enter a unique ID or name for the test.
    - **Description** - Enter a detailed description for the test.
    - **Type** - Select the type of results produced by the test. For quantitative tests, choose *Fraction* or *Integer*. For qualitative tests, choose *Option*.
    - **Test instrument** - Select a [test instrument](quality-test-instruments.md) to be used for the test.
    - **Unit** - Select the unit of measurement to be used for recording the test results for tests with a **Type** of *Fraction* or *Integer*.
1. Close the page.

> [!NOTE]
> Once you save a test, you can no longer edit the **Type** field in the grid. If you need to change the type of test result that will be recorded for a test, select **Change quality test type** on the Action Pane to open the **Change quality test type** dialog box. Then set **New type** to the desired type and select **OK** to close the dialog box.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management test groups](quality-test-groups.md)
- [Quality management test variables](quality-test-variables.md)
- [Quality associations](quality-associations.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]