---
title: Set up a local development environment
description: This topic explains how to setup a local development environment for Microsoft Dynamics 365 Commerce Cloud scale unit (CSU) and POS development.
author: mugunthanm
ms.date: 09/16/2021
ms.topic: article
audience: Developer
ms.reviewer: rhaertle
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 09-16-2021
ms.dyn365.ops.version: AX 10.0.22
---

# Set up a local development environment

[!include [banner](../../includes/banner.md)]

This topic explains how to set up a local development environment for Microsoft Dynamics 365 Commerce Cloud scale unit (CSU) and Point of Sale (POS) development. It applies to Dynamics 365 Commerce application version 10.0.22 and later.

> [!NOTE]
> The environment setup described in this topic is onl for extension development. It can't be used for testing, user acceptance testing (UAT), or production.

## Commerce supports different development environment types

Cloud-based and local environments are supported:

+ Cloud-based: Deploy a cloud-based development environment using [Lifecycle Service (LCS)](../../fin-ops-core/dev-itpro/dev-tools/access-instances.md)
+ Local: There are two options to set up a development environment on your own machine:

    - **Self-hosted CSU** – This environment type deploys the CSU locally (self hosted-hosted as an executable). There is no IIS, no Commerce data sync, and no Headquarters (HQ) connectivity for real-time calls. With this option there will not be any data sync between the HQ and CSU channel databases. Channel databases will be populated with the default demo data for development purpose. All the requests and calls to HQ will be mocked by the local CSU. For example, a call to issue gift card will be mocked by the local CSU.
    - **IIS-Hosted CSU** - This environment type deploys the CSU in IIS and sets up an async client to sync the data between the HQ and CSU channel databases. It also sets up real-time connection support with the HQ. This setup requires some additional configuration like AAD app setup and certificates deployment. For detailed step to install the IIS-Hosted CSU, see [Configure and install IIS-Hosted Commerce Scale Unit document.](retail-store-scale-unit-configuration-installation#configure-a-new-commerce-scale-unit)

## Local self-hosted CSU

This is a very lightweight version of the scale unit. It provides a quick way to develop a wide spectrum of CRT/RTS extensions that require minimal or no dependencies on other systems and services.

Pros:

- Doesn't require HQ.
- Doesn't require IIS. Retail Server is hosted in a console app.
- TLS configuration is not required.
- RTS communication is mocked via a set of demo-mode CRT Handlers.
- Async Client is not needed. The Channel database is automatically populated with a demo data.
- Requires very few parameters to initiate the Scale Unit deployment so the required prerequisites are minimal. For example, no certificates have to be explicitly created and provided to the installer.
- Provides very fast and easy introduction into CRT/Retail Server development and runtime capabilities.

Cons:

- Doesn't match the topology used in real production environments (no CPOS, no Async Client, no RTS calls, no HTTPS).
- Real Time operations cannot be fully tested. They must be mocked.

## Local IIS CSU

IIS mode is a complete on-prem Scale Unit with all the components matching real production deployments where nothing is mocked.

Pros:

- Represents fully capable on-prem Scale Unit hosting Retail Server in IIS.
- Employs real (not mocked) RTS interaction with HQ.
- Includes Async Client populating the Channel DB based on HQ DB data as regular Scale Unit does. Therefore, no demo data is involved.

Cons:

- Requires additional steps for creating certificates and AAD registrations, and downloading the configuration file from HQ.

## Prerequisites for setting up the local development environment

Before you set up the self-hosted or IIS environment, install these prerequisites, in this order:

1. Install .Net Core SDK 3.1 for Windows x64 from [Download .NET Core 3.1](https://dotnet.microsoft.com/download/dotnet/3.1).
2. Install any edition of [SQL server](/sql-server/sql-server-downloads) with full text search enabled. For more information, see [Add Features to an Instance of SQL Server (Setup)](/sql/database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup). The minimum supported version is 13.0.5026.0 SqlServer 2016 SP2.
    + Enable Mixed (SQL + Windows/Integrated) authentication.
    + If you don't have a default instance of SQL Server installed then the deployment of CSU will fail with an error indicating an instance could not be located. If you want to use a named instance instead then modify the file **Install.ps1** (You can find this script in Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Scripts folder) by inserting this line after line #78:

    ```powershell
    $installerArgs += $("--sqlservername", "PutYourSqlServerSeenInSSMSHere")
    ```

    Substitute **PutYourSqlServerSeenInSSMSHere** with your SQL Server name.

3. Installed NuGet.exe from [Download latest version NuGet.exe](https://www.nuget.org/downloads). Copy it to some location and then add update the PATH environment variable to point to the folder.
4. If msbuild is not installed then install the Visual Studio tools from [Visual Studio downloads](https://visualstudio.microsoft.com/downloads/). Expand the section **Tools for Visual Studio**. Download and run **Build Tools for Visual Studio**. Do not specify any components. Select **Install** for the default installation.

    After it is installed, open a command prompt and run the command `where msbuild`. If msbuild is not found, run the command from within **Developer Command Prompt for VS**.

    After you locate msbuild.exe, make sure that the PATH environment variable contains a path to the folder containing msbuild at the beginning of the path. The path should contain an msbuild.exe of at least version 15. To check the version, run the command `msbuild /version`.

    To verify that the PATH variable is set correctly, run the command `msbuild/version` from within a plain command prompt. Don't use the Developer Command Prompt. It should print at least version 15. After you finish setting up msbuild, restart Visual Studio Code.

5. Install the Microsoft.NET.Sdk using the previously downloaded **Tools for Visual Studio** to install the SDK by navigating to **Individual components**. Enter **.NET SDK** and check the checkbox for .NET SDK. Select **Install**.
6. Install 64 bit Node.JS from [Download and Install Node](https://nodejs.org/en/download/) and make sure that PATH environment variable contains its location. If you are prompted, check the checkbox **Automatically install the necessary tools**.
7. Install 64-bit version of Visual Studio Code for Windows from [Download Visual Studio Code](https://code.visualstudio.com/download).
8. Install the C# for Visual Studio Code (powered by OmniSharp) extension for Visual Studio Code by following the [Install the extension VS document]( Managing Extensions in Visual Studio Code)
9. Clone or download the [Scale Unit GitHub repo](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit).
10. Navigate to the [Shared asset library](https://lcs.dynamics.com/V2/SharedAssetLibrary) and select the section **Retail Self-service package**. Find the file ending with **Commerce Scale Unit (PREVIEW)**. Make sure to select there the version for the release you need, for example 10.0.22 or 10.0.23. Download the file and put it in your download folder. You can find the download folder in scale unit GitHub repo you cloned or downloaded in the previous step (Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Download/).

## Additional prerequisites for IIS-hosted CSU

Prerequisites:

+ IIS with several features turned on, the installer will report any required but not yet enabled features.
+ Transport Layer Security (TLS) 1.2 should be enabled in the system (not TLS 1.0/1.1). You can leave this prerequisite check to the installer. The installer will print out actionable instructions if your machine needs changes for TSL 1.2.
+ You can proactively configure strong cryptography for TLS by making the following changes in the **.vscode/tasks.json** file:

    - **baseProduct_Port** - You can keep the default port 446 or change it to any value you want. If you specify the port used by another application then the Base Installer deployment will detect that and ask you to provide another port.
    - **baseProduct_SslCertFullPath** - This path should point to the SSL certificate used by CSU Web Site to be capable of HTTPS communication. For this non-production setup the certificate can be a Self-Signed one and it must be stored in LocalMachine/Personal certificate store. Generate the certificate by following these steps:

        1. Open IIS and double-click the icon for your machine name.
        2. Double-click **Server Certificates** icon.
        3. On right-hand side click the link **Create Self-Signed Certificate**.
        4. A popup asks you to provide a friendly name of the certificate. Specify there Fully Qualified Domain Name (FQDN) of your machine which includes the machine name itself as well as a domain if it is joined into one. You can find out FQDN by executing the Powershell command `[System.Net.Dns]::GetHostEntry("")`. The FQDN can also be retrieved from the System widget of the Windows Control Panel, look in the field Full computer name.
        5. Keep the default value for the certificate store - **Personal**.
        6. After you select **OK**, find the new certificate in the list and double-click it.
        7. Select the **Details** tab and locate a **Thumbprint**.
        8. Copy and paste the thumbprint into a text editor. Convert it to uppercase and specify it at the end of the predefined template for the option **baseProduct_SslCertFullPath** so that it looks like: `store:///My/LocalMachine?FindByThumbprint=YourThumbprintGoesHere`.

        > [!NOTE]
        > The base installer requires 2 more certificates, so there are 3 certificates in total. For all production deployments 3 different certificates should be created for security reasons. For this development setup you may decide to save time and use the same certificate for all 3 configuration options if this is not against your policies. In this case you can provide the same thumbprint in the 2 options described below.

    - **baseProduct_RetailServerCertFullPath** - Update this parameter with the thumbprint of the certificate that you create. This certificate is used to represent Retail Server's identity. The identity is used, for example, when CSU issues security tokens for POS scenarios. To create this certificate, follow the same process as for the above SSL certificate but specify any FriendlyName you want, for example, RsTestIdentity. You will need this certificate later when you set up the AAD application.
    - **baseProduct_AsyncClientCertFullPath** - This certificate is used by Async Client when it acquires a security token from AAD for communicating with HQ. Follow the same process above to create the certificate. Again, you can name it anything you want, for example, AsyncClientTestIdentity.
    - **baseProduct_RetailServerAadClientId** - This value is the AAD Application Client ID that represents the Retail Server's identity. It is used, for example, when CSU issues security tokens for POS scenarios. Follow step #3 in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) to create the application and retrieve its Application (client) ID.
    - **baseProduct_RetailServerAadResourceId** - This value is the resource ID of the above registered AAD application. Use the value described as Application ID URI in  step #3c [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) .
    - **baseProduct_CposAadClientId** - This value is AAD Application Client ID representing your Cloud POS. Follow the step #4 in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) to create the application and retrieve its Application (client) ID. This completes the CSU/CPOS setup in AAD. Follow the step #6 from [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) to complete required setup in HQ.
    - **baseProduct_AsyncClientAadClientId** - This value is the AAD Application Client ID used by Async Client when it needs to authenticate with HQ. To create this application register one more AAD application by following steps 3a-3b in [How to configure CPOS to use your own Azure AD application](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application). To register only the created application with HQ, follow step #2 from [here](https://community.dynamics.com/ax/b/axforretail/posts/service-to-service-authentication-in-ax7).
    - **baseProduct_Config** - Specify only the file name, not the full path, corresponding to the Channel Database Configuration downloadable from HQ as described in the step #4 of the task [Download the CSU installer](retail-store-scale-unit-configuration-installation#download-the-commerce-scale-unit-installer). After you download the file from HQ, put it in the [Download](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-ScaleUnit?path=/src/ScaleUnitSample/Download&version=GC0acfab2d3d7cbd734ea5b19f2b2ac6713d7391ef) folder.
    - **baseProduct_UseSelfHost** - Set this value to **false**.

## Debug an extension using the self-hosted CSU

1. Launch Visual Studio Code as administrator and open the `src\ScaleUnitSample` folder. You can find the `ScaleUnitSample` in scale unit GitHub repo you cloned or downloaded earlier.
2. Open the file `.vscode/tasks.json`, and set `baseProduct_UseSelfHost`  to `true`.
3. Select **Terminal**, **Run Task**, and **build-extension**.

    If there is an error that the running scripts is disabled on this system, then open a command prompt as administrator and execute `powershell Set-ExecutionPolicy RemoteSigned`. Restart Visual Studio Code. Do not change the ExecutionPolicy on production machines unless you understand the implications of changing security policies.

4. Put a break point in your extension method and click F5 to debug the extension.

After you click F5, the following are done automatically (supported in Visual Studio Code only):

- The Scale Unit Sample code is compiled. The compilation results in a package that contains the Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it was not yet deployed.
- The package containing demo data is downloaded from the SDK's feed and then applied to the Channel database.
- The Sealed Scale Unit Extension installer is deployed.
- A web browser page with a result of a call to CSU's health-check endpoint is displayed.
- The debugger is attached to the process hosting the CSU and the CSU is ready to serve incoming requests at the Url http://localhost:12345.

While the local scale unit is serving the requests, use the **DEBUG CONSOLE** to watch the scale unit's internal diagnostics logging in real-time. The log can be helpful when you are debugging.

## Debug an extension using the IIS-Hosted CSU

1. In Visual Studio Code click **Run and Debug** (Ctrl+Shift+D). A drop down menu with a green arrow will be displayed under the top navigation bar. Select **Debug with IIS**.
2. Click F5. Like debugging in self-hosted CSU mode, the base installer is deployed first and then the extension installer is deployed.
3. The base installer performs prerequisite checks and reports any actions required. The prerequisites include SQL Server, IIS, TLS, and .Net Core Hosting Bundle.
4. After the base and extension packages are deployed, Visual Studio Code opens a browser window with the results of a call to health-check. It also displays a dialog asking to attach a debugger. Attaching is optional. If you want to attach, then type **w3wp** in the list of processes and select the row that contains **RssuCore**. **RssuCore** is the name of the IIS Application Pool used to run the CSU web site.

    You now have a fully functional On-Prem deployed Scale Unit that includes:

    - Channel database
    - Async Client
    - ASP.NET  Core 3.1 based Retail Server capable of interacting with HQ via RTS
    - Cloud POS

You can find URLs corresponding to the just deployed CPOS and CSU if you review the base installer's log towards the end when CSU and CPOS are health-checked. In order to populate the Channel database with data from HQ you will need to execute the step #28 from here assuming you have already performed previous steps described in that document.

## Switching from IIS mode to Self-Hosted mode

If you will switch between IIS and Self-Host modes make sure to do the below steps (if this is your first run - you can skip them because those settings are default ones):

- In  Visual Studio Code hit the button Run and Debug (Ctrl+Shift+D), a Drop Down Menu with a green arrow will be displayed under the top navigation bar, select there Debug with Self-Host
- Open the file .vscode/tasks.json and make sure baseProduct_UseSelfHost is set to false.

### Once F5 is hit the following will be done automatically (supported in Visual Studio Code only)

- The Scale Unit Sample code is compiled. This essentially means an extension compilation which results in a package containing Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it was not deployed yet.
- The package containing Demo Data is downloaded from the SDK's feed and then being applied to the Channel DB
- Sealed Scale Unit Extension installer is deployed
- Web browser page with a result of a call to CSU's health-check endpoint is rendered
- The debugger is attached to the process hosting the CSU and the CSU is ready to serve incoming requests at the Url http://localhost:12345 .

While the local scale unit is serving the requests, you can observe "DEBUG CONSOLE" to watch its internal diagnostics logging in real-time which can be helpful while debugging.

## Deploy extension package to production:

Once the build is successfully completed, you can leverage the outputs to deploy your extensions:

- **Cloud Scale Unit extension package** is in ScaleUnit\bin\Debug\netstandard2.0 folder - used for Cloud deployments.
- **Scale Unit extension installer** is in Installer\bin\Debug\net461 - used for on-prem (in-store) installations.

It's recommended to setup a [build pipeline to generate the package](build-pipeline.md), [steps to deploy the package is documented here](retail-sdk/retail-sdk-packaging.md#deploy-the-package-to-csu).

### Troubleshooting

If anything doesn't go as expected while the packages were deployed, review the verbose set of logs and associated messages in the TERMINAL tab. If you cannot figure out what is wrong on your own, then contact Microsoft to get help and provide:

- Verbose description of the actions performed.
- The log file referenced at the very beginning and the very end of the Base Product's deployment process output.
-  Visual Studio Code Terminal's output including warnings/errors.

Runtime logs corresponding to Retail Server and Async Client (in case of IIS host) can be found in Event Viewer under Windows Logs->Application. Filter the log by the Sources:

- Microsoft Dynamics - Async Client Service
- Microsoft Dynamics - Retail Server
- Self-Hosted CSU will also print runtime logs directly to the  Visual Studio Code Terminal.

## Out Of the Box Tasks in  Visual Studio Code

A set of tasks is available via  Visual Studio Code's Terminal->Run Task... to achieve various goals:

- **build-extension** - builds an extension.
- **check-msbuild** - reveals msbuild's version available for Visual Studio Code.
- **check-ps-bitness** - checks if PowerShell available for Visual Studio Code is of required 64 bit version.
- **clean-extension** - cleans build output generated while the extension was built.
- **install** - verifies all Dev Time prerequisites and then performs all required actions for the selected mode (Self-Hosted vs IIS) to deploy the Scale Unit ready for a debug session. This includes installation of the Base Scale Unit as well as Extension Installer.
- **uninstall** - uninstall an Extension and Base Scale Unit.
- **uninstall-base-product** - uninstalls Base Scale Unit. Will fail if it detects an installed Extension.
- **uninstall-extension** - uninstalls an Extension.

### Feedback

If the setup doesn't work as expected or you need help, reach out via:

+ [microsoft/Dynamics365Commerce.ScaleUnit](https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/issues)
+ [Dynamics 365 Commerce Forum](https://community.dynamics.com/365/commerce/f/dynamics-365-commerce-forum)
+ [Retail Interest Group](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=1585934)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
