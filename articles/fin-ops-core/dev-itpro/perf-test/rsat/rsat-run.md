---
# required metadata

title: Run test cases by using the Regression suite automation tool (RSAT)
description: This topic explains how to load test cases from Azure DevOps, generate automation files, modify test parameters, run tests, investigate results, and save your work back to Azure DevOps.
author: robadawy
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21631
ms.search.region: Global
# ms.search.industry: 
ms.author: robadawy
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0

---

# Run test cases by using the Regression suite automation tool (RSAT)

[!include [banner](../../includes/banner.md)]

This topic explains how to load test cases from Azure DevOps, generate automation files, modify test parameters, run tests, investigate results, and save your work back to Azure DevOps.

## Load test cases and create automation files
In Azure DevOps, select **Load** to download test cases and test case automation files. All test cases belonging to the test plan specified in the **Settings** dialog box are downloaded.
 
![Load test cases](media/load-test-cases.png)

Test cases are organized by test suites under a common test plan. These are test suites you created in your Azure DevOps project. Using this tool, you can work with one test suite at a time.

If the tool fails to load any test case, verify that your test plan in Azure DevOps is properly created and contains the desired test suites and test cases.

If this is the first time you load this test plan, the **Parameters File** column will be blank. You will need to create test automation files for your test cases. Test automation files consist of:

+ Test parameter files (Microsoft Excel files contain test case parameters)
+ Other binary and XML files needed to execute the tests.

When you select **New**, test automation files are generated in your working directory. The Excel test parameter files will appear on the grid under **Parameters File**.

![List of test cases that were loaded](media/rsat-test-cases.png)
 
You can also generate **test execution files** only, without overwriting your parameter files. Select **New \> Generate Execution Files** to regenerate only execution files and leave Excel files unaffected. 

You must generate test execution files when you install a new version of the tool, and when you modify or load a recording file. In this way, you update your execution files but also preserve the test parameter files.

![Generate Test Execution files only menu item](media/generate-execution-files.png)

## Modify test parameters

This section describes how to modify Excel files to specify input and validation parameters for your test run. Select one or more test cases to modify, and then select the Microsoft Excel symbol on the toolbar. An Excel window is opened for each test case that you selected. Alternatively, you can open the Excel files directly from the working directory. 

In addition to the **General** tab, the Excel parameter file contains a data tab for every form that the test case visits.

Select the desired form (Excel tab) that you want to edit and identify the parameter values that you want to change. Values are identified by their control name. If you are not sure which control is correct, open the form in the application, right-click the control whose value you want to change, and select **form information**.

Save the Excel files when you are done making edits.

### Run a test as a specific user
By default, tests are executed using the admin role. If you want to run the test as a specific security role, specify the email address of a user under the **Test User** parameter in the **General** tab of the Excel parameter file. The **Test User** must be a valid user of the environments you are connecting to. The test will run under the security roles that the specific user belongs to. You need version 1.200 or newer for this feature to be functional.

![General tab of the Excel parameter file](media/rsat-excel-general-tab.png)
 
### Run a test in the context of a specific company
The **General** tab of the Excel parameter file also allows you to specify the name of a legal entity (Company). The test will run in the context of this company. You can specify your default company in the **Settings** dialog box of the tool.

### Other notable test case execution settings

**Fail on warning message in the Infolog**

By default, test cases fail when an error occurs or a validation step fails. If you want a test case to fail
in response to a warning message too, set the **Fail on warning message in the Infolog** option to **True** on the **General** tab of the Excel parameter file. This setting is useful if, for example, a test case adds a duplicate customer. The default setting is **False**.

**Abort test suite execution on failure**

If you set the **Abort test suite execution on failure** option to **True**, execution of the test suite is aborted if the test case fails. All the remaining test cases will have a status of **Not Executed**. The default setting is **False**.

**Pause between steps**

The number of seconds to pause between test steps. The default value is **0** (zero).

### Infolog and message validation
Excel parameter files that are generated using version 1.200 or newer contain a **MessageValidation** tab.

You can enter messages in this tab under **Message Validation**. After a test case completes execution, it validates that the messages specified here appear in the Infolog. The test case will fail if these messages are not found.

You can specify any expected messages including error messages that are expected. If an expected error occurred, but exists in this section, the test will not fail.
 
![Message validation example](media/message-validation.png)


## Run
Select **Run** to execute the selected test cases. Only test cases with existing automation files can be run. The tool will open and execute these tests with the data you entered in Excel.

You can modify the order in which test cases are executed using the up and down arrow buttons.

### Pause prior to a test case run 
You can add a pause before a test case starts execution. If you want to pause, update the cell **Pause (seconds)** on the **General** tab of the Excel parameters file.

## Investigate results
When all test cases complete execution, **Pass** or **Fail** will be populated in the **Result** column. You can click on the result to see error messages.

Additional investigation details are available in Azure DevOps. To view this information, from your Azure DevOps project page, go to **Test > Runs**.

![Test results](media/test-results.png)

Select the desired test run. It will include the results of all tests that were executed during that run.
 
![Outcome pie chart](media/outcome-pie-chart.png)

![Results for each test](media/pass-fail.png)

You can open a failed test result and review the **ErrorMessage** section for information about the failure.
 
![Error message information](media/error-message.png)

All error messages are also available locally under **C:\Users\$YourUserName\AppData\Roaming\regressionTool\errormsg-<TestCaseId>.txt**.

### Test response times
In addition to execution logs, the duration of a test case is also available in the test result.
 
![Duration of a test case](media/test-duration.png)

You can also review the response time of each step of the test case by opening the **BaseTime.xml** file attached to the test result.
 
![Response time file](media/response-time.png)

You need version 1.200 or newer for response times to be available.

## Save your work
To preserve your work, select **Upload**. This will upload test automation files, including Excel test parameter files, of all selected test cases to Azure DevOps for future use.
After test automation files are uploaded to Azure DevOps, the next time you use the Regression suite automation tool, even from a different computer, you can simply use **Load** and then **Run**, without generating test execution files or editing Excel parameter files.

## Process compliance
RSAT provides capabilities for managing the readiness of test cases. It also provides a sign-off process for test runs.

![Process compliance file](media/rsat-process-compliance-settings.png)

### Enforce test case readiness

You can set up the test case so that it isn't run unless it has a status of **Ready** in Azure DevOps. In the **Settings** dialog box, on the **Process** tab, select the **Enforce test case readiness** check box. By default, the check box is cleared.

### Signoffs

When your test run is completed, RSAT can create sign-off work items in Azure DevOps. In the **Settings** dialog box, on the **Process** tab, select the **Sign-off tasks** check box. Then set the type of work item that should be created for each person who signs off. You can select **Functional**, **IT Manager** and **Team Manager** roles for sign-offs, and then specify appropriate email addresses. Work items will then be created in Azure DevOps and assigned to owners for approval.

