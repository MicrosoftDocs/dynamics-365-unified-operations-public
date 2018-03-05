---
# required metadata

title: Update the local agent
description: This topic provides information about how to update the local agent.
author: sarvanisathish
manager: AnnBe
ms.date: 03/05/2018
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

[!include[banner](../includes/banner.md)]

This topic provides information about how to update the local agent. The latest version of the local agent is version 2.0.0 released in March 2018. 

| Local agent version | Capability                   | Download location |
|---------------------|------------------------------|-------------------|
| Null                | Initial version. Deploys Platform update 8. |                   |
| 1.0.0               | Enables Reconfigure for failed deployments. |  |
| 1.1.0               | Enables Reconfigure on successful deployments. Enables multi-model package deployments. Deploys Platform update 12. | |
| 2.0.0               | Enables servicing flows. Deploys Platform update 12. | |

## Whats new in local agent 2.0.0?
- Is able to deploy Platform update 12.
- Enables Reconfigure feature until the first deployment of Platform update 12 succeeds.
- Disables Reconfigure feature on the 1st successful deployment of Platform update 12. Once deployment succeeds you may use the regular update experience to update the environment.

> [!Note]
> Local agent 2.0.0 **cannot** deploy Platform update 8 and Platform update 11. You will need version 1.1.0 to deploy those platform updates.

## Download the latest local agent and configuration from LCS 

> [!NOTE] 
> If you need the older version of the agent for your current deployments, download it from the LCS asset library location specified in the table above.

> [!IMPORTANT]
> You will need version 2.0.0 or above to deploy Platform update 12 and exercise update flows.

1. In Lifecycle Services (LCS), go to **Project Settings** > **On-prem Connectors**. 
2. Select the connector to your environment and click **Edit**. 
3. On the left menu, click **Setup host infrastructure**, and then click, **Download agent installer**.
4. Navigate to the downloaded zip file to verify that the zip file is unblocked. 
5. Right-click the file, and then select **Properties**. 
6. In the dialog box, select **Unblock**, and then click **Apply**. 
7. On the **Configure agent** tab, click **Download configurations** to download the localagent-config.json configuration file. 

## Update the local agent 

1. Copy the .zip file and the localagent-config.json file into the one of the **Orchestrator** nodes. For example, **c:\DynamicsAgent** in **Orch1** VM. 
2. Unzip the agent installer to C:\DynamicsAgent\LocalAgent. 
3. Copy the localagent-config.json file to C:\DynamicsAgent\LocalAgent. 
4. In a Command Prompt window, navigate to C:\DynamicsAgent\LocalAgent and run the following command:

   ```LocalAgentCLI.exe Cleanup <path of localagent-config.json> ``` 
   
> [!NOTE] 
> You will need to use the current agent's binaries to cleanup the agent. In the event you do not have the current agent's binaries, you may delete the local agent application from service fabric explorer.

5. Press any key to exit the cleanup operation. 
6. Verify that the local agent is cleaned up successfully by checking the Service Fabric Explorer and ensuring that in the Orchestrator nodes there are no apps under the **Deployed Applications** section.
7. After the local agent is successfully cleaned up, run the following command. 

    ```LocalAgentCLI.exe Install <path of local-agent-config.json>``` 

8. After the local agent is successfully installed, navigate back to your on-premises connector in LCS. 
9. On the **Validate setup** tab, select **Message agent** to test the LCS connectivity to your new local agent. 
