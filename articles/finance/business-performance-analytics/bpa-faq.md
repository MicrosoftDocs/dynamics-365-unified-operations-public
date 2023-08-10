---
# required metadata

title: Business performance analytics FAQ
description: This article answers frequently asked questions about business performance analytics.
author: jinniew
ms.author: jiwo
ms.reviewer: twheeloc 
ms.date: 07/25/2023
ms.topic: faq
ms.prod: 
ms.technology:
ms.custom:

---
# Business performance analytics FAQ

This article answers frequently asked questions about business performance analytics.

> [!NOTE]
> The functionality that's described in this article is available as part of a preview release. The functionality and the content of this article are subject to change. For more information about how to participate in the public preview of business performance analytics, contact <bpaquestions@service.microsoft.com>.

### How do I sign up for the public preview of business performance analytics?

We're implementing a public preview to ensure that we can provide a successful experience for our customers and obtain valuable feedback. To sign up for public preview, follow the steps listed [here](install-bpa.md#install-the-business-performance-analytics-app).

### What's the estimated time that's required to set up business performance analytics?

The setup of business performance analytics takes about 30 minutes. However, it takes up to 24 hours for data to be available on reports.

### I received an error during the installation of business performance analytics. How do I fix it?

The following errors are likely to occur if another operation is in progress during the installation of business performance analytics. If these errors persist, retry the installation.

- "There's another \[RibbonMetadataGeneration\] running at this moment."
- "Issues with enabling Change tracking: msdyn\_BpaTablesVirtualEntities."
- "Import Failed - errorCode: 0Description: Unable to complete updates to the Track changes option for table."
- "Flight EnableSqlRowVersionChangeTracking isn't enabled. The functionality requires enabling sql row version change tracking feature. Enable flight EnableSqlRowVersionChangeTracking."

### How do I retry the installation of business performance analytics if it fails?

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/) by using Microsoft Dataverse admin credentials.
2. Go to **Environments**, and select **Dynamics 365 Apps**.
3. Find **Business performance analytics**, and select **Installation failed**.
4. Select the link to retry the installation, and monitor the app installation process.

### When will data be available in reports after the business performance analytics is installed for the first time?

Data will be available after 24 hours after installation is completed.

### When will data be available on reports?

We recommend that you check 24 hours after the installation of business performance analytics is completed.

### How many years of data are available on reports?

Business performance analytics has data for the current fiscal year plus the previous three years.

### After business performance analytics is set up, how often is the data refreshed?

Data is refreshed once per day, at 00:00:00 AM (UTC).

### How long does it take for fresh data to be available every day on business performance analytics reports?

The amount of time that's required depends on the volume of data. However, there should be fresh data every 24 hours.

### How do I uninstall business performance analytics?
There are two options available to uninstall business performance analytics. 

Option one:

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/). 
2. Click Ctrl+Shift+I to open the developer console or go to **More tools**, select **Developer tools** and **Console** tab.
3. Paste the below JavaScript code to start uninstall process.

UninstallBPA JavaScript
```
// Get the current org URL
const ORG = window.location.hostname;
const WEB_API = `https://${ORG}/api/data/v9.2`;
const SOLUTIONS = [
  "msdyn_BpaAnchor",
  "msdyn_BpaPlugins",
  "msdyn_Bpa",
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
  let installedBPASoltuins = installedSolutions
    .filter((i) => SOLUTIONS.indexOf(i.uniquename) > -1)
    .sort(
      (i, j) =>
        SOLUTIONS.indexOf(i.uniquename) - SOLUTIONS.indexOf(j.uniquename)
    );
  for (let solution of installedBPASoltuins) {
    console.info(`Removing solution ${solution.friendlyname}`);
    await _deleteSolution(solution.solutionid);
  }
  console.info("BPA Solutions removed successfully");
};

start();
```

### Uninstall business performance analytics

Option two: Business performance analytics can be manually uninstalled through Power Platform admin center. The solutions must be manually deleted in the following order.

1. Business performance analytics anchor solution  
2. Business performance analytics plugins solution 
3. Business performance analytics solution 
4. Business performance analytics permissions 
5. Business performance analytics tables 
6. Business performance analytics controls 
7. Business performance analytics tables anchor solution 
8. Business performance analytics tables user roles 
9. Business performance analytics analytical tables workspace 
10. Business performance analytics analytical tables 
11. Business performance analytics tables transformation job flows 
12. Business performance analytics tables data processing configuration 
13. Business performance analytics tables data lake synchronization 
14. Business performance analytics tables standard entities 
15. Business performance analytics tables virtual entities 
16. Business performance analytics tables managed data lake 
17. Business performance analytics pipeline plugins solution 
18. Business performance analytics tables security 

To delete each of the preceding solutions, follow these steps.

1. In the [maker portal](https://make.preview.powerapps.com/), on the **Solution** tab, select the solution to delete, and then select **Delete**.
2. Select **Delete** again to confirm the operation.
3. Wait for the **Deleting** message box to disappear. If the operation is successful, you receive the following message: "Successfully deleted solution."

The approximate time that's required to delete all the solutions is 20 minutes.

>[!NOTE]
>If you uninstall and install business performance analytics, any new reports that were created won't be saved. 

### How often will updates for business performance analytics be released?

- **New features:** Once per month 
- **Bugs:** Bi-weekly 

### Is there any cost to install and use business performance analytics during public preview?

No. The data is restricted to the current fiscal year plus the previous three fiscal years.

### How do I know when a new release of business performance analytics is available?

You can view any updates that are available for business performance analytics through Power Platform admin center. Sign in to the environment, and go to **Installed apps**.

### What should I do when a new release of business performance analytics is available?

When a new release of business performance analytics is available, you can update the package through Power Platform admin center.

1. Sign in to [Power Platform admin center](https://admin.powerplatform.microsoft.com/).
2. In your environment, go to **Installed apps**.
3. Select **Update available**.

### During public preview, what can I expect each time that data is restored from production to sandbox?

As a customer, you might want to restore data from your production environment to a sandbox environment, so that you can validate new data as part of business performance analytics. In public preview, data won't be able to move again from production to sandbox. If you want to move data again from production to sandbox, delete the existing environment, create new environment and install business performance analytics.
Any new data changes done in Dynamics 365 finance and operations UI can still be seen in business performance analytics. The limitation above is only for changes via data movement from production to sandbox.

