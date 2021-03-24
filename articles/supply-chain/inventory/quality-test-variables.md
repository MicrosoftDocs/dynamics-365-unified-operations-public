---
# required metadata

title: Quality management test variables
description: This topic describes how you can use and create test variables for use with qualitative tests on quality orders in Dynamics 365 Supply Chain Management.
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

# Quality management test variables

[!include [banner](../includes/banner.md)]

This topic describes how you can use and create test variables for use with qualitative tests on quality orders in Dynamics 365 Supply Chain Management.

Use the **Test variables** page to set up, edit, and view the possible results for a test variable that is associated with a qualitative test. For each outcome, you assign a **pass** or **fail** status. You must define a variable and its outcomes for each qualitative test that is defined on the **Tests** page. (For qualitative tests, the test **Type** is set to *Option* on the **Tests** page.) Use the **Test groups** page to assign a test variable and the default outcome to an individual qualitative test.

The recommended practice is that each test variable must have at least two **Outcomes** defined; one outcome with an **Outcome status** of Pass, and one outcome with an **Outcome status** of Fail. There is no limit to the total number of variables or outcomes that can be defined. Many tests can also use the same test variables for recording results.

## Examples of a test variable

**Example 1**: A manufacturing company performs two tests on manufactured materials. One test uses a test strip to associate the level of the pH to a color strip. Acceptable pH levels are lighter colors and unacceptable pH levels are darker colors. In another test, multiple visual inspections are performed and the quality worker uses their subjective judgement to determine if the item passes or fails the visual inspection.

**Example 2**: A manufacturing company that produces cookies uses an inspection test for the finished product. This inspection test has several variables. One variable is taste, and the possible outcomes for this variable are good and bad. A second variable is color, and the possible outcomes are too dark, too light, and correct.

## Create a test variable

To create a test variable:

1. Go to **Inventory management > Setup > Quality control > Test variables**.
1. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Variable** - Enter a unique ID or name for the variable.
    - **Description** - Enter a detailed description for the variable.
1. With your new row still selected, select **Outcomes** on the Action Pane.
1. The **Test variable outcomes** page opens. Select **New** on the Action Pane to add a new row to the grid and then make the following settings for it:
    - **Outcome** - Enter a unique ID or name for the outcome.
    - **Description** - Enter a detailed description for the outcome.
    - **Outcome status** - Select either *Pass* or *Fail* to indicate if the test will pass or fail when this outcome is selected on a test result.
1. Repeat the previous step for each additional outcome, and make sure that at least one outcome has an **Outcome status** of *Pass* and one with *Fail*.
1. Close the pages.

## Additional resources

- [Quality management test instruments](quality-test-instruments.md)
- [Quality management tests](quality-tests.md)
- [Quality management test groups](quality-test-groups.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]