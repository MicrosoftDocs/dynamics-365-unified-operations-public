

# Local Agent Pre and Post Deployment Scripts

[!include [banner](../includes/banner.md)]

Local Agent 2.3.0. supports the execution of pre and post deployment scripts. Customers can now setup PowerShell scripts that will be executed before and after deploying the environment. This is applicable to both deployments/redeployments as well as servicing operations.

To enable this feature, a **Scripts** folder needs to be created in the agent file share. To enable executing a pre deployment script create a **PreDeployment.ps1** file in this folder. Similarly, to enable executing a post deployment script create a **PostDeployment.ps1** file. Examples of the folder structure are shown below:

- \\\fileserver\agent\scripts\PreDeployment.ps1 
- \\\fileserver\agent\scripts\PostDeployment.ps1  

If these files don't exist, the deployment will carry on as usual. Examples of the new deployment flow are shown below:

Deploy/Redeploy:

1. Get unhealthy modules – Gets the health of existing apps to get the unhealthy ones (only in Redeploy)
2. Cleanup setup modules – Cleaning up environment
3. Link download artifacts – Download extract and process artifacts from LCS
4. Execute PreDeployment.ps1 script (if exists) 
5. Setup modules – Deploy Services
6. Execute PostDeployment.ps1 script (if exists) 

Servicing:

1. Preparation Phase - Preparation of the package on LCS and download to the environment.
2. Cleanup setup modules - Cleaning up environment
3. Link download artifacts - Extract and process previously downloaded artifacts from LCS
4. Execute PreDeployment.ps1 script (if exists) 
5. Setup modules – Deploy Services
6. Execute PostDeployment.ps1 script (if exists) 

> [!NOTE]
> These scripts can contain anything, and it is solely the customer’s responsibility what they execute. The Local Agent will simply invoke them.

## Customizations

The default timeout for a scripts execution is set to 30 minutes. This value can be changed by modifying the localagent-config.json file and reinstalling the Local Agent using the modified file. The following attribute defines timeout value and needs to be set as shown below (this is part of the LocalAgent component in the file):
```json 
"powershellScriptRunner": { 
    "timeoutMinutes": { 
        "value": "30" 
        } 
    }
```

## Logging
 
Outputs and errors of the script will be written into the the Logs folder located in the Scripts directory as .log and .err files. In case the script times out, only an error message with a timeout message will be logged, other outputs will not be logged.

Execution of the scripts will also be logged as ETW events which can be seen in the Event Viewer. In case a script produces any errors, an error event will be logged, and deployment will continue as usual. 