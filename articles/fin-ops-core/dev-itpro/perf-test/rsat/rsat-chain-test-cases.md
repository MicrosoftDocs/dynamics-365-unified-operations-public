---
title: Copy variables to chain test cases
description: Learn about how the Regression Suite Automation Tool can be used to chain test cases, which is the ability of a test to pass values to other tests.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Copy variables to chain test cases

[!include [banner](../../includes/banner.md)]

One of the key features of the Regression Suite Automation Tool is the chaining of test cases, that is, the ability of a test to pass values to other tests. You execute test cases in the order you define in the Azure DevOps test plan. You can also update this order in the test tool itself. If you want to pass variables from one test case to another, make sure you order the tests correctly.

To save the value of a variable while recording the test in Task Recorder, right-click the field and select **Task recorder > Copy**, as shown in the following image. Copying saves the variable in the recording file. You can use this variable in subsequent tests.

:::image type="content" source="media/task-recorder-copy.png" alt-text="Screenshot of the Copy menu item in task recorder.":::

When RSAT generates the Excel parameters file, saved variables appear in the **Saved variables** table on the **General** Tab. These variables also appear in the context of the test case steps in the **TestCaseSteps** tab. In the following image, the purchase order ID value was copied during the recording of the test case (step 5). This value is stored in a variable named **{{PurchCreateOrder_PurchTable_PurchId_86_Copy}}**.

:::image type="content" source="media/saved-variables.png" alt-text="Screenshot of saved variables in Excel.":::

To reuse these variables during test playback, copy the variable name and use it in place of a parameter value in the data file of another test (or the same test), as shown in the following image. You can use variables directly by their name in cells with strings, such as cell D4. When you use variables in formulas, always enclose the variable name in double quotation marks to make the variable part of a string. For example, in cell D9, the variable should be enclosed in double quotation marks.

:::image type="content" source="media/reuse-variables.png" alt-text="Screenshot of reusing variables in Excel.":::

You can use variables in the same test case where you define them. You can also pass variables between tests during the same test run.

## Support for formulas of saved variables

You can create formulas that contain saved (copied) variables. If you use an older version of the Regression Suite Automation Tool, you need to regenerate new Excel parameter files to take advantage of this functionality. Supported operators are `+`, `-`, `/`, and `\`. Only numerical variables can be used in the Regression Suite Automation Tool formulas. Strings or dates aren't supported. Always enclose variable names in double braces, enclose each variable in double quotation marks, and get the value of each variable by using the **VALUE** function. For example, `VALUE("{{var1}}") + VALUE("{{var2}}")`.

In the following image, two different variables are used in a formula.

:::image type="content" source="media/formulas.png" alt-text="Screenshot of creating a formula in Excel.":::

As of RSAT version 1.220, you can also use Excel functions, such as **ROUND**, **CONCAT**, and **UPPER**, to create formulas with RSAT variables. This feature is implemented by using the Excel formula evaluation functionality, so any function supported by Excel is supported by RSAT.

This behavior changed in RSAT version 2.6. Variables that contain numeric values are now considered a string and should be converted to their number value by using the **VALUE** function.

For example,

+ To round a value to the nearest whole number, use:

    `=ROUND(VALUE("{{Item_Price_3274_Copy}}"), 0)`

+ To concatenate strings, use:

    `=CONCAT("{{AccountNum_3274_Copy}}", " ", "{{AddressBP_Locator_3274_Copy}}")`

+ To calculate and format a date and convert it to a string, use:

    `=TEXT(DATEVALUE("{{SystemDate_CurrentDate_3276_Copy}}") - 1, "mm/dd/yyyy")`

    Always convert RSAT date values to text for reliable test case execution.

RSAT evaluates these formulas during test execution, so you must precede the formula with a single quote **\'** to prevent Excel from attempting to prematurely calculate the formula. An example is shown in this image.

:::image type="content" source="media/formulas-2.png" alt-text="Screenshot of creating a formula in Excel with single quote prefix.":::

## Use variables in message validation

You can also use a saved variable as part of a string in the Message Validation tab. Here's an example that validates the message `Customer account {{variable name}} already exists`. It appears in the Infolog during test execution. `{{variable name}}` is a variable that the recording copies.

You can use saved (copied) variables within the same test case or across more than one test case in the same test suite.

:::image type="content" source="media/rsat-message-with-variable.png" alt-text="Screenshot of message with variable.":::


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
