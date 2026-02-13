---
title: Create and automate user acceptance tests
description: Learn about using Task guides and BPM to create and execute acceptance test suites, including the process of creating a scenario acceptance testing BPM library.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 01/22/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 
ms.dyn365.ops.version: 2012
ms.assetid: 
---

# Create and automate user acceptance tests

[!include [banner](../includes/banner.md)]

Use Task recorder and Business process modeler (BPM) to create user acceptance test libraries. Task recorder is a powerful tool to record test cases and organize them by business process using BPM. As a Microsoft partner, use BPM to distribute test libraries to your customers via Lifecycle Services and Lifecycle Services solutions. If you're a customer, use BPM to author and distribute test libraries across different projects and teams.

Because you can synchronize BPM with Azure DevOps (formerly known as Visual Studio Team Services), you can automatically create test cases (including test steps) in your Azure DevOps project. Azure DevOps can then serve as your test configuration and test management tool where you can create targeted test plans and test suites, manage the execution of tests, and investigate results. For more information about testing with Azure DevOps, see [What are test plans, test suites, and test cases?](/azure/devops/test/create-a-test-plan#what-are-test-plans-test-suites-and-test-cases)

This article walks through the process of creating and executing acceptance test suites to use for manual or automated testing.

## Create a Scenario Acceptance Testing BPM library

BPM is a great Lifecycle Services tool to describe a hierarchy of business processes and user tasks. Lifecycle Services also allows Microsoft partners and customers to author and distribute BPM libraries across Lifecycle Services projects via the Asset library. This section describes how to take advantage of BPM to define your acceptance test library.

### Create a BPM library

You can create a Business process modeler (BPM) library in several ways. For more information about how to create libraries in BPM, see [Create, edit, and browse Business process modeler (BPM) libraries](creating-editing-browsing.md).

For illustration purposes, this article uses a library that contains common business processes, such as create an expense report and approve order requests. The article uses the Excel import functionality to create the library.  

:::image type="content" source="./media/import-from-excel.PNG" alt-text="Screenshot of Import from Excel dialog.":::

### Record test cases and save to BPM

After you create a BPM library, use Task recorder to create your test cases and then upload the cases to BPM. You can use several methods to do this.

If you're using a BPM library that already has all of the necessary task recordings (test cases) attached, you can skip this step. Otherwise, follow the instructions in this section to create new task recordings.

#### Create and save a new task recording

> [!NOTE]
> Starting in January 2026, you can only create, edit, or use Task Recordings in Sandbox and Production environments.  Cloud-hosted environments no longer have this capability.

1. Open the client and sign in.
1. Select the company that you want to use while recording.
1. Go to **Settings** > **Task recorder**.

    :::image type="content" source="./media/select_task_recorder.PNG" alt-text="Screenshot of Select Task recorder option.":::

1. Select **Create a new recording**.
1. Enter a name for the recording, and then select **Start**. Recording begins the moment that you select **Start**.
1. When the recording is complete, in the Task recorder pane, select **Stop**.
1. To save the task recording to an attached BPM, select **Save to Lifecycle Services**.

    :::image type="content" source="./media/task_recorder_options.PNG" alt-text="Screenshot of Task recorder options.":::

1. Select the library that you want to save the recording to, and then select **Save**. Otherwise, select **Save to Disk** and follow the steps in the next section, "Upload an AXTR file to BPM."

 >[!NOTE]
 > To enable the effective execution of your tests using automation tools, make sure all of your task recordings start on the main dashboard of your application.
 > For end-to-end processes that are performed by more than one user, divide your task recordings into user-specific tasks. This approach simplifies the maintenance of test cases and allows you to execute test cases in the context of security roles, which is a best practice.

#### Upload an AXTR file to BPM

If you save your recordings (AXTR files) to disk, follow these steps to upload them to BPM.

1. In Lifecycle Services, in your project, on the **Business process libraries** page, select the library to upload the task recording to.
1. Select **Author and edit** and in the lines, locate and select the process to upload the task recording to.
1. In the right pane, select **Upload**.

    :::image type="content" source="./media/upload_axtr_1.PNG" alt-text="Screenshot of Upload AXTR step 1.":::

1. Select **Browse** to find and select the file to upload, and then select **Upload**.

    :::image type="content" source="./media/upload_axtr_2.PNG" alt-text="Screenshot of Upload AXTR step 2.":::

#### Save an existing task recording to BPM

> [!NOTE]
> Starting in January 2026, you can only create, edit, or use Task Recordings in Sandbox and Production environments.  Cloud-hosted environments no longer have this capability.

1. To attach an existing task recording, sign in to the client.
1. Go to **Settings** > **Task recorder**.
1. Select **Edit Task Recording** and attach the file by either saving directly to Lifecycle Services or downloading the AXTR and then uploading to BPM.

### Guidelines for recording test cases

Follow these guidelines when authoring and recording your test cases, especially if you're planning to automate test execution.
The process and tools described in this article apply to business process acceptance tests. They aren't meant to replace component and unit testing that is typically owned by developers.

- Author a limited number of test cases that, when combined, cover complete end-to-end processes.
- Focus on business processes that have been customized.
- An individual test case (recording) should cover one or two business tasks only, typically executed by one person. This simplifies task recording maintenance. Don't combine a complete end-to-end business process such as "Procure to Pay" or "Order to Cash" into one large task recording. For example, instead of having RFQ > Purchase Order > Product Receipt > Vendor Invoice > Vendor Payment as one test case, divide the process into three or four test cases. You'll have the opportunity to combine these tests into an ordered test suite later.
- A test case should have at least one validation. Try to validate critical fields that cover the impact of other fields. For example: Validation of totals on sales or purchase orders cover the unit price/quantity/discount/tax ...etc.
- Avoid printing a report in a test case. If a test case needs to print a report, it should be selected on screen.
- 80+% of test cases should be of transactions or source documents. Master data should be limited to up to 20% of test cases only.

## Synchronize and configure your test plan in Azure DevOps

An acceptance test library is your starting point. It typically contains all test cases (task recordings) of a particular application organized by business process. During a particular test pass, you usually don't need to execute all test cases. What test cases you select depends on the phase of your implementation or the nature of the update you're planning to apply to your production environment. Azure DevOps enables you to organize your test cases in test plans and test suites. A test plan contains one or more test suites (A subset of your test library); test cases can belong to more than one test suite.

Once you have selected your acceptance testing BPM library, synchronize it with Azure DevOps and create your test plan and test suites.

### Sync with Azure DevOps

Synchronize your BPM library with your Azure DevOps project. For more information, see [Synchronize BPM libraries with Azure DevOps](synchronize-bpm-vsts.md#configure-your-lifecycle-services-project-to-connect-to-azure-devops).

After configuration is complete, synchronize the BPM library with an Azure DevOps project.

1. On the **Business process libraries** page, on the tile for the library that you want to synchronize, select the ellipsis button (…), and then select **Azure DevOps sync**.

    :::image type="content" source="./media/vsts_sync_1.png" alt-text="Screenshot of VSTS Sync step 1.":::

    You can also start Azure DevOps synchronization from the toolbar in a BPM library. Select the ellipsis button (…), and then select **Azure DevOps sync**.

    :::image type="content" source="./media/vsts_sync_2.png" alt-text="Screenshot of VSTS Sync step 2.":::

1. After Azure DevOps synchronization is complete, select the ellipsis button (…), and then select **Sync test cases**.

    :::image type="content" source="./media/sync_test_case.PNG" alt-text="Screenshot of Sync test cases option.":::

1. When this step is complete, your task recordings become test cases in Azure DevOps, and a link appear under the **Requirements** tab.

    :::image type="content" source="./media/view_test_case.PNG" alt-text="Screenshot of View test case.":::

In addition to the test steps, the task recording XML file is attached to the Azure DevOps test case. This file is needed if you want to automate test execution.

### Create a test suite in Azure DevOps

Next, you need to create a test plan and test suite in Azure DevOps. This allows you to execute an ordered suite of test cases and easily manage, investigate, and track the results.

1. Sign in to Azure DevOps and select the project and test plan that you want to test in.
1. On the toolbar, select **Test** > **Test Plans**.
1. In the left pane, select **+**, and then select **Static suite**.
1. Enter a name for the suite.
1. Select **Add existing** and query the tag **Lifecycle Services:Test Cases**.
1. Select **Run** > **Add test cases**.

    :::image type="content" source="./media/add_test_cases.PNG" alt-text="Screenshot of Add test cases dialog.":::

1. Select the test case to view details and the attached XML file.

    :::image type="content" source="./media/test_case_details.PNG" alt-text="Screenshot of Test case details.":::

 >[!NOTE]
 > This example shows how to create one comprehensive acceptance test suite with all test cases added. Instead, you should create various test suites under the same test plan and then use custom queries to add specific test cases to a test suite. A test case can belong to more than one test suite.

## Execute your tests

### Run manual test cases

After you have a test suite, you are ready to use it for regression testing after updates have been made to your application in a sandbox or test environment. You can run the test cases in your test suite manually or play the task recordings that are part of the test suite and use Azure DevOps to mark the test cases as passed or failed.

:::image type="content" source="./media/vsts_test_marked.png" alt-text="Screenshot of VSTS test marked as passed or failed.":::

Azure DevOps also provides a tool, **Test Runner**, to manage manual test case execution. For more information about using Test Runner, see [Run manual tests](/vsts/manual-test/getting-started/run-manual-tests).

We recommend that you take advantage of Azure DevOps as it provides a rich set of management features not only for testing, but result management and mitigation.

### Run automated test cases

The platform for finance and operations provides developers with tools to author test cases based on task recordings and use Azure DevOps to manage the automated execution of these test cases.

Developers can use the build and test automation capabilities of **build and test** environments. For details, see the [Continuous delivery home page](../dev-tools/continuous-delivery-home-page.md).

Functional power users can automate the execution of their test cases using the **Regression suite automation tool**. For more information, [download the tool](https://www.microsoft.com/download/details.aspx?id=57357) and read the [Regression suite automation tool](../perf-test/rsat/rsat-overview.md).

#### Investigate test runs

Once an automated run is complete, on the Azure DevOps toolbar, select **Test > Runs** (or **Test Plans > Runs**) to investigate your test run. Select the desired test run to investigate test case failures and errors. You can also go to your test suite in Azure DevOps to see the latest results associated with your test cases.
For more information on testing and test management in Azure DevOps, see the [Azure DevOps documentation](/azure/devops).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
