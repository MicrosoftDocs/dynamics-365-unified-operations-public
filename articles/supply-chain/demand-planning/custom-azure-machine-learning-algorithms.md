---
title: Use custom Azure Machine Learning algorithms in Demand planning
description: Learn how to use custom Microsoft Azure Machine Learning algorithms for demand forecasting in Dynamics 365 Supply Chain Management while you use demand planning.
author: AndersEvenGirke
ms.author: aevengir
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Use your own custom Azure Machine Learning algorithms in Demand planning

[!include [banner](../includes/banner.md)]

In addition to the standard forecasting algorithms provided with Demand planning, you can also create your own custom algorithms and use them in your [Demand planning forecast models](design-forecast-models.md). To do so, you must create and publish your algorithms using Microsoft Azure Machine Learning, set up a connection from Demand planning to Azure, and place one of the following types of steps to your forecast models as needed (instead of using the standard *Forecast* step):

- *Custom* step – Lets you use custom algorithms that you've created using Microsoft Azure Machine Learning, but which you've never before used with Dynamics 365 Supply Chain Management.
- *Finance and operation* step – Lets you use custom algorithms that you previoiusly used in Dynamics 365 Supply Chain Management (as described in [Demand forecasting overview](../master-planning/introduction-demand-forecasting.md)).

This article describes the setup that is required to enable Demand planning to connect to your [Azure Machine Learning workspace](/azure/machine-learning/concept-workspace). It also explains how to set up each type of custom algorithm step in your forecat models.

## Set up a new Microsoft Entra application

Follow the steps in this section to create a new Microsoft Entra application in your Azure Machine Learning workspace. This resource in the [Azure portal](/azure/azure-portal/azure-portal-overview) holds your algorithms. The Microsoft Entra application is an enterprise application that enables Demand planning to connect to your Azure Machine Learning algorithms. Learn more about how to set up a Microsoft Entra application in [Register an application](/entra/identity-platform/quickstart-register-app#register-an-application).

1. Sign in to the [Azure portal](https://portal.azure.com/) by using an account that has at least *Cloud Application Administrator* privileges.
1. Register a new Microsoft Entra application as described in [Create a Microsoft Entra application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal).
1. Follow the on-screen instructions to complete the wizard. Use the default settings.
1. In the **Certificates & secrets** section of the new Microsoft Entra application, create a secret for the application as described in [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret).
1. Make a note of the application ID and its secret. You'll need these details later.

## Grant access for the new Microsoft Entra application to the Azure Machine Learning workspace and Azure Machine Learning workspace storage account

Follow these steps to grant access for the new Microsoft Entra application to the Azure Machine Learning workspace.

1. In the [Azure portal](https://portal.azure.com/), go to the resource group that contains your Azure Machine Learning workspace.
1. On the left navigation pane, select **Access control**.
1. On the **Role assignments** tab, select **Add** to add a new role assignment.
1. On the **Privileged administrator roles** tab, select *Contributor*.
1. Select **Next**.
1. Select the **User, group, or service principal** option.
1. Select **Select members**. Use the filter on the menu on the right to find the name of the Microsoft Entra application that you created, and then select it.
1. The application now appears in the **Members** list. Select **Next**.
1. On the **Review \+ assign** tab, select **Next**.

Follow these steps to allow the new Microsoft Entra application to access the storage account that Azure Machine Learning workspace is connected to.

1. In the [Azure portal](https://portal.azure.com/), go to the resource group that contains your storage account (the storage account that your Azure Machine Learning workspace is using).
1. On the left navigation pane, select **Access control**.
1. On the **Role assignments** tab, select **Add** to add a new role assignment.
1. On the **Job function roles** tab, select *Storage account contributor* and *Storage blob data contributor*. To find these roles quickly, enter *storage contributor* into the **Search** field.
1. Select **Next**.
1. Select the **User, group, or service principal** option.
1. Select **Select members**. Use the filter on the menu on the right to find the name of the Microsoft Entra application that you created, and then select it.
1. The application now appears in the **Members** list. Select **Next**.
1. On the **Review \+ assign** tab, select **Next**.

The application is now listed in the **All** section of the **Role assignments** tab on both the Azure Machine Learning workspace and the storage account.

## Connect to the Azure Machine Learning service from Demand planning

Follow these steps to set up the Azure Machine Learning service connection in Demand planning.

1. Sign in to Demand planning.
1. On the left navigation pane, select **Custom Azure ML**.
1. In the toolbar, select **New** to create a new connection and set the following fields for it:

    - **Name** – Enter a name for the connection.
    - **Subscription ID** – Enter the ID for your Azure subscription.
    - **Resource group name** – Enter the name of the resource group that contains your Azure Machine Learning workspace.
    - **Workspace name** – Enter the name of your Azure Machine Learning workspace.
    - **Storage Account Name** – Enter the name of the Azure storage account that you specified when you ran the setup wizard in your Azure workspace.
    - **Application ID** – Enter the application ID of the Microsoft Entra application that you created. This value is used to authorize API requests to the Azure Machine Learning service.
    - **Application secret** – Enter the service principal application secret for the Microsoft Entra application that you created. This value is used to acquire the access token for the security principal that you created to perform authorized operations against Azure Storage and the Azure Machine Language workspace.

1. On the Action Pane, select **Save**.
1. On the **ML workspace pipelines URLs** FastTab, add a row for each pipeline provided by your workspace. Each pipeline requires a unique **Name** (which is only used internally in Demand planning) and a **Pipeline URL**, which is the full URL that Demand planning must use to access the pipeline. <!-- KFM: Few more details are needed here. For example: What is a "pipeline" and what do we need it for? What do the **Activate** and **Deactivate** toolbar buttons do--do we need to use them? I understand we use "pipelines" for *FnO* steps, but "batch" for *Custom* steps--what does that mean for the settings we see here? Where do we find URLs to communicate via "batch" instead of "pipeline"? "Batch" is not mentioned anywhere in this article. -->

## Set up a forecast that uses your own Azure Machine Learning algorithms

Follow these steps to set up a forecast that uses your own Azure Machine Learning algorithms.

1. Create a new forecast profile as described in [Create and manage forecast profiles](forecast-profiles.md#create-profile).
1. On the **Select a forecasting model preset** page, select *None*.
1. After you've created and saved the profile, select the **Forecast model** tab. (Learn more in [Design forecast models](design-forecast-models.md).)
1. Set up your model. Add a *Finance and operations* step in the position where you want to run your algorithm. <!-- KFM: Or maybe the *Custom* step? Or mention both?-->
1. Open the **Actions** menu for the *Finance and operations* step and then select **Settings**.
1. In the **Configure step** dialog, make the following settings for the step:
    - **Step name** – Enter a name for the step.
    - **Description** – Enter a description for the step.
    - **Custom action configuration** – <!-- KFM: description needed -->
    - **Azure ML endpoint** – <!-- KFM: description needed -->
    - **Custom parameters** – <!-- KFM: description needed -->
1. Select **Save** to close the dialog.
1. Complete the model by adding a *Save* step.

## Download sample code and other resources

To download sample code and other resources that demonstrate how to use custom Azure Machine Learning algorithms in Demand planning, go to the [Custom-ML-in-DemandPlanning repository on GitHub](https://github.com/microsoft/Dynamics-365-Demand-Planning-Custom-Azure-ML-Template). It provides insights into how to read input data, handle standard and custom parameters, and generate output that aligns with the application's consumption requirements. The repository consists of a readme file, a scoring script, a docker file, and demonstrative videos.
