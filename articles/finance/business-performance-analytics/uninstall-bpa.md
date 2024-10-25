---
title: Uninstall Business performance analytics
description: This article describes how to uninstall Business performance analytics.
author: lizmota
ms.author: jiwo
ms.topic: faq
ms.custom:
ms.reviewer: twheeloc 
audience: Application User
ms.date: 9/11/2024
---

# Uninstall Business performance analytics

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

### Uninstall Business performance analytics

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
>If you uninstall and install Business performance analytics, any new reports that were created won't be saved. 
