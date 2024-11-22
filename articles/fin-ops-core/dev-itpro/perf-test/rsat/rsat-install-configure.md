---
title: Regression suite automation tool installation and configuration
description: Learn about how to install and configure the Regression suite automation tool (RSAT), including prerequisites and an overview of the installation process.
author: FrankDahl
ms.author: fdahl
ms.topic: article
ms.date: 11/27/2023
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2019-08-01
ms.dyn365.ops.version: AX 7.0.0
---

# Regression Suite Automation Tool installation and configuration

[!include [banner](../../includes/banner.md)]

This article contains information about how to install and configure the Regression suite automation tool (RSAT).

## Prerequisites

### Excel

You need Microsoft Excel installed to edit test parameters.

### Azure DevOps (Prerequisite)

You must have an Azure DevOps project to store and manage your test cases, test plans, and test case results. You need an Azure DevOps Test Manager or Test Plans license. For example, if you have a Visual Studio Enterprise subscription, you already have a license to Test Plans. For more information, see [Pricing for Azure DevOps Services](https://azure.microsoft.com/pricing/details/devops/azure-devops-services/) or [Pricing for Azure DevOps Server](https://azure.microsoft.com/pricing/details/devops/server/).

### Certificate-based or user-based authentication

RSAT is designed to be installed on any Windows 10 or later computer and connect remotely via a web browser to an environment.

> [!NOTE]
> If you are using RSAT on a Cloud Hosted Environment (CHE) or VHD Development image, the tool will run on Windows Server 2019 or later.

To enable secure authentication, RSAT must authenticate access with the Dynamics 365 finance and operations apps environment that's being tested. There are two options for authenticating access: certificate-based authentication and user-based authentication.

Certificate-based authentication requires that a certificate is installed on the RSAT client computer. The RSAT settings dialog box lets you automatically create and install the authentication certificate. You must also configure the virtual machine (VM) to trust the connection. Follow the instructions in the next sections to install and configure RSAT.

User-based authentication requires some setup steps. For more information, see [User-based authentication](rsat-user-based-authentication.md).

## Installation

### Installer

Download the .msi file from the [Regression Suite Automation Tool Download](https://www.microsoft.com/download/details.aspx?id=57357) to your machine and double-click it to run the installer.

### Selenium and Browser Drivers

RSAT requires Selenium and web browser driver libraries. RSAT prompts you if needed libraries are missing and automatically installs them for you. Select Yes when you see the following (or similar) messages.

![Selenium driver.](media/driver-1.png)

![Browser driver.](media/driver-2.png)

RSAT uses [Selenium 3.13.1](https://selenium-release.storage.googleapis.com/3.13/selenium-dotnet-strongnamed-3.13.1.zip). The web driver library and browser-specific drivers are downloaded to **C:\Program Files (x86)\Regression Suite Automation Tool\Common\External\Selenium**.

## Configuration

1. Open the **Regression Suite Automation Tool** application from your desktop icon.
2. Select the **Settings** tab on the upper left to configure RSAT.

    ![RSAT settings.](media/rsat-settings.png)

### General settings

These settings are required.

#### Azure DevOps (General settings)

Configure your connection to the Azure DevOps project and test plan.

+ **Azure DevOps URL** – This is the URL of your Azure DevOps organization. For example, `https://yourAzureDevOpsUrlHere.visualStudio.com`.

    > [!NOTE]
    > If you're using Azure DevOps Server, add **/DefaultCollection** to the end of your Azure DevOps URL.

+ **Access Token** – The access token that allows the tool to connect to Azure DevOps. You need to create a personal access token or use an existing one that you have saved. We recommend that you create this with scope selected as Full Access. For more information, see [Authenticate access with personal access tokens](/azure/devops/organizations/accounts/use-personal-access-tokens-to-authenticate#create-a-pat).
+ **Project Name** – The name of your Azure DevOps project. RSAT automatically detects project names and test plans available based on the Azure DevOps URL specified. You can then select the Test Project and Test Plan.
+ **Test Plan** – The Azure DevOps test plan that contains your test cases. For more information, see [Create test plans and test suites](https://www.visualstudio.com/docs/test/manual-exploratory-testing/getting-started/create-a-test-plan).

Select **Test Connection** to test your connection to Azure DevOps.

#### Test environment (General settings)

Configure your connection to the test environment.

+ **Hostname** – The hostname of the test environment, such as myhost.cloudax.dynamics.com. Don't include the https:// or http:// prefix.
+ **SOAP Hostname** – The SOAP hostname of the test environment.

    + If your test environment is a user acceptance testing (UAT) or higher-tier sandbox environment that has no Remote Desktop access, the SOAP hostname is equal to the hostname.
    + If you don't know the SOAP hostname of your test environment, you can find it in the web.config file for the AOS server in Infrastructure.SoapServicesUrl.

+ **Admin User Name** – The email address of an admin user in the test environment. The admin user name must be the email address of a user who belongs to the System Administrator role on the finance and operations test environment that RSAT is connecting to. The user account (email address) must also belong to the same tenant as the test environment. For example, if your test environment's default tenant is contoso.com, the admin user must end with @constoso.com.

+ **Authentication method** – Select the method for authenticating access to the hostname. The options are **Certificate** and **User-Based**. Both options include steps to complete. The Microsoft-recommended method is user-based authentication, and there are plans to remove the option for certificate-based authentication in Dynamics 365 finance and operations apps.

+ **Thumbprint** – The thumbprint of the authentication certificate that you're using.
 If you don't have Remote Desktop Protocol (RDP) access to your environment, follow the steps later in this article to download the certificate from Lifecycle Services and paste the thumbprint here.
 Otherwise, if you do have RDP access to the environment, follow these steps to generate a self-signed certificate.

    1. Select **New** to create and install a new authentication certificate. When prompted, place the .cer file somewhere so you have it saved for your records.
    2. When the process is completed, the new certification is installed in the local machine's trusted root store.

        ![Successfully created.](media/thumbprint-certificate.png)

    3. The thumbprint of the newly created certificate is automatically inserted on this form. Copy this thumbprint, you use it in the next section to configure the AOS to trust the connection.

+ **KeyVault URL, Tenant ID, Client ID, Client Secret** – These fields are used when you configure user-based authentication. For information about how to set up user-based authentication, see [User-based authentication](rsat-user-based-authentication.md).

+ **Company name** – Specify a company name to use as your default company during creation of Excel parameters files. It can be changed later by editing an Excel file.

#### Run setting

Configure your local settings.

+ **Working directory** - Folder location for storing test automation files, including Excel test data files. For example: **C:\Temp\RegressionTool**.
+ **Default browser** - Select the browser to use for test execution. RSAT supports (the new) Microsoft Edge, Microsoft Internet Explorer, and Google Chrome. We recommend Microsoft Edge, which you can download from [Introducing the new Microsoft Edge](https://www.microsoft.com/edge).

Select **Ok** to apply your settings and close the dialog box. Select **Cancel** to cancel your changes and close the dialog. The **Save As** and **Open** buttons allow you to save your settings for reuse later. Select **Save As** to save your current settings into a configuration file on your computer. Select **Open** to restore your settings from a configuration file.

### Optional settings

Select the **Optional** tab to configure optional settings.

+ **Test Run Prefix** – RSAT reports test run results to Azure DevOps. Test runs are named using the following convention: **\<Run ID\> \<Prefix\> \<Test Suite\>**. Use this setting to set the **\<Prefix\>**.
+ **Test Run Timeout** – The time-out (in minutes) of a test run. All active windows are closed and pending test cases fail when this time-out is reached.
+ **Test Action Timeout** – The time-out (in minutes) of individual test steps. When a test step times out, the test case fails.
+ **Pause between steps** – The number of seconds to pause between test steps during automated execution of a test case. The default value is **0** (zero). Set this value to force a pause during test execution, for auditing or investigative purposes. You can also specify a pause for an individual test case by changing the **Pause between steps (Seconds)** parameter on the **General** tab of the Excel parameter file for the test case.
+ **Fail test on first validation error** – By default, if a test case has multiple validation steps, and there's a validation failure, the test case stops running when the first failure occurs. The test case is then marked as failed. If you want test cases to continue to run until all validations are completed, clear this option. The test case can then evaluate all validations.
+ **Fail test on Infolog error** - Check this option to force test cases to fail when an error is encountered in the finance and operations Infolog during test case execution.
+ **Abort test suite execution on failure** – By default, a test suite run continues even if one of the test cases fails. If you check this setting, the test run is aborted if a test case fails. All the remaining test cases have a status of **Not Executed**.
+ **Enable local file validation rules** - Check this setting to validate whether your test cases are ready for execution. See [Validate readiness of test automation files](rsat-run.md#validate-readiness-of-test-automation-files) for more details.
+ **Enable upload to Azure DevOps** - To prevent accidental upload to Azure DevOps (therefore overriding project-wide recordings and automation files), you can uncheck this setting. This is especially useful when RSAT is deployed on a client machine for execution purposes only, and you want to prevent users from making permanent changes to the test cases.
+ **Cloud provider** – Select the provider of the cloud tenant of your test environment. Supported providers are **Global** (Public cloud) and **China** (Sovereign cloud).

    > [!IMPORTANT]
    > The **Cloud provider** setting is required, and the selected value must be **China** if your finance and operations apps were deployed in 21Vianet.

### Configure the test environment to trust the connection

The following subsections are relevant only when you use certificate-based authentication. For user-based authentication, use the information in [User-based authentication](rsat-user-based-authentication.md) instead.

#### If your AOS allows for Remote Desktop connections

After creating the certificate, configure AOS to trust the test automation connection. On a multi-AOS environment, repeat the following steps for all AOS machines.

1. Open a Remote Desktop connection to the AOS machine.
2. Open IIS and find AOSService in the list of sites.

    ![Find AOS in IIS.](media/configure-aos.png)

3. Right-click **AOSService**, then select **Explore**.
4. Open and find the file **wif.config**.

    ![Open wif.config.](media/open-wif-config.png)

5. Update the **wif.config** file by adding a new authority entry. Use **127.0.0.1** for the authority name and paste your certificate thumbprint.

   The following section needs to be pasted after this line in the **wif.config**: `<issuerNameRegistry type="Microsoft.Dynamics.AX.Security.SharedUtility.AxIssuerNameRegistry, Microsoft.Dynamics.AX.Security.SharedUtility">`

    ```xml
        <authority name="CN=127.0.0.1">
            <keys>
                <add thumbprint="ccbc124d0a119xxxxxxxxxxxxxxxxxxxx841e797" />
            </keys>
                <validIssuers>
                    <add name="CN=127.0.0.1" />
                </validIssuers>
        </authority>
    ```

#### If you have no Remote Desktop access to the server

In cases where your Remote Desktop Protocol (RDP) access is removed, such as Microsoft-managed or self-service type sandboxes, Microsoft generates the certificate for your environment and has it preconfigured. Follow these steps to retrieve the RSAT certificate and use it using the LCS user interface. For automation, there's information on the [Fetch an environment's RSAT certificate in a zip file](../../lifecycle-services/api/v1/reference-download-rsat-certificate.md) API reference page.

1. Under **Maintain** on your environment details page in Lifecycle Services you see two new options.

    - Download RSAT certificate
    - Regenerate RSAT certificate

![Download and regenerate RSAT certificate options.](media/rsat-lcs1.png)

Use the **Download** button to retrieve the certificate bundle as a .zip file.

2. You receive a warning that a clear-text password is displayed on your screen. You need the password in subsequent steps.  Select **Yes** to continue.

3. Copy the clear-text password for later use. You see the .zip file has been downloaded. Inside the .zip file is a certificate (.cer) and a personal information exchange (.pfx) file. Unzip the file.

4. Install the certificate in the local machine's trusted root store:
    + Double-click the certificate (.cer) to open it, and then select **Install Certificate**. 
    + Select **local machine**, and then browse to the **Trusted Root Certification Authorities** store to install it in the trusted root store.

5. Install the pfx file in the local machine's personal store:
   + Double-click the personal information exchange (.pfx) file to open it, and select **Local Machine**. 
   + Enter the password saved in step 2, and browse to the **Personal** store.

6. Double-click the certificate file to open it. Browse to the **Details** tab, and scroll down until you see the **Thumbprint** section. Select **Thumbprint**, and note the ID in the text box. Select or paste this thumbprint in RSAT settings.
![Thumbprint settings.](media/rsat-lcs4.png)

You can now run your tests against the environment using this certificate. The certificate is autorotated by Microsoft before it expires, at which time you need to download a new version of this certificate starting from step 1 above. For self-service environments, this is rotated every 60 days during a downtime window that is closest to the expiry. These downtime windows include customer initiated package deployment, and database movement operations that target the environment.

<!-- Link appears to be outdated and needs to be replaced.

## Manual configuration of authentication certificates

Optionally, you can manually configure the RSAT authentication certificate.

If you aren't familiar with this process, get help from your system administrator. Make sure you have Windows Kits installed on your machine. If you don't have Windows Kits installed on your machine, you can download the Windows 10 SDK from [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk). You need these components for the steps described in this document.

+ Windows SDK Signing Tools for Desktop Apps
+ Windows SDK for UWP-Managed Apps. -->



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]

