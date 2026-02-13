---
title: Patch SQL Server Reporting Services (SSRS) in one-box environments
description: Learn about the procedure on applying SSRS hotfixes to a one-box development environment, including an overview on patching the reporting service.
author: johnmichalak
ms.author: johnmichalak
ms.topic: how-to
ms.date: 11/11/2025
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 744bd1dc-d109-40df-a5dd-9db8982523a6
---

# Patch SQL Server Reporting Services (SSRS) in one-box environments

[!include [banner](../includes/banner.md)]

The following procedure is for one-box development environments only.

## Patch the Reporting Service

The following procedure is for one-box development environments only.

-   Download the patch .zip file from Lifecycle Services.
-   If there are any font files in the Reporting Service patch's data folder, install these fonts on the machine where SQL Server Reporting Services (SSRS) is running. For more information about installing fonts on Windows, see [How to install or remove a font in Windows](https://support.microsoft.com/help/314960/how-to-install-or-remove-a-font-in-windows). You don't need to reinstall any fonts that are already installed.
-   Copy the files in the Reporting Services patch scripts folder to the Report plug-in folder located under C:\\Packages\\Plugins\\AxReportVmRoleStartupTask.
-   Change the directory to the Report plug-in folder where you stored the script files.
-   Use one of the following methods to replace the old instance of reporting extensions:
    -   Remove and reinstall the reporting extension. This option requires that you redeploy all reports after you finish the reinstallation.
    -   Manually copy binaries to the SQL Server binary folder. If you choose to manually copy the files, you don't need to redeploy reports.

### Remove and reinstall the reporting extension
Complete the following procedure as a user in the administrator group for the machine where SSRS is running.

-   Using Windows PowerShell, remove the Dynamics SSRS extension by running the following script:
    -   PowerShell .\\DeploySsrsExtension.ps1 –UninstallOnly
-   In PowerShell, reinstall the Dynamics SSRS extension by running the following script:
    -   PowerShell .\\DeploySsrsExtension.ps1
-   Removing the reporting extension removes all the reports. If you remove and then reinstall the reporting extension, you need to redeploy the reports by running the following script:
    -   PowerShell .\\DeployAllReportsToSsrs.ps1
-   This task takes 20 to 30 minutes to complete.

### Manually copy binaries to the SQL Server binary folder
1.  Stop SQL Server Reporting Services. You can stop the service from either the **Services management** console or the **Reporting Services Configuration Manager**. 

:::image type="content" source="./media/configuration_rshotfix.png" alt-text="Screenshot of Configuration_RSHotfix.":::

1.  Find the SQL Server Reporting Services binary folder. This folder is located at `C:\Program Files\Microsoft SQL Server\MSRS11.MSSQLSERVER\Reporting Services\ReportServer\bin`.
1.  If the patch contains any of the following files, copy them to the SQL Server Reporting Services bin folder.* *

> [!NOTE]
> Patches can either be full patches, which contain all of the files used by the service, or incremental patches, which contain only the files that changed. If you have an incremental patch, some files might not be included. You don't need to replace files that aren't included in the patch.

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
The reporting service installation makes the following changes: The installation copies the following files into the reporting service bin folder (C:\\Program Files\\Microsoft SQL Server\\MSRS11.MSSQLSERVER\\Reporting Services\\ReportServer\\bin), and updates the corresponding SSRS config files so that SSRS is aware of the extension.

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

The installation updates an SSRS service account to use the local system. It creates a new SSRS catalog database named DynamicsAxReportServer and a temp database named DynamicsAxReportServerTempDB, and configures SSRS to use these two databases. The default catalog databases ReportServer and ReportServerTempDB still exist, but the installation sets them to not be used by reporting services. The installation updates the SSRS service to use Windows Authentication. It creates an XML configuration file named ReportPVMConfiguration.xml in the SSRS bin folder for the report runtime. It creates a report root folder named **Dynamics** and a new security role named **DynamicsBrowser**. Both AOS Web application AppPool identity and batch service account are added to this custom role. During deployment, the report folder is deleted and then recreated. Therefore, all the previously deployed reports are deleted from the SSRS server. After you reinstall the reporting extension, you must redeploy the reports.  





[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
