---
title: Set up and install Regression suite automation tool tutorial
description: Access a tutorial that shows how to set up and install Regression suite automation tool (RSAT), including an overview of key concepts.
author: frankdahl
ms.author: johnmichalak
ms.topic: tutorial
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-05-30
ms.dyn365.ops.version: AX 7.0.0, Operations
ROBOTS: NOINDEX, NOFOLLOW
ms.custom: sfi-image-nochange
---

# Set up and install Regression suite automation tool tutorial

This article is a tutorial that helps you set up and get started with RSAT and the tools associated with using RSAT.

[!include [banner](../../includes/banner.md)]

> [!NOTE]
> Use your internet browser tools to download and save this page in PDF format.

## Key concepts

- Understand the installation and prerequisite setup that are required for the various applications that support Regression suite automation tool (RSAT).
- Understand how the Task recorder feature, together with Microsoft Dynamics Lifecycle Services and Microsoft Azure DevOps, let you create, configure, run, investigate, and report on test cases.
- Empower functional users to record business tasks by using Task recorder, and then convert the task recordings into a suite of automated tests, without having to write source code.

## Before you begin

### Prerequisites

- An environment that runs Microsoft Dynamics 365 for Finance and Operations version 10.0 (April 2019) or later is required for this tutorial. For customers who are using Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3, Platform update 20 (PU20) or later is also supported.
- Admin rights to the environment.
- Access to the customer tenant Lifecycle Services and Azure DevOps (previously known as Microsoft Visual Studio Team Services [VSTS]).
- An Azure DevOps Test Plans or Test Manager license for the user creating and managing tests suites. The following licenses also give you access to Test Plans:
    - Visual Studio Enterprise license
    - Visual Studio Test Professional license
    - MSDN Platforms subscriber license
- RSAT must have access to the test environment via a web browser.
- To generate and edit test parameters, Microsoft Excel must be installed.

## Configure Azure DevOps

### User eligibility

Make sure that the user is created in Azure DevOps and has a subscription level that provides access to Azure Test Plans. An Azure DevOps Test Plans license is required only if the user creates and manages test cases (that is, not all RSAT users require this license). For information about the license requirements, see [License requirements](/azure/devops/test/manual-test-permissions#license-requirements).

### Create a new Azure DevOps project

RSAT uses Azure DevOps for test case and test suite management, reporting, and investigating test run results.

> [!NOTE]
> You can use an existing Azure DevOps project. However, if your existing Azure DevOps project is set up with a custom template, you receive a "VSTS Sync Failure" error when you sync test cases from Business process modeler (BPM) to Azure DevOps (see the [Test the synchronization from BPM to Azure DevOps](#test-the-synchronization-from-bpm-to-azure-devops) section). If the following best practices are followed for the custom template, you can sync the test cases to Azure DevOps. (These best practices are listed in the error message.)

- Do not delete any work item types or out-of-the-box fields.
> - Don't delete any work item types or out-of-the-box fields.
> - Don't delete any state of a work item type.

> - Don't add any required fields to a work item type.

Otherwise, for this tutorial, we recommend that you create a new Azure DevOps project. For more information, see [Issues when syncing to BPM using a custom Azure DevOps (VSTS) process template](https://blogs.msdn.microsoft.com/lcs/2018/11/28/issues-when-syncing-to-bpm-using-a-custom-azure-devops-vsts-process-template/).

1. Open the Azure DevOps URL (`https://dev.azure.com/<Azure DevOps Name>`).
1. Select **Create project** in the upper-right corner of the Azure DevOps page.

    :::image type="content" source="./media/setup_rsa_tool_03.png" alt-text="Screenshot of Create project button.":::

1. Fill in the following fields, and then select **Create**:

    - **Project name**
    - **Version control** – Select **Team Foundation Version Control**. The default option, **Git**, isn't supported.
    - **Work item process**

    :::image type="content" source="./media/setup_rsa_tool_04.png" alt-text="Screenshot of Create new project dialog box.":::

### Create a personal access token

In this tutorial, you use the Lifecycle Services Business Process Modeler (BPM) to create a test case library and synchronize your test cases with Azure DevOps. You need a personal access token to sync BPM with Azure DevOps.

1. Select the profile icon in the upper-right corner of the page for your Azure DevOps project. Then, select **Security**.

    :::image type="content" source="./media/setup_rsa_tool_05.png" alt-text="Screenshot of Security command.":::

1. In the left pane, under **Security**, select **Personal access tokens**. Then select **New Token**.

    :::image type="content" source="./media/setup_rsa_tool_06.png" alt-text="Screenshot of New Token button on the Personal access tokens tab in User settings.":::

1. Fill in the following fields, and then select **Create**:

    - **Name**
    - **Expiration (UTC)** – Select **Custom defined**, and then use the date picker to select the last available date.
    - **Scopes** – Select the **Full access** option.

    :::image type="content" source="./media/setup_rsa_tool_07.png" alt-text="Screenshot of Create a new personal access token dialog box.":::

    > [!NOTE]
    > Make a note of the personal access token that you create. You need it later when you set up the RSAT configuration.

    :::image type="content" source="./media/setup_rsa_tool_08.png" alt-text="Screenshot of Personal access token.":::

## Configure the Lifecycle Services project

You need a Lifecycle Services project for your master test library. Use the Lifecycle Services Business Process Modeler (BPM) as the master library for your test cases. BPM manages and distributes test libraries across Lifecycle Services projects. For example, a Microsoft partner or independent software vendor (ISV) building test libraries releases test cases in the form of BPM libraries. In BPM, test cases are organized by business process. BPM doesn't define the execution order or frequency of your test pass. You manage these details in Azure DevOps, as described later in this article.  

For your Lifecycle Services project, you can use an existing customer implementation or partner project.

### Update the Lifecycle Services language

> [!NOTE]
> For the user interface (UI) to correctly show business processes, set the Lifecycle Services preferred language to **English (United States)**.

1. Go to the Lifecycle Services implementation project.
1. Select the **Settings** button (the gear symbol) in the upper-right corner, and then select **Language preference**.

    :::image type="content" source="./media/setup_rsa_tool_09.png" alt-text="Screenshot of Update language preference.":::

1. In the **Preferred language** field, select **English (United States)**, and then select **Save**.

    :::image type="content" source="./media/setup_rsa_tool_10.png" alt-text="Screenshot of Language preference tab in User settings.":::

### Configure Lifecycle Services to connect to the Azure DevOps project

If you created a new Azure DevOps project earlier, configure the Lifecycle Services project to connect to it. Otherwise, if your Lifecycle Services project is already connected to your Azure DevOps project, you can continue to the next section.

1. Go to the Lifecycle Services implementation project.
1. Select the **Menu** button, and then select **Project settings**.

    :::image type="content" source="./media/setup_rsa_tool_11.png" alt-text="Screenshot of Project settings command.":::

1. In the left pane, select **Visual Studio Team Services**, and then select **Setup Visual Studio Team Services**.

    :::image type="content" source="./media/setup_rsa_tool_12.png" alt-text="Screenshot of Visual Studio Team Services tab in Project settings.":::

1. In the **Azure DevOps site URL** field, enter the URL of the Azure DevOps site. In the **Personal access token** field, enter the personal access token that you created earlier.

    > [!NOTE]
    > Although VSTS is now known as Azure DevOps, to connect Lifecycle Services to your Azure DevOps project, use the old URL. For example, the Azure DevOps URL that is used in this tutorial is `https://dev.azure.com/D365FOFastTrack/`. However, in the following illustration, it's entered as `https://D365FOFastTrack.visualstudio.com/`.


1. Select **Continue**.
1. In the **Visual Studio Team Services project** field, select the VSTS project on the selected site to link with the Lifecycle Services project. The **Process template** field is set to **Agile** by default. For a custom template, review the best practice guidance in the [Create a new Azure DevOps project](#create-a-new-azure-devops-project) section. Then select **Continue**.

    :::image type="content" source="./media/setup_rsa_tool_14.png" alt-text="Screenshot of Step 2 in Setup Visual Studio Team Services.":::

1. Review your settings, and then select **Save**.

    :::image type="content" source="./media/setup_rsa_tool_15.png" alt-text="Screenshot of Step 3 in Setup Visual Studio Team Services.":::

1. Select **Authorize** to authorize Lifecycle Services to access the configured Azure DevOps site on your behalf and to turn on features that integrate with VSTS.

    :::image type="content" source="./media/setup_rsa_tool_16.png" alt-text="Screenshot of Authorize button.":::

1. A message box appears that states, "You are about to be redirected to an eternal site to authorize Lifecycle Services to connect to Visual Studio Team Services on your behalf. Proceed?" Select **Yes**.

    :::image type="content" source="./media/setup_rsa_tool_17.png" alt-text="Screenshot of Message box.":::

1. Select **Accept**.

    :::image type="content" source="./media/setup_rsa_tool_18.png" alt-text="Screenshot of Authorizing access.":::

1. If you're authorized as a user, the UI returns to the Lifecycle Services project settings page.

    :::image type="content" source="./media/setup_rsa_tool_19.png" alt-text="Screenshot of Authorized user.":::

### Create a new BPM library

1. Go to the Lifecycle Services implementation project.
1. Select the **Menu** button, and then select **Business process modeler**.

    :::image type="content" source="./media/setup_rsa_tool_20.png" alt-text="Screenshot of Business process modeler command.":::

1. Select **New library**.

    :::image type="content" source="./media/setup_rsa_tool_21.png" alt-text="Screenshot of New library button.":::

1. In the **Library name** field, enter a name, and then select **Create**. For this tutorial, name the BPM library **RSAT**.

    :::image type="content" source="./media/setup_rsa_tool_22.png" alt-text="Screenshot of Create new library dialog box.":::

1. Open the new **RSAT** BPM library.
1. Select the **Sample Core Business Process** process, and then, on the right, select **Edit mode**.

    :::image type="content" source="./media/setup_rsa_tool_23.png" alt-text="Screenshot of Edit mode button.":::

1. Change the value of both the **Name** field and the **Description** field to **Create a product**. Then select **Save**.

    :::image type="content" source="./media/setup_rsa_tool_24.png" alt-text="Screenshot of Name and Description fields.":::

## Environment

### Version requirement

You need a test or sandbox environment that runs version 10. If you're using version 7.3, Platform update 20 or later also supports this feature.

> [!NOTE]
> RSAT must access your test environment through a web browser.

### User criteria

The user must have admin rights to this environment.

### Set up Help settings to connect with Lifecycle Services

Complete this step to connect to Lifecycle Services. By using this connection, you can save task recordings to the appropriate BPM library in Lifecycle Services through the client.

1. Open the client.
1. Go to **System Administration \> Setup \> System parameters**.
1. On the **Help** tab, in the **Lifecycle Services help configuration** field, select the relevant Lifecycle Services project (**RSAT** for this tutorial).

    :::image type="content" source="./media/setup_rsa_tool_25.png" alt-text="Screenshot of Lifecycle Services help configuration field on the Help tab.":::

    BPM libraries are filled in under the appropriate Lifecycle Services project.

1. Select **Save**.
1. You might need to refresh the browser to see the updated Help content.

    :::image type="content" source="./media/setup_rsa_tool_26.png" alt-text="Screenshot of Notification about refreshing the browser.":::

## Task recordings

> [!NOTE]
> Make sure that all your task recordings start on the main dashboard. Keep individual recordings short, and focus on one business task, such as creating a sales order.

### Create a task recording and save it to the BPM library

Create a task recording that you can attach to the simple business process you created in the new BPM library.

1. Open the client.
1. On the main dashboard, select the **Settings** button (the gear symbol), and then select **Task recorder**.

    :::image type="content" source="./media/setup_rsa_tool_27.png" alt-text="Screenshot of Select Task recorder on Settings menu.":::

1. Select **Create recording**.

    :::image type="content" source="./media/setup_rsa_tool_28.png" alt-text="Screenshot of Create recording button.":::

1. Fill in the **Recording name** and **Recording description** fields, and then select **Start**.

    :::image type="content" source="./media/setup_rsa_tool_29.png" alt-text="Screenshot of Recording name and Recording description fields.":::

1. Record the steps for creating a product. When you finish, select **Stop** to stop recording.

    :::image type="content" source="./media/setup_rsa_tool_30.png" alt-text="Screenshot of Steps for creating a product.":::

1. Select **Save to Lifecycle Services**.

    :::image type="content" source="./media/setup_rsa_tool_31.png" alt-text="Screenshot of Save task recording to Lifecycle Services.":::

    Library information is loaded from Lifecycle Services.

    :::image type="content" source="./media/setup_rsa_tool_32.png" alt-text="Screenshot of Loading library information.":::

1. Select the BPM library to associate the task recording with. For this tutorial, select the **RSAT** BPM library that you created earlier and the **Create a product** business process under it. Then select **OK**.

    :::image type="content" source="./media/setup_rsa_tool_33.png" alt-text="Screenshot of Associating the task recording with a BPM library and a business process.":::

    A "Saving to Lifecycle Services was successful" message appears.

    :::image type="content" source="./media/setup_rsa_tool_34.png" alt-text="Screenshot of Message about a successful save to Lifecycle Services.":::

1. If you want to save the task recording locally and then upload it to BPM through Lifecycle Services, follow these steps:

    1. After the recording is completed, select **Save to this PC**.

        :::image type="content" source="./media/setup_rsa_tool_35.png" alt-text="Screenshot of Save to this PC.":::

    1. In the browser's notification bar, select **Save** or **Save As** to save the file on your local computer.

        :::image type="content" source="./media/setup_rsa_tool_36.png" alt-text="Screenshot of Notification bar.":::

    1. Go to the **RSAT** BPM library, and select the business process to save the task recording against.
    1. On the **Overview** tab, select **Upload**.

        :::image type="content" source="./media/setup_rsa_tool_37.png" alt-text="Screenshot of Upload button.":::

    1. Select **Browse**, and select the .axtr file that you saved earlier. Then select **Upload**.

        :::image type="content" source="./media/setup_rsa_tool_38.png" alt-text="Screenshot of Selecting the .axtr file to upload.":::

### Test the synchronization from BPM to Azure DevOps

Now that you attached a task recording to the business process, validate that you can sync the business process and the associated task recording to Azure DevOps as a feature and a test case (respectively) by using the VSTS sync feature in Lifecycle Services.

> [!NOTE]
> The corresponding work item type that is created in Azure DevOps varies, depending on the process template that you selected when you configured the Lifecycle Services project with Azure DevOps, as described in the [Create a new Azure DevOps project](#create-a-new-azure-devops-project) section.

1. Go to the BPM library, and open the **RSAT** library that you created earlier.
1. Select the ellipsis button (**...**), and select **VSTS sync**.

    :::image type="content" source="./media/setup_rsa_tool_39.png" alt-text="Screenshot of VSTS sync command on the ellipsis menu.":::

    After VSTS sync completes, a **Requirements** tab appears on the left side and includes the corresponding Azure DevOps work item.

    > [!NOTE]
    > The work item that is created in Azure DevOps has the BPM library name as the title prefix.

    :::image type="content" source="./media/setup_rsa_tool_40.png" alt-text="Screenshot of Requirements tab.":::

1. Refresh the page.
1. Select the ellipsis button (**...**). You see an additional option, **Sync test cases**. Select this option.

    :::image type="content" source="./media/setup_rsa_tool_41.png" alt-text="Screenshot of Sync test cases command on the ellipsis menu.":::

    > [!NOTE]
    > If the **Sync test cases** option isn't available after you refresh the page, go to main page for BPM, and select **Sync test cases** for the whole library itself. In this way, you effectively force a synchronization for the whole library.
    >
    > :::image type="content" source="./media/setup_rsa_tool_42.png" alt-text="Screenshot of Selecting Sync test cases for the whole library.":::

    After Sync test cases completes, a new test case is created on the **Requirements** tab.

    :::image type="content" source="./media/setup_rsa_tool_43.png" alt-text="Screenshot of New test case on the Requirements tab.":::

1. Go to your Azure DevOps project, and select **Boards \> Work Items**.

    :::image type="content" source="./media/setup_rsa_tool_44.png" alt-text="Screenshot of Work Items command under Boards.":::

1. Validate that the work item and test case that you created through BPM synchronization exist.

    :::image type="content" source="./media/setup_rsa_tool_45.png" alt-text="Screenshot of Work item and test case.":::

## Install and configure RSAT

You can install RSAT on any computer that runs Windows 10 and that can connect to the environment through a web browser.

> [!NOTE]
> Before you installing a new version of the tool, uninstall the previous version.

### Install an authentication certificate

To enable authentication, generate and install a certificate on the same computer that RSAT runs on.

#### Generate a certificate

1. To generate a certificate file, open a Microsoft Windows PowerShell window as an admin, and run the following command.

    ```powershell
    $certificate = New-SelfSignedCertificate -dnsname 127.0.0.1 -CertStoreLocation cert:\LocalMachine\My -FriendlyName "D365 Automated testing certificate" -Provider "Microsoft Strong Cryptographic Provider"
    ```

1. Open certificate manager by entering **certlm.msc** in the **Run** dialog box, and confirm that the **D365 Automated testing certificate** certificate is created under **Personal \> Certificates**.

    > [!NOTE]
    > Be sure to enter **certlm.msc**, not **certmgr.msc**, because the certificates are stored on the local computer.

    :::image type="content" source="./media/setup_rsa_tool_46.png" alt-text="Screenshot of D365 Automated testing certificate certificate.":::

1. Right-click the certificate, and then select **Copy**.
1. Go to **Trusted Root Certification Authorities \> Certificates**.

    :::image type="content" source="./media/setup_rsa_tool_47.png" alt-text="Screenshot of Certificates folder under the Trusted Root Certification Authorities folder.":::

1. On the **Action** menu, select **Paste** to copy the certificate to the **Trusted Root Certification Authorities** location.

    :::image type="content" source="./media/setup_rsa_tool_48.png" alt-text="Screenshot of Paste command on the Action menu.":::

1. To get the thumbprint of the installed certificate, but without spaces or special characters, open a Windows PowerShell window as an admin, and run the following commands.

    ```powershell
    cd Cert:\LocalMachine\My

    Get-ChildItem | Where-Object { $_.Subject -like "CN=127.0.0.1" }
    ```

    > [!NOTE]
    > Save the thumbprint, because you need it later when you update the .wif files for Application Object Server (AOS) and set up the RSAT configuration.

#### Configure the AOS computer to trust the connection

> [!NOTE]
> If the environment is a Tier 2+ environment, update the certificate thumbprint in the wif.config file for **all** AOS computers for the environment.

1. Establish a Remote Desktop Protocol (RDP) connection to the AOS computer. Sign-in details are available on the environment details page in Lifecycle Services.
1. Open Microsoft Internet Information Services (IIS), and find **AOSService** in the list of sites.

    :::image type="content" source="./media/setup_rsa_tool_49.png" alt-text="Screenshot of AOSService in the list of sites.":::

1. Right-click **Explore** to open the **\<Drive\>: \\AosService\\WebRoot** folder. Find the **wif.config** file.

    :::image type="content" source="./media/setup_rsa_tool_50.png" alt-text="Screenshot of Wif.config file in the WebRoot folder.":::

1. Update the **wif.config** file by adding a new authority entry for your certificate and authority name, as shown in the following example.

    ```Xml
    <issuerNameRegistry type="Microsoft.Dynamics.AX.Security.SharedUtility.AxIssuerNameRegistry,Microsoft.Dynamics.AX.Security.SharedUtility">
        <authority name="CN=127.0.0.1">
            <keys>
                <add thumbprint="xxxxxxxxxxxxxxxxxxxx" />
                <add thumbprint="xxxxxxxxxxxxxxxxxxxx" />
            </keys>
            <validIssuers>
                <add name="CN=127.0.0.1" />
            </validIssuers>
        </authority>
    ```

    > [!NOTE]
    > If multiple users use the same application, each user must generate separate thumbprints, and each of those thumbprints must be added in the **\<keys\>** section.

1. If there's more than one AOS computer, repeat steps 3 through 4 for each additional computer.

    > [!NOTE]
    > Unlike older Tier 2 environments, new Tier 2 environments are deployed with two AOS instances.

1. Run **iisreset** on all the AOS computers.

    > [!NOTE]
    > If you don't have admin rights to run **iisreset** on a Tier 1 computer, on the Environment details page in Lifecycle Services, select Maintain > Restart services.

#### Tier 2+ environment

If you use a Tier 2+ environment (Standard Acceptance Test sandbox or higher), verify or set the following registry setting on the computer where you install RSAT. This step helps you avoid authentication or RSAT connection errors.

```PowerShell
if ((Test-Path HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319))
{
    Set-ItemProperty HKLM:\SOFTWARE\Wow6432Node\Microsoft\.NETFramework\v4.0.30319 -Name SchUseStrongCrypto -Value 1 -Type dword -Force -Confirm:$false
}
```

### Install RSAT

1. Go to <https://www.microsoft.com/download/details.aspx?id=57357>, and select **Download**.
1. Select all the files, and then select **Next**.

    :::image type="content" source="./media/setup_rsa_tool_51.png" alt-text="Screenshot of Selecting all files.":::

1. Double-click the .msi package to run the installer. When the installation finishes, select **Finish**.

    :::image type="content" source="./media/setup_rsa_tool_52.png" alt-text="Screenshot of RSAT Installer file.":::

### Install Selenium and browser drivers

In older versions of RSAT, you had to install Selenium and browser drivers. You no longer need to install these drivers because the installation process automatically installs them.

1. The first time you open RSAT, a prompt asks if you want to automatically download and install Selenium. For more information, see the [Configure RSAT](#configure-rsat) section.
1. Before you can run a test case, a prompt asks if you want to automatically download and install the browser driver that corresponds to the default browser selected in the RSAT configuration. For more information, see the [Load and run test cases](#load-and-run-test-cases) section.

## Get started with RSAT

### Create a test plan and test suites

1. Go to the Azure DevOps project, and select **Test Plans**.

    :::image type="content" source="./media/setup_rsa_tool_53.png" alt-text="Screenshot of Test plans command.":::

1. Select **New Test Plan**.

    :::image type="content" source="./media/setup_rsa_tool_54.png" alt-text="Screenshot of New Test Plan button.":::

1. Fill in the **Name** field, and then select **Create**. For this tutorial, name the test plan **RSAT Test Plan**.

    :::image type="content" source="./media/setup_rsa_tool_55.png" alt-text="Screenshot of New Test Plan dialog box.":::

1. Select the plus sign (**+**), and then select **Static suite** to create a static suite under the new test plan. Name the new test suite **T01 – Make to Stock**.

    > [!NOTE]
    > You can also create a query-based suite if you want the new test cases from BPM to automatically be pulled into the RSAT test suite.

    :::image type="content" source="./media/setup_rsa_tool_56.png" alt-text="Screenshot of Creating a static suite.":::

### Attach test cases to test suites

1. Select **Add existing** on the right side to add existing test cases to the test suite.

    :::image type="content" source="./media/setup_rsa_tool_57.png" alt-text="Screenshot of Add existing button.":::

1. On **Add test cases to suite**, select **Run query**, and then select the test case to add to the test suite. For this tutorial, select the **Create a new product** test case. Then select **Add test cases** in the lower-right corner of the page (this button isn't shown in the following illustration).

    :::image type="content" source="./media/setup_rsa_tool_58.png" alt-text="Screenshot of Run query button.":::

    The test case is added to the **T01-Make to Stock** test suite.

    :::image type="content" source="./media/setup_rsa_tool_59.png" alt-text="Screenshot of Test case added to the test suite.":::

### Configure RSAT

1. Open RSAT.

    :::image type="content" source="./media/setup_rsa_tool_60.png" alt-text="Screenshot of RSAT icon.":::

1. You receive a warning message that states, "The Regression Suite Automation Tool requires Selenium, do you want to automatically download and install it now?" Select **Yes**.

    :::image type="content" source="./media/setup_rsa_tool_61.png" alt-text="Screenshot of Warning message that Regression Suite Automation Tool requires Selenium.":::

1. Select the **Settings** button (the gear symbol) in the upper-right corner. In the dialog box that appears, fill in the following fields:

    - **Azure DevOps Url** – Enter the URL of your Azure DevOps project, such as `https://yourAzureDevOpsUrlHere.visualStudio.com`.
    - **Access Token** – Enter the access token that lets the tool connect to Azure DevOps. Use the personal access token that you created earlier in this tutorial. For more information, see [Authenticate access with personal access tokens](https://www.visualstudio.com/docs/setup-admin/team-services/use-personal-access-tokens-to-authenticate).
    - **Project Name** – Select the name of your Azure DevOps project.
    - **Test Plan** – Select the Azure DevOps test plan that contains your test cases. For more information, see [Create test plans and test suites](https://www.visualstudio.com/docs/test/manual-exploratory-testing/getting-started/create-a-test-plan). After you select a test plan, select **Test Connection** to test your connection to Azure DevOps.
    - **Hostname** – Enter the host name of the test environment, such as **\<myaos\>.cloudax.dynamics.com**. Don't include the **https://** or **http://** prefix.
    - **SOAP Hostname** – Enter the SOAP host name of the test environment. Typically, the SOAP host name is the same as the host name, but it has a **soap** suffix. Here's an example: **\<myaos\>soap.cloudax.dynamics.com**. Don't include the **https://** or **http://** prefix.

        > [!NOTE]
        > To find the host name and SOAP host name, open IIS Manager, right-click **Sites \> AOSService**, and then select **Edit bindings**. The values in the **Host Name** column give you the host name and SOAP host name (the SOAP host name has the suffix **soap** in the URL).

        :::image type="content" source="./media/setup_rsa_tool_63.png" alt-text="Screenshot of Host name and SOAP host name in the Host Name column.":::

    - **Admin user name** – Enter the email address of an admin user in the test environment.
    - **Thumbprint** – Enter the thumbprint of the authentication certificate, as described earlier in this tutorial.
    - **Working directory** – Specify the folder location for storing test automation files, such as Excel test data files. For example, enter or select **C:\\Temp\\RegressionTool**.

        > [!NOTE]
        > If the name of the folder has spaces, execution fails because the folder can't be found. This issue is a known issue and should be fixed in the latest version of the tool.

    - **Default browser** – Select the default web browser that you prefer. Make sure that the appropriate browser drivers are installed.
    - **Test run timeout** – Specify the time-out period, in minutes, for test runs. When the time-out period elapses, all active windows close, and pending test cases fail.
    - **Test action timeout** – This field controls the time-out period, in minutes, for Finance and Operation environment server requests. Usually, the default value (two minutes) is enough. However, for slower environments, you might want to increase the value if errors that are related to time-outs occur.
    - **Company name** – Enter the company name to use as your default company when Excel parameter files are created. You can change the company later by editing the Excel parameter file.

1. Select **Apply** to apply and save your settings.

    To save your current settings to a configuration file on your computer, select **Save as**. To restore your settings from a configuration file on your computer, select **Open**.

1. Select **Close** to close the dialog box.

### Load and run test cases

1. Select **Load** to load the **RSAT Test Plan** test plan from the Azure DevOps project.

    :::image type="content" source="./media/setup_rsa_tool_64.png" alt-text="Screenshot of Load button.":::

1. Select the **Create a new product** test case from the test suite, and then select **New \> Generate Test Execution and Parameter files**.

    :::image type="content" source="./media/setup_rsa_tool_65.png" alt-text="Screenshot of Generate Test Execution and Parameter files command on the New menu.":::

    The Excel parameter file is created in the local folder that you specified in the RSAT configuration (for example, **C:\\Temp\\RegressionTool**).

    :::image type="content" source="./media/setup_rsa_tool_66.png" alt-text="Screenshot of Excel parameter file created.":::

1. If you want to save the parameter files, select **Upload**. Test automation files of all selected test cases are uploaded to Azure DevOps for future use. These files include Excel test parameter files.

    By using this process, you can select **Load** to load the parameter files and automation files from the test case directly from Azure DevOps. You don't have to regenerate the parameter files. This approach becomes important later when you want to keep the modifications in the parameter file and don't want them to be overwritten.

1. To verify that the automation files and parameter files are saved to Azure DevOps, go to the Azure DevOps project, select **Boards \> Work Items**, and select the **Create a new product** test case. On the **Attachments** tab, you should see four files:

    - **.cs** – C\# automation file
    - **.dll** – Compiled automation file as an assembly
    - **.xlsx** – Excel parameter file
    - **.xml** – Recording file

    :::image type="content" source="./media/setup_rsa_tool_67.png" alt-text="Screenshot of Files on the Attachments tab.":::

1. Select the test case to run, and then select **Run**.

    > [!NOTE]
    > Before you run test cases, if you're using Internet Explorer as the browser, make sure that your desktop resolution is set to **100%** at **Windows Display settings \> Scale and layout**. If you can't change this setting on a virtual machine (VM), change it on the client (laptop) that you're trying to access the VM from. The resolution settings are then inherited by the VM display settings.

    :::image type="content" source="./media/setup_rsa_tool_68.png" alt-text="Screenshot of Desktop resolution set to 100%.":::

1. If the browser drivers aren't installed in the system, you receive a warning message that states, "This operation requires the \<browser name\> driver. Do you want to automatically downloads and install it now?" Select **Yes**.

    :::image type="content" source="./media/setup_rsa_tool_69.png" alt-text="Screenshot of Warning message for Internet Explorer.":::

    :::image type="content" source="./media/setup_rsa_tool_70.png" alt-text="Screenshot of Warning message for Chrome.":::

    > [!NOTE]
    > If you're using Chrome as the browser and receive an error message that states that the session wasn't created because the Chrome version isn't correct, download the latest Chrome driver from <http://chromedriver.chromium.org/downloads> to the **C:\\Program Files (x86)\\Regression Suite Automation Tool\\Common\\External\\Selenium** folder.

    :::image type="content" source="./media/setup_rsa_tool_71.png" alt-text="Screenshot of Error message for Chrome.":::

    The test case runs, and the **Result** field updates.

    :::image type="content" source="./media/setup_rsa_tool_72.png" alt-text="Screenshot of Updated Result field.":::

    If you follow this tutorial as it's written, the **Create a new product** test case fails, because the task recording for creating a product saved the product name as a hard-coded value. If you rerun the same test case, you receive an error message, because the product already exists.

    :::image type="content" source="./media/setup_rsa_tool_72.png" alt-text="Screenshot of Result field set to Failed.":::

### View the test results

1. Double-click the failed test case.

    You receive an error message.

    :::image type="content" source="./media/setup_rsa_tool_73.png" alt-text="Screenshot of Error message.":::

1. Select **Details** to view the whole error message.

    :::image type="content" source="./media/setup_rsa_tool_74.png" alt-text="Screenshot of Whole error message.":::

1. To view a detailed version of the error message in Azure DevOps, select **Open in Azure DevOps**. In Azure DevOps, you can view the status of the test case and the detailed error message.

    :::image type="content" source="./media/setup_rsa_tool_75.png" alt-text="Screenshot of Detailed error message in Azure DevOps.":::

1. To view the test results directly in the Azure DevOps project, go to **Test Plans \> Test Plans \> Runs**. Double-click the test run that you want to see more details for.

    :::image type="content" source="./media/setup_rsa_tool_76.png" alt-text="Screenshot of List of test runs in Azure DevOps.":::

1. The **Run summary** tab indicates that the test case failed, but it doesn't provide the actual error message. To view the detailed error message, select the **Test results** tab.

    :::image type="content" source="./media/setup_rsa_tool_77.png" alt-text="Screenshot of Run summary tab.":::

    The **Test results** tab provides the test case information, together with the outcome and the error message.

    :::image type="content" source="./media/setup_rsa_tool_78.png" alt-text="Screenshot of Test results tab.":::

1. Double-click the relevant record to view the detailed error message.

    :::image type="content" source="./media/setup_rsa_tool_79.png" alt-text="Screenshot of Detailed error message.":::

    > [!NOTE]
    > You can also find all error messages locally in **C:\\Users\\\$YourUserName\\AppData\\Roaming\\regressionTool\\errormsg-.txt**.

1. You can export the test run results from the test plan level by selecting **Export**.

    :::image type="content" source="./media/setup_rsa_tool_80.png" alt-text="Screenshot of Exporting a test plan.":::

### Modify the Excel parameter file

1. Open RSAT.
1. Select the test case, and then select **Edit** to open the Excel parameter file.

    On the **EcoResProductCreate** sheet, you see that the value of the **Product number** field is hard-coded. You must update this field to a new product number before you run the test case again.

1. To generate a unique product number for each run without reopening the Excel parameter file and manually updating the product number every time, use the following Excel formula.

    ```vba
    ="RSAT_"&TEXT(NOW(),"yyymmddhhmm")
    ```

    > [!NOTE]
    > In addition to the **General** tab, the Excel parameter file contains a data tab for every form page the test case visits.

    :::image type="content" source="./media/setup_rsa_tool_81.png" alt-text="Screenshot of Product number field.":::

1. Select **Save**, and then close the Excel workbook.
1. Select **Upload** to save the Excel parameter file to Azure DevOps.

    :::image type="content" source="./media/setup_rsa_tool_82.png" alt-text="Screenshot of Successful upload message.":::

    > [!NOTE]
    > To run test cases in a specific user context, enter the user's email ID in the **Test User** field on the **General** tab of the Excel parameter file. In the latest version of RSAT, the layout of the fields in the Excel parameter file is updated, but the concept remains the same.
    >
    > :::image type="content" source="./media/setup_rsa_tool_83.png" alt-text="Screenshot of Test User field.":::

### Validate the results

- Select **Run** to run the test case again. Verify that the test case passes. You can view the test results as described in the [View the test results](#view-the-test-results) section.

    :::image type="content" source="./media/setup_rsa_tool_84.png" alt-text="Screenshot of Result field set to Passed.":::

### Chaining test cases

One key feature of RSAT is the chaining of test cases (that is, the capability of a test to pass values to other tests). Run test cases in the order you define in the Azure DevOps test plan. You can also update this order in the test tool itself. Therefore, if you want to pass variables from one test case to another, make sure the tests are in the correct order.

In this section, you create a saved variable in the first test case, create a second test case, and pass the saved variable from the first test case to the second test case. Then, you run the test cases as a chained test case in RSAT.

#### Modify an existing task recording to create a saved variable

1. Open the client.
1. Select the **Settings** button (the gear symbol), and then select **Task recorder**.
1. Select **Edit Recording**.

    :::image type="content" source="./media/setup_rsa_tool_85.png" alt-text="Screenshot of Edit Recording button.":::

1. Select **Open from Lifecycle Services**.

    :::image type="content" source="./media/setup_rsa_tool_86.png" alt-text="Screenshot of Open from Lifecycle Services button.":::

1. Select **Select the Lifecycle Services library**.

    :::image type="content" source="./media/setup_rsa_tool_87.png" alt-text="Screenshot of Select the Lifecycle Services library button.":::

    BPM libraries are loaded from Lifecycle Services.

    :::image type="content" source="./media/setup_rsa_tool_88.png" alt-text="Screenshot of Loading BPM libraries.":::

1. After the BPM libraries load from Lifecycle Services, select the **RSAT** BPM library and the **Create a new product** business process that the task recording was associated with. Then select **OK**.

    :::image type="content" source="./media/setup_rsa_tool_89.png" alt-text="Screenshot of Selecting a BPM library and a business process.":::

1. Enter the name of the appropriate task recording in the **Recording name** field. Select **Start**.

    :::image type="content" source="./media/setup_rsa_tool_90.png" alt-text="Screenshot of Name of the task recording in the Recording name field.":::

1. Go to **Product information management \> Products**, and select **New** to open the page where the original task recording, **Create a product**, was recorded.
1. Select **Insert step**.

    > [!NOTE]
    > The new step is inserted **after** the step that you selected in the pane.

    :::image type="content" source="./media/setup_rsa_tool_91.png" alt-text="Screenshot of Insert step button.":::

1. Right-click the **Product number** field, and then select **Task recorder \> Copy**.

    :::image type="content" source="./media/setup_rsa_tool_92.png" alt-text="Screenshot of Copy command.":::

1. A new step is added in the pane. Make a note of the value in the **Product number** field, because you need it later.

    :::image type="content" source="./media/setup_rsa_tool_93.png" alt-text="Screenshot of New step added.":::

1. Select **Done editing**.
1. Select **Save to Lifecycle Services**, and associate the new task recording with the same BPM library and business process that the original task recording was associated with. For more information, see the [Create a task recording and save it to the BPM library](#create-a-task-recording-and-save-it-to-the-bpm-library) section.
1. Go to the BPM library, and select **Sync testcases** to overwrite the task recording that is attached to the test case in Azure DevOps, as described in the [Test the synchronization from BPM to Azure DevOps](#test-the-synchronization-from-bpm-to-azure-devops) section.
1. Open RSAT, and select **Load** to reload all the test cases in the test suite. You must regenerate the automation and parameter files for the appropriate test case by selecting the test case and then selecting **New \> Generate Test Execution and Parameter files**, as described in the [Load and run test cases](#load-and-run-test-cases) section.

    > [!NOTE]
    > If the Excel parameter file is open, regeneration fails. Therefore, make sure that the Excel parameter file for the test case is closed before you generate the new Excel parameter file.

1. Select **Edit** to open the new Excel parameter file. You see a new **Saved variable** entry on line 9. This variable, **{{EcoResProductCreate\_Identification\_ProductNumber\_Copy}}**, is saved in the task recording's XML file and can be used in subsequent tests.

    :::image type="content" source="./media/setup_rsa_tool_94.png" alt-text="Screenshot of Saved variable entry.":::

#### Create a new test case

1. Go to the **RSAT** BPM library.
1. Select the **Sample Support Business Process** process, and then, on the right, select **Edit mode**.
1. Change the value of both the **Name** field and the **Description** field to **Release a product**. Then select **Save**.

    :::image type="content" source="./media/setup_rsa_tool_95.png" alt-text="Screenshot of Name and description changed to Release a product.":::

#### Create a new task recording that has a Validate function

- Create a task recording to release the product that you created earlier to the USRT legal entity. For more information, see the [Create a task recording and save it to the BPM library](#create-a-task-recording-and-save-it-to-the-bpm-library) section.

    > [!NOTE]
    > For chained test cases, always find or filter for the record that you require by *manually typing the value of the field*. In that way, the tool can determine the record that the action must be taken against in the subsequent test case.

    :::image type="content" source="./media/setup_rsa_tool_96.png" alt-text="Screenshot of New task recording that has a Validate function.":::

    As the preceding illustration shows, after the product is found by using the Quick Filter, but before you select **Release products**, you validate the value of the **Product number** field to make sure that the product ID is the product ID that you created earlier. To validate the value, right-click the **Product number** field, and then select **Task recorder \> Validate \> Current Value**.

    :::image type="content" source="./media/setup_rsa_tool_97.png" alt-text="Screenshot of Validating the current value.":::

#### Save the task recording to BPM

1. After the task recording is completed, select **Save to Lifecycle Services**.

    :::image type="content" source="./media/setup_rsa_tool_98.png" alt-text="Screenshot of Save completed task recording to Lifecycle Services.":::

1. Library information is loaded from Lifecycle Services.

    :::image type="content" source="./media/setup_rsa_tool_99.png" alt-text="Screenshot of Loading library information from Lifecycle Services.":::

1. Select the BPM library to associate the task recording with. For this tutorial, select the **RSAT** BPM library that you created earlier and the **Release a product** business process under it. Then select **OK**.

#### Sync BPM to Azure DevOps

1. Go to the BPM library, and open the **RSAT** library.
1. Select **VSTS sync** and then **Sync test cases**. For more information, see the [Test the synchronization from BPM to Azure DevOps](#test-the-synchronization-from-bpm-to-azure-devops) section.

    After the synchronization is completed, the new work item and the corresponding test case for the **Release a product** business process appear in Azure DevOps at **Boards \> Work Items**.

#### Add the new test case to the existing test suite

1. Go to **Test plans \> Test plans**, and select the **RSAT Test Plan** plan.
1. Select **Add existing**.
1. On the **Add test cases to suite** page, select **Run query**.
1. Select the new test case that you created for **Release a product**, and then select **Add test cases** in the lower-right corner of the page (this button isn't shown in the following illustration).

    :::image type="content" source="./media/setup_rsa_tool_100.png" alt-text="Screenshot of Add test cases to suite page.":::

    The test suite now has two test cases.

    :::image type="content" source="./media/setup_rsa_tool_101.png" alt-text="Screenshot of Two test cases in the test suite.":::

#### Load test cases into RSAT

1. Open RSAT, and select **Load**.
1. The test cases are loaded, and you receive a warning that states, "This action will overwrite Excel test data files, local changes are lost. Do you want to proceed?" Select **Yes** to update the Excel parameter files in the local system but not the Excel parameter files that were uploaded to Azure DevOps.

    :::image type="content" source="./media/setup_rsa_tool_102.png" alt-text="Screenshot of This action will overwrite Excel test data files.":::

    Both test cases load, along with the Excel parameter file for the first test case. Because you selected **Upload** in the last run, the parameter files come from Azure DevOps.

    :::image type="content" source="./media/setup_rsa_tool_103.png" alt-text="Screenshot of Test cases loaded.":::

1. Select only the second test case, and then select **New \> Generate test execution and parameter files**.

#### Edit the Excel parameter file

1. Select only the second test case, and then select **Edit** to open the corresponding Excel parameter file.
1. Copy the **{{EcoResProductCreate\_Identification\_ProductNumber\_Copy}}** saved variable (see the [Modify an existing task recording to create a saved variable](#modify-an-existing-task-recording-to-create-a-saved-variable) section) from the first test case into all the fields where the product number is used. In this case, you copy the variable into the **Product number** and **Validate Product number** fields on the **EcoResProductListPage** sheet.

    :::image type="content" source="./media/setup_rsa_tool_104.png" alt-text="Screenshot of Product number and Validate Product number fields.":::

    > [!NOTE]
    > You can pass variables between tests only during the same test run. The names of the variables must match exactly.

1. Select **Save**, and then close the Excel workbook.
1. Select **Upload** to save the changes that you made to the Excel parameter file.

#### Run the chained test cases

1. Select both test cases, and then select **Run**.
1. Verify that both test cases pass.

    :::image type="content" source="./media/setup_rsa_tool_105.png" alt-text="Screenshot of Result field set to passed for both test cases.":::


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
