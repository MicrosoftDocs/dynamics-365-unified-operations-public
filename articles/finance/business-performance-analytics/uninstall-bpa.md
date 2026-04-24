---
title: Uninstall Business performance analytics
description: Learn how to uninstall Business performance analytics.
author: yvishwa 
ms.author: yvishwa
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 4/13/2026 
---

# Uninstall Business performance analytics

You can uninstall Business performance analytics by using either code-based uninstallation or manual uninstallation.  

If you need to reinstall Business performance analytics after uninstalling it, wait four hours before reinstalling.

If you uninstall and then reinstall Business performance analytics, you can save custom reports in the following ways:

1. **Custom reports in the default solution** – When you reinstall Business performance analytics, the app restores reports it owns in the default solution.
1. **Reports protected by the `msdyn_bpaconfig` solution** – As long as you don't uninstall the `msdyn_bpaconfig` solution, Business performance analytics can recover custom reports from it. This safeguard helps protect against reports being deleted by an admin or other processes with elevated access.  
1. **Manually saving custom reports** – You can export and reimport your custom reports. For more information, see [Preserve and manage custom reports](./custom-reports.md).  

If you uninstall and then reinstall Business performance analytics, custom reports can be saved in the following ways:

1. **Custom reports in the default solution** – When Business performance analytics is reinstalled, reports owned by the Business performance analytics app in the default solution are restored.
2. **Reports protected by the `msdyn_bpaconfig` solution** – As long as the `msdyn_bpaconfig` solution isn't uninstalled, Business performance analytics can recover custom reports from it. This safeguard was introduced to help protect against reports being deleted by an admin or other processes with elevated access.  
3. **Manually saving custom reports** – You can export and re-import your custom reports. For more information, see [Preserve and manage custom reports](./custom-reports.md).  

## Data cleanup before uninstall

When you uninstall Business performance analytics, certain analytical components, such as report backups, transformation job flows, managed lake configurations, and metadata, remain in your storage. The uninstallation process doesn't automatically delete these residual elements. To help maintain a clean and efficient environment, run the following data cleanup script before uninstalling. This step ensures that no Business performance analytics related data is left on disk, prevents unnecessary storage consumption, and supports compliance with data hygiene standards. Cleanup might include removing folders like `msdyn_BpaConfigs`, backup directories, and other Business performance analytics managed artifacts that aren't needed.

To perform data cleanup before uninstallation:

> [!NOTE]
> This process is required for Business performance analytics 2.5 and must be completed while the `msdyn_BpaTablesManagedDataLake` and `msdyn_bpapipelineplugins` solutions are still installed.

1. Before you uninstall the solutions, open Business performance analytics.
1. Press **F12** to open your browser's developer console.
1. Copy the following script into the console and press **Enter**:

    ```javascript
    processDatalakeFolderDeletion()
    ```

1. The cleanup process starts. This process might take a while to complete.
1. To check the status of the cleanup, you can:
    - Rerun steps 3 and 4 to get the current status.
    - Check the execution history of the **Business performance analytics uninstall datalake cleanup** flow.

> [!IMPORTANT]
> Wait for the cleanup process to complete before uninstalling the solution.

```
processDatalakeFolderDeletion = (shouldReset) => {
    console.log("Starting cleanup of data lake folder");

    const ENV_VAR_CLEANUP_STATUS = "msdyn_bpacleanupdatalakeexecution";
    const WORKFLOW_KEY = "analyticspipelinecleantransforms";

    // Helper function to get environment variable value
    async function getEnvironmentVariableValue(variableName) {
        const result = await Xrm.WebApi.online.retrieveMultipleRecords(
            "environmentvariabledefinition",
            `?$filter=schemaname eq '${variableName}'&$expand=environmentvariabledefinition_environmentvariablevalue($select=value)`
        );

        if (result.entities.length > 0) {
            const definition = result.entities[0];
            if (definition.environmentvariabledefinition_environmentvariablevalue &&
                definition.environmentvariabledefinition_environmentvariablevalue.length > 0) {
                return definition.environmentvariabledefinition_environmentvariablevalue[0].value;
            } else if (definition.defaultvalue) {
                return definition.defaultvalue;
            }
        }
        return null;
    }

    async function resetEnvValue(variableName, value) {
        const result = await Xrm.WebApi.online.retrieveMultipleRecords(
            "environmentvariabledefinition",
            `?$filter=schemaname eq '${variableName}'&$expand=environmentvariabledefinition_environmentvariablevalue($select=environmentvariablevalueid)`
        );

        if (result.entities.length > 0) {
            const definition = result.entities[0];
            if (definition.environmentvariabledefinition_environmentvariablevalue &&
                definition.environmentvariabledefinition_environmentvariablevalue.length > 0) {
                await Xrm.WebApi.online.updateRecord('environmentvariablevalue', definition.environmentvariabledefinition_environmentvariablevalue[0].environmentvariablevalueid, {value: value});

                return value;
            }
        }
    }

    // Helper function to trigger workflow via custom action
    function triggerCleanupWorkflow() {
        const request = {
            msdyn_workflowkey: WORKFLOW_KEY,

            getMetadata: function () {
                return {
                    boundParameter: null,
                    parameterTypes: {
                        msdyn_workflowkey: {
                            typeName: "Edm.String",
                            structuralProperty: 1
                        }
                    },
                    operationType: 0, // Action
                    operationName: "msdyn_frhbpapipelineplugintrigger"
                };
            }
        };

        return Xrm.WebApi.online.execute(request);
    }

    // Main logic
    return Promise.all([
        getEnvironmentVariableValue(ENV_VAR_CLEANUP_STATUS)
    ]).then(async function (values) {
        let runVarValue = values[0];

        if (runVarValue === null) {
            console.log("Environment variables not found, proceeding with solution delete");
            return Promise.resolve();
        }

        if (shouldReset === true) {
            runVarValue = await resetEnvValue(ENV_VAR_CLEANUP_STATUS, "notstarted");
        }

        try {
            const status = runVarValue.toLowerCase();

            switch (status) {
                case "notstarted":
                    console.log("Data Lake folder cleanup is enabled, proceeding with cleanup");

                    await triggerCleanupWorkflow();
                    return Promise.resolve({
                        message: "The option to clean up Business performance analytics transformation output folder has been selected. Clean up has started and the solution can't be deleted until it has completed.",
                        errorCode: "DATA_LAKE_CLEANUP_STARTED"
                    });

                case "running":
                    console.log("Data Lake folder cleanup is in progress");

                    return Promise.resolve({
                        message: "Cleanup of the transformation folder is in progress. The solution can't be deleted until it has completed. This may take a while.",
                        errorCode: "DATA_LAKE_CLEANUP_RUNNING"
                    });

                case "failed":
                    console.log("Data Lake folder cleanup failed. Trying again.");

                    await triggerCleanupWorkflow();
                    return Promise.resolve({
                        message: "'Business performance analytics uninstall data lake cleanup' execution failed. Retrying. Contact support for repeated failures.",
                        errorCode: "DATA_LAKE_CLEANUP_RETRY"
                    });

                default:
                    console.log("Data lake cleanup completed successfully, proceeding with solution delete");
                    return Promise.resolve();
            }
        } catch (ex) {
            console.error("Error converting environment variable value: " + ex.message);

            return Promise.reject({
                message: "Can't proceed with solution removal. Please update the environment variable'" +
                    ENV_VAR_CLEANUP_ENABLED + "' value to 'true' or 'false'",
                errorCode: "INVALID_ENV_VAR_VALUE",
                originalError: ex
            });
        }
    }).catch(function (error) {
        // If it's already a structured error, re-throw it
        if (error.errorCode) {
            throw error;
        }

        // Otherwise wrap it
        console.error("Unexpected error during data lake folder deletion processing: " + error.message);
        throw {
            message: "Unexpected error during data lake folder deletion processing",
            errorCode: "UNEXPECTED_ERROR",
            originalError: error
        };
    });
};

```

After the cleanup script executes successfully, you can proceed to uninstall Business performance analytics by using Option 1 or 2.  

## Option 1: Code-based uninstallation

1. Sign in to the [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials.
1. Select the environment to uninstall Business performance analytics.
1. Select the environment URL that is provided in the details. You're redirected to the sign-in page for the Dataverse environment.
1. Open your browser's developer tools by selecting **Ctrl**+**Shift**+**I** or going to **More tools** > **Developer tools**. Then select the **Console** tab to open the developer console.
1. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process.

    ```javascript
    // Get the current org URL
    const ORG = window.location.hostname;
    const WEB_API = `https://${ORG}/api/data/v9.2`;
    const SOLUTIONS = [
        "msdyn_BpaAnchor",
        "msdyn_BpaMcp",
        "msdyn_Bpa",
        "msdyn_BpaReports",
        "msdyn_BpaPlugins",
        "msdyn_BpaPermissions",
        "msdyn_BpaTablesTransformationJobFlows",
        "msdyn_BpaTables",
        "msdyn_BpaControls",
        "msdyn_BpaTablesAnchorSolution",
        "msdyn_BpaTablesUserRoles",
        "msdyn_BpaAnalyticalTables",
        "msdyn_BpaTablesDataProcessingConfigurations",
        "msdyn_BpaTablesDataLakeSynchronization",
        "msdyn_BpaTablesVirtualEntities",
        "msdyn_BpaTablesManagedDataLake",
        "msdyn_BpaPipelinePlugins",
        "msdyn_BpaTablesSecurity",
        "msdyn_BpaConfigs"
    ];
    
    // Get all solutions
    let _getSolutions = () => {
        var requestOptions = {
            method: "GET",
        };
        return fetch(
            `${WEB_API}/solutions?$filter=(isvisible%20eq%20true)&$select=solutionid,friendlyname,uniquename`,
            requestOptions
        ).then((response) => response.json());
    };
    
    // Delete the solution by solution ID
    let _deleteSolution = (solutionid) => {
        var requestOptions = {
            method: "DELETE",
        };
        return fetch(`${WEB_API}/solutions(${solutionid})`, requestOptions);
    };
    let start = async () => {
        console.info("Uninstalling BPA solutions");
        let installedSolutions = (await _getSolutions()).value;
    
        // Sort the installed BPA solutions 
         let installedBPASolutions = installedSolutions
            .filter((i) => SOLUTIONS.indexOf(i.uniquename) > -1)
            .sort(
                (i, j) =>
                    SOLUTIONS.indexOf(i.uniquename) - SOLUTIONS.indexOf(j.uniquename)
            );
        for (let solution of installedBPASolutions) {
            console.info(`Removing solution ${solution.friendlyname}`);
            await _deleteSolution(solution.solutionid);
        }
        console.info("BPA Solutions removed successfully");
    };
    
    start();
    ```

Deleting all the solutions takes about 20 minutes. If the operation is successful, you see the following message: "Business performance analytics solutions removed successfully."

## Option 2: Manual uninstallation

You can manually uninstall Business performance analytics through the Power Platform admin center. You must manually delete the solutions in the following order:

1. Business performance analytics anchor solution
1. Business performance analytics MCP
1. Business performance analytics solution
1. Business performance analytics reports
1. Business performance analytics plugins solution
1. Business performance analytics permissions
1. Business performance analytics tables transformation job flows
1. Business performance analytics tables
1. Business performance analytics controls
1. Business performance analytics tables anchor solution
1. Business performance analytics tables user roles
1. Business performance analytics analytical tables
1. Business performance analytics tables data processing configuration
1. Business performance analytics tables data lake synchronization
1. Business performance analytics tables virtual entities
1. Business performance analytics tables managed data lake
1. Business performance analytics pipeline plugins solution
1. Business performance analytics tables security
1. Business performance analytics configs

To delete each of the preceding solutions, follow these steps:

1. In [Power Apps](https://make.preview.powerapps.com/), on the left navigation pane, select **Solutions**.
1. Select the solution to delete, and then select **Delete**.
1. Select **Delete** again to confirm the operation.
1. Wait for the **Deleting** message box to disappear.

Deleting all the solutions takes about 20 minutes. If the operation is successful, you receive the following message: "Successfully deleted solution."

If you encounter any problems during the cleanup or uninstall process, contact support.
