---
# required metadata

title: Update the local agent
description: This topic explains how to update the local agent.
author: sarvanisathish
manager: AnnBe
ms.date: 07/02/2018
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 60373
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: sarvanis
ms.search.validFrom: 2017-12-05
ms.dyn365.ops.version: 7.3

---
# Update the local agent

[!include [banner](../includes/banner.md)]

This topic explains how to update the local agent. The latest version of the local agent is version 2.0.0, which was released in March 2018.

| Local agent version | Capability | 
|---------------------|------------|
| Null                | This initial version deploys Platform update 8. |
| 1.0.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) for failed deployments. |
| 1.1.0               | This version enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md)  for successful deployments, enables multi-model package deployments, and deploys Platform update 8 and 11. | 
| 2.0.0               | This version enables servicing flows and deploys Platform update 12. |
| 2.1.0               | This version enables two-phased servicing where **Preparation** and **Update** are two separate steps. |

## What's new in local agent 2.1.0?
- Local agent 2.1.0 enables the two-phased servicing where **Environment preparation** and **Environment update** are two distinct steps and explicit actions. This reduces the total downtime customers must take when applying updates to their on-premises environments by preparing upfront and allowing users to use the environment during preparation and then communicating the downtime when the actual update environment action is triggered.

## What's new in local agent 2.0.0?
- Local agent 2.0.0 can deploy Platform update 12.
- It enables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) until the first deployment of Platform update 12 succeeds.
- It disables the [Reconfigure feature](../../dev-itpro/lifecycle-services/reconfigure-environment.md) on the first successful deployment of Platform update 12. After deployment succeeds, you can use the regular update experience to update the environment.

> [!NOTE]
> Local agent 2.0.0 **cannot** deploy Platform update 8 and Platform update 11. You must have version 1.1.0 to deploy those platform updates.

## Download the latest local agent and configuration from LCS

> [!NOTE]
> If you require an older version of the local agent for your current deployments, download it from the Asset library in Microsoft Dynamics Lifecycle Services (LCS). To download Local agent v1.1.0 navigate to **Shared Asset Library -> Model and click on Dynamics 365 for Finance and Operations on-premises - Local agent v1.1.0**.

> [!IMPORTANT]
> You must have version 2.0.0 or later to deploy Platform update 12 and complete update flows.

1. In LCS, select **Project settings** &gt; **On-prem connectors**.
2. Select the connector to your environment, and then select **Edit**.
3. On the menu on the left side of the page, select **Setup host infrastructure**, and then select **Download agent installer**.

    You must now verify that the zip file that is downloaded is unblocked.

4. Navigate to the zip file, right-click it, and then select **Properties**.
5. In the **Properties** dialog box, select **Unblock**, and then select **Apply**.
6. On the **Configure agent** tab, select **Download configurations** to download the localagent-config.json configuration file.

## Update the local agent

1. Copy the zip file and the localagent-config.json file into one of the **Orchestrator** nodes, such as **c:\\DynamicsAgent** in the **Orch1** virtual machine (VM).
2. Unzip the agent installer to C:\\DynamicsAgent\\LocalAgent.
3. Copy the localagent-config.json file to C:\\DynamicsAgent\\LocalAgent.
4. In a **Command Prompt** window, navigate to C:\\DynamicsAgent\\LocalAgent, and run the following command.

    ```
    LocalAgentCLI.exe Cleanup <path of localagent-config.json>
    ```

    > [!NOTE]
    > You must use the current agent's binaries to clean up the agent. If you don't have the current agent's binaries, you can delete the local agent application from Service Fabric Explorer.

5. Press any key to exit the cleanup operation.
6. Verify that the local agent has been successfully cleaned up by looking in Service Fabric Explorer and making sure that there are no apps in the **Deployed Applications** section in the **Orchestrator** nodes.
7. After the local agent is successfully cleaned up, run the following command.

    ```
    LocalAgentCLI.exe Install <path of localagent-config.json>
    ```

8. After the local agent is successfully installed, navigate back to your on-premises connector in LCS.
9. On the **Validate setup** tab, select **Message agent** to test LCS connectivity to your new local agent.
