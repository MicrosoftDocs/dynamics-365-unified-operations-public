---
title: Installation steps for Retail channel components in an on-premises environment
description: Learn about the installation steps for Commerce channel components in an on-premises environment, including prerequisites and installation steps. 
author: johnmichalak
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 10/30/2025
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2018-10-31
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 8.1.1
ms.service: dynamics-365-op
---

# Installation steps for Retail channel components in an on-premises environment

[!include[banner](../includes/banner.md)]

This article covers the installation steps for Commerce channel components in an on-premises environment.

> [!IMPORTANT]
> A known issue currently prevents self-service packages from being correctly applied to on-premises environments. To work around this issue, pull the installers directly from Microsoft Dynamics Lifecycle Services and use them as needed. In this case, you don't use Commerce headquarters to download the installers but use it to download only the configuration files as needed.

In an on-premises environment, you enable channel functionality exclusively by using Commerce Scale Unit (self-hosted). For an overview, see [Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-system-begin.md).

Unlike a cloud deployment, an on-premises environment doesn't enable seamless, high-availability deployment of channel components through Lifecycle Services. The only way to use channel components is by installing Commerce Scale Unit (self-hosted).

## Prerequisites

Before you start the installation of channel components, complete all prior installation steps for an on-premises environment. These steps are listed in [Set up and deploy on-premises environments (Platform update 41 and later)](setup-deploy-on-premises-pu41.md). You must install at least version 8.1.1 for Commerce to have full functionality. We recommend that you update to the latest application version that's available.

> [!NOTE]
> It's critical to ensure that a secure network that isn't publicly accessible is used to connect Commerce Scale Unit to Headquarters. You must also restrict network access to Headquarters, so access is only allowed to known Commerce Scale Unit devices through network filtering or other means. This requirement means that a firewall must exist and using an allowlist is highly recommended.

## Installation steps

1. On the previously created [Application share](setup-deploy-on-premises-pu41.md#setupfile) (not the **LocalAgent** share folder), in the root directory of the share location, create a folder that is named **selfservicepackages**.  
1. On each AOS node, create an easily accessible directory, such as **C:\\RetailSelfService**.
1. On one AOS node (it doesn't matter which node), run the **RetailUpdateDatabase.ps1** script. If you used the remoting scripts, this script is available at the path **C:\\D365FFO-LBD** on each AOS node.

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
    > There's currently a known issue where self-service packages aren't correctly applied to on-premises environments. Therefore, we recommend that you pull the installers directly from Lifecycle Services and use them as needed. In this case, Commerce headquarters is no longer used to download the installers but is used to download only the configuration files as needed.

1. On each AOS node, run the following PowerShell script.

    ```powershell
    .\RetailUpdateDatabase.ps1 -RetailSelfServicePackages 'C:\RetailSelfService\Packages'
    ```

    > [!NOTE]
    > The **-RetailSelfServicePackages** parameter is the full path location that you created in the beginning of this procedure (**C:\\RetailSelfService**).

1. Download the appropriate binary update from Lifecycle Services to get the Commerce installers. For instructions, see [Download updates from Lifecycle Services (LCS)](../migration-upgrade/download-hotfix-lcs.md).
1. Extract the zip file, and copy all self-service installers into the **C:\\RetailSelfService** folder that you defined and created on each AOS machine in step 2. The six self-service installers are as follows:

    - AsyncServerConnectorServiceSetup.exe
    - RealtimeServiceAX63Setup.exe
    - HardwareStationSetup.exe
    - ModernPosSetup.exe
    - ModernPosSetupOffline.exe
    - StoreSystemSetup.exe

    > [!NOTE]
    > Cloud environments can synchronize self-service installers through Headquarters from what is available in Lifecycle Services ([Synchronize self-service installers in Dynamics 365 Commerce](../../../commerce/dev-itpro/synchronize-installers.md)). On-premises environments can't utilize this functionality. However, these environments can still download from Lifecycle Services. The SDK is available in the deployable package zip file. The self-service installers are available from the Lifecycle Services **Asset library**. You can utilize the upload and download mechanism from within Lifecycle Services, but the Headquarters synchronization functionality won't work.

1. Navigate to the AD FS machine, open a PowerShell window with administrator privileges, navigate to the file share that contains your infrastructure scripts folder, and run the following command.

    ```powershell
    # Host URL is your DNS record\host name for accessing the AOS
    .\Create-ADFSServerApplicationForRetail -HostUrl 'https://ax.d365ffo.onprem.contoso.com'
    ```

    > [!NOTE]
    > As a security best practice, you should run this script for each Commerce Scale Unit. In this way, you help maximize security and minimize the workload if there's a security breach.

1. In AD FS Management, access the newly generated Server application from **Application Groups**.
1. Edit the newly generated Server application, and select **Reset the Secret**.

    > [!NOTE]
    > It's critical that you keep this secret safe. It should be copied only once and never stored on the system. The client ID and secret that are generated are used in the Commerce Scale Unit installer. Therefore, you need them later. Although you can always reset the secret, it must then be updated on any Commerce Scale Unit that used the previous secret.

1. In Commerce headquarters, go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce shared parameters**.
1. On the **Security** tab, under **Transaction service legacy properties**, select the **Real-time Service profile** field, and then select the newly created **Default** value.
1. On the **Identity providers** tab, on the **Identity providers** FastTab, select **Add**.
1. In the new **Issuer** row, enter the new identity provider value `https://sts.windows.net/` in the field.
1. On the Action Pane, select **Save**.
1. Go to **Retail and Commerce \> Headquarters setup \> Parameters \> Commerce parameters**.
1. On the **General** tab, select the **Initialize** link to configure seed data for Commerce functionality.

    > [!NOTE]
    > - Read the important message at the beginning of this article regarding a known issue with installers no longer functioning through headquarters for download.
    > - The installers won't download from the relevant pages the first time that a download is attempted. This behavior occurs because the installers have been placed in the download location, and the associated database values don't yet exist. When the **Download** functionality is attempted in Commerce headquarters (for example, for Commerce Scale Unit or Modern POS), an error is shown. Automated upload functionality is then initiated to enable the installers to be downloaded the second time that the download is attempted. (Wait one minute before you try to download the installer again.)
    > - The Peripheral Simulator (downloaded on the Hardware profile page in headquarters) won't be available until at least one Hardware profile is created and functional. After that point is achieved, the following script can be run.
    >
    >     ```powershell
    >     .\RetailUpdateDatabase.ps1 -envName '<Environment name>' -UpdateRetailHardwareProfileSelfServicePackage
    >     ```

1. Follow the installation steps for installing the Commerce Scale Unit. For instructions, see [Configure and install Commerce Scale Unit (self-hosted)](../../../commerce/dev-itpro/retail-store-scale-unit-configuration-installation.md). At multiple locations in that article, notes reference changes to the instructions for an on-premises deployment. It's important that you note each of these changes.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
