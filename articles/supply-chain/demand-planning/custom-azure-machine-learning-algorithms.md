---
title: Use your own custom Azure Machine Learning algorithms in Demand planning (preview)
description: If you're already using your own Azure Machine Learning algorithms for demand forecasting in Supply Chain Management, then you can continue to do so while using the Demand planning app. This article describes how.
author: t-benebo
ms.author: benebotg
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/15/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Use your own custom Azure Machine Learning algorithms in Demand planning (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!-- KFM: Preview until further notice -->

If you're already using your own Azure Machine Learning algorithms for demand forecasting in Supply Chain Management (as described in [Demand forecasting overview](../master-planning/introduction-demand-forecasting.md)), then you can continue to do so while using the Demand planning app.

This article describes the setup steps required to enable the Demand planning app to connect to your own [Azure Machine Learning workspace](/azure/machine-learning/concept-workspace?view=azureml-api-2).

## Set up a new Microsoft Entra application

Follow the steps in this section to create a new Microsoft Entra application in your Azure Machine Learning workspace. This resource in [Azure portal](/azure/azure-portal/azure-portal-overview) is where your algorithms are held. This enterprise application allows the Demand planning app to connect to your Azure Machine Learning algorithms. (For more information about how to set up a Microsoft Entra application, see also [Quickstart: Register an app in the Microsoft identity platform \| Microsoft Learn](/entra/identity-platform/quickstart-register-app#register-an-application).)

1. Sign in to the [Azure portal](https://portal.azure.com/) with at least *Cloud Application Administrator* privileges.
1. Register a new Microsoft Entra application as described in [Create a Microsoft Entra application and service principal that can access resources](/azure/active-directory/develop/howto-create-service-principal-portal).
1. Follow the on-screen instructions as you complete the wizard. Use the default settings.
1. In the **Certificates & secrets** section of your new Microsoft Entra application, create a secret for the application as described in [Add a client secret](/azure/active-directory/develop/quickstart-register-app#add-a-client-secret).
1. Make a note of the application ID and its secret. You'll need these details later.

## Assign access for the new Microsoft Entra application to Azure Machine Learning workspace

Follow these steps to assign access for the new Microsoft Entra application to Azure Machine Learning workspace:

1. In [Azure portal](https://portal.azure.com/), go to the resource group that contains your Azure Machine Learning workspace.
1. Select **Access control** in the left column.
1. On **Role assignments**, select **Add** to add a new role assignment.
1. Under **Privileged administrator roles**, select **Contributor**.
1. Select **Next**.
1. Select **User, group, or service principal**.
1. Select **Select members**. Use the filter in the menu on the right to find the name of the Microsoft Entra application you created and select it.
1. The application now appears in the **Members** list. Select **Next**.
1. Select **Next** on **Review + assign**.
1. The application is now listed in the **All** section for **Role assignments**.

## Connect to the Azure Machine Learning service from Demand planning

Follow these steps to set up the Azure Machine Learning service connection in Demand planning:

1. Sign in to the Demand planning app.
1. In the left column, select **Custom Azure ML**.
1. Select the **&plus;** button to establish a new connection and make the following settings for it:
    - **Name** – Enter a name for the connection.
    - **Subscription ID** – Enter the ID for your Azure subscription.
    - **Resource group name** – Enter the name of the resource group that contains your Azure Machine Learning workspace.
    - **Workspace name** – Enter the name of your Azure Machine Learning workspace.
    - **Storage Account Name:** – Enter the Azure storage account name that you specified when you ran the setup wizard in your Azure workspace.
    - **Application ID** – Enter the application ID for the Microsoft Entra application that you created. This value is used to authorize API requests to Azure Machine Learning service.
    - **Application secret** – Enter the service principal application secret for the Microsoft Entra application that you created. This value is used to acquire the access token for the security principal that you created to perform authorized operations against Azure Storage and the Azure Machine Language workspace.

## Create a forecast using your own Azure Machine Learning algorithms

Follow these steps to create a forecast using your own Azure Machine Learning algorithms:

1. Create a new forecast profile as described in [Work with forecast profiles (preview)](forecast-profiles.md#create-profile).
1. On the **Select a forecasting model preset** page, select *None*.
1. After you're done creating and saving the profile, go to the **Forecast model** tab (see also [Design forecast models (preview)](design-forecast-models.md)).
1. Set up your model and include a **Finance and operations – Azure Machine Learning** tile at the position where you want to run your algorithm.
1. Finish the model by adding a **Save** block.
