---
# required metadata

title: Regression suite automation tool installation and configuration
description: This topic contains information about how install and configure the Regression suite automation tool (RSAT).
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

# Regression Suite Automation Tool installation and configuration

[!include [banner](../../includes/banner.md)]

This topic contains information about how install and configure the Regression suite automation tool (RSAT).

## Prerequisites

### Test environment
Your test environment must be running Platform update 15 or newer. The Regression suite automation tool must have access to your test environment via a web browser.  

### Excel
You need Microsoft Excel installed to generate and edit test parameters. 

### Azure DevOps
You must have an Azure DevOps project to store and manage your test cases, test plans, and test case results. You will need an Azure DevOps Test Manager or Test Plans license. For example, if you have a Visual Studio Enterprise subscription, you already have a license to Test Plans. For more information, see [Pricing for Azure DevOps](https://azure.microsoft.com/pricing/details/devops/azure-devops-services/).

### Authentication Certificate
RSAT is designed to be installed on any Windows 10 computer and connect remotely via a web browser to an environment.

![Client computer and environment](media/client-environment.png)

To enable secure authentication, RSAT requires a certificate to be installed on the RSAT client computer. The RSAT settings dialog box allows you to automatically create and install the authentication certificate. You will also need to configure the virtual machine (VM) to trust the connection. Follow the instructions in the next sections to install and configure RSAT.

## Installation

### Installer
Download the .msi file from the [Regression Suite Automation Tool Download](https://www.microsoft.com/download/details.aspx?id=57357) to your machine and double-click it to run the installer. 
 
### Selenium and Browser Drivers
RSAT requires Selenium and web browser driver libraries. RSAT will prompt you if needed libraries are missing and will automatically install them for you. Select Yes when you see the following (or similar) messages.
 
![Selenium driver](media/driver-1.png)
 
![Browser driver](media/driver-2.png)

Alternatively, refer to [Install Selenium Driver](#install-selenium-drivers).

## Configuration

Open RSAT from your desktop.

![RSAT desktop icon](media/desktop-icon.png)
 
Select **Settings** button in the upper right to configure RSAT.

![RSAT settings](media/rsat-settings.png)

### General settings
These settings are required.

#### Azure DevOps
Configure your connection to the Azure DevOps project and test plan.

+ **Azure DevOps Url** - This is the URL of your Azure DevOps organization. For example, `https://yourAzureDevOpsUrlHere.visualStudio.com`.
+ **Access Token** - The access token that allows the tool to connect to Azure DevOps. You need to create a Personal Access Token or use an existing one that you have saved. For more information, see [Authenticate access with personal access tokens](https://www.visualstudio.com/docs/setup-admin/team-services/use-personal-access-tokens-to-authenticate). 
+ **Project Name** - The name of your Azure DevOps project. RSAT will automatically detect project names and test plans available based the Azure DevOps URL specified. You can then select the Test Project and Test Plan.
+ **Test Plan** - The Azure DevOps test plan that contains your test cases. For more information, see [Create test plans and test suites](https://www.visualstudio.com/docs/test/manual-exploratory-testing/getting-started/create-a-test-plan). 

Select **Test Connection** to test your connection to Azure DevOps.

#### Test environment
Configure your connection to the test environment.

+ **Hostname** – The hostname of the test environment, such as myhost.cloudax.dynamics.com. Don't include the https:// or http:// prefix.
+ **SOAP Hostname** – The SOAP hostname of the test environment. Typically, you must add a **soap** suffix to the hostname. For example, if your hostname is myhost.cloudax.dynamics.com, use myhost**soap**.cloudax.dynamics.com as the SOAP hostname.

    + If you don't know the SOAP hostname of your test environment, you can find it in the web.config file for the AOS server in Infrastructure.SoapServicesUrl.
    + If your test environment is a self-service user acceptance testing (UAT) or higher-tier sandbox environment that has no Remote Desktop access (that is, it's an environment that is running on the Azure Service Fabric infrastructure), the SOAP hostname matches the hostname.

+ **Admin User Name** – The email address of an admin user in the test environment.
+ **Thumbprint** – The thumbprint of the authentication certificate that you're using.

    1. Select **New** to create and install a new authentication certificate. When prompted, place the .cer file somewhere so you have it saved for your records.
    2. When the process completes, the new certification is installed in the local machine's trusted root store.

        ![Successfully created](media/thumbprint-certificate.png)

    3. The thumbprint of the newly created certificate is automatically inserted on this form. Copy this thumbprint, you will use it in the next section to configure the AOS to trust the connection.

+ **Company name** – Specify a company name to use as your default company during creation of Excel parameters files. It can be changed later by editing an Excel file.


#### Run setting
Configure your local settings.

+ **Working directory** - Folder location for storing test automation files, including Excel test data files. For example: **C:\Temp\RegressionTool**.
+ **Default browser** - Select the browser to use for test execution.

Select **Ok** to apply your settings and close the dialog box. Select **Cancel** to cancel your changes and close the dialog. The **Save As** and **Open** buttons allow you to save your settings for reuse later. Select **Save As** to save your current settings into a configuration file on your computer. Select **Open** to restore your settings from a configuration file.

### Optional settings
Select the **Optional** tab to configure optional settings.

+ **Test Run Prefix** – RSAT reports test run results to Azure DevOps. Test runs are named using the following convention: **\<Run ID\> \<Prefix\> \<Test Suite\>**. Use this setting to set the **\<Prefix\>**.
+ **Test Run Timeout** – The time-out (in minutes) of a test run. All active windows are closed and pending test cases fail when this time-out is reached.
+ **Test Action Timeout** – The time-out (in minutes) of individual test steps. When a test step times out, the test case fails.
+ **Pause between steps** – The number of seconds to pause between test steps during automated execution of a test case. The default value is **0** (zero). Set this value to force a pause during test execution, for auditing or investigative purposes. You can also specify a pause for an individual test case by changing the **Pause between steps (Seconds)** parameter on the **General** tab of the Excel parameter file for the test case.
+ **Fail test on first validation error** – By default, if a test case has multiple validation steps, and there is a validation failure, the test case stops running when the first failure occurs. The test case is then marked as failed. If you want test cases to continue to run until all validations are completed, clear this option. The test case can then evaluate all validations.
+ **Abort test suite execution on failure** – By default, execution of a test suite continues even if one of the test cases fails. If you set this option to **True**, the test run is aborted if a test case fails. All the remaining test cases will have a status of **Not Executed**.
+ **Cloud provider** – Select the provider of the cloud tenant of your test environment. Supported providers are **Global** (Public cloud) and **China** (Sovereign cloud).

### Configure the test environment to trust the connection

#### If your AOS allows for Remote Desktop connections

After creating the certificate, configure AOS to trust the test automation connection. On a multi-AOS environment, repeat the following steps for all AOS machines.

1.	Open a Remote Desktop connection to the AOS machine.
2.	Open IIS and find AOSService in the list of sites.

    ![Find AOS in IIS](media/configure-aos.png)

3.	Right-click **AOSService**, then click **Explore**.
4.	Open and find the file **wif.config**.
  
    ![Open wif.config](media/open-wif-config.png)

5.	Update the **wif.config** file by adding a new authority entry, as shown in the following example. Use **127.0.0.1** for the authority name and paste your certificate thumbprint.

    ```xml
    <issuerNameRegistry type="Microsoft.Dynamics.AX.Security.SharedUtility.AxIssuerNameRegistry, Microsoft.Dynamics.AX.Security.SharedUtility">
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

If your test environment doesn't allow for Remote Desktop access, follow these steps to configure the environment to trust the RSAT connection. An environment might not allow for Remote Desktop access if, for example, it's a self-service UAT or higher-tier sandbox environment (that is, it's an environment that is running on the Service Fabric infrastructure).

1. Create the RSAT authentication certificate by using the **New** button in the RSAT settings dialog box, as described earlier in this topic.
2. Open a support request, and provide the following information to the support engineer:

    - Your environment ID (You can find this ID on the environment page in Microsoft Dynamics Lifecycle Services \[LCS\].)
    - The .cer file that RSAT generated
    - An acceptable downtime window for the sandbox environment (Downtime is expressed in minutes.)

### Installation of RSAT on multiple computers

A test environment can be configured to trust more than one RSAT connection. If you install RSAT on more than one computer, you must generate a new certificate for each RSAT installation. The certificate must be generated and installed on the same computer as RSAT. You can have more than one thumbprint entry in the AOS wif.config file if you want your AOS to trust connections from more than one client where RSAT is installed. The following example shows multiple thumbprint nodes.

```xml
<keys>
    <add thumbprint="ccbc124d0a119xxxxxxxxxxxxxxxxxxxx841e797" />
    <add thumbprint="bbbbbbbbbbbbbbxxxxxxxxxxxxxxxxxxxx999999" />
</keys>
```

## Install Selenium drivers

For manual installation of Selenium drivers, follow these steps:
1. Download [Selenium 3.13.1](https://selenium-release.storage.googleapis.com/3.13/selenium-dotnet-strongnamed-3.13.1.zip). Or, go to https://docs.seleniumhq.org/download and click **Previous releases**. Choose **3.13** and download **selenium-dotnet-strongnamed-3.13.1.zip**.
2. Install the Selenium libraries:
    + Unzip the downloaded file. 
    + Unpack the file **dist\Selenium.WebDriver.StrongNamed.3.13.1.nupkg**. To unpack this file, add the .zip suffix to the file and unzip it. 
    + Copy the contents of the folder named **Selenium.WebDriver.StrongNamed.3.13.1.nupkg\lib** to **C:\Program Files (x86)\Regression Suite Automation Tool\Common\External\Selenium**.
3.	Download the [Internet Explorer driver version 3.4.0](https://selenium-release.storage.googleapis.com/3.4/IEDriverServer_x64_3.4.0.zip). Or, go back in the browser, open the **3.4** folder and download **IEDriverServer_x64_3.4.0.zip**.
4.	Unzip the downloaded file and move the contents to **C:\Program Files (x86)\Regression Suite Automation Tool\Common\External\Selenium**.

If you want to use Google Chrome as your browser, follow these steps:
1. Go to https://sites.google.com/a/chromium.org/chromedriver/downloads. 
2. Download **chromedriver_win32.zip** from the latest/current release.
3. Unzip the downloaded file and move the contents to **C:\Program Files (x86)\Regression Suite Automation Tool\Common\External\Selenium**.

## Manual configuration of authentication certificates

Optionally, you can manually configure the RSAT authentication certificate.

If you are not familiar with this process, get help from your system administrator. Make sure you have Windows Kits installed on your machine. If you do not have Windows Kits installed on your machine, you can download the Windows 10 SDK from [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk). You will need these components for the steps described in this document.

+ Windows SDK Signing Tools for Desktop Apps
+ Windows SDK for UWP Managed Apps.

### Generate the certificate

You must generate the certificate file on the RSAT client computer. **The certificate must be generated on the same computer that the test tool is running on.** To generate the certificate file, follow these steps:
1. Create the **C:\Temp** folder if it does not already exist on your computer.
2. Open a command line window as Administrator.
3. Go to the folder where you installed the Windows SDK. Your exact folder may be different, depending on where you have installed the windows SDK). You can also use Windows Kits 8.1.

    ```Console
    cd c:\Program Files (x86)\Windows Kits\10\bin\10.0.17763.0\x64
    ```

4. Run the following command. When you are prompted to enter a private key password, enter **None**. 

    ```Console
    makecert.exe -n "CN=127.0.0.1" -ss My -sr LocalMachine -a sha256 -len 2048 -cy end -r -eku 1.3.6.1.5.5.7.3.1 c:\temp\authCert.cer
    ````

### Install the certificate to the Trusted Root

To install the certificate, follow these steps:

1. Double-click **authCert.cer** to install the certificate.
2. Click **Install Certificate**.
3. Select **Local Machine > Place all certificates in the following Store > Browse > Trusted Root Certification Authorities** and click **Next** through each screen.
4. Leave the **Password** field blank.
5. In the **Certificate** dialog box, browse to **Details** and look for **Thumbprint**.

    ![Certificate dialog showing thumbprint listing](media/certificate-dialog.png)
 
6. Copy and save the thumbprint. You will need it to configure the AOS as described earlier in this topic.
