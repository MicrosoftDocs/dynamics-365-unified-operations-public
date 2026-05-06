---
title: Business events and Azure Service Bus Queue
description: Learn how to configure a Microsoft Azure Service Bus Queue endpoint through a numbered list detailing steps on how to create an endpoint.
author: jaredha
ms.author: jaredha
ms.topic: article
ms.date: 04/08/2026
# ms.custom: NotInToc
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2021-11-03
ms.search.form:
ms.dyn365.ops.version: 10.0.22
ms.custom: sfi-image-nochange
---

# Business events and Azure Service Bus Queue

[!include[banner](../../includes/banner.md)]

This article explains how to configure a Microsoft Azure Service Bus Queue endpoint.

## Create an Azure Service Bus Queue endpoint

1. On **Business events**, select the **Endpoints** tab, and then select **New** to create an endpoint.
1. In **Configure new endpoint**, select the appropriate endpoint type in the **Endpoint type** field. To create an endpoint to a Service Bus queue, select **Azure Service Bus Queue**.
1. Select **Next**.

    :::image type="content" source="../../media/businesseventsnewendpoint1.png" alt-text="Screenshot of selecting Azure Service Bus Queue as the endpoint type in the Configure new endpoint dialog box.":::

1. Enter the name of the endpoint in the **Endpoint name** field.
1. Set up Azure Key Vault to provide the secret to the Azure messaging resource.
1. Set up the Microsoft Entra application ID and application secret.
1. Back in **Configure new endpoint**, enter the name that you created for the Service Bus queue in the **Queue name** field.

    :::image type="content" source="../../media/BusinessEventsSBQueueName.PNG" alt-text="Screenshot of Service Bus Queue name in the Azure Service Bus Queue configuration in Azure.":::

1. Enter the application ID that you created in Microsoft Entra ID in the Azure portal in the **Microsoft Entra application ID** field.

    :::image type="content" source="../../media/businesseventsaad1.png" alt-text="Screenshot of Application ID in Microsoft Entra ID in the Azure portal.":::

1. Enter the secret value for the application in the **Azure application secret** field.

    :::image type="content" source="../../media/businesseventsaad2.png" alt-text="Screenshot of the secret value for the application in the Azure portal.":::

1. Enter the Domain Name System (DNS) name from your Key Vault setup in the **Key Vault DNS name** field.

    :::image type="content" source="../../media/businesseventskeyvault1.png" alt-text="Screenshot of the DNS name from your Key Vault setup.":::

1. Enter the secret name for the endpoint resource that you must create in Key Vault in the **Key Vault secret name** field.

    :::image type="content" source="../../media/businesseventskeyvault2.png" alt-text="Screenshot of the secret name for the endpoint resource that must be created in Key Vault.":::

    The **Key Vault Secret** value in Azure is the **Primary Connection String** value for the Service Bus. You can find this value in the Service Bus that you configured, at **Shared Access Policies \> RootManagedSharedAccessKey**.

    :::image type="content" source="../../media/BusinessEventsKVSValue.PNG" alt-text="Screenshot of the Business events Key Vault key value.":::

1. Select **OK**.

    :::image type="content" source="../../media/businesseventsnewendpoint2.png" alt-text="Screenshot of specifying the name of the endpoint and the Service Bus queue in the Configure new endpoint dialog box.":::

> [!IMPORTANT]
> Add the registered Azure application to the Key Vault setup under **Access policies** in the key vault. To complete this setup, select the **Key, Secret & Certificate Management** template, and then select the application as the **principal**.
