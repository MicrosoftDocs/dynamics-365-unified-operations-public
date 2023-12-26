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
search.app:
  - financeandoperationsonprem-docs
---

# Installation steps for Retail channel components in an on-premises environment

[!include[banner](../includes/banner.md)]

This article covers the installation steps for Commerce channel components in an on-premises environment.

> [!IMPORTANT]
> There is currently a known issue where self-service packages aren't correctly applied to on-premises environments. Therefore, we recommend that you pull the installers directly from Microsoft Dynamics Lifecycle Services and use them as needed. In this case, Commerce headquarters will no longer be used to download the installers but will be used to download only the configuration files as needed.

Channel functionality, in an on-premises environment, is enabled exclusively via use of Commerce Scale Unit (self-hosted). For an overview, see [Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-system-begin.md). 

Unlike a cloud deployment, an on-premises environment does not enable seamless, high-availability deployment of channel components via Lifecycle Services. The only way to use channel components is by installing Commerce Scale Unit (self-hosted).

## Prerequisites 

Before you can start installation of channel components, you must first complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 41 and later)](setup-deploy-on-premises-pu41.md). At least version 8.1.1 must be installed in order for Commerce to have full functionality. We recommend that you update to the latest application version that is available.

> [!NOTE]
> It is critical to ensure that a secure network, that is not publicly  accessible, is used to connect Commerce Scale Unit to Headquarters. You must also restrict network access to Headquarters, so access is only allowed to known Commerce Scale Unit devices via network filtering or other means. This means that a firewall must exist and using a safe list is highly recommended.

## Installation steps

1. On the previously created [Application share](setup-deploy-on-premises-pu41.md#setupfile) (not the **LocalAgent** share folder), in the root directory of the share location, create a folder that is named **selfservicepackages**.  
2. On each AOS node, create an easily accessible directory, such as **C:\\RetailSelfService**.
3. On one AOS node (it doesn't matter which node), run the **RetailUpdateDatabase.ps1** script. If you used the remoting scripts, this script will be available at the path **C:\\D365FFO-LBD** on each AOS node.

    If your Commerce headquarters is on version 10.0.0 or later, run the following PowerShell script.

    ```powershell
    .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -AosUrl 'https://ax.d365ffo.onprem.contoso.com/namespaces/AXSF/' -SendProductSupportTelemetryToMicrosoft
    ```

    If your Commerce headquarters is on a version that is earlier than 10.0.0, run the following PowerShell script.

    ```powershell
    .\RetailUpdateDatabase.ps1 -DatabaseServer '<Database server name for AOS database>' -DatabaseName '<Database name for AOS database>' -envName '<Environment name>' -RetailSelfServicePackages '<Local path of Retail self-service packages, such as C:\RetailSelfService>' -SendProductSupportTelemetryToMicrosoft
    ```

    - The **-envName** parameter is the name that was assigned to the environment in Microsoft Dynamics Lifecycle Services when it was originally deployed.
    - The **-SendProductSupportTelemetryToMicrosoft** parameter is required to enable telemetry to Microsoft. Telemetry is critical to maximize support from Microsoft.
    - The script performs various actions, including updating the Service user and role, and updating registry keys.

    > [!IMPORTANT]
    > There is currently a known issue where self-service packages aren't correctly applied to on-premises environments. Therefore, we recommend that you pull the installers directly from Lifecycle Services and use them as needed. In this case, Commerce headquarters will no longer be used to download the installers but will be used to download only the configuration files as needed.

4. On each AOS node, run the following PowerShell script.

    ```powershell
    .\RetailUpdateDatabase.ps1 -RetailSelfServicePackages 'C:\RetailSelfService\Packages'
    ```

    > [!NOTE]
    > The **-RetailSelfServicePackages** parameter is the full path location that you created in the beginning of this procedure (**C:\\RetailSelfService**).

5. Download the appropriate binary update from Lifecycle Services to get the Commerce installers. For instructions, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
6. Extract the zip file, and copy all self-service installers into the **C:\\RetailSelfService** folder that you defined and created on each AOS machine in step 2. The six self-service installers are as follows:

    - AsyncServerConnectorServiceSetup.exe
    - RealtimeServiceAX63Setup.exe
    - HardwareStationSetup.exe
    - ModernPosSetup.exe
    - ModernPosSetupOffline.exe
    - StoreSystemSetup.exe

    > [!NOTE]
    > Cloud environments can synchronize self-service installers through Headquarters from what is available in Lifecycle Services ([Synchronize self-service installers in Dynamics 365 Commerce](../../../commerce/dev-itpro/synchronize-installers.md)). On-premises environments cannot utilize this functionality. However, these environments can still download from Lifecycle Services. The SDK is available in the deployable package zip file. The self-service installers are available from the Lifecycle Services **Asset library**. You can utilize the upload and download mechanism from within Lifecycle Services, but the Headquarters synchronization functionality will not work.

7. Navigate to the AD FS machine, open a PowerShell window with administrator privileges, navigate to the file share that contains your infrastructure scripts folder, and run the following command. 

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Create-ADFSServerApplicationForRetail -HostUrl 'https://ax.d365ffo.onprem.contoso.com'
    ```

    > [!NOTE]
    > As a security best practice, you should run this script for each Commerce Scale Unit. In this way, you help maximize security and minimize the workload in the event of a security breach.

8. In AD FS Management, access the newly generated Server application from **Application Groups**.
9. Edit the newly generated Server application, and select **Reset the Secret**.

    > [!NOTE]
    > It's critical that you keep this secret safe. It should be copied only once and never stored on the system. The client ID and secret that are generated will be used in the Commerce Scale Unit installer. Therefore, you will need them later. Although you can always reset the secret, it must then be updated on any Commerce Scale Unit that used the previous secret.

10. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
11. On the **Security** tab, under **Transaction service legacy properties**, select the **Real-time Service profile** field, and then select the newly created **Default** value.
12. On the **Identity providers** tab, on the **Identity providers** FastTab, select **Add**.
13. In the new **Issuer** row, enter the new identity provider value `https://sts.windows.net/` in the field.
14. On the Action Pane, select **Save**.
15. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
16. On the **General** tab, select the **Initialize** link to configure seed data for Commerce functionality.

    > [!NOTE]
    > - Read the important message at the beginning of this article regarding a known issue with installers no longer functioning through headquarters for download.
    > - The installers won't download from the relevant pages the first time that a download is attempted. This behavior occurs because the installers have just been placed in the download location, and the associated database values don't yet exist. When the **Download** functionality is attempted in Commerce headquarters (for example, for Commerce Scale Unit or Modern POS), an error is shown. Automated upload functionality is then initiated to enable the installers to be downloaded the second time that the download is attempted. (Wait one minute before you try to download the installer again.)
    > - The Peripheral Simulator (downloaded on the Hardware profile page in headquarters) will not be available until at least one Hardware profile has been created and is functional. After that point has been achieved, the following script can be run.
    >
    >     ```powershell
    >     .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -UpdateRetailHardwareProfileSelfServicePackage
    >     ```

17. Follow the installation steps for installing the Commerce Scale Unit. For instructions, see [Configure and install Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-scale-unit-configuration-installation.md). At multiple locations in that article, notes reference changes to the instructions for an on-premises deployment. It's important that you note each of these changes. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
