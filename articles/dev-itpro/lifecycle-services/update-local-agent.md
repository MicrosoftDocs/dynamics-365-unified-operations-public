---
# required metadata

title: Update the local agent
description: This topic provides information about how to update the local agent.
author: sarvanisathish
manager: AnnBe
ms.date: 12/05/2017
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

This topic provides information about how to update the local agent.

## Download the local agent and configuration from LCS 

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

5. Press any key to exit the cleanup operation. 
6. Verify that the local agent is cleaned up successfully by checking the Service Fabric Explorer and ensuring that in the Orchestrator nodes there are no apps under the **Deployed Applications** section.
7. After the local agent is successfully cleaned up, run the following command. 

    ```LocalAgentCLI.exe Install <path of local-agent-config.json>``` 

8. After the local agent is successfully installed, navigate back to your on-premises connector in LCS. 
9. On the **Validate setup** tab, select **Message agent** to test the LCS connectivity to your new local agent. 
