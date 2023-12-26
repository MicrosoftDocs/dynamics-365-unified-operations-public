---
# required metadata

title: Local agent pre-deployment and post-deployment scripts
description: This article provides information about local agent pre-deployment and post-deployment scripts.
author: faix
ms.date: 08/07/2019
ms.topic: article
ms.prod: dynamics-365
ms.service:
ms.technology: 

# optional metadata

# ms.search.form: [Operations AOT form name to tie this article to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: osfaixat
ms.search.validFrom: 2019-07-31 
ms.dyn365.ops.version: Platform update 28 
search.app:
  - financeandoperationsonprem-docs
---

# Local agent pre-deployment and post-deployment scripts

[!include [banner](../includes/banner.md)]

Local agent 2.3.0 supports the execution of pre-deployment and post-deployment scripts. Therefore, customers can now set up Microsoft Windows PowerShell scripts that are run before and after the environment is deployed. This feature applies to deployments and redeployments, and also to servicing operations.

To make this feature available, you must create a Scripts folder in the agent file share. To run a pre-deployment script, create a **PreDeployment.ps1** file in the Scripts folder. To run a post-deployment script, create a **PostDeployment.ps1** file. The following examples show the folder structure:

- \\\\\\fileserver\\agent\\scripts\\PreDeployment.ps1
- \\\\\\fileserver\\agent\\scripts\\PostDeployment.ps1

If these files don't exist, the deployment continues as usual. The following examples show the new deployment flow.

**Deployment or redeployment:**

1. Get unhealthy modules. In this step, the health of existing services is obtained to find which are unhealthy. This step applies only to redeployment scenarios.
2. Clean up modules. In this step, the services are removed and the contents of the **wp** folder are deleted. This step applies only to redeployment scenarios.
3. Link download artifacts. In this step, download, extraction, and processing of artifacts from Microsoft Dynamics Lifecycle Services (LCS) takes place.
4. Pre-deployment script. In this step the **PreDeployment.ps1** script is executed (if it exists).
5. Set up modules. In this step, the new services are deployed.
6. Post-Deployment script. In this step the **PostDeployment.ps1** script is executed (if it exists).

**Servicing:**

1. Prepare for servicing. In this step, the package is prepared in LCS and gets downloaded to the environment.
2. Clean up modules. In this step, the services are removed and the contents of the **wp** folder are deleted.
3. Link download artifacts. In this step, extraction and processing of previously downloaded artifacts from LCS takes place.
4. Pre-deployment script. In this step the **PreDeployment.ps1** script is executed (if it exists).
5. Set up modules. In this step, the new services are deployed.
6. Post-Deployment script. In this step the **PostDeployment.ps1** script is executed (if it exists).

> [!NOTE]
> The pre-deployment and post-deployment scripts can contain anything. The code that the scripts run is solely the customer's responsibility. The local agent just invokes the scripts.

## Customizations

The default time-out for script execution is 30 minutes. To change this value, modify the localagent-config.json file, and then reinstall the local agent by using the modified file. The following attribute defines time-out value and must be set as shown here. (The code that is shown here is part of the **LocalAgent** component in the file.)

```json
"powershellScriptRunner": {
    "timeoutMinutes": {
        "value": "30"
        }
    }
```

## Logging

The outputs and error messages from the scripts are written, as .log and .err files, into the Logs folder in the Scripts folder. If a script times out, only an error message is logged. This error message has a time-out message. No other outputs are logged in this situation.

Execution of the scripts is also logged as Event Tracing for Windows (ETW) events. You can view these events in Event Viewer. If a script produces any errors, an error event is logged, but deployment continues as usual.



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
