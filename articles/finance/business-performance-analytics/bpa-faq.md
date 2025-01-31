---
title: Business performance analytics FAQ
description: This article answers some frequently asked questions about Business performance analytics, including questions about signing up for public previews of analytics.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 12/16/2024
---

# Business performance analytics FAQ

This article answers frequently asked questions about Business performance analytics.

### I received an error during the installation of Business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of Business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of Business performance analytics if it fails?

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### I am having trouble opening Business performance analytics. What can I do? 
If you are accessing Business performance analytics from the maker portal, click **Play** in the top right corner to avoid viewing the app in editor mode.

### Why isn't my data showing up in Business performance analytics?

To maintain the accuracy of report data, Business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, Business performance analytics logs information in the **Bpa self help logs** table in Dataverse. To learn more, see [Business performance analytics self-help](/troubleshoot/dynamics-365/finance/business-performance-analytics/business-performance-analytics-self-help-overview).

Some customers might reach the storage capacity limits of their Power BI Embedded SKU. In this case, the Power BI dataset that they need for reports can't be updated. By default, Business performance analytics uses the A3 SKU for Power BI Embedded. We recommend that you scale up your SKU to raise your Power BI Embedded storage capacity. For more information, see [Capacity and SKUs in Power BI embedded analytics](/power-bi/developer/embedded/embedded-capacity).

### Why is Business performance analytics using a lot of managed data lake storage in Dataverse?

As part of the data pipeline for Business performance analytics, your data is transformed to fit our dimensional data model. This process creates files that are saved to the managed data lake. The data transformation process occurs every time Business performance analytics refreshes its data. It generates new files in the managed data lake without deleting the old, obsolete files. The old files are deleted in 30 days, or our team manually deletes them when Business performance analytics uses 50 percent or more of the managed data lake's storage capacity.

### What's the estimated time that's required to set up Business performance analytics?

The setup of the Business performance analytics app takes up to 60 minutes.

### When will data be available in reports after Business performance analytics is installed?

Data will be available 24 hours after installation is completed. The time that's required to load data depends on the data size.

### How many years of data are available on reports?

Business performance analytics has data for the current calendar year plus the previous three calendar years.

### After Business performance analytics is set up, how often is the data refreshed?

Data is refreshed twice per day, at 12:00:00 AM and 12:00:00 PM (Coordinated Universal Time). To view exactly when a report's data was last refreshed, open the report. Near the top of the page, the rightmost item shows when the data for the report was last refreshed.

### How long does it take for fresh data to be available every day on Business performance analytics reports?

The amount of time that's required depends on the volume of data. However, there should be fresh data every 24 hours.

### How do I uninstall Business performance analytics?

Two options are available for uninstalling Business performance analytics: code-based uninstallation and manual uninstallation. If you must reinstall Business performance analytics after you uninstall it, wait four hours before reinstallation.

> [!NOTE]
> If you uninstall and then reinstall Business performance analytics, no new reports that were created are saved.

#### Option 1: Code-based uninstallation

1. Sign in to the [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Dataverse admin credentials.
2. Select the environment where you want to uninstall Business performance analytics.
3. Select the environment URL that's provided in the details. You're redirected to the sign-in page for the Dataverse environment.
4. Open your browser's developer tools by selecting <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd> or going to **More tools** \> **Developer tools**. Then select the **Console** tab to open the developer console.
5. Copy the following JavaScript code, and paste it into the developer console to start the uninstallation process.

    The approximate time to delete all the solutions is 20 minutes. If the operation is successful, you receive the following message: "Business performance analytics solutions removed successfully."

    ```javascript
    // Get the current org URL
    const ORG = window.location.hostname;
    const WEB_API = `https://${ORG}/api/data/v9.2`;
    const SOLUTIONS = [
        "msdyn_BpaAnchor",
        "msdyn_Bpa",
        "msdyn_BpaReports",
        "msdyn_BpaReports_TIP",
        "msdyn_BpaPlugins",
        "msdyn_BpaPermissions",
        "msdyn_BpaPermissions_TIP",
        "msdyn_BpaTables",
        "msdyn_BpaControls",
        "msdyn_BpaTablesAnchorSolution",
        "msdyn_BpaTablesUserRoles",
        "msdyn_BpaTablesUserRoles_TIP",
        "msdyn_BpaAnalyticalTablesWorkspace",
        "msdyn_BpaAnalyticalTables",
        "msdyn_BpaTablesTransformationJobFlows",
        "msdyn_BpaTablesTransformationJobFlows_TIP",
        "msdyn_BpaTablesDataProcessingConfigurations",
        "msdyn_BpaTablesDataProcessingConfigurations_TIP",
        "msdyn_BpaTablesDataLakeSynchronizationWorkspace",
        "msdyn_BpaTablesDataLakeSynchronization",
        "msdyn_BpaTablesStandardEntities",
        "msdyn_BpaTablesVirtualEntitiesWorkspace",
        "msdyn_BpaTablesVirtualEntities",
        "msdyn_BpaTablesManagedDataLake",
        "msdyn_BpaTablesManagedDataLake_TIP",
        "msdyn_BpaPipelinePlugins",
        "msdyn_BpaTablesSecurity",
        "msdyn_BpaTablesSecurity_TIP",
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
    let _deleteSolution = async (solutionid) => {
        var requestOptions = {
            method: "DELETE",
        };
        const response = await fetch(`${WEB_API}/solutions(${solutionid})`, requestOptions);
        if (!response.ok) {
            const errorMessage = await response.text(); // Get the error message from the response
            throw new Error(`Failed to delete solution with ID ${solutionid}: ${errorMessage}`);
        }
    };
    
    let start = async () => {
        console.info("Uninstalling BPA solutions");
        let hadErrors = false; // Boolean flag to indicate if there were errors uninstalling solutions
    
        let installedSolutions = (await _getSolutions()).value;
    
        // Sort the installed BPA solutions 
        let installedBPASoltuions = installedSolutions
            .filter((i) => SOLUTIONS.indexOf(i.uniquename) > -1)
            .sort(
                (i, j) =>
                    SOLUTIONS.indexOf(i.uniquename) - SOLUTIONS.indexOf(j.uniquename)
            );
    
        for (let solution of installedBPASoltuions) {
            console.info(`Removing solution ${solution.friendlyname}`);
            try {
                await _deleteSolution(solution.solutionid);
            } catch (error) {
                console.error(`Error removing solution ${solution.friendlyname}:`, error);
                hadErrors = true; // Set the flag to true if there was an error
            }
        }
    
        if (hadErrors) {
            throw new Error("Some solutions failed to uninstall. Retrying the script may fix this issue.");
        }
        console.info("BPA Solutions removed successfully");
    };
    
    start();
    ```

#### Option 2: Manual uninstallation

You can manually uninstall Business performance analytics through the Power Platform admin center. The solutions must be manually deleted in the following order:

1. Business performance analytics anchor solution
2. Business performance analytics solution
3. Business performance analytics reports
4. Business performance analytics plugins solution
5. Business performance analytics permissions
6. Business performance analytics tables
7. Business performance analytics controls
8. Business performance analytics tables anchor solution
9. Business performance analytics tables user roles
10. Business performance analytics analytical tables workspace
11. Business performance analytics analytical tables
12. Business performance analytics tables transformation job flows
13. Business performance analytics tables data processing configuration
14. Business performance analytics tables data lake synchronization
15. Business performance analytics tables standard entities
16. Business performance analytics tables virtual entities
17. Business performance analytics tables managed data lake
18. Business performance analytics pipeline plugins solution
19. Business performance analytics tables security
20. Business performance analytics configs

To delete each of the preceding solutions, follow these steps.

1. In [Power Apps](https://make.powerapps.com/), in the left pane, select **Solutions**.
2. Select the solution to delete, and then select **Delete**.
3. Select **Delete** again to confirm the operation.
4. Wait for the **Deleting** message box to disappear. If the operation is successful, you receive the following message: "Successfully deleted solution."

    The approximate time to delete all the solutions is 20 minutes.

### How often will updates for Business performance analytics be released?

- **New features** – Once per month 
- **Bugs** – Bi-weekly 

### Is there any cost to install and use Business performance analytics during public preview?

No. The data is restricted to the current calendar year plus the previous three calendar years.

### How do I know when a new release of Business performance analytics is available?

You can view any updates that are available for Business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of Business performance analytics is available?

When a new release of Business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.

### Why does Data Lake storage consumption grow steadily while using BPA, and what solutions are being implemented to address this issue?
Some customers may observe that Data Lake storage consumption grows steadily more often than others due to operating on significant amounts of data, while others may never experience this issue. This happens because older BPA releases rely on staging-table references that block file deletion, causing multiple transform output files to accumulate over time. The BPA engineering team proactively checks for potential capacity concerns every two weeks and intervenes to remove old temporary files if usage approaches critical thresholds. Customers must open a support incident upon noticing storage constraints for more frequent manual cleanup by Microsoft engineers.

In the BPA January 2025 update, a routine is introduced which removes staging file dependencies and implements a 3-day retention policy to regularly clear older files. After upgrading to BPA version 2.0.29241185 or later, Microsoft will enable the auto-cleanup flight in each environment, drastically reducing reliance on manual cleanup processes. The solution for this issue is the latest BPA update, making automatic purging a regular process and minimizing manual interventions.

> [!IMPORTANT] Customers affected by storage capacity growth after completing the update to BPA version 2.0.29241185 or later should create a Support Request with a request to enable the temporary files cleanup routine for their environment.

### How do I receive the latest news about Business performance analytics?

To receive the latest updates about Business performance analytics, join the Business performance analytics Yammer group.

1. Complete the [FAR Preview Agreement](https://forms.office.com/r/wfcUBtP67J).
2. Join the [Dynamics 365 and Power Platform Preview Programs](https://www.yammer.com/dynamicsaxfeedbackprograms/#/home).
3. Join the [Business performance analytics Yammer](https://www.yammer.com/dynamicsaxfeedbackprograms/#/threads/inGroup?type=in_group&feedId=73748324352&view=unviewed).
