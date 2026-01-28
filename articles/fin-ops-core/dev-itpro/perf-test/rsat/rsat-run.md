---
title: Run test cases by using the Regression suite automation tool (RSAT)
description: Learn about how to load test cases from Azure DevOps, run tests, and save your work back to Azure DevOps, including an overview on how to modify test parameters.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 11/27/2023
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Use the Regression suite automation tool (RSAT)

[!include [banner](../../includes/banner.md)]

This article explains how to load test cases from Azure DevOps, generate automation files, modify test parameters, run and investigate results, and save your work back to Azure DevOps.

## Load test cases and create automation files

In RSAT, select the **Test Plans** tab and then select **Load** to download test cases and test case automation files. The local working directory receives all test cases and their corresponding attachments that belong to the test plan specified in the **Settings** tab.

:::image type="content" source="media/load-test-cases.png" alt-text="Screenshot of Load test cases.":::

Test cases are organized by test suites under a common test plan. These test suites are created in your Azure DevOps project. By using this tool, you can work with one test suite at a time.

If the tool fails to load any test case, verify that your test plan in Azure DevOps is properly created and contains the desired test suites and test cases.

If this is the first time you're using this test plan, the **Parameters File** column is blank. You must create test automation files for your test cases.

A test case requires the following attachments for successful execution:

+ A **recording file**: This recording file is created by the finance and operations Task recorder. It defines the steps of your test case. It's typically named **recording.xml**, but you can also name it to match the test case title in Azure DevOps. You attach it to the test case in Azure DevOps and download it into the **attachment** folder of the local working directory of the test case.
+ **Test automation files** consisting of **a test parameter file** (Microsoft Excel file) containing configurable test case parameters and **test execution files**: RSAT generates these files to enable automated execution of the test recording. Filenames are suffixed by **_Base.cs**, **_Base.xml**, and **_Base.dll**.

When a recording file is available with the test case, select **Generate** to generate test automation files in your working directory. If the test case doesn't already have an Excel test parameter file, the process creates one and it appears in the grid under **Parameters File**. Existing parameter files aren't affected.

To generate only **test execution files**, without affecting your parameter files, select **Generate > Generate Test Execution files only**.

Select **Generate > Generate Test Execution and Parameter files** to generate both test automation files and a new Excel parameter file in your working directory. This option is useful after you upload a new recording file that has changed steps, because it creates a new parameter file that has matching steps.

:::image type="content" source="media/rsat-test-cases.png" alt-text="Screenshot of List of test cases that were loaded.":::

You must generate test execution files when you install a new version of the tool, and when you modify or load a new version of the recording file. In this way, you update your execution files but also preserve the test parameter files.

:::image type="content" source="media/generate-execution-files.png" alt-text="Screenshot of Generate Test Execution files only menu item.":::

## Modify test parameters

This section describes how to modify Excel files to specify input and validation parameters for your test run. Select one or more test cases to modify, and then select the **Parameters** button (Microsoft Excel symbol) on the toolbar. An Excel window opens for each test case that you selected. Alternatively, you can open the Excel files directly from the working directory.

In addition to the **General** tab, the Excel parameter file contains a **MessageValidation** tab and a **TestCaseSteps** tab.

Select the **TestCaseSteps** tab to configure input and validation parameters for your test case. The input and validation parameters are placed directly next to their corresponding test case step, enabling test authors with context and a simple experience. When you modify parameters, it's clear what steps of the test case you're affecting. You can enter values or formulas in context. Color coding differentiates input parameters from validation steps.

:::image type="content" source="media/test-case-steps.PNG" alt-text="Screenshot of Test case steps.":::

Reusable variables that the recording process copies are also shown in the context of the test case step. You can easily locate a variable and copy it to use in subsequent steps and formulas. For more information, see [Copy variables to chain test cases](rsat-chain-test-cases.md).

:::image type="content" source="media/test-case-steps-rsat-var.png" alt-text="Screenshot of Test case steps variables.":::

Save the Excel files when you're done making edits, and make sure that you then select **Generate** to create new execution files that have the new parameters.

### Run a test as a specific user

By default, the admin role executes tests. If you want to run the test as a specific security role, specify the email address of a user under the **Test User** parameter in the **General** tab of the Excel parameter file. The **Test User** must be a valid user of the environments you're connecting to. The test runs under the security roles that the specific user belongs to. You need version 1.200 or newer for this feature to be functional.

:::image type="content" source="media/rsat-excel-general-tab.png" alt-text="Screenshot of General tab of the Excel parameter file.":::

### Run a test in the context of a specific company

The **General** tab of the Excel parameter file also allows you to specify the name of a legal entity (Company). The test runs in the context of this company. You can specify your default company in the **Settings** dialog box of the tool.

### Pause after a specific test step

You can insert a pause between specific test steps. Go to the **TestCaseSteps** tab of the Excel parameters file and insert a value (in seconds) in the pause column of a test step. This value pauses test case execution after the test step finishes.

:::image type="content" source="media/Pause-after-specific-step.png" alt-text="Screenshot of Pause set for Customer account field.":::

If you don't see the **Pause** column, you're using an older version of the Excel parameters file and need to regenerate it. Select the test case that you want, and then select **Generate \> Generate Test Execution and Parameter files**. This action might override any edits you made to the parameters file, so back up the existing Excel file first.

### Other notable test case execution settings

You might find the following settings useful. You can find them on the **General** tab of the Excel parameter file.

+ **Fail on warning message in the Infolog**: By default, test cases fail when an error occurs or a validation step fails. If you want a test case to also fail in response to a warning message, set the **Fail on warning message in the Infolog** option to **True**. This setting is useful, for example, if a test case adds a duplicate customer record. The default setting is **False**.
+ **Abort test suite execution on failure**: If you set the **Abort test suite execution on failure** option to **True**, execution of the test suite stops if the test case fails. All the remaining test cases have a status of **Not Executed**. The default setting is **False**.
+ **Pause between steps**: The number of seconds to pause between test steps. This setting affects every test step. The default value is **0** (zero).

### Infolog and message validation

Excel parameter files that are generated by using version 1.200 or newer contain a **MessageValidation** tab.

You can enter messages in this tab under **Message Validation**. After a test case completes execution, it validates that the messages specified here appear in the Infolog. The test case fails if these messages aren't found.

You can specify any expected messages, including error messages. Any message specified in this section causes a test case to fail unless it's found in the Infolog during execution. Two operators are available: **Equals** and **Contains**. If you use **Equals**, RSAT performs a string comparison with all messages in the Infolog and fails validation if the full message isn't found. If you use **Contains**, RSAT validates that at least one message in the Infolog contains the string you specify.

:::image type="content" source="media/message-validation.png" alt-text="Screenshot of Message validation example.":::

You can configure whether string comparison is case sensitive or not in the **Optional** page of the **Settings** tab.

## Run

Select **Run** to execute the selected test cases. You can only run test cases that have existing automation files. The tool opens and runs these tests by using the data you entered in Excel.

You can change the order of test case execution by using the up and down arrow buttons.

### Pause before a test case runs

Add a pause before a test case starts execution. To add a pause, update the **Pause (seconds)** cell on the **General** tab of the Excel parameters file for the test case.

### Stop a run

When a test run is in progress, select the **Stop** button on the toolbar to cancel the run. Execution stops after the currently running test case finishes. The remaining test cases are marked as **Not Executed** in Azure DevOps.

### Validate readiness of test automation files

Optionally, turn on a setting that validates whether your test cases are ready for execution. This setting prevents unknown errors related to the validity of recordings and test automation files. This option is available as of RSAT version 1.210. Enable it by selecting the **Settings** tab and then selecting the **Optional** tab.

:::image type="content" source="media/enable-local-file-validation-rules.png" alt-text="Screenshot of Setting for Enable local file validation rules.":::

When enabled, a background process continuously validates the following items for each test case.

+ The local working directory exists.
+ The Excel parameter file exists.
+ Test automation files (binary and XML files) needed for execution exist.
+ Test automation files are compatible with current version of RSAT. You must regenerate test automation files
when you install a new version of RSAT.
+ Test case ID specified in the Excel parameter file matches the test cases ID in Azure DevOps.

The **Valid** column in the grid indicates the result of the validation process. If validation fails, select the **X** in the **Valid** column to view the error and recommended action.

:::image type="content" source="media/enable-local-file-validation-rules-2.png" alt-text="Screenshot of Valid column grid.":::

## Investigate results

When all test cases finish running, the **Result** column shows **Pass** or **Fail**. Select the result to see error messages.

You can find more investigation details in Azure DevOps. To view this information, go to **Test > Runs** from your Azure DevOps project page.

:::image type="content" source="media/test-results.png" alt-text="Screenshot of Test results.":::

Select the test run that you want. It shows the results for all tests that ran during that test run.

:::image type="content" source="media/outcome-pie-chart.png" alt-text="Screenshot of Outcome pie chart.":::

:::image type="content" source="media/pass-fail.png" alt-text="Screenshot of Results for each test.":::

Open a failed test result and review the **ErrorMessage** section for information about the failure.

:::image type="content" source="media/error-message.png" alt-text="Screenshot of Error message information.":::

You can also find all error messages locally under `C:\Users\$YourUserName\AppData\Roaming\regressionTool\errormsg-<TestCaseId>.txt`.

### Test response times

In addition to execution logs, the test result shows the duration of a test case.

:::image type="content" source="media/test-duration.png" alt-text="Screenshot of Duration of a test case.":::

You can also review the response time of each step of the test case by opening the **BaseTime.xml** file attached to the test result.

:::image type="content" source="media/response-time.png" alt-text="Screenshot of Response time file.":::

You need version 1.200 or newer for response times to be available.

## Upload to Azure DevOps to commit your work

Select **Upload** to commit your work to Azure DevOps. This action uploads recordings and test automation files, including Excel test parameter files, for all selected test cases to Azure DevOps for future use. After you upload test automation files to Azure DevOps, the next time you use the Regression suite automation tool, even from a different computer, you can use **Load** and then **Run**, without generating test execution files or editing Excel parameter files.

In the upload menu, you can also choose to upload only recording files (Task recordings).

If you're unsure which test cases to select and you want to commit all changes since the last load to Azure DevOps, select **Upload all modified automation files** in the upload menu.

## Process compliance

RSAT provides capabilities for managing the readiness of test cases. It also provides a sign out process for test runs. You can configure this process in the **Process** tab under Settings.

:::image type="content" source="media/rsat-process-compliance-settings.png" alt-text="Screenshot of Process compliance file.":::

### Enforce test case readiness

Set up the test case so that it can't run unless it has a status of **Ready** in Azure DevOps. Select the **Enforce test case readiness** check box. By default, the check box is cleared.

### Signoffs

When your test run finishes, RSAT can create signoff work items in Azure DevOps. Select the **Sign-off tasks** check box. Then set the type of work item that each person who signs off should receive. You can select the **Functional**, **IT Manager**, or **Team Manager** role for signoffs, and then specify appropriate email addresses. RSAT creates work items in Azure DevOps and assigns them to owners for approval.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
