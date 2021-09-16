---
title: Setup a local development environment
description: This topic explains how to setup a local development environment for Microsoft Dynamics 365 Commerce Cloud scale unit (CSU) and POS development.
author: mugunthanm
ms.date: 09/16/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: rhaertle
ms.custom: "intro-internal"
ms.search.region: Global
ms.author: mumani
ms.search.validFrom: 09-16-2021
ms.dyn365.ops.version: AX 10.0.22
---

# Setup a local development environment

[!include [banner](../../../includes/banner.md)]

This topic explains how to setup a local development environment for Microsoft Dynamics 365 Commerce Cloud scale unit (CSU) and POS development, and applies to Dynamics 365 Commerce application version 10.0.22 and later.

### Commerce supports different development environment types:

The below environment setup must be done only for extension development purpose, it must not be used for test/UAT or production.

- Deploy cloud based development environment using [Lifecycle Service (LCS)]( https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/dev-tools/access-instances)
- Local development environment - Setup a development environment in your own machine, there are two options to setup your own development environment:

    - **Self-hosted CSU** – This environment type deploys commerce scale unit locally (self hosted- hosted as exe) without any IIS, Commerce data sync, and no HQ connectivity for real time calls. With this option there will not be any data sync between HQ and CSU channel database, channel database will be populated with the default demo data for development purpose and all the request/calls to HQ will be mocked by the local CSU. Ex: Call to issue gift card will be mocked by the local CSU.
    - **IIS-Hosted CSU** - This environment type deploys commerce scale unit in IIS and sets up async client to sync the data between HQ and CSU channel database and real time connection support with the HQ. This setup requires some additional configuration like AAD app setup, certificates deployment etc. For detailed step to install the IIS-Hosted CSU refer the [Configure and install IIS-Hosted Commerce Scale Unit document.] ( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-store-scale-unit-configuration-installation#configure-a-new-commerce-scale-unit)


### Choosing between Self hosted vs IIS hosted:

#### Self-hosted modeSelf-hosted mode

This is a very light-weight version of the scale unit providing a quick way to develop wide spectrum of CRT/RTS extensions requiring minimal to no dependencies on other systems/services.

**Pros**

- Doesn't require HQ.
- Doesn't require IIS. Retail Server is hosted in a Console Application
- TLS configuration is not required
- RTS communication is mocked via a set of Demo Mode CRT Handlers
- Async Client is not needed, the Channel DB is automatically populated with a Demo Data.
- Requires very few parameters to initiate the Scale Unit deployment so the required prerequisites are minimal. For instance - no certificates have to be explicitly created and provided to the installer
- Provides very fast and easy introduction into CRT/Retail Server development and runtime capabilities

**Cons**

- Doesn't match topology used in real production environments (no CPOS, no Async Client, no RTS calls, no HTTPS).
- Real Time operations cannot be fully tested (they must be mocked).

#### IIS mode

This is a complete on-prem Scale Unit with all the components matching real production deployments where nothing is mocked.

**Pros**

- Represents fully capable on-prem Scale Unit hosting Retail Server in IIS, employs real (not mocked) RTS interaction with HQ as well as involves Async Client populating Channel DB based on HQ DB data as regular Scale Unit does so no Demo Data is involved.

**Cons**

- Requires additional steps for creating certificates, AAD registrations and downloading the configuration file from HQ.

### Prerequisites to setup the local development environment 

To setup the self-hosted or IIS CSU, install the below prerequisites: 

1.	Install .Net Core SDK 3.1 for Windows x64 from https://dotnet.microsoft.com/download/dotnet/3.1
2.	Install any edition of [SQL server]( https://www.microsoft.com/en-us/sql-server/sql-server-downloads)  with [full text search enabled] (https://docs.microsoft.com/en-us/sql/database-engine/install-windows/add-features-to-an-instance-of-sql-server-setup?view=sql-server-ver15#to-add-features-to-an-instance-of-), minimum supported version is 13.0.5026.0 SqlServer 2016 SP2.
a.	Enable Mixed (SQL + Windows/Integrated) authentication.
b.	If you don't have Default instance of SQL Server installed then the deployment of CSU will fail with error indicating an instance could not be located, if you want to use Named instance instead then modify the file Install.ps1 (you can find this script in Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Scripts folder) by inserting this line after #78: $installerArgs += $("--sqlservername", "PutYourSqlServerSeenInSSMSHere"). Substitute PutYourSqlServerSeenInSSMSHere with your SQL Server Name. Number of features must be enabled on the SQL Server:

3.	[Download latest version NuGet.exe] (https://www.nuget.org/downloads) and copy to some location and then add Environment Variables PATH, pointing to the folder.
4.	If msbuild is not installed then install Visual studio tools from https://visualstudio.microsoft.com/downloads/ , scroll down to "Tools for Visual Studio", expand it and download/run "Build Tools for Visual Studio", while installing do not specify any components, just hit "Install" button. 

    Once it is installed, open cmd.exe and execute where msbuild, if msbuild will not be found, execute the same command from within "Developer Command Prompt for VS". 

    Once you locate the msbuild.exe make sure that Environment System Variable PATH contains a PATH to the folder containing msbuild at the very top of the list. 
    That path should contain an msbuild.exe of at least version 15, to check the version execute msbuild /version. 

    To verify the PATH variable is sect correctly, execute msbuild/version from within regular cmd.exe, don't use Developer Command Prompt this time, 
    it should print at least version 15. Once you finished setting up msbuild, restart VS Code.

5.	Install 'Microsoft.NET.Sdk' use the previously downloaded "Tools for Visual Studio" to install the SDK by navigating to: "Individual components"->Type '.NET SDK'-> Check the CheckBox .NET SDK and hit "Install".
6.	[Download and Install Node]( https://nodejs.org/en/download/) and ensure that Environment System Variable PATH contains its location." install 64 bit Node.JS, if prompted set the checkbox "Automatically install the necessary tools".
7.	Install 64-bit version of VS Code for Windows from https://code.visualstudio.com/download
8.	Install the C# for Visual Studio Code (powered by OmniSharp) extension for VS Code by following the [Install the extension VS document.]( Managing Extensions in Visual Studio Code)
9.	Clone or download the [Scale Unit GitHub repo] (https://github.com/microsoft/Dynamics365Commerce.ScaleUnit)
10.	Navigate to https://lcs.dynamics.com/V2/SharedAssetLibrary  select the section Retail Self-service package files and then locate there the file ending with Commerce Scale Unit (PREVIEW). Make sure to select there the version for the release you need, for instance 10.0.22, 10.0.23 and so on. Download the file and place it in the Download folder, you can find the Download folder in scale unit GitHub repo you cloned or downloaded in the previous step (Dynamics365Commerce.ScaleUnit/src/ScaleUnitSample/Download/ )

#### Additional prerequisites for IIS-Hosted CSU

1. IIS (Internet Information Services) with several features turned on, the installer will report any required but not yet enabled features.
2. Only TLS 1.2 (not TLS 1.0/1.1) should be enabled in the system, you can leave this prerequisite check to the installer which will print out actionable instructions in case your machine needs changes in that area. Or you can proactively configure strong cryptography as described here .

4. Make the following changes in the file .vscode/tasks.json
 - **baseProduct_Port** - you can keep the default port 446 or change it to any value you want. If you will specify the port used by another application the Base Installer deployment will detect that and ask you to provide another port.
 - **baseProduct_SslCertFullPath** should point to the SSL certificate used by CSU Web Site to be capable of HTTPS communication. For this non-Production setup the certificate can be a Self-Signed one and it must be stored in LocalMachine/Personal certificate store.

    **To generate the certificate follow the steps**:

    - Open IIS and double-click the icon representing your machine name

    -  Double-click Server Certificates icon
    -  On right hand side click the link Create Self-Signed Certificate...
    -  A popup will be opened and will ask you to provide a friendly name of the certificate. Specify there Fully Qualified Domain Name (FQDN) of your machine which includes the machine name itself as well as a domain if it is joined into one. You can find out FQDN by executing the Powershell [System.Net.Dns]::GetHostEntry(""). FQDN can also be retrieved from the System widget of the Windows Control Panel, look there into the field Full computer name.
    -  Keep the default value for the certificate store - Personal
    -  Once you click OK button, find just created certificate in the list and double click it
    -  Select the tab Details and locate a Thumbprint there
    -  Copy/paste the thumbprint into a text editor, make it uppercased and specify it at the end of the predefined template for the option baseProduct_SslCertFullPath so it should look like: store:///My/LocalMachine?FindByThumbprint=YourThumbprintGoesHere


Note: The Base Installer requires 2 more certificates, so there are 3 certificates in total. For all production deployments 3 different certificates should be created for security reasons but for this dev setup you may decide to save time and use the same certificate for all 3 configuration options if this is not against your policies. In this case you can provide the same thumbprint in the 2 options described below.

  - **baseProduct_RetailServerCertFullPath** In the way like the above, you need to update this parameter with the thumbprint of the certificate you will create. This certificate will be used to represent Retail Server's Identity, which is used, for instance, when CSU issues security tokens used in POS scenarios. To create this certificate, follow the same process as for the above SSL certificate but specify any FriendlyName you want, for instance, RsTestIdentity. You will need this certificate later while setting up AAD application.
  - **baseProduct_AsyncClientCertFullPath** This certificate is used by Async Client when it acquires a security token from AAD for a sake of communication with HQ. Follow the same approach as above to create the certificate and similarly name it as you want, for instance, AsyncClientTestIdentity.
  - **baseProduct_RetailServerAadClientId** AAD Application Client ID representing Retail Server's identity which is used, for instance, when CSU issues security tokens used in POS scenarios. Follow the steps under #3 described [here](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application)  to create the application and retrieve its Application (client) ID.
  - **baseProduct_RetailServerAadResourceId** This is the resource ID of the above registered AAD application. Supply here the value described as Application ID URI in 3c [here](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) .
  - **baseProduct_CposAadClientId** This is AAD Application Client ID representing your Cloud POS. Follow the step #4 [here](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application)  to create the application and retrieve its Application (client) ID. This completes CSU/CPOS setup in AAD, make sure to follow the step #6 from [here](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application)  to complete required setup in HQ.
  - **baseProduct_AsyncClientAadClientId** This is the AAD Application Client ID used by Async Client when it needs to authenticate with HQ. To create this application register one more AAD application by following 3a-3b from [here](https://community.dynamics.com/ax/b/axforretail/posts/how-to-point-cpos-to-use-your-own-azure-ad-application) . To register just created application with HQ follow #2 from [here](https://community.dynamics.com/ax/b/axforretail/posts/service-to-service-authentication-in-ax7) 
  - **baseProduct_Config** Specify the file name, without a full path, corresponding to the Channel Database Configuration downloadable from HQ as described in the bullet 4 of the section [Download the CSU installer](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-store-scale-unit-configuration-installation#download-the-commerce-scale-unit-installer). Once you download the file from HQ place it in the [Download](https://msazure.visualstudio.com/D365/_git/Commerce-Samples-ScaleUnit?path=/src/ScaleUnitSample/Download&version=GC0acfab2d3d7cbd734ea5b19f2b2ac6713d7391ef) folder.
  - **baseProduct_UseSelfHost** Set to false.


## How to debug extensions:

### Self-hosted CSU:

1.	Launch the VS Code as Administrator and open src\ScaleUnitSample by leveraging the menu File->Open Folder. (You can find the ScaleUnitSample in scale unit GitHub repo you cloned or downloaded in the previous step),
2.	In VS code open the file .vscode/tasks.json
      - Set baseProduct_UseSelfHost  to true.
3.	In VS Code click Terminal->Run Task...->build-extension:

If there is an error indicating running scripts is disabled on this system, then open cmd.exe as Administrator and execute powershell Set-ExecutionPolicy RemoteSigned then restart VS Code. Do not change the ExecutionPolicy on production machines unless you understand the implications of changing security policies. .

4.	Place a break point in your extension method and press F5 in VS code.

#### Once F5 is hit the following will be done automatically (supported in Visual Studio Code only):

- The Scale Unit Sample code is compiled. This essentially means an extension compilation which results in a package containing Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it was not deployed yet.
- The package containing Demo Data is downloaded from the SDK's feed and then being applied to the Channel DB
- Sealed Scale Unit Extension installer is deployed
- Web browser page with a result of a call to CSU's health-check endpoint is rendered
- The debugger is attached to the process hosting the CSU and the CSU is ready to serve incoming requests at the Url http://localhost:12345 .
While the local scale unit is serving the requests, you can observe "DEBUG CONSOLE" to watch its internal diagnostics logging in real-time which can be helpful while debugging.

### IIS-Hosted CSU

1.	In VS Code hit the button Run and Debug (Ctrl+Shift+D), a Drop Down Menu with a green arrow will be displayed under the top navigation bar, select there Debug with IIS
2.	Hit F5. As in case of the Self-Hosted mode the Base Installer will be deployed first and that will be followed by a deployment of the Extension Installer.
3.	While Base Installer will execute it will perform number of prerequisite checks and report any actions required, the prerequisites verify: SQL Server, IIS, TLS, .Net Core Hosting Bundle, and so on.
4.	Once Base and Extension packages are deployed, VS Code will open a browser window with the results of a call to health-check and will also display a dialog asking to attach a debugger. Attaching is optional, if you want to attach type w3wp in the list of processes and select the row which will contain RssuCore in it, that is the name of the IIS Application Pool used to run CSU Web Site.

    At this time, you have fully functional On-Prem deployed Scale Unit which includes:

      - Channel DB
      - Async Client
      - ASP.NET  Core 3.1 based Retail Server capable of interacting with HQ via RTS
      - Cloud POS

You can find URLs corresponding to just deployed CPOS and CSU if you review the Base Installer's log towards the end when CSU and CPOS are health-checked. In order to populate the Channel DB with data from HQ you will need to execute the step #28 from here  assuming you have already performed previous steps described in that document.

### Switching from IIS mode to Self-Hosted mode

If you will switch between IIS and Self-Host modes make sure to do the below steps (if this is your first run - you can skip them because those settings are default ones):

- In VS Code hit the button Run and Debug (Ctrl+Shift+D), a Drop Down Menu with a green arrow will be displayed under the top navigation bar, select there Debug with Self-Host
- Open the file .vscode/tasks.json and make sure baseProduct_UseSelfHost is set to false.

#### Once F5 is hit the following will be done automatically (supported in Visual Studio Code only):

- The Scale Unit Sample code is compiled. This essentially means an extension compilation which results in a package containing Sealed CSU Extension installer.
- The Base Sealed Scale Unit installer is deployed if it was not deployed yet.
- The package containing Demo Data is downloaded from the SDK's feed and then being applied to the Channel DB
- Sealed Scale Unit Extension installer is deployed
- Web browser page with a result of a call to CSU's health-check endpoint is rendered
- The debugger is attached to the process hosting the CSU and the CSU is ready to serve incoming requests at the Url http://localhost:12345 .

While the local scale unit is serving the requests, you can observe "DEBUG CONSOLE" to watch its internal diagnostics logging in real-time which can be helpful while debugging.

### Deploy extension package to production:

Once the build is successfully completed, you can leverage the outputs to deploy your extensions:

- **Cloud Scale Unit extension package** is in ScaleUnit\bin\Debug\netstandard2.0 folder - used for Cloud deployments.
- **Scale Unit extension installer** is in Installer\bin\Debug\net461 - used for on-prem (in-store) installations.

It's recommended to setup a [build pipeline to generate the package]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/build-pipeline), [steps to deploy the package is documented here]( https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging#deploy-the-package-to-csu).

#### Troubleshooting

If anything doesn't go as expected while the packages were deployed, review the verbose set of logs and associated messages in the TERMINAL tab. If you cannot figure out what is wrong on your own, then contact Microsoft to get help and provide:

- Verbose description of the actions performed.
- The log file referenced at the very beginning and the very end of the Base Product's deployment process output.
- VS Code Terminal's output including warnings/errors.

Runtime logs corresponding to Retail Server and Async Client (in case of IIS host) can be found in Event Viewer under Windows Logs->Application. Filter the log by the Sources:

- Microsoft Dynamics - Async Client Service
- Microsoft Dynamics - Retail Server
- Self-Hosted CSU will also print runtime logs directly to the VS Code Terminal.

#### Out Of the Box Tasks in VS Code

A set of tasks is available via VS Code's Terminal->Run Task... to achieve various goals:
- **build-extension** - builds an extension.
- **check-msbuild** - reveals msbuild's version available for Visual Studio Code.
- **check-ps-bitness** - checks if PowerShell available for Visual Studio Code is of required 64 bit version.
- **clean-extension** - cleans build output generated while the extension was built.
- **install** - verifies all Dev Time prerequisites and then performs all required actions for the selected mode (Self-Hosted vs IIS) to deploy the Scale Unit ready for a debug session. This includes installation of the Base Scale Unit as well as Extension Installer.
- **uninstall** - uninstall an Extension and Base Scale Unit.
- **uninstall-base-product** - uninstalls Base Scale Unit. Will fail if it detects an installed Extension.
- **uninstall-extension** - uninstalls an Extension.

#### Feedback

If anything, in regards to the Scale Unit Dev Experience, is not working as expected or you need help, reach out via:
https://github.com/microsoft/Dynamics365Commerce.ScaleUnit/issues 
https://community.dynamics.com/365/commerce/f/dynamics-365-commerce-forum 
https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=1585934 
