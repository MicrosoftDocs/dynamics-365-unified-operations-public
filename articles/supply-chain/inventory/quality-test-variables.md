---
# required metadata

title: Quality management test variables
description: This article describes how to create test variables that can be used for qualitative tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.
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

# Quality management test variables

[!include [banner](../includes/banner.md)]

This article describes how to create test variables that can be used for qualitative tests on quality orders in Microsoft Dynamics 365 Supply Chain Management.

For every qualitative test that is defined on the **Tests** page, you must define a test variable and its possible outcomes (results). (For qualitative tests, the **Type** field on the **Tests** page is set to *Option*.)

You use the **Test variables** page to set up, edit, and view the possible outcomes for a test variable that is associated with a qualitative test. For each outcome, you assign an outcome status of either *Pass* or *Fail* to indicate whether the test is passed or failed when that outcome is selected as a test result. You use the **Test groups** page to assign a test variable and a default outcome for it to an individual qualitative test.

For every test variable, we recommend that you define at least two outcomes: one that has an outcome status of *Pass* and one that has an outcome status of *Fail*. There is no limit on the total number of variables or outcomes that can be defined. Additionally, multiple tests can use the same test variables to record results.

## Examples of test variables

### Example 1

A manufacturing company performs two tests on manufactured materials. In one test, the pH level is associated with a color strip. Acceptable pH levels are in lighter colors, and unacceptable pH levels are in darker colors. In another test, multiple visual inspections are performed, and quality workers use their judgement to determine whether the item passes or fails the visual inspection.

### Example 2

A manufacturing company that produces cookies uses an inspection test for the finished product. This inspection test has several variables. One variable is taste, and the possible outcomes for it are good and bad. A second variable is color, and the possible outcomes for it are too dark, too light, and correct.

## Create a test variable

Follow these steps to create a test variable.

1. Go to **Inventory management \> Setup \> Quality control \> Test variables**.
1. On the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Variable** – Enter a unique ID or name for the variable.
    - **Description** – Enter a detailed description of the variable.

1. While the new row is still selected, select **Outcomes** on the Action Pane.
1. On the **Test variable outcomes** page, on the Action Pane, select **New** to add a row to the grid. Then set the following fields for the new row:

    - **Outcome** – Enter a unique ID or name for the outcome.
    - **Description** – Enter a detailed description of the outcome.
    - **Outcome status** – Select either *Pass* or *Fail* to indicate whether the test is passed or failed when the outcome is selected as a test result.

1. Repeat the previous step for each additional outcome. Make sure that at least one outcome has an outcome status of *Pass* and at least one has an outcome status of *Fail*.
1. Close the pages.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management tests](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
