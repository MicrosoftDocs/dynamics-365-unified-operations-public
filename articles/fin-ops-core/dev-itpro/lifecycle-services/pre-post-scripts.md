---
title: Local agent pre-deployment and post-deployment scripts
description: Learn about local agent pre-deployment and post-deployment scripts, including overviews on customizations and logging.
author: faix
ms.author: osfaixat
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 03/06/2026
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: Platform update 28 
search.app:
  - financeandoperationsonprem-docs
---

# Local agent predeployment and postdeployment scripts

[!include [banner](../includes/banner.md)]
[!include [LCS freeze](../includes/lcs-freeze-banner.md)]

Local agent 2.3.0 supports the execution of predeployment and postdeployment scripts. Therefore, you can now set up Microsoft Windows PowerShell scripts that run before and after the environment is deployed. This feature applies to deployments and redeployments, and also to servicing operations.

To make this feature available, create a **Scripts** folder in the agent file share. To run a predeployment script, create a **PreDeployment.ps1** file in the **Scripts** folder. To run a postdeployment script, create a **PostDeployment.ps1** file. The following examples show the folder structure:

- \\\\\\fileserver\\agent\\scripts\\PreDeployment.ps1
- \\\\\\fileserver\\agent\\scripts\\PostDeployment.ps1

If these files don't exist, the deployment continues as usual. The following examples show the new deployment flow.

**Deployment or redeployment:**

1. Get unhealthy modules. In this step, the local agent gets the health of existing services to find which ones are unhealthy. This step applies only to redeployment scenarios.
1. Clean up modules. In this step, the local agent removes the services and deletes the contents of the **wp** folder. This step applies only to redeployment scenarios.
1. Link download artifacts. In this step, the local agent downloads, extracts, and processes artifacts from Microsoft Dynamics Lifecycle Services (LCS).
1. Predeployment script. In this step, the local agent runs the **PreDeployment.ps1** script (if it exists).
1. Set up modules. In this step, the local agent deploys the new services.
1. Postdeployment script. In this step, the local agent runs the **PostDeployment.ps1** script (if it exists).

**Servicing:**

1. Prepare for servicing. In this step, the local agent prepares the package in LCS and downloads it to the environment.
1. Clean up modules. In this step, the local agent removes the services and deletes the contents of the **wp** folder.
1. Link download artifacts. In this step, the local agent extracts and processes previously downloaded artifacts from LCS.
1. Predeployment script. In this step, the local agent runs the **PreDeployment.ps1** script (if it exists).
1. Set up modules. In this step, the local agent deploys the new services.
1. Postdeployment script. In this step, the local agent runs the **PostDeployment.ps1** script (if it exists).

> [!NOTE]
> The predeployment and postdeployment scripts can contain any code. You're solely responsible for the code that the scripts run. The local agent just invokes the scripts.

## Customizations

The default timeout for script execution is 30 minutes. To change this value, modify the **localagent-config.json** file, and then reinstall the local agent by using the modified file. The following attribute defines the timeout value and must be set as shown. (The code that is shown here is part of the **LocalAgent** component in the file.)

```json
"powershellScriptRunner": {
    "timeoutMinutes": {
        "value": "30"
        }
    }
```

## Logging

The scripts write their outputs and error messages as `.log` and `.err` files into the `Logs` folder in the `Scripts` folder. If a script times out, only an error message is logged. This error message has a timeout message. No other outputs are logged in this situation.

The local agent also logs the execution of the scripts as Event Tracing for Windows (ETW) events. You can view these events in Event Viewer. If a script produces any errors, the local agent logs an error event but continues the deployment as usual.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
