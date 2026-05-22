---
title: AD FS Microsoft 365 compatibility
description: Learn how to use the instances of Active Directory Federation Services (AD FS) for a Dynamics 365 Finance + Operations (on-premises) environment and for Microsoft 365.
author: faix
ms.author: osfaixat
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 04/02/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: Platform update 28 
ms.service: dynamics-365-op
---

# AD FS Microsoft 365 compatibility

[!include [banner](../includes/banner.md)]

> [!IMPORTANT]
> This feature is only fully supported starting with application update 10.0.8, Platform update 32, and LocalAgent 2.2.0. For details, see [Partial support](#partialsupport). 

This article explains how to use the same instance of Active Directory Federation Services (AD FS) for a Dynamics 365 Finance + Operations (on-premises) environment and for Microsoft 365.

## Existing deployments

1. Download the new local agent version from Microsoft Dynamics Lifecycle Services. Use version 2.2.0 or later.
1. Update your agent configuration in Lifecycle Services by setting the deployment option to **Enable AD FS Microsoft 365 Compatibility**.
1. Download the new version of the local agent configuration file.
1. Run the following command to uninstall the old local agent version from your cluster.

    ```powershell
    .\LocalAgentCLI.exe Cleanup '<path of localagent-config.json>'
    ```

1. Run the following command to install the new local agent version.

    ```powershell
    .\LocalAgentCLI.exe Install '<path of localagent-config.json>'
    ```

1. Perform any servicing operation with Platform update 28 or later to make the new configuration available.
1. After servicing is completed, run the following script.

    ```powershell
    .\Reset-DatabaseUsers.ps1 -DatabaseServer '<FQDN of the SQL server>' -DatabaseName '<AX database name>'
    ```

    > [!IMPORTANT]
    > If you skip this step, the primary admin user can't sign in.

1. Use Service Fabric Explorer to [Restart applications (such as AOS)](troubleshoot-on-prem.md#restartapplications).
1. Verify that you can sign in to the product with the system administrator user that you specified during deployment. 
1. Download the newest version of the infrastructure scripts from the Lifecycle Services Shared asset library.
1. Copy the Reset-SID.ps1 script from the downloaded infrastructure scripts folder into one of your AOS machines.
1. Execute the Reset-Sid.ps1 script.
    
    ```powershell
    Import-Module ".\D365FO-OP" -Force
    .\Reset-SID.ps1 -AxsfCodePath 'C:\ProgramData\SF\AOS_13\Fabric\work\Applications\AXSFType_App184\AXSF.Code.1.0.20190902'
    ```

## New deployments

1. Follow the instructions for installing the local agent in the "Configure a connector and install an on-premises local agent" section of [Set up and deploy on-premises environments](setup-deploy-on-premises-latest.md#configureconnector). However, before you install the local agent, complete step 2 of this procedure.
1. Modify the local agent configuration file, and set the **office365AdfsCompatibility** value to **True**.
1. Continue to follow the instructions in the "Configure a connector and install an on-premises local agent" section of [Set up and deploy on-premises environments](setup-deploy-on-premises-latest.md#configureconnector), and deploy a base version that runs Platform update 28 or later. If there's no base version that runs Platform update 28 or later, deploy the latest base version that's available. Then service it so that Platform update 28 is deployed on top.

## <a name="partialsupport"></a> Partial support

For partial support, you need to install Local Agent 2.2.0 or later and update the service with Platform update 28 or later.

With partial support, authentication against the Financial Reporting service isn't supported.  


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
