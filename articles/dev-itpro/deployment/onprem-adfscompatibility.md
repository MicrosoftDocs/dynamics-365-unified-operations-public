---
# required metadata

title: Local Agent 2.2.0 ADFS Office 365 Compatibility
description: [Full description that appears in the search results. Often the first paragraph of your topic.]
author: faix
manager: AnnBe
ms.date: 08/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
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


# Local Agent 2.2.0 ADFS Office 365 Compatibility

[!include banner]

This topic provides information on how to use the same ADFS for Microsoft Dynamics 365 for Finance and Operation on-premises environment and Office 365.

## Existing deployments

1.	Download the new local agent version from Lifecycle Services (LCS). It should be version 2.2.0 or later.  
2.	Redownload the configuration file as it has additional configuration needed for this functionality. 
3.	Modify the new local agent configuration file and set the **office365AdfsCompatibility** value to **True**.
4.	Uninstall the old local agent version from your cluster using the following command:

    ```powershell
    .\LocalAgentCLI.exe Cleanup '<path of localagent-config.json>' 
    ```
    
5.	Install the new local agent version using:

    ```powershell
    .\LocalAgentCLI.exe Install  '<path of localagent-config.json>' 
    ```
    
6.	Servicing the environment with Plafrom update 28 or later will enable this new configuration. For existing environments with Plafrom update 28 or later, doing any servicing operation will enable this new configuration.

7. After servicing is complete, run the following script:

    ```powershell
    .\Reset-DatabaseUsers.ps1 -DatabaseServer '<FQDN of the SQL server>' -DatabaseName '<AX database name>'. 
    ```
    
    Otherwise, the primary administrator user won’t be able to login. 	

8. Using the Service Fabric Explorer, [restart an AOS node](troubleshoot-on-prem.md#restartapplications).

9.	Run a SQL query on the USERINFO table to modify the NETWORKDOMAIN field. If your old configuration was `https://ax.contoso.com/adfs`, then you should change all your users entries to `http://ax.contoso.com/adfs/services/trust`. 

## New deployments

1.	Run through the LocalAgent Installation instructions in the [Setup and Deploy On-Premises](setup-deploy-on-premises-pu12.md#configureconnector) guide. However, before installing the LocalAgent do step 2 below. 
2.	Modify the local agent configuration file and set the **office365AdfsCompatibility** value to **True**.
3.	Continue going through the [Setup and deploy on-premises](setup-deploy-on-premises-pu12.md#configureconnector) guide and deploy a base version that contains Plafrom update 28 or later. If there is no base Plafrom update 28 version, deploy the highest base version available. Then service with Platform update 28 on top.


