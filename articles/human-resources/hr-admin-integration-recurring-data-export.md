---
# required metadata

title: Create a recurring data export app
description: This article describes how to create a Microsoft Azure logic app that exports data from Microsoft Dynamics 365 Human Resources on a recurring schedule.
author: twheeloc    
ms.date: 05/14/2026
ms.topic: how-to
# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources
ms.custom: sfi-image-nochange

---

# Create a recurring data export app

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes how to create a Microsoft Azure logic app that exports data from Microsoft Dynamics 365 Human Resources on a recurring schedule. The tutorial takes advantage of Human Resources' DMF package REST application programming interface (API) to export the data. After the data is exported, the logic app saves the exported data package to a Microsoft OneDrive folder.

## Business scenario

In one typical business scenario for Microsoft Dynamics 365 integrations, you need to export data to a downstream system on a recurring schedule. This tutorial shows how to export all worker records from Microsoft Dynamics 365 Human Resources and save the list of workers in a OneDrive folder.

> [!TIP]
> The specific data that you export in this tutorial and the destination of the exported data are only examples. You can easily change them to meet your business needs.

## Technologies used

This tutorial uses the following technologies:

- **[Dynamics 365 Human Resources](https://www.microsoft.com/dynamics-365/products/human-resources)** – The master data source for workers that you export.
- **[Azure Logic Apps](https://azure.microsoft.com/services/logic-apps/)** – The technology that provides orchestration and scheduling of the recurring export.

  - **[Connectors](/azure/connectors/apis-list)** – The technology that connects the logic app to the required endpoints.

    - [HTTP with Microsoft Entra ID](/connectors/webcontents/) connector
    - [OneDrive](/azure/connectors/connectors-create-api-onedriveforbusiness) connector

- **[DMF package REST API](../fin-ops-core/dev-itpro/data-itpro/data-management-api.md)** – The technology that triggers the export and monitors its progress.
- **[OneDrive](https://onedrive.live.com/about/business/)** – The destination for the exported workers.

## Prerequisites

Before you begin the exercise in this tutorial, make sure you have the following items:

- A Human Resources environment that has admin-level permissions in the environment
- An [Azure subscription](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) to host the logic app

## The exercise

At the end of this exercise, you will have a logic app that is connected to your Human Resources environment and your OneDrive account. The logic app will export a data package from Human Resources, wait for the export to be completed, download the exported data package, and save the data package in the OneDrive folder that you specified.

The completed logic app resembles the following illustration.

:::image type="content" source="media/integration-logic-app-overview.png" alt-text="Screenshot of the completed logic app overview.":::

### Step 1: Create a data export project in Human Resources

In Human Resources, create a data export project that exports workers. Name the project **Export Workers**, and set the **Generate data package** option to **Yes**. Add a single entity (**Worker**) to the project, and select the format to export in. (This tutorial uses the Microsoft Excel format.)

:::image type="content" source="media/integration-logic-app-export-workers-project.png" alt-text="Screenshot of the Export Workers data project.":::

> [!IMPORTANT]
> Remember the name of the data export project. You need it when you create the logic app in the next step.

### Step 2: Create the logic app

Most of this exercise involves creating the logic app.

1. In the Azure portal, create a logic app.

    :::image type="content" source="media/integration-logic-app-creation-1.png" alt-text="Screenshot of the logic app creation page.":::

1. In the Logic Apps Designer, start with a blank logic app.
1. Add a [Recurrence Schedule trigger](/azure/connectors/connectors-native-recurrence) to run the logic app every 24 hours (or according to a schedule of your choice).

    :::image type="content" source="media/integration-logic-app-recurrence-step.png" alt-text="Screenshot of the Recurrence dialog box.":::

1. Call the [ExportToPackage](../fin-ops-core/dev-itpro/data-entities/data-management-api.md#exporttopackage) DMF REST API to schedule the export of your data package.

    1. Use the **Invoke an HTTP request** action from the HTTP with Microsoft Entra connector.

        - **Base Resource URL:** The URL of your Human Resources environment (Don't include path or namespace information.)
        - **Microsoft Entra Resource URI:** `http://hr.talent.dynamics.com`

        > [!NOTE]
        > The Human Resources service doesn't yet provide a connector that exposes all the APIs that make up the DMF package REST API, such as **ExportToPackage**. Instead, you must call the APIs by using raw HTTPS requests through the HTTP with Microsoft Entra connector. This connector uses Microsoft Entra ID for authentication and authorization to Human Resources.

    1. Sign in to your Human Resources environment through the HTTP with Microsoft Entra connector.
    1. Set up an HTTP **POST** request to call the **ExportToPackage** DMF REST API.

        - **Method:** POST
        - **Url of the request:** `https://<hostname>/namespaces/<namespace_guid>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.ExportToPackage`
        - **Body of the request:**

            ```JSON
            {
                "definitionGroupId":"Export Workers",
                "packageName":"talent_package.zip",
                "executionId":"",
                "reExecute":false,
                "legalEntityId":"USMF"
            }
            ```

    > [!TIP]
    > You might want to rename each step so that it's more meaningful than the default name, **Invoke an HTTP request**. For example, you can rename this step **ExportToPackage**.

1. [Initialize a variable](/azure/logic-apps/logic-apps-create-variables-store-values#initialize-variable) to store the execution status of the **ExportToPackage** request.

    :::image type="content" source="media/integration-logic-app-initialize-variable-step.png" alt-text="Screenshot of the Initialize variable action.":::

1. Wait until the execution status of the data export is **Succeeded**.

    1. Add an [Until loop](/azure/logic-apps/logic-apps-control-flow-loops#until-loop) that repeats until the value of the **ExecutionStatus** variable is **Succeeded**.
    1. Add a **Delay** action that waits five seconds before it polls for the current execution status of the export.

        :::image type="content" source="media/integration-logic-app-until-loop-step.png" alt-text="Screenshot of the Until loop container.":::

        > [!NOTE]
        > Set the limit count to **15** to wait a maximum of 75 seconds (15 iterations × 5 seconds) for the export to be completed. If your export takes more time, adjust the limit count as appropriate.

    1. Add an **Invoke HTTP request** action to call the [GetExecutionSummaryStatus](../fin-ops-core/dev-itpro/data-entities/data-management-api.md#getexecutionsummarystatus) DMF REST API, and set the **ExecutionStatus** variable to the result of the **GetExecutionSummaryStatus** response.

        > This sample doesn't do error checking. The **GetExecutionSummaryStatus** API can return non-successful terminal states (that is, states other than **Succeeded**). For more information, see the [API documentation](../fin-ops-core/dev-itpro/data-entities/data-management-api.md#getexecutionsummarystatus).

        - **Method:** POST
        - **Url of the request:** `https://<hostname>/namespaces/<namespace_guid>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExecutionSummaryStatus`
        - **Body of the request:** `body('Invoke_an_HTTP_request')?['value']`

            > [!NOTE]
            > You might have to enter the **Body of the request** value either in code view or in the function editor in the designer.

        :::image type="content" source="media/integration-logic-app-get-execution-status-step.png" alt-text="Screenshot of the Invoke an HTTP request 2 action.":::

        :::image type="content" source="media/integration-logic-app-set-variable-step.png" alt-text="Screenshot of the Set variable action.":::

        > [!IMPORTANT]
        > The value for the **Set variable** action (**body('Invoke\_an\_HTTP\_request\_2')?['value']**) differs from the value for the **Invoke an HTTP request 2** body value, even though the designer shows the values in the same way.

1. Get the download URL of the exported package.

    - Add an **Invoke HTTP request** action to call the [GetExportedPackageUrl](../fin-ops-core/dev-itpro/data-entities/data-management-api.md#getexportedpackageurl) DMF REST API.

        - **Method:** POST
        - **Url of the request:** https://\<hostname\>/namespaces/\<namespace\_guid\>/data/DataManagementDefinitionGroups/Microsoft.Dynamics.DataEntities.GetExportedPackageUrl
        - **Body of the request:** {"executionId": body('GetExportedPackageURL')?['value']}

        :::image type="content" source="media/integration-logic-app-get-exported-package-step.png" alt-text="Screenshot of the GetExportedPackageURL action.":::

1. Download the exported package.

    - Add an HTTP **GET** request (a built-in [HTTP connector action](/azure/connectors/connectors-native-http)) to download the package from the URL that the previous step returns.

        - **Method:** GET
        - **URI:** body('Invoke\_an\_HTTP\_request\_3').value

            > [!NOTE]
            > You might have to enter the **URI** value either in code view or in the function editor in the designer.

        :::image type="content" source="media/integration-logic-app-download-file-step.png" alt-text="Screenshot of the HTTP GET action.":::

        > [!NOTE]
        > This request doesn't require any additional authentication, because the URL that the **GetExportedPackageUrl** API returns includes a shared access signatures token that grants access to download the file.

1. Save the downloaded package by using [OneDrive](/azure/connectors/connectors-create-api-onedriveforbusiness) connector.

    - Add an OneDrive file [Create File](/connectors/onedriveforbusinessconnector/#create-file) action.
    - Connect to your OneDrive account, as required.

        - **Folder Path:** A folder of your choice
        - **File Name:** worker\_package.zip
        - **File Content:** The body from the previous step (dynamic content)

        :::image type="content" source="media/integration-logic-app-create-file-step.png" alt-text="Screenshot of the Create file action.":::

### Step 3: Test the logic app

To test your logic app, select **Run** in the designer. You see that the steps of the logic app start to run. After 30 to 40 seconds, the logic app finishes running, and your OneDrive folder includes a new package file that contains the exported workers.

If a failure is reported for any step, select the failed step in the designer, and examine the **Inputs** and **Outputs** fields for it. Debug and adjust the step as required to correct the errors.

The following illustration shows what the Logic Apps designer looks like when all the steps of the logic app run successfully.

:::image type="content" source="media/integration-logic-app-successful-run.png" alt-text="Screenshot of a successful logic app run.":::

## Summary

In this tutorial, you learned how to use a logic app to export data from Human Resources and save the exported data to a OneDrive folder. You can modify the steps of this tutorial as required to suit your business needs.

[!INCLUDE[footer-include](../includes/footer-banner.md)]
