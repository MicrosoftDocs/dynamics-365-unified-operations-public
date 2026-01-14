---
title: Uninstall Business performance analytics
description: Learn how to uninstall Business performance analytics.
author: lizmota
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 8/20/2025
---

# Uninstall Business performance analytics

Two options are available for uninstalling Business performance analytics: code-based uninstallation and manual uninstallation.  

If you must reinstall Business performance analytics after you uninstall it, wait four hours before reinstallation.

If you uninstall and then reinstall Business performance analytics, custom reports can be saved in the following ways:
1. **Custom reports in the default solution** – When Business performance analytics is reinstalled, reports owned by the Business performance analytics app in the default solution are restored.   
2. **Reports protected by the `msdyn_bpaconfig` solution** – As long as the `msdyn_bpaconfig` solution isn't uninstalled, Business performance analytics can recover custom reports from it. This safeguard was introduced to help protect against reports being deleted by an admin or other processes with elevated access.  
3. **Manually saving custom reports** – You can export and re-import your custom reports. For more information, see [Preserve and manage custom reports](./custom-reports.md).  
 
### Data clean up before uninstall

When Business performance analytics is uninstalled, certain analytical components, such as report backups, transformation job flows, managed lake configurations, and metadata, may remain in the customer's storage. These residual elements aren't automatically deleted and can persist unless explicitly removed. To help maintain a clean and efficient environment, customers should run the data cleanup script provided below before performing the uninstall. This ensures that no Business performance analytics related data is left on disk, prevents unnecessary storage consumption, and supports compliance with data hygiene standards. Cleanup may include removing folders like msdyn_BpaConfigs, backup directories, and other Business performance analytics managed artifacts that aren't needed.

To perform data cleanup before uninstallation:

> [!NOTE]
> This process is required for Business performance analytics 2.5 and must be completed while the `msdyn_BpaTablesManagedDataLake` and `msdyn_bpapipelineplugins` solutions are still installed.

1. Before you uninstall the solutions, open Business performance analytics.
2. Open your browser's developer console by pressing **F12**.
3. Copy the following script into the console and press **Enter**:

    ```javascript
    processDatalakeFolderDeletion()
    ```

4. The cleanup process starts. This process might take a while to complete.
5. To check the status of the cleanup, you can:
    - Rerun steps 3 and 4 to get the current status
    - Check the execution history of the flow "Business performance analytics uninstall data lake cleanup"

> [!IMPORTANT]
> Wait for the cleanup process to complete before proceeding with the solution uninstallation.


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
                        message: "The option to clean up Business performance analytics transformation output folder has been selected. Clean up has started and the solution cannot be deleted until it has completed.",
                        errorCode: "DATA_LAKE_CLEANUP_STARTED"
                    });

                case "running":
                    console.log("Data Lake folder cleanup is in progress");

                    return Promise.resolve({
                        message: "Clean up the transformation folder is in progress. The solution cannot be deleted until it has completed. This may take a while.",
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
                message: "Cannot proceed with solution removal. Please update the environment variable '" +
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

Once the cleanup script executes successfully, you can proceed to uninstall Business performance analytics using Option 1 or 2.  

## Option 1: Code-based uninstallation

1. Sign in to the [Microsoft Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials.
2. Select the environment where you want to uninstall Business performance analytics.
3. Select the environment URL that is provided in the details. You're redirected to the sign-in page for the Dataverse environment.
4. Open your browser's developer tools by selecting **Ctrl**+**Shift**+**I** or going to **More tools** \> **Developer tools**. Then select the **Console** tab to open the developer console.
5. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process.

    ```javascript
    // Get the current org URL
    const ORG = window.location.hostname;
    const WEB_API = `https://${ORG}/api/data/v9.2`;
    const SOLUTIONS = [
        "msdyn_BpaAnchor",
        "msdyn_Bpa",
        "msdyn_BpaReports",
        "msdyn_BpaPlugins",
        "msdyn_BpaPermissions",
        "msdyn_BpaTables",
        "msdyn_BpaControls",
        "msdyn_BpaTablesAnchorSolution",
        "msdyn_BpaAnalyticalTablesWorkspace",
        "msdyn_BpaAnalyticalTables",
        "msdyn_BpaTablesTransformationJobFlows",
        "msdyn_BpaTablesDataProcessingConfigurations",
        "msdyn_BpaTablesDataLakeSynchronizationWorkspace",
        "msdyn_BpaTablesDataLakeSynchronization",
        "msdyn_BpaTablesStandardEntities",
        "msdyn_BpaTablesVirtualEntitiesWorkspace",
        "msdyn_BpaTablesVirtualEntities",
        "msdyn_BpaTablesManagedDataLake",
        "msdyn_BpaPipelinePlugins",
        "msdyn_BpaTablesUserRoles",
        "msdyn_BpaTablesSecurity",
        "msdyn_BpaConfig"
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

Deletion of all the solutions requires approximately 20 minutes. If the operation is successful, you receive the following message: "Business performance analytics solutions removed successfully."

## Option 2: Manual uninstallation

You can manually uninstall Business performance analytics through the Power Platform admin center. The solutions must be manually deleted in the following order:

1. Business performance analytics anchor solution
2. Business performance analytics solution
3. Business performance analytics reports 
4. Business performance analytics plugins solution
5. Business performance analytics permissions 
6. Business performance analytics tables
7. Business performance analytics controls
8. Business performance analytics tables anchor solution
9. Business performance analytics analytical tables workspace
10. Business performance analytics analytical tables
11. Business performance analytics tables transformation job flows
12. Business performance analytics tables data processing configuration 
13. Business performance analytics tables data lake synchronization workspace
14. Business performance analytics tables data lake synchronization
15. Business performance analytics tables standard entities
16. Business performance analytics tables virtual entities workspace
17. Business performance analytics tables virtual entities
18. Business performance analytics tables managed data lake 
19. Business performance analytics pipeline plugins solution
20. Business performance analytics tables user roles 
21. Business performance analytics tables security 
22. Business performance analytics config 

To delete each of the preceding solutions, follow these steps.

1. In [Power Apps](https://make.preview.powerapps.com/), on the left navigation pane, select **Solutions**.
2. Select the solution to delete, and then select **Delete**.
3. Select **Delete** again to confirm the operation.
4. Wait for the **Deleting** message box to disappear.

Deletion of all the solution requires approximately 20 minutes. If the operation is successful, you receive the following message: "Successfully deleted solution."

If you encounter any issues during the cleanup or uninstall process, create a support ticket for assistance.
