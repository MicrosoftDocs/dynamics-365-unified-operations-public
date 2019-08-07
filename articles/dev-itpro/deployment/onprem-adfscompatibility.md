---
# required metadata

title: AD FS Office 365 compatibility
description: This topic explains how to use the same instance of Active Directory Federation Services (AD FS) for a Microsoft Dynamics 365 for Finance and Operations on-premises environment and for Microsoft Office 365.
author: faix
manager: AnnBe
ms.date: 08/07/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: Platform update 28 

---

# AD FS Office 365 compatibility

[!include [banner](../includes/banner.md)]

>[!IMPORTANT]
>It is necessary to have Local Agent 2.2.0 or greater installed and to service with Platform update 28 or later.

This topic explains how to use the same instance of Active Directory Federation Services (AD FS) for a Microsoft Dynamics 365 for Finance and Operations on-premises environment and for Microsoft Office 365.

## Existing deployments

1. Download the new local agent version from Microsoft Dynamics Lifecycle Services (LCS). It should be version 2.2.0 or later.
2. Download the new version of the local agent configuration file, because it has additional configuration that is required for this functionality.
3. Modify the new local agent configuration file, and set the **office365AdfsCompatibility** value to **True**.
4. Run the following command to uninstall the old local agent version from your cluster.

    ```powershell
    .\LocalAgentCLI.exe Cleanup '<path of localagent-config.json>'
    ```

5. Run the following command to install the new local agent version.

    ```powershell
    .\LocalAgentCLI.exe Install '<path of localagent-config.json>'
    ```

6. Perform any servicing operation with Platform update 28 or later to make the new configuration available.
7. After servicing is completed, run the following script.

    ```powershell
    .\Reset-DatabaseUsers.ps1 -DatabaseServer '<FQDN of the SQL server>' -DatabaseName '<AX database name>'
    ```

    > [!IMPORTANT]
    > If you skip this step, the primary admin user won't be able to sign in.

8. Use Service Fabric Explorer to [restart an Application Object Server (AOS) node](troubleshoot-on-prem.md#restartapplications).
9. Run a SQL query on the USERINFO table to modify the **NETWORKDOMAIN** field. If your old configuration was `https://ax.contoso.com/adfs`, you should change all your user entries to `http://ax.contoso.com/adfs/services/trust`.

## New deployments

1. Follow the instructions for installing the local agent in the "Configure a connector and install an on-premises local agent" section of [Set up and deploy on-premises environments](setup-deploy-on-premises-pu12.md#configureconnector). However, before you actually install the local agent, complete step 2 of this procedure.
2. Modify the local agent configuration file, and set the **office365AdfsCompatibility** value to **True**.
3. Continue to follow the instructions in the "Configure a connector and install an on-premises local agent" section of [Set up and deploy on-premises environments](setup-deploy-on-premises-pu12.md#configureconnector), and deploy a base version that runs Platform update 28 or later. If there is no base version that runs Platform update 28 or later, deploy the latest base version that is available. Then service it so that Platform update 28 is deployed on top.
