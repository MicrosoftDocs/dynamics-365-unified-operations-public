---
# required metadata

title: Installation steps for Retail channel components in an on-premises environment
description: This article covers the installation steps for Commerce channel components in an on-premises environment. 
author: jashanno
ms.date: 08/31/2022
ms.topic: article
ms.prod: dynamics-365 
ms.service:
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
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

This article covers the installation steps for Commerce channel components in an on-premises environment.

> [!IMPORTANT]
> There is currently a known issue where self-service packages will not correctly apply to on-premises environments. For that reason it is recommended to pull the installers directly from Microsoft Dynamics Lifecycle Services (LCS) and use them as needed. Commerce headquarters would thereby no longer be used to download the installers but only the configuration files as needed.

Channel functionality, in an on-premises environment, is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see [Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-system-begin.md). 

Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of channel components via Lifecycle Services (LCS). The only way to use channel components is by installing Commerce Scale Unit (self-hosted).

## Prerequisites 

Before you can start installation of channel components, you must first complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 41 and later)](setup-deploy-on-premises-pu41.md). At least version 8.1.1 must be installed in order for Commerce have full functionality. We recommend that you update to the latest application version available.

> [!NOTE]
> It is critical to ensure that a secure network, that is not publicly  accessible, is used to connect Commerce Scale Unit to Headquarters. You must also restrict network access to Headquarters, so access is only allowed to known Commerce Scale Unit devices via network filtering or other means. This means that a firewall must exist and using a safe list is highly recommended.

## Installation steps

1. On the previously created [Application share](setup-deploy-on-premises-pu41.md#setupfile), (not the **LocalAgent** share folder), create a new folder called **selfservicepackages** in the root directory of the share location.  
2. On each AOS node, create an easily accessible directory, such as **C:\RetailSelfService**.
3. On one AOS node (doesn't matter which one), run the RetailUpdateDatabase.ps1 script. If you used the remoting scripts, this script will be available in each AOS node in this path `C:\D365FFO-LBD`.

     If your commerce headquarters is on version 10.0.0 or later execute
     ```powershell
     .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -AosUrl 'https://ax.d365ffo.onprem.contoso.com/namespaces/AXSF/' -SendProductSupportTelemetryToMicrosoft
     ```

     If your commerce headquarters is on a version prior to 10.0.0 execute
     ```powershell
     .\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database>' -DatabaseName '<Database name for AOS database>' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages, such as **C:\RetailSelfService**>' -SendProductSupportTelemetryToMicrosoft
     ```

     - The parameter **-envName** is the name assigned to the environment in Lifecycle Services when it was originally deployed.
     - The parameter **-SendProductSupportTelemetryToMicrosoft** is a required value to enable telemetry to Microsoft.  This is critical to maximize support from Microsoft.
     - This script will perform a variety of actions, including updating the Service user and role and updating registry keys.

    > [!IMPORTANT]
    > There is currently a known issue where self-service packages will not correctly apply to on-premises environments. For that reason it is recommended to pull the installers directly from Microsoft Dynamics Lifecycle Services (LCS) and use them as needed. Commerce headquarters would thereby no longer be used to download the installers but only the configuration files as needed.

4. On each AOS node, run the following PowerShell script.

     ```powershell
     .\RetailUpdateDatabase.ps1 -RetailSelfServicePackages 'C:\RetailSelfService\Packages'
     ```

    > [!NOTE]
    > The parameter **-RetailSelfServicePackages** is the full path location created in the beginning of this step (**C:\RetailSelfService**).

5. Download the appropriate binary update from LCS to have the Commerce installers. For instructions, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
6. Extract the zip file and copy all self-service installers into the folder **C:\RetailSelfService** defined and created in step 2 in each of the AOS machines. The six self-service installers include: 
    - AsyncServerConnectorServiceSetup.exe
    - RealtimeServiceAX63Setup.exe
    - HardwareStationSetup.exe
    - ModernPosSetup.exe
    - ModernPosSetupOffline.exe
    - StoreSystemSetup.exe

     > [!NOTE]
     > Cloud environments can synchronize self-service installers through Headquarters from what is available in LCS ([Synchronize self-service installers in Dynamics 365 Commerce](../../../commerce/dev-itpro/synchronize-installers.md)). On-premises environments cannot utilize this functionality, however, these environments can still download from LCS. The SDK is available in the deployable package zip file. The self-service installers are available from the LCS **Asset library**. You can utilize the upload and download mechanism from within LCS, but the Headquarters synchronization functionality will not work.

7. Navigate to the AD FS machine, open a powershell window with administrator privileges and navigate to the file share that contains your infrastructure scripts folder and run the following command. 
     ```powershell
     # Host URL is your DNS record\host name for accessing the AOS
     .\Create-ADFSServerApplicationForRetail -HostUrl 'https://ax.d365ffo.onprem.contoso.com'
     ```
     > [!NOTE]
     > It is a security best practice to run this script for each Commerce Scale Unit. This maximizes security and minimizes the workload in case of a security breach.

8. Access the newly generated Server application from the **Application Groups** in AD FS Management.
9. Edit the newly generated Server application and select **Reset the Secret**.

     > [!NOTE]
     > It is critical to keep this secret safe. This secret should only be copied once and never stored on the system. The Client ID and Secret generated will be used during the Commerce Scale Unit installer, so it is required to be used at a later time. You can always reset the secret again, but it must then be updated on any Commerce Scale Unit that used the previous secret.

10. In Headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
11. Select the **Security** tab.
12. Under the sub-heading **Transaction service legacy properties**, select the **Real-time Service profile** field, and then select the newly created **Default** value.
13. Select the **Identity providers** tab.
14. On the **Identity providers** FastTab, select **Add**.
15. In the new **Issuer** row, enter the new Identity provider value **https://sts.windows.net/** in the field.
16. Select **Save** on the Action Pane.
17. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
18. On the **General** tab, select the **Initialize** link to configure seed data for Commerce functionality.

     > [!NOTE]
     > - Read the important message at the beginning of this article regarding a known issue with installers no longer functioning through headquarters for download.
     > - The installers will not download from their relevant pages the first time a download is attempted. This is because the installers have only just been placed into the download location and the associated database values do not yet exist. In Headquarters, when the **Download** functionality is attempted (for example, Commerce Scale Unit or Modern POS), an error will display and then an automated upload functionality will be initiated to allow the installers to be downloaded the second time that the download is attempted. (Wait one minute before attempting to download the installer again).
     > - The Peripheral Simulator (downloaded on the Hardware profile page in headquarters) will not be available until at least one Hardware profile has been created and is functional. After that point has been achieved, the following script can be run.
     >
     > ```powershell
     > .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -UpdateRetailHardwareProfileSelfServicePackage
     > ```

19. Follow the installation steps for installing the Commerce Scale Unit. For instructions, see [Configure and install Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-scale-unit-configuration-installation.md).  At multiple locations in this document there will be notes referencing changes to the instructions for an on-premises deployment. It is important to note each of these changes. 


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
