---
# required metadata

title: Business events and Azure Service Bus Queue
description: This topic explains how to configure a Microsoft Azure Service Bus Queue endpoint.
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

This topic explains how to configure a Microsoft Azure Service Bus Queue endpoint.

## Create an Azure Service Bus Queue endpoint

1. On the **Business events** page, on the **Endpoints** tab, select **New** to create an endpoint.
2. In the **Configure new endpoint** dialog box, in the **Endpoint type** field, select the appropriate endpoint type. To create an endpoint to a Service Bus queue, select **Azure Service Bus Queue**.
3. Select **Next**.

    ![Selecting Azure Service Bus Queue as the endpoint type in the Configure new endpoint dialog box.](../../media/businesseventsnewendpoint1.png)

4. In the **Endpoint name** field, enter the name of the endpoint.
5. Set up Azure Key Vault to provide the secret to the Azure messaging resource.
6. Set up the Azure Active Directory (Azure AD) application ID and application secret.
7. Back in the **Configure new endpoint** dialog box, in the **Queue name** field, enter the name that you created for the Service Bus queue  in the Azure Service Bus Queue configuration in Azure.

    ![Service Bus Queue name in the Azure Service Bus Queue configuration in Azure.](../../media/BusinessEventsSBQueueName.PNG)

8. In the **Azure Active Directory application ID** field, enter the application ID that you created in Azure AD in the Azure portal.

    ![Application ID in Azure AD in the Azure portal.](../../media/businesseventsaad1.png)

9. In the **Azure application secret** field, enter the secret value for the application.

    ![Secret value for the application in the Azure portal.](../../media/businesseventsaad2.png)

10. In the **Key Vault DNS name** field, enter the Domain Name System (DNS) name from your Key Vault setup.

    ![DNS name from your Key Vault setup.](../../media/businesseventskeyvault1.png)

11. In the **Key Vault secret name** field, enter the secret name for the endpoint resource that must be created in Key Vault.

    ![Secret name for the endpoint resource that must be created in Key Vault.](../../media/businesseventskeyvault2.png)

    The **Key Vault Secret** value in Azure will be the **Primary Connection String** value for the Service Bus. You can find this value in the Service Bus that you configured, at **Shared Access Policies \> RootManagedSharedAccessKey**.

    ![Business events Key Vault key value.](../../media/BusinessEventsKVSValue.PNG)

12. Select **OK**.

    ![Specifying the name of the endpoint and the Service Bus queue in the Configure new endpoint dialog box.](../../media/businesseventsnewendpoint2.png)

> [!IMPORTANT]
> The Azure application that was registered must be also added to the Key Vault setup under **Access policies** in the key vault. To complete this setup, select the **Key, Secret & Certificate Management** template, and then select the application as the **principal**.
