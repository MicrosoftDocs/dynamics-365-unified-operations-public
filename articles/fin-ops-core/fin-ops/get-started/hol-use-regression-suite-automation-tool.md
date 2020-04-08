---
# required metadata

title: Use the Regression suite automation tool tutorial
description: This topic shows how to use Regression suite automation tool (RSAT). It describes various features and provides examples that use advanced scripting. 
author: robinarh
manager: AnnBe
ms.date: 06/09/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form:
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 21761
ms.search.region: Global
# ms.search.industry: 
ms.author: rhaertle
ms.search.validFrom: 2017-06-30
ms.dyn365.ops.version: AX 7.0.0, Operations

---

# Use the Regression suite automation tool tutorial

[!include [banner](../includes/banner.md)]

> [!NOTE]
> Use your internet browser tools to download and save this page in pdf format. 

This tutorial walks through some of the advanced features of the Regression suite automation tool (RSAT), includes a demo assignment, and describes strategy and key learning points. 

## Notable Features of RSAT and Task recorder

### Validate a field value

RSAT allows you to include validation steps within your test case to validate expected values. For information about this feature, see the article [Validate expected values](../../dev-itpro/perf-test/rsat/rsat-validate-expected.md).

The following example shows how you can use this feature to validate whether the on-hand inventory is more than 0 (zero).

1. In the demo data in the **USMF** company, create a task recording that has the following steps:

    1. Go to **Product information management \> Products \> Released products**.
    2. Use the Quick Filter to find records. For example, filter on a value of **1000** for the **Item number** field.
    3. Select **On-hand inventory**.
    4. Use the Quick Filter to find records. For example, filter on a value of **1** for the **Site** field.
    5. In the list, mark the selected row.
    6. Validate that the value of the **Total available** field is **411.0000000000000000**.

2. Save the task recording and attach it to your test case in Azure Devops.
3. Add the test case to the test plan, and load the test case into RSAT.
4. Open the Excel parameter file. On the **InventOnhandItem** tab, you will see a **Validate InventOnhandItem** section that includes an **Operator** field.

    ![Operator field](./media/use_rsa_tool_08.png)

5. To validate whether the inventory on-hand will always be more than 0, change the value of the **Value** field from **411** to **0** and the value of the **Operator** field from an equal sign (**=**) to a greater than sign (**\>**).

    ![Values of the Value and Operator fields changed](./media/use_rsa_tool_09.png)

6. Save and close the Excel parameter file.
7. Select **Upload** to save the changes that you made to the Excel parameter file to Azure DevOps.

Now, if the value of the **Total Available** field for the specified item in inventory is more than 0 (zero), tests will pass, regardless of the actual on-hand inventory value.

### Saved variables and chaining of test cases

One of the key features of RSAT is the chaining of test cases, that is, the ability of a test to pass variables to other tests. For more information, see the article [Copy variables to chain test cases](../../dev-itpro/perf-test/rsat/rsat-chain-test-cases.md).

### Derived test case

RSAT lets you use the same task recording with multiple test cases, enabling a task to run with different data configurations. See the article [Derived test cases](../../dev-itpro/perf-test/rsat/rsat-derived-test-cases.md) for more information.

### Validate notifications and messages

This feature can be used to validate whether an action occurred. For example, when a production order is created, estimated, and then started, the app shows a "Production – Start" message to notify you that the production order has been started.

![Production – Start notification](./media/use_rsa_tool_05.png)

You can validate this message through RSAT by entering the message text on the **MessageValidation** tab of the Excel parameter file for the appropriate recording.

![Message Validation tab](./media/use_rsa_tool_06.png)

After the test case is run, the message in the Excel parameter file is compared to the message that is shown. If the messages don't match, the test case will fail.

> [!NOTE]
> You can enter more than one message on the **MessageValidation** tab in the Excel parameter file. The messages also can be error or warning messages instead of informational messages.

### Snapshot

This feature takes screenshots of the steps that were performed during task recording. It is useful for auditing or debugging purposes.

- To use this feature, open the **Microsoft.Dynamics.RegressionSuite.WindowsApp.exe.config** file under the RSAT installation folder (for example, **C:\\Program Files (x86)\\Regression Suite Automation Tool**), and change the value of the following element from **false** to **true**.

    ```xml
    <add key="VerboseSnapshotsEnabled" value="false" />
    ```

When your run the test case, RSAT will generate snapshots (images) of the steps in the playback folder of the test cases in the working diretory. If you are using an older version of RSAT, the images are saved to **C:\\Users\\\<Username\>\\AppData\\Roaming\\regressionTool\\playback**, a separate folder is created for each test case that is run.

## Assignment

### Scenario

1. The product designer creates a new released product.
2. The production manager initiates a production order to bring the stock level to two pieces.
3. Manufacturing starts and ends the production order, and verifies that the on-hand quantity is two pieces.
4. The sales team receives an order for four pieces of the new product. Therefore, the sales team updates the net requirements via the dynamic plan. Because no additional capacity is available, the default order policy is set to "buy instead of make." Therefore, a planned purchase order is created.
5. The buyer adds a vendor, firms the planned purchase order, and then confirms the purchase order.
6. When the goods that were purchased arrive at the store, the store operator searches the related purchase order and receives the goods. Because the order is now completed, goods can be picked and packed against the sales order.
7. Finance posts the purchase invoice and sales invoice.

The following illustration shows the flow for this scenario.

![Flow for the demo scenario](./media/use_rsa_tool_14.png)

The following illustration shows the business processes hierarchy for this scenario in the LCS Business Process Modeler.

![Business processes for the demo scenario](./media/use_rsa_tool_15.png)

## Strategy – Key learning

### Data

- Make sure that you have representative data volumes (a copy of production/golden configuration data plus migrated data).
- When you generate new data via Task recorder, create test names that won't conflict with existing names (for example, use a prefix such as **RSATxxx**).
- Use Azure Point-In-Time restore to rerun tests in non-Tier 1 environments.
- Although you can use the **RANDOM** and **NOW** Excel functions to generate a unique combination, the effort is considerably high. Here is an example.

    ```Excel
    product = "AT" &TEXT(NOW(),"yyymmddhhmm")
    ```

### Task recorder

- Define scenarios before you start recording. A well-managed project has predefined test scenarios. To build a test case, consider how predictable the outcome of those test scenarios is.
- Split recordings if they are performed by different roles, or if there is waiting time or an external event before the next step.
- Avoid selecting values in lists. Instead, use text formats, such as **FIFO**, **AudioRM**, and **SiteWH**. When you select in a list, the position of the value in the list is recorded, not the value itself. If items are added to that list, the position of the value can change. Therefore, your recording will use a different parameter, and the rest of the scenario might be affected.
- Think about multi-user behavior. For example, don't assume that your newly created sales order will always be automatically selected. Instead, always use the filter to find the correct order.
- Use the Copy function in Task recorder to save the name of a newly created product so it can be used in chained test cases.
- Use the Validate function in Task recorder to set checkpoints that verify that steps have been run correctly.

### RSAT

- To run the test in another company, you can change the company on the **General** tab of the Excel parameter file. Make sure that settings and data are available in the newly selected company.
- You can change the test user on the **General** tab of the Excel parameter file. Specify the email ID of the user who will run the test case. In this way, the test case can be run by using the security permissions of the specified user.
- To wait before the test is started, you can define a pause on the **General** tab of the Excel parameter file. This pause can be used in a batch job (for example, if a workflow must be run before the next step can be performed.)

## Advanced scripting

### CLI

RSAT can be called from a **Command Prompt** or **PowerShell** window.

> [!NOTE]
> Verify that the **TestRoot** environment variable is set to the RSAT installation path. (In Microsoft Windows, open **Control Panel**, select **System and Security \> System \> Advanced system settings**, and then select **Environment Variables**.)

1. Open a **Command Prompt** or **PowerShell** window as an admin.
2. Navigate to the RSAT installation directory.

    ```Console
    cd "c:\Program Files (x86)\Regression Suite Automation Tool\"
    ```

3. List all commands.

    ```Console
    C:\Program Files (x86)\Regression Suite Automation Tool>Microsoft.Dynamics.RegressionSuite.ConsoleApp.exe help

    Usage:
        Microsoft.Dynamics.RegressionSuite.ConsoleApp.exe command
        or
        Microsoft.Dynamics.RegressionSuite.ConsoleApp.exe /settings "C:\Path to\file.settings" command

    Available commands:
        ?
        about
        cls
        download
        edit
        generate
        generatederived
        generatetestonly
        generatetestsuite
        help
        list
        listtestplans
        listtestsuite
        listtestsuitenames
        playback
        playbackbyid
        playbackmany
        playbacksuite
        quit
        upload
        uploadrecording
        usage
    ```

#### ? 
Shows help about all available commands and their parameters.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``?``**``[command]``

##### Optional parameters

**``command``**


Where ``[command]`` is one of the commands specified below.


#### about
Displays the current version.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``about``**

#### cls
Clears the screen.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``cls``**


#### download
Downloads attachments for the specified test case to the output directory. 
You can use the ``list`` command to get all available test cases. Use any value from the first column as a **test_case_id** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``download``**``[test_case_id] [output_dir]``

##### Required parameters
**``test_case_id``** Represents the test case ID.  
**``output_dir``** Represents the output directory. The directory must exist.

##### Examples

``download 123 c:\temp\rsat``   
``download 765 c:\rsat\last``


#### edit
Allows you to open parameters file in Excel program and edit it.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``edit``**``[excel_file]``

##### Required parameters
**``excel_file``** Must contain a full path to an existing Excel file.

##### Examples
``edit c:\RSAT\TestCase_123_Base.xlsx``  
``edit e:\temp\TestCase_456_Base.xlsx``


#### generate
Generates test execution and parameter files for the specified test case in the output directory.
You can use the ``list`` command to get all available test cases. Use any value from the first column as a **test_case_id** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``generate``**``[test_case_id] [output_dir]``

##### Required parameters
**``test_case_id``** Represents the test case ID.  
**``output_dir``** Represents the output directory. The directory must exist.

##### Examples
``generate 123 c:\temp\rsat``  
``generate 765 c:\rsat\last``


#### generatederived
Generates a new test case, derived from the provided test case. 
You can use the ``list`` command to get all available test cases. Use any value from the first column as a **test_case_id** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``generatederived``**``[parent_test_case_id] [test_plan_id] [test_suite_id]``

##### Required parameters
**``parent_test_case_id``** Represents the parent test case ID.  
**``test_plan_id``** Represents the test plan ID.  
**``test_suite_id``** Represents the test suite ID.

##### Examples
``generatederived 123 8901 678``


#### generatetestonly
Generates only test execution file for the specified test case in the output directory. 
You can use the ``list`` command to get all available test cases. Use any value from the first column as a **test_case_id** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``generatetestonly``**``[test_case_id] [output_dir]``

##### Required parameters
**``test_case_id``** Represents the test case ID.  
**``output_dir``** Represents the output directory. The directory must exist.

##### Examples
``generatetestonly 123 c:\temp\rsat``  
``generatetestonly 765 c:\rsat\last``


#### generatetestsuite
Generates all test cases for the specified suite in the output directory.
You can use ``listtestsuitenames`` command to get all available test suits. Use any value from the column as a **test_suite_name** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``generatetestsuite``**``[test_suite_name] [output_dir]``

##### Required parameters
**``test_suite_name``** Represents the test suite name.  
**``output_dir``** Represents the output directory. The directory must exist.

##### Examples
``generatetestsuite Tests c:\temp\rsat``   
``generatetestsuite Purchase c:\rsat\last``


#### help
Identical to the [?](#section) command


#### list
Lists all available test cases.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``list``**


#### listtestplans
Lists all available test plans.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``listtestplans``**


#### listtestsuite
Lists test cases for the specified test suite. 
You can use ``listtestsuitenames`` command to get all available test suites. Use any value from first column as **suite_name** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``listtestsuite``**``[suite_name]``

##### Required parameters
**``suite_name``** Name of the desired suite.

##### Examples
``listtestsuite "sample suite name"``  
``listtestsuite NameOfTheSuite``


#### listtestsuitenames
Lists all available test suites.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``listtestsuitenames``**


#### playback
Plays back a test case using an Excel file.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``playback``**``[excel_file]``

##### Required parameters
**``excel_file``** A full path to the Excel file. File must exist. 

##### Examples
``
playback c:\RSAT\TestCaseParameters\sample1.xlsx
playback e:\temp\test.xlsx
``


#### playbackbyid
Plays back multiple test cases at once.
You can use the ``list`` command to get all available test cases. Use any value from the first column as a **test_case_id** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``playbackbyid``**``[test_case_id1] [test_case_id2] ... [test_case_idN]``

##### Required parameters
**``test_case_id1``** ID of exisiting test case.  
**``test_case_id2``** ID of exisiting test case.  
**``test_case_idN``** ID of exisiting test case.  

##### Examples
``playbackbyid 878``  
``playbackbyid 2345 667 135``


#### playbackmany
Plays back many test cases at once, using Excel files.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``playbackmany``**``[excel_file1] [excel_file2] ... [excel_fileN]``

##### Required parameters
**``excel_file1``** Full path to the Excel file. File must exist.  
**``excel_file2``** Full path to the Excel file. File must exist.  
**``excel_fileN``** Full path to the Excel file. File must exist.  

##### Examples
``playbackmany c:\RSAT\TestCaseParameters\param1.xlsx``  
``playbackmany e:\temp\test.xlsx f:\rsat\sample1.xlsx c:\RSAT\sample2.xlsx``


#### playbacksuite
Plays back all test cases from the specified test suite. 
You can use ``listtestsuitenames`` command to get all available test suites. Use any value from first column as **suite_name** parameter.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``playbacksuite``**``[suite_name]``

##### Required parameters
**``suite_name``** Name of the desired suite.

##### Examples
``playbacksuite suiteName``  
``playbacksuite sample_suite``


#### quit
Closes the  application.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``quit``**


#### upload
Uploads all files belonging to the specified test suite or test cases.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``upload``**``[suite_name] [testcase_id]``

#### Required parameters
**``suite_name``** All files belonging to the specified test suite will be uploaded.
**``testcase_id``** All files beloning to the specified test case(s) will be uploaded.

##### Examples
``upload sample_suite``  
``upload 123``  
``upload 123 456``


#### uploadrecording
Uploads only recording file belonging to the specified test cases.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``uploadrecording``**``[testcase_id]``

##### Required parameters
**``testcase_id``** Recording file belonging to the specified test cases will be uploaded.

##### Examples
``uploadrecording 123``  
``uploadrecording 123 456``


#### usage
Shows two ways to invoke this application: one using a default setting file, another one providing a setting file.

``Microsoft.Dynamics.RegressionSuite.ConsoleApp``**``usage``**


### Windows PowerShell examples

[!IMPORTANT] The example scripts below are provided AS IS for illustration purposes and are not supported by Microsoft.

#### Run a test case in a loop

You have a test script that creates a new customer. Via scripting, this test case can be run in a loop by randomizing the following data before each iteration is run:

- Customer ID
- Customer name
- Customer address

The customer ID will be in the format *ATCUS\<number\>*, where \<number\> is a value between **000000001** and **999999999**.

The following example uses one parameter, **start**, to define the first number that is used. Is uses a second parameter, **nr**, to define the number of customers that must be created. For each iteration, the parameters in the Excel parameter file are changed by using an UpdateCustomer function. Then the RSAT command line is called in a RunTestCase function.

Open Microsoft Windows PowerShell Integrated Scripting Environment (ISE) in admin mode, and paste the following code into the window that is named **Untitled1.ps1**.

```powershell
param ( [int]$start = 1, [int]$nr = 1 )
function UpdateCustomer
{
    param ([string]$paramFilename, [string]$sheetName, [string]$CustId)
    $xl = New-Object -COM "Excel.Application"
    $xl.Visible = $false
    $wb = $xl.Workbooks.Open($paramFilename)
    $ws = $wb.Sheets.Item($sheetName)
    $ws.Cells.Item(3, 2).Value = "ATCUS" + $CustId
    $ws.Cells.Item(4, 2).Value = "Automated Test Customer " + $CustId
    $ws.Cells.Item(8, 2).Value = "Automated Test Street " + $CustId
    $wb.Save()
    $wb.Close()
    $xl.Quit()
    [System.Runtime.Interopservices.Marshal]::ReleaseComObject($xl)
}
function RunTestCase
{
    param ( [string]$filename )
    $cmd = "cd c:\Program Files (x86)\Regression Suite Automation Tool\ &&  "
    $cmd = $cmd + "Microsoft.Dynamics.RegressionSuite.ConsoleApp.exe playback "
    $cmd = $cmd + $filename
    cmd /c $cmd
}
$excelFilename = "full path to Excel parameter file"
l$sheetName = "DirPartyQuickCreateForm"
for ($i = $start; $i -lt $start + $nr; $i++ )
{
    $CustomerId = $i.ToString("000000000")
    Write-Host "customer : " $CustomerId
    UpdateCustomer $excelFilename $sheetName $CustomerId
    RunTestCase $excelFilename
```

#### Run a script that depends on data in Microsoft Dynamics 365

The following example uses an Open Data Protocol (OData) call to find the order status of a purchase order. If the status isn't **invoiced**, you can, for example, call an RSAT test case that posts the invoice.

```xpp
function Odata_Get
{
    Param ( [string] $environment, [string] $cmd )
    [Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
    $tenant = "your tenant"
    $creds = @{
        grant_type = "client_credentials"
        client_id = "your client application Id"
        client_secret = "your client secret"
        resource = $environment
    }
    $headers = $null
    $bearer = Invoke-RestMethod https://login.microsoftonline.com/$tenant/oauth2/token -Method Post -Body $creds -Headers $headers;
    $headers = @{
        Authorization = "Bearer " + $bearer.access_token
    }
    $Odata_cmd = $environment + '/data/' + $cmd
    return (Invoke-RestMethod -Uri $Odata_cmd -Method Get -Headers $headers -ContentType application/json )
}
function PurchaseOrderStatus
{
    Param ( [string] $environment, [string] $purchaseOrderNumber )
    $cmd = 'PurchaseOrderHeaders?$filter=PurchaseOrderNumber eq '
    $cmd = $cmd + "'" + $purchaseOrderNumber + "'"
    $response = Odata_Get -environment $environment -cmd $cmd
    return $response.value.PurchaseOrderStatus
}
$environment = "https://your environment"
$orderStatus = PurchaseOrderStatus -environment $environment -purchaseOrderNumber '000003'
if ($orderStatus -eq $null) {   write-host 'doesn''t exist'}
elseif ($orderStatus -ne 'invoiced') { RunTestCase "PostInvoice" }
```
