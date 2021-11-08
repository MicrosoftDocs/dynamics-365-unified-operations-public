---
# required metadata

title: Business events and Azure Service Bus Queue
description: This topic explains how to configure a Microsoft Azure Service Bug Queue endpoint.
author: jaredha
ms.date: 11/08/2021
ms.topic: article
ms.prod:
ms.technology: 

# optional metadata

# ms.search.form:
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: NotInToc
ms.search.region: Global
# ms.search.industry:
ms.author: jaredha
ms.search.validFrom: 2021-11-03
ms.dyn365.ops.version: 10.0.22
---

# Business events and Azure Service Bus Queue
[!include[banner](../../includes/banner.md)]

This topic explains how to configure a Microsoft Azure Service Bug Queue endpoint.

## Create an Azure Service Bus Queue endpoint

1. To create a new endpoint, select **New**. 
2. In the **Endpoint type** field, select the appropriate endpoint type. To create an endpoint to a Service Bus queue, select **Azure Service Bus Queue**. 
3. Select **Next**.

![To create an endpoint to a Service Bus queue, select **Azure Service Bus Queue**.](../../media/businesseventsnewendpoint1.png)

4. Specify the name of the endpoint and the Service Bus queue.  
5. Set up Azure Key Vault to provide the secret to the Azure messaging resource. 
6. Set up the Azure Active Directory (Azure AD) application ID and application secret.

    ![Specify the name of the endpoint and the Service Bus queue.](../../media/businesseventsnewendpoint2.png)

In the **Queue Name** field, enter the **Azure Service Bus Queue** name that you created in the Azure Service Bus Queue configuration in Azure.  

![Enter the **Azure Service Bus Queue** name that you created in the Azure Service Bus Queue configuration in Azure.](../../media/BusinessEventsSBQueueName.PNG)

In the **Azure Active Directory application ID** field, enter the application ID that is created in Azure AD in the Azure portal.

![Enter the application ID that is created in Azure AD in the Azure portal.](../../media/businesseventsaad1.png)

In the **Azure application secret** field, enter the secret value for the application.

![Enter the secret value for the application.](../../media/businesseventsaad2.png)

In the **Key vault DNS name** field, enter the name from your Key Vault setup.

![Enter the name from your Key Vault setup.](../../media/businesseventskeyvault1.png)

In the **Key vault secret name** field, enter the secret name for the endpoint resource that must be created in Key Vault.

![Enter the secret name for the endpoint resource that must be created in Key Vault.](../../media/businesseventskeyvault2.png)

The **Key Vault Secret** value, in Azure, will be the Azure Service Bus **Primary Connection String** value. This value is found in the Azure Service Bus that you configured in **Shared Access Policies > RootManagedSharedAccessKey**.

![Business events Azure Key Vault key value.](../../media/BusinessEventsKVSValue.PNG)

> [!IMPORTANT]
> The Azure application that was registered must be also added to the Key Vault set up under Access policies in the Key Vault. For this setup to be complete, select the **Key, Secret & Certificate Management** template and then select the application as the **principal**.
