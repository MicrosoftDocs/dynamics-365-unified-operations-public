---
title: Set up a local development environment
description: This article explains how to set up a local development environment for the Commerce Scale Unit (CSU) and point of Sale (POS) development in Microsoft Dynamics 365 Commerce.
author: josaw1
ms.date: 05/03/2023
ms.topic: article
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2021-09-16
ms.dyn365.ops.version: AX 10.0.22
---

# Set up a local development environment

[!include [banner](../../includes/banner.md)]

This article explains how to set up a local development environment for the Commerce Scale Unit (CSU) and point of Sale (POS) development in Microsoft Dynamics 365 Commerce.

> [!IMPORTANT]
> The environment setup that is described in this article can be used only for extension development. It can't be used for testing, user acceptance testing (UAT), or production.

## Supported development environment types

Commerce supports both cloud-based environments and local environments.

+ **Cloud-based:** Deploy a cloud-based development environment by using [Microsoft Dynamics Lifecycle Service (LCS)](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md).
+ **Local:** You have two options for setting up a development environment on your own machine:

    - **Self-hosted CSU** – This environment type deploys the CSU locally (self-hosted as an executable file). There is no Internet Information Services (IIS), Commerce data synchronization, or Commerce Headquarters connectivity for real-time calls. If you use this option, no data synchronization occurs between Commerce Headquarters and CSU channel databases. Channel databases are filled with the default demo data for development purposes. All requests and calls to Commerce Headquarters, such as a call to issue a gift card, are mocked by the local CSU.
    - **IIS-hosted CSU** – This environment type deploys the CSU in IIS and sets up an Async Client to sync the data between Commerce Headquarters and CSU channel databases. It also sets up support for real-time connections with Commerce Headquarters. This setup requires some additional configuration. For example, Azure Active Directory (Azure AD) apps must be set up, and certificates must be deployed. For detailed information about how to install the IIS-hosted CSU, see [Configure and install IIS-Hosted Commerce Scale Unit document](retail-store-scale-unit-configuration-installation.md#configure-a-new-commerce-scale-unit).

## Hardware requirements

We recommend that you use a Windows machine with 16 GB of RAM and a minimum of two CPU cores. If you are running finance and operations apps, Retail Server, e-Commerce development, and other concurrent process, then we recommend 24 GB of RAM with four CPU cores.

## Local self-hosted CSU

This version of the scale unit is very lightweight. It provides a quick way to develop a wide range of Commerce runtime (CRT)/RTS extensions that require minimal or no dependencies on other systems and services.

**Pros:**

- Commerce Headquarters isn't required.
- IIS isn't required. Retail Server is hosted in a console app.
- Configuration of Transport Layer Security (TLS) isn't required.
- Real-time service (RTS) communication is mocked via a set of demo-mode CRT handlers.
- Async Client isn't required. The channel database is automatically filled with a demo data.
- Very few parameters are required to initiate the scale unit deployment. Therefore, the deployment prerequisites are minimal. For example, no certificates must be explicitly created and provided to the installer.
- This version provides a very fast and easy introduction to CRT/Retail Server development and runtime capabilities.

**Cons:**

- This version doesn't match the topology that is used in real production environments, because there is no Cloud POS (CPOS), Async Client, or HTTPS, and there are no RTS calls.
- Real-time operations can't be fully tested. They must be mocked.

## Local IIS-hosted CSU

IIS mode is a complete on-premises scale unit, where all the components match real production deployments, and nothing is mocked.

**Pros:**

- This version represents a fully capable on-premises scale unit that hosts Retail Server in IIS.
- It uses real (not mocked) RTS interaction with Commerce Headquarters.
- It includes Async Client, which fills the channel database, based on data in the Commerce Headquarters database, just as a regular scale unit does. Therefore, no demo data is involved.

**Cons:**

- Additional steps are required to create certificates and Azure AD registrations, and to download the configuration file from Commerce Headquarters.

## Prerequisites for setting up the local development environment

Before you set up the self-hosted or IIS-hosted environment, complete the following prerequisites in this order:

1. Install .NET Core SDK 3.1 for Windows x64 from [Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1).
2. Install any edition of [SQL server](/sql/database-engine/install-windows/install-sql-server), and enable full text search. For more information, see [Add Features to an Instance of SQL Server (Setup)](/sql/database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup). The minimum supported version is 13.0.5026.0 SqlServer 2016 SP2.

    + Enable Mixed (SQL + Windows/Integrated) authentication.
    + If no default instance of SQL Server is installed, the deployment of CSU will fail. An error message will indicate that an instance could not be found. If you want to use a named instance instead, edit the **Install.ps1** file by inserting the following line after line 78. (You can find this script in **Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Scripts** folder.)

        ```powershell
        $installerArgs += $("--sqlservername", "PutYourSqlServerSeenInSSMSHere")
        ```

        (When you insert this line, substitute **PutYourSqlServerSeenInSSMSHere** with your SQL Server name.)

3. Install NuGet.exe from [Available NuGet Distribution Versions](https://www.nuget.org/downloads). Copy it to some location, and then add update the **PATH** environment variable so that it points to that location.
4. If MSBuild isn't installed, install the Visual Studio tools from [Download Visual Studio Tools](https://visualstudio.microsoft.com/downloads/). Expand the **Tools for Visual Studio** section, and download and run **Build Tools for Visual Studio**. Don't specify any components. Select **Install** for the default installation.

    + After Visual Studio tools are installed, open a Command Prompt window, and run the command `where msbuild`. If msbuild.exe isn't found, run the command from Visual Studio Developer Command Prompt.
    + After you find msbuild.exe, make sure that the **PATH** environment variable points to the folder that contains "msbuild" at the beginning of the path. The path should contain a version of msbuild.exe that is at least version 15. To determine the version number, run the command `msbuild /version`.
    + To verify that the **PATH** variable is set correctly, run the command `msbuild/version` from a regular command prompt. Don't use Developer Command Prompt. The command should print a version number of at least 15. After you've finished setting up MSBuild, restart Visual Studio Code.

5. Install Microsoft.NET.Sdk by using the previously downloaded Visual Studio tools. Go to **Individual components**, enter **.NET SDK**, select the checkbox for the .NET SDK, and then select **Install**.
6. Install the 64-bit version of Node.js from [Download and Install Node](https://nodejs.org/en/download/). Make sure that the **PATH** environment variable point to the location. If you're prompted, select the **Automatically install the necessary tools** checkbox.
7. Install the 64-bit version of Visual Studio Code for Windows from [Download Visual Studio Code](https://code.visualstudio.com/download).
8. Install the C# for Visual Studio Code (powered by OmniSharp) extension for Visual Studio Code by following the instructions in [Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-marketplace).
9. Clone or download the [Scale Unit GitHub repository (repo)](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit).
10. In LCS, go to the [Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary), select **Retail Self-service package** as the asset type, and find the file that ends with **Commerce Scale Unit (SEALED)**. Be sure to select the version for the release that you require (for example, version 10.0.22 or 10.0.23). Download the file, and put it in the **Download** folder in the Scale Unit GitHub repo that you cloned or downloaded in the previous step (**Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Download/**).

## Additional prerequisites for IIS-hosted CSU

+ IIS is required, and several features must be turned on. The installer will report any features that are required but that aren't yet enabled.
+ TLS 1.2 should be enabled in the system. (You should not use TLS 1.0 or 1.1.) You can let the installer check for this prerequisite. If your machine requires changes for TSL 1.2, the installer will show actionable instructions.
+ You can proactively configure strong cryptography for TLS by making the following changes in the **.vscode/tasks.json** file:

    - **baseProduct\_Port** – You can keep the default port (446), or you can change it to any value that you want. If the port that you specify is used by another application, the base installer deployment will prompt you to specify a different port.
    - **baseProduct\_SslCertFullPath** – This path should point to the Secure Sockets Layer (SSL) certificate that the CSU website uses for HTTPS communication. For this non-production setup, the certificate can be self-signed. It must be stored in the **LocalMachine/Personal** certificate store. To generate the certificate, follow these steps:

        1. Open IIS, and double-tap (or double-click) the icon for your machine name.
        2. Double-tap (or double-click) **Server Certificates**.
        3. On the right, select **Create Self-Signed Certificate**.
        4. When you're prompted to provide a friendly name for the certificate, specify the fully qualified domain name (FQDN) of your machine. The FQDN includes the machine name itself and a domain, if the machine is joined to a domain. You can find the FQDN by running the Windows PowerShell command `[System.Net.Dns]::GetHostEntry("")`. You can also get the FQDN from **Full computer name** field in the **System** control panel item in Windows.
        5. Keep the default value for the certificate store (**Personal**).
        6. Select **OK**.
        7. Find the new certificate in the list, and double-tap (or double-click) it.
        8. On the **Details** tab, find the **Thumbprint** value.
        9. Copy and paste the thumbprint into a text editor, and convert all the letters to uppercase. Then add the converted value to the end of the predefined template for the **baseProduct\_SslCertFullPath** option, so that the template resembles `store:///My/LocalMachine?FindByThumbprint=YourThumbprintGoesHere`.

        > [!NOTE]
        > The base installer requires two more certificates, for a total of three. For all production deployments, three different certificates should be created for security reasons. However, for this development setup, you can save time by using the same certificate for all three configuration options, unless this approach violates your policies. In this case, you can provide the same thumbprint for the next two parameters.

    - **baseProduct\_RetailServerCertFullPath** – Update this parameter with the thumbprint of the certificate that you create. This certificate represents Retail Server's identity. The identity is used, for example, when CSU issues security tokens for POS scenarios. To create this certificate, follow the same procedure that you used for the SSL certificate, but specify any friendly name that you want (for example, **RsTestIdentity**). You will need this certificate later, when you set up the Azure AD application.
    - **baseProduct\_AsyncClientCertFullPath** – Async Client uses this certificate when it acquires a security token from Azure AD for communication with Commerce Headquarters. To create this certificate, follow the same procedure that you used for the SSL certificate, but specify any friendly name that you want (for example, **AsyncClientTestIdentity**).
    - **baseProduct\_RetailServerAadClientId** – The value is the Azure AD application client ID that represents the Retail Server's identity. It's used, for example, when CSU issues security tokens for POS scenarios. To create the application and retrieve its application (client) ID, follow step 3 in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application).
    - **baseProduct\_RetailServerAadResourceId** – The value is the resource ID of the registered Azure AD application. Use the value that is described as the "application ID URI" in step 3c in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application).
    - **baseProduct\_CposAadClientId** – The value is the Azure AD application client ID that represents CPOS. To create the application and retrieve its application (client) ID, follow step 4 in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application). This step completes the CSU/CPOS setup in Azure AD. To complete the required setup in Commerce Headquarters, follow step 6 in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application).
    - **baseProduct\_AsyncClientAadClientId** – The value is the Azure AD application client ID that Async Client uses when it must authenticate with Commerce Headquarters. To create this application, register one more Azure AD application by following steps 3a through 3b in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application). To register only the created application with Commerce Headquarters, follow step 2 in [Service to Service authentication in AX7](https://community.dynamics.com/ax/b/axforretail/posts/service-to-service-authentication-in-ax7).
    - **baseProduct\_Config** – Specify only the file name, not the full path, that corresponds to the channel database configuration that can be downloaded from Commerce Headquarters as described in step 4 in [Download the CSU installer](retail-store-scale-unit-configuration-installation.md#download-the-commerce-scale-unit-installer). After you download the file from Commerce Headquarters, put it in the [Download](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-ScaleUnit?path=/src/ScaleUnitSample/Download&version=GC0acfab2d3d7cbd734ea5b19f2b2ac6713d7391ef) folder.
    - **baseProduct\_UseSelfHost** – Set this value to **false**.

## Debug an extension by using the self-hosted CSU

1. Open Visual Studio Code as an administrator.
2. In the Scale Unit GitHub repo that you cloned or downloaded earlier, open the **src\\ScaleUnitSample** folder.
2. Open the **.vscode/tasks.json** file, and set **baseProduct\_UseSelfHost** to **true**.
3. On the **Terminal** menu, select **Run Task**, and enter **build-extension**.

    If you receive an error message that states that the running script is disabled on this system, open a Command Prompt window as an administrator, and run `powershell Set-ExecutionPolicy RemoteSigned`. Then close and reopen Visual Studio Code. Don't change the execution policy on production machines unless you understand the implications of changing security policies.

4. Put a break point in your extension method, and select the **F5** key to debug the extension.

After you select **F5**, the following actions are automatically performed. (These actions are supported in Visual Studio Code only.)

- The scale unit sample code is compiled. The compilation produces a package that contains the Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it wasn't already deployed.
- The package that contains demo data is downloaded from the SDK's feed and applied to the channel database.
- The Sealed Scale Unit Extension installer is deployed.
- A web browser window is opened that shows the results of a call to CSU's health check endpoint.
- The debugger is attached to the process that is hosting the CSU, and the CSU is ready to serve incoming requests at the URL `http://localhost:12345`.

While the local scale unit is serving the requests, use the Debug Console to watch logging of the scale unit's internal diagnostics in real time. The log can be helpful when you're debugging.

## Debug an extension by using the IIS-hosted CSU

1. In Visual Studio Code, select **Run and Debug** (or select **Ctrl+Shift+D**). A drop-down menu that has a green arrow appears under the top navigation bar. Select **Debug with IIS**.
2. Select the **F5** key. As when you debug in self-hosted CSU mode, the base installer is deployed first. Then the extension installer is deployed.
3. The base installer performs prerequisite checks and reports any actions that are required. The prerequisites include SQL Server, IIS, TLS, and .Net Core Hosting Bundle.
4. After the base and extension packages are deployed, Visual Studio Code opens a web browser window that shows the results of a call to health check. Visual Studio Code also opens a dialog box that prompts you to attach a debugger. This step is optional. If you want to attach a debugger, enter **w3wp** in the list of processes, and select the row that contains **RssuCore**. RssuCore is the name of the IIS application pool that is used to run the CSU website.

You now have a fully functional on-premises deployed scale unit that includes the following elements:

- Channel database
- Async Client
- ASP.NET Core 3.1–based Retail Server that can interact with Commerce Headquarters via RTS
- CPOS

To find URLs that correspond to the CPOS and CSU that you just deployed, review the base installer's log. The URLs appear near the end of the log, where CSU and CPOS are health-checked. To fill in the channel database with data from Commerce Headquarters, follow step 28 in [Configure a new Commerce Scale Unit](retail-store-scale-unit-configuration-installation.md#configure-a-new-commerce-scale-unit). (You must have already completed the previous steps in that document.)

## Switching from IIS mode to self-hosted mode

If you switch between IIS and self-hosted modes, be sure to follow these steps. (If this is your first run, you can skip these steps, because the values that are described here are the default values.)

- In Visual Studio Code, select **Run and Debug** (or select **Ctrl+Shift+D**). A drop-down menu that has a green arrow appears under the top navigation bar. Select **Debug with Self-Host**.
- Open the **.vscode/tasks.json** file, and make sure that **baseProduct\_UseSelfHost** is set to **false**.

After you select **F5**, the following actions are automatically performed. (These actions are supported in Visual Studio Code only.)

- The scale unit sample code is compiled. The compilation produces a package that contains the Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it wasn't already deployed.
- The package that contains demo data is downloaded from the SDK's feed and applied to the channel database.
- The Sealed Scale Unit Extension installer is deployed.
- A web browser window is opened that shows the results of a call to CSU's health check endpoint.
- The debugger is attached to the process that is hosting the CSU, and the CSU is ready to serve incoming requests at the URL `http://localhost:12345`.

While the local scale unit is serving the requests, use the Debug Console to watch logging of the scale unit's internal diagnostics in real time. The log can be helpful when you're debugging.

## Deploy the extension package to production

If the build is completed without errors, you can use the outputs to deploy your extensions:

- **Cloud Scale Unit extension package** – This package is in the **ScaleUnit\\bin\\Debug\\netstandard2.0** folder and is used for Cloud deployments.
- **Scale Unit extension installer** – This installer is in the **Installer\\bin\\Debug\\net461** folder and is used for on-premises (in-store) installations.

You should set up a build pipeline to generate the package and then deploy it. For more information, see [Set up a build pipeline for the independent-packaging SDK](build-pipeline.md) and [Deploy the package to CSU](retail-sdk/retail-sdk-packaging.md#deploy-the-package-to-csu).

### Troubleshooting

To troubleshoot deployment issues, review the verbose set of logs and associated messages on the **Terminal** tab of Visual Studio Code. If you can't determine what is wrong on your own, contact Microsoft for help. When you contact Microsoft, provide the following data:

- A verbose description of the actions that were performed
- The log file that is referenced at the very beginning and the very end of the output for the Base Scale Units's deployment process
- The output of the Visual Studio Code terminal, including warnings and errors

You can find runtime logs that correspond to Retail Server and Async Client (in the case of an IIS host) in Event Viewer, under **Windows Logs \> Application**. Filter the log by the following sources:

- Microsoft Dynamics - Async Client Service
- Microsoft Dynamics - Retail Server

Self-hosted CSU will also print runtime logs directly to the Visual Studio Code terminal.

## Out-of-box tasks in Visual Studio Code

The following set of tasks is available when you select the **Run Task** command on the **Terminal** menu in Visual Studio Code:

- **build-extension** – Build an extension.
- **check-msbuild** – Show the version of MSBuild that is available for Visual Studio Code.
- **check-ps-bitness** – Determine whether the version of Windows PowerShell that is available for Visual Studio Code is the required 64-bit version.
- **clean-extension** – Clean the build output that was generated while the extension was built.
- **install** – Verify all development-time prerequisites, and then perform all required actions for the selected mode (Self-hosted or IIS). This task includes installation of the Base Scale Unit and Extension installer.
- **uninstall** – Uninstall an extension and the Base Scale Unit.
- **uninstall-base-product** – Uninstall the Base Scale Unit. This task fails if it detects an installed extension.
- **uninstall-extension** – Uninstall an extension.

### Support

If the setup doesn't work as expected, or if you need help, use the following links to get support:

+ [microsoft/Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/issues)
+ [Dynamics 365 Commerce Forum](https://community.dynamics.com/365/commerce/f/dynamics-365-commerce-forum)
+ [Retail Interest Group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=1585934)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

