---
# required metadata

title: Update the local agent
description: This topic explains how to update the local agent.
author: faix
manager: AnnBe
ms.date: 12/19/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: osfaixat
ms.search.validFrom: 2017-12-05
ms.dyn365.ops.version: 7.3

---
# Update the local agent

[!include [banner](../includes/banner.md)]

This topic explains how to update the local agent. The latest version of the local agent is version 2.4.0, which was released in December 2019.

| Local agent version | Capability | 
|---------------------|------------|
| Null                | This initial version deploys Platform update 8. |
| 1.0.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) for failed deployments. |
| 1.1.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md)  for successful deployments, enables multi-model package deployments, and deploys Platform update 8 and 11. | 
| 2.0.0               | This version enables servicing flows and deploys Platform update 12. |
| 2.1.0               | This version enables two-phased servicing where **Preparation** and **Update** are two separate steps. |
| 2.1.1               | This version fixes an issue that occurs when the download fails and the LCS Maintain button is not available. Additional changes include updates to Azure storage libraries to improve communication with Azure storage and enable TLS 1.2.  |
| 2.1.2               | This version contains updated Azure dependencies for improved download stability and logic to correctly evaluate if files are downloaded. This fixes an issue where files are fully downloaded, but the logic would still consider them as missing a few bytes and therefore fail the download.  |
| 2.2.0               | This version fixes locked dlls during cleanup and enables prerequisites for supporting Active Directory Federation Services (ADFS) that also is used for Office 365. |
| 2.3.0               | This version adds support for pre- and post-deployment scripts.  |
| 2.3.1               | This version fixes orchestration service crashes that may occur during clean up on some environments.<br><br>Deploying version 10.0.5 with Platform update 29 or earlier requires the use of pre-deployment scripts for automatic updating of FinancialReportingDeployer.exe.config. For more information, see [Troubleshoot on-premises deployments](../../dev-itpro/deployment/troubleshoot-on-prem.md#FREntityFramework). |
| 2.4.0               | This version fixes a deployment issue and upgrades the runtime of the local agent. |

## What's new in local agent 2.4.0

- Local agent 2.4.0 now requires .Net Framework 4.8 to uptake the newest changes from Lifecycle Services (LCS). Please be sure to run the latest Infrastructure Scripts available in LCS to meet the newest requirements.
- This release also fixes the 255/-1 exit error from the AOSSetupHybridCloud.exe where the deployment ended when deploying the AXSFType.

## What's new in local agent 2.3.0

- Local agent 2.3.0 enables the execution of custom [pre- and post- deployment scripts](../../dev-itpro/lifecycle-services/pre-post-scripts.md).
- It fixes the problem introduced in 2.2.0 with regard to deploying older platform updates.
- This release removes the monitoring agent and introduces a new service called LBDTelemetry, which will be used to install the ETWManifests.

> [!IMPORTANT]
> This release requires that a new local agent configuration file be downloaded from LCS. Refer to the [Troubleshoot on-premises deployments](../../dev-itpro/deployment/troubleshoot-on-prem.md) topic if you encounter problems. 

## What's new in local agent 2.1.0
- Local agent 2.1.0 enables the two-phased servicing where **Environment preparation** and **Environment update** are two distinct steps and explicit actions. This reduces the total downtime customers must take when applying updates to their on-premises environments by preparing upfront and allowing users to use the environment during preparation and then communicating the downtime when the actual update environment action is triggered.

## What's new in local agent 2.0.0
- Local agent 2.0.0 can deploy Platform update 12.
- It enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) until the first deployment of Platform update 12 succeeds.
- It disables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) on the first successful deployment of Platform update 12. After deployment succeeds, you can use the regular update experience to update the environment.

> [!NOTE]
> Local agent 2.0.0 **cannot** deploy Platform update 8 and Platform update 11. You must have version 1.1.0 to deploy those platform updates.

## Download the latest local agent and configuration from LCS

> [!NOTE]
> If you require an older version of the local agent for your current deployments, download it from the Asset library in Microsoft Dynamics Lifecycle Services (LCS). To download Local agent version 1.1.0, go to **Shared Asset Library -> Model** and click on Dynamics 365 for Finance and Operations on-premises - Local agent v1.1.0**.
>
> You must have version 2.0.0 or later to deploy Platform update 12 and complete update flows.

1. In LCS, select **Project settings** > **On-prem connectors**.
2. Select the connector to your environment, and then select **Edit**.
3. On the menu on the left side of the page, select **Setup host infrastructure**, and then select **Download agent installer**.

    You must now verify that the zip file that is downloaded and unblocked.

4. Go to the zip file, right-click it, and then select **Properties**.
5. In the **Properties** dialog box, select **Unblock**, and then select **Apply**.
6. On the **Configure agent** tab, select **Download configurations** to download the localagent-config.json configuration file.

## Update the local agent

1. Copy the zip file and the localagent-config.json file into one of the **Orchestrator** nodes, such as **c:\\DynamicsAgent** in the **Orch1** virtual machine (VM).
2. Unzip the agent installer to C:\\DynamicsAgent\\LocalAgent.
3. Copy the localagent-config.json file to C:\\DynamicsAgent\\LocalAgent.
4. In a **Command Prompt** window, go to C:\\DynamicsAgent\\LocalAgent, and run the following command.

    ```Console
    LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

    > [!NOTE]
    > You must use the current agent's binaries to clean up the agent. If you don't have the current agent's binaries, you can delete the local agent application from Service Fabric Explorer.

5. Press any key to exit the cleanup operation.
6. Verify that the local agent has been successfully cleaned up by looking in Service Fabric Explorer and making sure that there are no apps in the **Deployed Applications** section in the **Orchestrator** nodes.
7. After the local agent is successfully cleaned up, run the following command.

    ```Console
    LocalAgentCLI.exe Install <path of localagent-config.json>
    ```

8. After the local agent is successfully installed, go back to your on-premises connector in LCS.
9. On the **Validate setup** tab, select **Message agent** to test LCS connectivity to your new local agent.
