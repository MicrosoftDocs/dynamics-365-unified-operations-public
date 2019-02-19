---
# required metadata

title: Tutorial - Recurring Data Export using Azure Logic App
description: This tutorial demonstrates how to create an Azure Logic App that exports data from Dynamics 365 for Talent on a recurring schedule.
author: gregboyko 
manager: AnnBe
ms.date: 02/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-talent
ms.technology: 

# optional metadata

# ms.search.form:
audience: IT Pro
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Talent, Core
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: gboyko
ms.search.validFrom: 2019-01-01
ms.dyn365.ops.version: Talent January 2019 update
---

# Tutorial - Recurring data export using Azure Logic App

[!include[banner](../includes/banner.md)]

This tutorial demonstrates how to create an Azure Logic App that exports data from Dynamics 365 for Talent Core HR on a recurring schedule. The tutorial makes use of Talent Core HR's DMF Package REST API to export the data. Once the data has been exported, the Logic App saves the exported data package to a OneDrive for Business folder.

## Business scenario

Exporting data to a downstream system on a recurring schedule is a common business scenario for Dynamics 365 integrations. In this tutorial, we will be exporting all Worker records from Talent and saving that list of Workers in a OneDrive for Business folder.

> [!TIP]
> The specific data being exported and the destination of the exported data are only examples, and can be easily changed to suit your business needs.

## Technologies used

This tutorial makes use of the following technologies:

- Dynamics 365 for Talent Core HR - The master data source for Workers that will be exported
- [Azure Logic Apps](https://azure.microsoft.com/en-us/services/logic-apps/) - orchestration and scheduling of the recurring export
  - HTTP with Azure AD Connector
  - OneDrive for Business Connector
- [DMF package REST API](../dev-itpro/data-entities/data-management-api.md) - to trigger the export and monitor the export progress
- OneDrive for Business - The destination for the export Workers

## Prerequisites

Before beginning this exercise, you will need:

- A Dynamics 365 for Talent Core HR environment with Administrator-level permissions in the environment
- An Azure subscription for the Azure Logic App

## The exercise

At the conclusion of this exercise, you will have completed an Azure Logic App that is connected to your Dynamics 365 for Talent Core HR environment and your OneDrive for Business account. The Logic App will export a data package from Talent Core HR, wait for the export to complete, download the exported data package, and save the data package in your chosen OneDrive for Business folder.

The completed Logic App will look similar to the following:

![Logic App Overview](media/integration-logic-app-overview.png)

### Step 1: Create a data export project in Core HR

In Core HR, create a data export project that exports Workers. Name the project **Export Workers**, ensure that **Generate data package** is set to **Yes**. Add a single entity (Worker) to the project, exporting in the format of your choice (we use Excel in this tutorial).

![Export Workers data project](media/integration-logic-app-export-workers-project.png)

> [!IMPORTANT]
> Remember the name of the data export project. It will be used later when creating the Logic App.

### Step 2: Create the Azure Logic App

The bulk of this exercise is creating the Logic App, which you will complete over the next several steps.

1. Create a Logic App in Azure Portal

![Logic App creation screen](media/integration-logic-app-creation-1.png)

2. In the Logic Apps Designer, start with a blank Logic App.
3. Add a Recurrence Schedule trigger to execute the Logic App every 24 hours.

![Logic App recurrence screen](media/integration-logic-app-recurrence-step.png)

4. Call the [ExportToPackage](../dev-itpro/data-entities/data-management-api#exporttopackage) DMF REST API to schedule the export of your data package.

    - Use the **Invoke an HTTP request** action from the HTTP with Azure AD Connector
    - Base Resource URL: The URL of your Talent environment (do not include path/namespace info)
    - Azure AD Resource URI: http://hr.talent.dynamics.com

> [!NOTE]
> The Talent Core HR service does not yet provide a Connector that exposes these APIs. We instead call the APIs using raw HTTPS requests.

![Logic App HTTP AAD connector screen](media/integration-logic-app-http-aad-connector-step.png)

  - Sign in to your Talent environment through the HTTP AAD connector
  - Set up an HTTP POST request to call the **ExportToPackage** DMF REST API
    - **Method**: POST
    - **Url of the request**: https://<hostname>/namespaces/<namespace_guid>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.ExportToPackage
    - **Body of the request**:

```JSON
{
    "definitionGroupId":"Export Workers",
    "packageName":"talent_package.zip",
    "executionId":"",
    "reExecute":false,
    "legalEntityId":"USMF"
}
```

![Logic App export to package screen](media/integration-logic-app-export-to-package-step.png)

> ![TIP]
> You may wish to rename each step to something more meaningful than the default name of **Invoke an HTTP request** (e.g. **ExportToPackage** for this step)

5. Initialize a variable to store the Execution Status of the ExportToPackage request.

![Logic App initialize variable screen](media/integration-logic-app-initialize-variable-step.png)

6. Wait until the Execution Status of the data export has succeeded

    - Add **Until** loop that repeats until the value of the ExecutionStatus variable is **Succeeded**.
    - Add a **Delay** that waits 5 seconds before polling for the current execution status of the export

![Logic App until loop screen](media/integration-logic-app-until-loop-step.png)

> ![NOTE]
> Set the limit count to 15 to allow a maximum of 75 seconds (15 iterations * 5 seconds) of wait time for the export to complete. Adjust as necessary if your export takes longer.

  - Add an **Invoke HTTP request** action to call the [GetExecutionSummaryStatus](../dev-itpro/data-entities/data-management-api#getexecutionsummarystatus) DMF REST API and set the ExecutionStatus variable to the result from the GetExecutionSummaryStatus response.
    - **Method**: POST
    - **Url of the request**: https://<hostname>/namespaces/<namespace_guid>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExecutionSummaryStatus
    - **Body of the request**: body('Invoke_an_HTTP_request').value

> [!NOTE] You may need to enter the Body value in code view or the function editor
  
![Logic App get execution status screen](media/integration-logic-app-get-execution-status-step.png)

![Logic App set variable screen](media/integration-logic-app-set-variable-step.png)

> ![IMPORTANT]
> The value for the **Set Variable** action (*body('Invoke_an_HTTP_request_2').value*) will be different than the value for the **Invoke HTTP request 2** body value, even though the designer will render the values the same way.

7. Get the download URL of the exported package
   
  - Add an **Invoke HTTP request** action to call the [GetExportedPackageUrl](../dev-itpro/data-entities/data-management-api#getexportedpackageurl) DMF REST API.
    - **Method**: POST
    - **Url of the request**: https://<hostname>/namespaces/<namespace_guid>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExportedPackageUrl
    - **Body of the request**: {"executionId": body('GetExportedPackageURL').value}

![Logic App get package URL screen](media/integration-logic-app-get-exported-package-step.png)

8. Download the exported package

  - Add an HTTP GET request (using the built-in HTTP connector) to download the package from the URL returned in the previous step.
    - **Method**: GET
    - **URI**: body('Invoke_an_HTTP_request_3').value (may need to enter through code view or function editor in designer)

![Logic App download file screen](media/integration-logic-app-download-file-step.png)

> ![NOTE]
> This request does not require any additional authentication since the GetExportedPackageUrl API returns a URL that includes a SAS token granting access to download the file.

9. Save the downloaded package in OneDrive

  - Add a OneDrive for Business **Create File** action
    - Connect to your OneDrive account if necessary
    - **Folder Path**: <pick a folder>
    - **File Name**: worker_package.zip
    - **File Content**: Body of the previous step (dynamic content)

![Logic App create file screen](media/integration-logic-app-create-file-step.png)

### Step 3: Test your Logic App

## Summary

## docs.microsoft extensions

docs.microsoft provides a few additional extensions to GitHub Flavored Markdown. 

### Alerts

It's important to use the following alert styles so they render with the proper style in the documentation site. However, the rendering engine on GitHub doesn't diferentiate them.

#### Note

> [!NOTE]
> This is a NOTE

#### Warning

> [!WARNING]
> This is a WARNING

#### Tip

> [!TIP]
> This is a TIP

#### Important

> [!IMPORTANT]
> This is IMPORTANT

And they'll render like this:
![Alert styles](../images/alerts.png)


