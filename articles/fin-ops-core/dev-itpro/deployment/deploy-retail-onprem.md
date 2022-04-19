---
# required metadata

title: Installation steps for Retail channel components in an on-premises environment
description: This topic covers the installation steps for Commerce channel components in an on-premises environment. 
author: jashanno
ms.date: 11/22/2021
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [retail]
ms.author: jashanno
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1.1
---

# Installation steps for Retail channel components in an on-premises environment

[!include[banner](../includes/banner.md)]

This topic covers the installation steps for Commerce channel components in an on-premises environment.

> [!IMPORTANT]
> There is currently a known issue where self-service packages will not correctly apply to on-premises environments. For that reason it is recommended to pull the installers directly from Microsoft Dynamics Lifecycle Services (LCS) and use them as needed. Commerce headquarters would thereby no longer be used to download the installers but only the configuration files as needed.

Channel functionality, in an on-premises environment, is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see [Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-system-begin.md). 

Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of channel components via Lifecycle Services (LCS). The only way to use channel components is by installing Commerce Scale Unit (self-hosted).

## Prerequisites 

Before you can start installation of channel components, you must first complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 12 and later)](setup-deploy-on-premises-pu12.md). In addition, version 8.1.1 must be installed in order for Commerce have full functionality. We recommend that you update to version 8.1.2.

> [!NOTE]
> It is critical to ensure that a secure network, that is not publicly  accessible, is used to connect Commerce Scale Unit to Headquarters. You must also restrict network access to Headquarters, so access is only allowed to known Commerce Scale Unit devices via network filtering or other means. This means that a firewall must exist and using a safe list is highly recommended.

## Installation steps

1. On the previously created [Application share](setup-deploy-on-premises-pu12.md#setupfile), (not the **LocalAgent** share folder), create a new folder called **selfservicepackages** in the root directory of the share location.  
2. On each AOS computer, create an easily accessible directory, such as **C:/selfservicepackages**.
3. On one AOS computer (which one does not matter), run the following PowerShell script.

    ```powershell
    .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -AosUrl 'https://<My Environment Name>.com/namespaces/AXSF/' -SendProductSupportTelemetryToMicrosoft
    ```
    > [!IMPORTANT]
    > - There is currently a known issue where self-service packages will not correctly apply to on-premises environments. For that reason it is recommended to pull the installers directly from Microsoft Dynamics Lifecycle Services (LCS) and use them as needed. Commerce headquarters would thereby no longer be used to download the installers but only the configuration files as needed.
    > - The steps above apply to version 10.0 and later.
    >
    > ```powershell
    > .\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database>' -DatabaseName '<Database name for AOS database>' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages, such as **C:/selfservicepackages**>' -SendProductSupportTelemetryToMicrosoft
    > ```
    > - The parameter **-envName** should be known based on creation when the environment is generated.
    > - The legacy parameters **-DatabaseServer** and **-DatabaseName** should be known based on the environment setup.
    > - The parameter **-SendProductSupportTelemetryToMicrosoft** is a required value to enable telemetry to Microsoft.  This is critical to maximize support from Microsoft.
    > - This script will perform a variety of actions, including updating the Service user and role and updating registry keys.

4. On each AOS computer, run the following PowerShell script.

   ```powershell
   .\RetailUpdateDatabase.ps1 -RetailSelfServicePackages 'C:\RetailSelfService\Packages'
   ```

    > [!NOTE]
    > The parameter **-RetailSelfServicePackages** is the full path location created in the beginning of this step (**C:/selfservicepackages**).

5.	Download the appropriate binary update from LCS to have the Commerce installers. For instructions, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
6.	Extract the zip file and copy all self-service installers into the folder **C:/selfservicepackages** defined and created in step 2 in each of the AOS machines. The six self-service installers include: 
    - AsyncServerConnectorServiceSetup.exe
    - RealtimeServiceAX63Setup.exe
    - HardwareStationSetup.exe
    - ModernPosSetup.exe
    - ModernPosSetupOffline.exe
    - StoreSystemSetup.exe

     > [!NOTE]
     > Cloud environments can synchronize self-service installers through Headquarters from what is available in LCS ([Synchronize self-service installers in Dynamics 365 Commerce](../../../commerce/dev-itpro/synchronize-installers.md)). On-premises environments cannot utilize this functionality, however, these environments can still download from LCS. The SDK is available in the deployable package zip file. The self-service installers are available from the LCS **Asset library**. You can utilize the upload and download mechanism from within LCS, but the Headquarters synchronization functionality will not work.


7.  Navigate to the AD FS machine, then go to the InfrastructureScripts folder. This is the same file directory where the previously run PowerShell script was located (**RetailUpdateDatabase.ps1**). Find the PowerShell script **Create-ADFSServerApplicationForRetail.ps1**.
8.  On the AD FS machine that you're currently using, run this script in a new PowerShell window using the command **.\Create-ADFSServerApplicationForRetail -HostUrl 'https://ax.d365ffo.onprem.contoso.com'**, where the **HostUrl** value can be found in Service Fabric.  To find the **HostUrl** value, go to **Service Fabric** &gt; **Application fabric:/AXSF** &gt; **Details** &gt; **Aad_AADValidAudience**.
9.  Access the newly generated Server application from the **Application Groups** in AD FS Management.
10.  Edit the newly generated Server application and select **Reset the Secret**.

     > [!NOTE]
     > It is an important security measure to run this script for each Commerce Scale Unit.  This maximizes security and minimizes the workload in case of a security breach. 
     >
     > It is critical to keep this secret safe. This secret should only be copied once and never stored on the system.  The Client ID and Secret generated will be used during the Commerce Scale Unit installer, so it is required to be used at a later time.  You can always reset the secret again, but it must then be updated on any Commerce Scale Unit that used the previous secret.

11.  Go to **Retail and Commerce \> Headquarters setup \> Commerce scheduler \> Connector for Microsoft Dynamics AX**.
12.  Select **Edit** on the Action pane.
13.  In the **Profile** field, enter the value **Default**.  If needed, enter a description in the **Description** field.

     > [!NOTE]
     > It is possible for the following fields in steps 12 through 14 to already have values. If this occurs, skip those steps and continue from there. What is important is to have a selectable profile title (default in this case).

14.  In the  **Web application name** field, enter **RetailCDXRealTimeService**.
15.  In the **Protocol** field, select **https**.
16.  In the **Common name** field, enter **AXServiceUser@contoso.com**.
17.  Select **Save** on the Action Pane.
18.  In Headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
19.  Select the **Security** tab.
20.  Under the sub-heading **Transaction service legacy properties**, select the **Real-time Service profile** field, and then select the newly created **Default** value.
21.  Select the **Identity providers** tab.
22.  On the **Identity providers** FastTab, select **Add**.
23.  In the new **Issuer** row, enter the new Identity provider value **https://sts.windows.net/** in the field.
24.  Select **Save** on the Action Pane.
25.  Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
26.  On the **General** tab, select the **Initialize** link to configure seed data for Commerce functionality.

     > [!NOTE]
     > - Read the important message at the beginning of this article regarding a known issue with installers no longer functioning through headquarters for download.
     > - The installers will not download from their relevant pages the first time a download is attempted.  This is because the installers have only just been placed into the download location and the associated database values do not yet exist.  In Headquarters, when the **Download** functionality is attempted (for example, Commerce Scale Unit or Modern POS), an error will display and then an automated upload functionality will be initiated to allow the installers to be downloaded the second time that the download is attempted. (Wait one minute before attempting to download the installer again).
     > - The Peripheral Simulator (downloaded on the Hardware profile page in headquarters) will not be available until at least one Hardware profile has been created and is functional. After that point has been achieved, the following script can be run.
     >
     > ```powershell
     > .\RetailUpdateDatabase.ps1 -envName 'LBDenv1' -UpdateRetailHardwareProfileSelfServicePackage
     > ```

28.	Follow the installation steps for installing the Commerce Scale Unit. For instructions, see [Configure and install Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-scale-unit-configuration-installation.md).  At multiple locations in this document there will be notes referencing changes to the instructions for an on-premises deployment. It is important to note each of these changes. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
