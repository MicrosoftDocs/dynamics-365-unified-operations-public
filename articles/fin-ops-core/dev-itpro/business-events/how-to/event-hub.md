---
title: Business events and Azure Event Hubs
description: This tutorial describes the steps that you must follow to make business events work with Microsoft Azure Event Hubs.
author: Sunil-Garg
ms.author: sunilg
ms.topic: article
ms.date: 04/08/2026
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: Platform update 28
# ms.search.form: [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-07-31 
ms.custom:
  - sfi-image-nochange
  - sfi-ropc-nochange
---

# Business events and Azure Event Hubs

[!include[banner](../../includes/banner.md)]

This tutorial describes the steps to make business events work with Microsoft Azure Event Hubs.

1. In Azure portal, create an Active Directory app registration. Make a note of the application ID.

   :::image type="content" source="../../media/BE_EH_aad.PNG" alt-text="Screenshot of the Application (client) ID value."​:::

1. Give the app permission to the Azure Key Vault application programming interface (API). 

   :::image type="content" source="../../media/BE_EH_api.png" alt-text="Screenshot of giving the app permission to the Azure Key Vault API."​:::

1. In the app registration, create an application secret. Make a note of the value.

   :::image type="content" source="../../media/BE_EH_secret.jpg" alt-text="Screenshot of creating an application secret."​:::

1. In the key vault, give permission to the new app registration.

   :::image type="content" source="../../media/BE_EH_permission.jpg" alt-text="Screenshot of giving the key vault permission to the app registration."​:::

1. In the key vault, create a new secret. The value of this secret must be the connection string to your event hub. Make a note of the value.

   :::image type="content" source="../../media/BE_EH_connectionstring.jpg" alt-text="Screenshot of the connection string."​:::

1. Create an endpoint configuration for the event hub. Go to **System administration \> Setup \> Business events \> Business events catalog**, and then, on the **Endpoints** tab, select **New** to open the **Configure new endpoint** wizard.

   :::image type="content" source="../../media/BE_EH_endpointconfig.jpg" alt-text="Screenshot of the Configure new endpoint wizard."​:::

1. In the **Endpoint type** field, select **Azure Event Hub**.
1. Select **Next**.
1. In the **Endpoint name** field, enter a name for the endpoint.
1. In the **Hub name** field, enter the name of your event hub.
1. In the **Microsoft Entra application ID** field, enter the application ID that you created earlier.
1. In the **Azure application secret** field, enter the value that you created earlier.
1. In the **Key Vault DNS name** field, enter the Domain Name System (DNS) name of your key vault. You can find this value on the **Overview** tab of the key vault configuration in the Azure portal.
1. In the **Key Vault secret name** field, enter the name from the secret that you created earlier.
1. Select **OK**.
1. You can now activate one or more business events that you want to send to this endpoint.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]