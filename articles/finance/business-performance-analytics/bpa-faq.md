---
title: Business performance analytics FAQ
description: Access answers to frequently asked questions about Business performance analytics, including questions about signing up for public previews of analytics.
author: jinniew
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 9/11/2024
---

# Business performance analytics FAQ

This article answers frequently asked questions about Business performance analytics.

[This article is prerelease documentation and is subject to change.]

### What's the estimated time that's required to set up Business performance analytics?

The setup of Business performance analytics takes up to 60 minutes. However, it takes up to 24 hours for data to be available on reports.

### I received an error during the installation of Business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of Business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of Business performance analytics if it fails?

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### Why isn't my data showing up in Business performance analytics?

To maintain the accuracy of report data, Business performance analytics assesses the quality of the source data. If the assessments don't meet defined rules, Business performance analytics logs information in the **Bpa self help logs** table in Microsoft Dataverse. To learn more, see [Business performance analytics self-help](/troubleshoot/dynamics-365/finance/business-performance-analytics/business-performance-analytics-self-help-overview).

Some customers might reach the storage capacity limits of their Power BI Embedded SKU. In this case, the Power BI dataset that they need for reports can't be updated. By default, Business performance analytics uses the A3 SKU for Power BI Embedded. We recommend that you scale up your SKU to raise your Power BI Embedded storage capacity. For more information, see [Capacity and SKUs in Power BI embedded analytics](/power-bi/developer/embedded/embedded-capacity).

### Why is Business performance analytics using a lot of managed data lake storage in Dataverse?

As part of the data pipeline for Business performance analytics, your data is transformed to fit our dimensional data model. This process creates files that are saved to the managed data lake. The data transformation process occurs every time Business performance analytics refreshes its data. It generates new files in the managed data lake without deleting the old, obsolete files. The old files are deleted in 30 days, or our team manually deletes them when Business performance analytics uses 50 percent or more of the managed data lake's storage capacity.

### When will data be available in reports after the Business performance analytics is installed for the first time?

Data will be available 24 hours after installation is completed.

### When will data be available on reports?

We recommend that you check 24 hours after the installation of Business performance analytics is completed.

### How many years of data are available on reports?

Business performance analytics has data for the current calendar year plus the previous three calendar years.

### After Business performance analytics is set up, how often is the data refreshed?

Data is refreshed once per day, at 00:00:00 AM (UTC). To see exactly when a report's data was last refreshed, open the report. Towards the top of the window, the rightmost item displays when the data for the report was last refreshed. 

### How long does it take for fresh data to be available every day on Business performance analytics reports?

The amount of time that's required depends on the volume of data. However, there should be fresh data every 24 hours.

### How do I uninstall Business performance analytics?
There are two options available to uninstall Business performance analytics. If you need to install Business performance analytics after uninstalling, wait four hours before installing.

Option one:

1. Sign into [Power Platform admin center](https://admin.powerplatform.microsoft.com/) using Microsoft Dataverse admin credentials. 
2. Select the environment where you want to uninstall.
3. Click on the environment URL provided in the details. This redirects you to the Dataverse environment login page.
4. Open the developer console by either pressing **Ctrl+Shift+I** or go to **More tools**, select **Developer tools** and **Console** tab.
5. Paste the following JavaScript code into the console to start the uninstallation process.
6. The approximate time that's required to delete all the solutions is 20 minutes. If the operation is successful, you receive the following message: Business performance analytics solutions removed successfully.
   
Uninstall Business performance analytics
```
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
    throw new Error("Some solutions failed to uninstall");
  }
  console.info("BPA Solutions removed successfully");
};

start();
```

### Uninstall Business performance analytics

Option two: Business performance analytics can be manually uninstalled through Power Platform admin center. The solutions must be manually deleted in the following order.

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

1. In the [maker portal](https://make.preview.powerapps.com/), on the **Solution** tab, select the solution to delete, and then select **Delete**.
2. Select **Delete** again to confirm the operation.
3. Wait for the **Deleting** message box to disappear. If the operation is successful, you receive the following message: "Successfully deleted solution."

The approximate time that's required to delete all the solutions is 20 minutes.

>[!NOTE]
>If you uninstall and install Business performance analytics, any new reports that were created won't be saved. 

### How often will updates for Business performance analytics be released?

- **New features** - Once per month 
- **Bugs** - Bi-weekly 

### Is there any cost to install and use Business performance analytics during public preview?

No. The data is restricted to the current calendar year plus the previous three calendar years.

### How do I know when a new release of Business performance analytics is available?

You can view any updates that are available for Business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of Business performance analytics is available?

When a new release of Business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.

### During public preview, what can I expect each time that data is restored from production to sandbox?

As a customer, you might want to restore data from your production environment to a sandbox environment, so that you can validate new data as part of Business performance analytics. In public preview, data won't be able to move again from production to sandbox. If you want to move data again from production to sandbox, delete the existing environment, create new environment and install Business performance analytics.
Any new data changes done in Dynamics 365 finance and operations UI can still be seen in Business performance analytics. The limitation above is only for changes via data movement from production to sandbox.
