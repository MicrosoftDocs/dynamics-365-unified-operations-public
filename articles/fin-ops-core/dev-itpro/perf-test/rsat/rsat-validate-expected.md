---
title: Validate expected values
description: Learn about how to use the Regression suite automation for validation of expected values, including how to validate the state of a control.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 01/21/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Validate expected values

[!include [banner](../../includes/banner.md)]

Validating expected values is an important part of a test case. Define validation parameters when you author your test cases by using Task Recorder. While recording, right-click on a control and select **CurrentValue** under the **Task Recorder > Validate** menu. This action adds a validation step that you can use with the Regression suite automation tool. The control value becomes a validation variable in the automatically generated Excel parameters file. The following image shows the menu item.

:::image type="content" source="media/validate-test-case.png" alt-text="Screenshot of Validate menu item.":::

For more information about how to create task recordings, see [Task recorder resources](../../user-interface/task-recorder.md).

When RSAT generates the Excel parameter file for a test case, it adds validation steps as shown in the following image. Enter the expected value to use during execution of the test case.

:::image type="content" source="media/rsat-validate-variables.png" alt-text="Screenshot of validate variables.":::

## Validate expected values by using operators

You can also use operators in validation steps to check that a variable isn't equal to, is less than, or is greater than a specified value. To use this feature, open the **Settings** tab and select the **Optional** tab. Turn on the setting named **Use operators for validation**. This option is available as of RSAT version 1.210. If you're using an older version of the tool, you must regenerate new Excel parameter files to take advantage of this functionality. In the Excel file, a new **Operator** field appears, as shown in the following image.

:::image type="content" source="media/validate-test-case-example.png" alt-text="Screenshot of Validation in Excel in earlier version.":::

## Validate the state of a control

When recording test cases, Task Recorder supports two extra validation actions:

+ Validate whether a control is enabled or disabled.
+ Validate whether a control is editable or read-only.

To take advantage of this validation, use a finance and operations app running on version 10.0.13 (or newer) and RSAT 2.0 (or newer). For more information, see [Validate](../../user-interface/task-recorder.md#validate).


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
