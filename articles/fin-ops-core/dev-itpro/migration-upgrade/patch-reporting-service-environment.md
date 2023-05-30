---
title: Patch SQL Server Reporting Services (SSRS) in one-box environments
description: Apply SSRS hotfixes to a one-box development environment.
author: RichdiMSFT
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: sericks
ms.search.region: Global
ms.author: richdi
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 744bd1dc-d109-40df-a5dd-9db8982523a6
---

# Patch SQL Server Reporting Services (SSRS) in one-box environments

[!include [banner](../includes/banner.md)]

The following procedure is for one-box development environments only.

## Patch the Reporting Service

The following procedure is for one-box development environments only.

-   Download the patch .zip file from Lifecycle Services (LCS).
-   If there are any font files in the Reporting Service patch’s data folder, install these to the machine where SQL Server Reporting Services (SSRS) is running. For more information about installing fonts on Windows, see [How to install or remove a font in Windows](https://support.microsoft.com/help/314960/how-to-install-or-remove-a-font-in-windows).  Any fonts that have already been installed do not need to be installed again.
-   Copy the files in the Reporting Services patch scripts folder to the Report plug-in folder located under C:\\Packages\\Plugins\\AxReportVmRoleStartupTask.
-   Change the directory to the Report plug-in folder where you stored the script files.
-   Using one of the methods listed below, replace the old instance of reporting extensions.
    -   Remove/reinstall the reporting extension. The remove/reinstall option requires that redeploy all reports after you have finished the reinstallation..
    -   Manually copy binaries to the sql server binary folder. If you choose to manually copy the files, then you do not need to redeploy reports.

### Remove/reinstall the reporting extension
Complete the following procedure as a user in the administrator group for the machine where SSRS is running.

-   Using Windows PowerShell, remove the Dynamics SSRS extension by running the following script:
    -   PowerShell .\\DeploySsrsExtension.ps1 –UninstallOnly
-   In PowerShell, reinstall the Dynamics SSRS extension by running the following script:
    -   PowerShell .\\DeploySsrsExtension.ps1
-   Removing the reporting extension removes all the reports. If you have removed and then reinstalled the reporting extension, it is necessary to re-deploy the reports by running the following script:
    -   Powershell .\\DeployAllReportsToSsrs.ps1
-   This task will take 20 to 30 minutes to complete.

### Manually copy binaries to the SQL Server binary folder
1.  Stop SQL Server Reporting Services. This can be done either from the **Services management** console or from the **Reporting Services Configuration Manager**. [![Configuration\_RSHotfix.](./media/configuration_rshotfix.png)](./media/configuration_rshotfix.png)
2.  Find the SQL Server Reporting Services binary folder. This folder is usually located at C:\\Program Files\\Microsoft SQL Server\\MSRS11.MSSQLSERVER\\Reporting Services\\ReportServer\\bin.
3.  If any of the following files are in the patch, copy them to the SQL Server Reporting Services bin folder.* *

> [!NOTE]
> Patches can either be full patches, which would contain all of the files used by the service, or incremental patches, which contain only the files that have changed. If you have an incremental patch, then some files may not be included. Files not included in the patch do not need to be replaced.

-   Microsoft.Dynamics.AX.Framework.Services.Platform.Client.dll
-   Microsoft.Dynamics.Framework.ReportsExtensions.dll
-   Microsoft.Dynamics.Framework.Reports.dll
-   Microsoft.Dynamics.ApplicationPlatform.SSRSReportRuntime.Instrumentation.dll
-   Microsoft.Dynamics.ApplicationPlatform.SSRSReportRuntime.man
-   Microsoft.Dynamics.Platform.Integration.ClientSdk.Abstraction.dll
-   Microsoft.Dynamics.AX.Framework.Reports.Shared.dll
-   Microsoft.Dynamics.AX.Framework.EncryptionEngine.dll
-   Microsoft.Dynamics.AX.Framework.Utilities.dll
-   Microsoft.Dynamics.ApplicationSuite.Reporting.BusinessLogic.dll
-   Microsoft.Dynamics.ApplicationPlatform.Environment.dll
-   Microsoft.Dynamics.AX.ReportConfiguration.axc
-   Microsoft.WindowsAzure.ServiceRuntime.dll
-   Microsoft.IdentityModel.dll
-   msshrtmi.dll

Restart SQL Server Reporting Services.

### Reporting service installation
The following changes are made with the reporting service installation: The following files will be copied into Reporting service bin folder (C:\\Program Files\\Microsoft SQL Server\\MSRS11.MSSQLSERVER\\Reporting Services\\ReportServer\\bin), and the corresponding SSRS config files will be updated so that SSRS is aware of the extension.

-   Dynamics.AX.Framework.Services.Platform.Client.dll
-   Dynamics.Framework.ReportsExtensions.dll
-   Dynamics.Framework.Reports.dll
-   Dynamics.ApplicationPlatform.SSRSReportRuntime.Instrumentation.dll
-   Dynamics.ApplicationPlatform.SSRSReportRuntime.man
-   Dynamics.Platform.Integration.ClientSdk.Abstraction.dll
-   Dynamics.AX.Framework.Reports.Shared.dll
-   Dynamics.AX.Framework.EncryptionEngine.dll
-   Dynamics.AX.Framework.Utilities.dll
-   Dynamics.ApplicationSuite.Reporting.BusinessLogic.dll
-   Dynamics.ApplicationPlatform.Environment.dll
-   Dynamics.AX.ReportConfiguration.axc
-   WindowsAzure.ServiceRuntime.dll
-   IdentityModel.dll
-   msshrtmi.dll

An SSRS service account will be updated to use the local system. A new SSRS catalog database DynamicsAxReportServer and temp database DynamicsAxReportServerTempDB database will be created, and SSRS will be configured to use these two databases. The default catalog database ReportServer and ReportServerTempDBstill exist, but are set to not be used by reporting services. The SSRS service will be updated to use Windows Authentication. An xml configuration file ReportPVMConfiguration.xml will be created in the SSRS bin folder for the report runtime. A report root folder named **Dynamics** and a new security role named **DynamicsBrowser** will be created. Both AOS Web application AppPool identity and batch service account will be added to this custom role. Note that during deployment, the report folder will be deleted and then recreated. Therefore all the previously deployed reports will be deleted from the SSRS server.  After you reinstall the reporting extension, you must redeploy the reports.  





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
