---
title: Business events and Azure Event Grid
description: Learn how to configure a Microsoft Azure Event Grid endpoint, and how to consume a business event from Event Grid.
author: jaredha
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/15/2026
ms.reviewer: johnmichalak
ms.search.region: Global for most topics. Set Country/Region name for localizations
ms.search.validFrom: Platform update 27
ms.dyn365.ops.version: 2019-6-30 

---
# Business events and Azure Event Grid
[!include[banner](../../includes/banner.md)]

This article explains how to configure a Microsoft Azure Event Grid endpoint and how to consume a business event from Event Grid.

## Scenario overview

Security best practices recommend that you store connection strings outside applications, in an Azure Key Vault drive, and that you give applications the correct access to the key vault keys, secrets, or certificates.

Here are two of the many benefits of this approach:

- Someone who gets access to the application database can't access the third-party connection string.
- Maintenance is easier, especially when multiple applications access the same resources, because you must update connection strings in only one place.

The following overview lists the procedures that you must complete:

1. Create a new Event Grid topic.
1. Create a new key vault to store the key for the Event Grid topic.
1. Register an Azure app that has permission to access the key vault.
1. Configure the parameters of the endpoint.
1. Consume the business event.

## Procedure 1: Create a new Event Grid topic

1. Sign in to the Azure portal.
1. Select **All services \> Integration \> Event Grid Topics**.
1. Select **Add** to create a new Event Grid topic. Set the parameters, and then select **Create**. You can create a new resource group as a container for your lab, or you can use an existing resource group.
1. After deployment is completed, select the new Event Grid. On the property blade, select **Overview**, and make a note of the **Topic Endpoint** value. You need this value later.
1. Back on the property blade, select **Access keys**, and copy the **Key 1** value. You need this value when you configure the key vault in the next procedure.


## Procedure 2: Create a key vault

In this procedure, you create a key vault to store the key that you copied in the previous procedure. A key vault is a secure drive that is used to store keys, secrets, and certificates. Instead of storing the connection string, a more typical and more secure approach is to store it in a key vault. You can then register a new application with Microsoft Entra and grant it the right to retrieve the secret from the key vault.

1. In the Azure portal, select **All services \> Security \> Key vaults**.
1. Create a new key vault in your resource group and set the default parameters.

    :::image type="content" source="../../media/BEF-Howto-Keyvault-02.png" alt-text="Screenshot of New Key Vault.":::

1. Select **Overview**, then copy and save the **DNS Name** value for the key vault. You use this value later.
1. Select **BE-key vault \> Secrets \> Generate/Import**. Enter a name for your secret, and paste the **Key 1** value that you saved earlier.
1. Select **Create**.

## Procedure 3: Register a new application

In this procedure, you register a new application with Microsoft Entra ID, and give it read and retrieve access to key vault secrets. The application uses this access to retrieve Event Grid secrets.

1. In the Azure portal, select **All services \> Security \> Microsoft Entra ID**.
1. Select **App registrations (preview) \> New registration**, and then enter a name for your application.
1. Select **Register**.
1. Select your new application, and then select **Certificates & secrets \> New client secret**. Enter a name for your secret, and set the secret so that it never expires. Then select **Add**.
1. Copy and save your new secret. You use it later.

    > [!IMPORTANT]
    > You can see the secret only one time. If you forget to copy the secret, you must delete it and create a new secret.

1. Select **Overview**, and copy and save the application ID. You use this value later.
1. Select **All services \> Security \> Key vaults**.
1. Select the key vault that you created earlier, and then select **Access policies \> Add new**.
1. On the **Principal** blade, select your new registered application. Select the check boxes for the **Get** and **List** secret permissions to retrieve key vault secrets.

    :::image type="content" source="../../media/BEF-Howto-Keyvault-12.png" alt-text="Screenshot of Key Vault access policy.":::

1. Save your new access policy.

## Procedure 4: Configure a Business Events endpoint

1. Sign in to the application and go to **System administration \> Setup \> Business events**.
1. Select **Endpoints**.
1. Select **New**.
1. Select **Azure Event Grid**.
1. Select **Next**.
1. Enter the required parameter values.
1. Select **OK**.

## Procedure 5: Consume a business event

The business scenario involves sending an email message whenever a free text invoice is posted for the USMF company. The message must contain details such as the customer account number, the customer name, and the total amount of the invoice.

1. Select the business event catalog and look for the **free text invoice posted** business event.
1. Activate the business event for the USMF company. Once activated, a test message is sent to validate the configuration and cache the connection.
1. To verify that the test message is received, in the Azure portal, select your Event Grid topic, and then select **Metrics**. Verify that both the **Published Events** metric and the **Unmatched Events** metric show a value of at least **1**. If they don't, wait for the batch job to pick up your message.

    When both metrics have a value of at least **1**, you create a new logic app to subscribe to your Event Grid topic.

1. Select **All services \> Integration \> Logic Apps**.
1. Create a new logic app in your resource group.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-10.png" alt-text="Screenshot of New logic apps.":::

1. After your logic app resource is created, select the option to create a blank logic app.
1. Search for **Event Grid**, and select the **When a resource event occurs (preview)** trigger.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-11.png" alt-text="Screenshot of Event Grid trigger.":::

1. Select your subscription, select **Microsoft.EventGrid.Topics** as the resource type, and select the name of the Event Grid topic that you created in procedure 1.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-12.png" alt-text="Screenshot of Event Grid trigger parameters.":::

1. Select **New Step** to add a new action.
1. Search for the **Parse Json** data operation. This step is required so that the message can be parsed by using the provided schema for the data contract.
1. In the **Content** field of the **Parse Json** action, select the **Data object** field of the Event Grid message that contains the payload transmitted by finance and operations.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-14.png" alt-text="Screenshot of Logic apps parse JSON.":::

    Next, enter the provided schema for the contract. This schema is only a sample payload. However, you can use a capability of Azure Logic Apps to generate a schema from a payload.

1. Select your event in the business event catalog, and then select the **Download schema** link. A text file is downloaded. Open the text file, and copy the contents.
1. Go back to Logic Apps, and select the **Use sample payload to generate schema** link. Paste the contents of the text file, and then select **Done**.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-16.png" alt-text="Screenshot of Event schema.":::

1. Depending on the quality of your sample payload, your generator might not be able to distinguish between an integer and a real value, especially if the real value is provided as a whole number in the sample payload. Review the schema that is generated, and determine whether you must change a field of the **integer** data type to the **number** data type. In JavaScript Object Notation (JSON), the **number** data type represents real values.

    :::image type="content" source="../../media/BEF-Howto-EventGrid-17.png" alt-text="Screenshot of JSON data types.":::

    Next, select a final action, such as sending a notification email that includes customer payment details.

1. Search for the **send email** action, and then sign in to your Microsoft 365 account.
1. Fill in the message with the required fields.
1. Save your logic app.
1. Trigger the business event by posting a customer payment. Then verify that the logic app runs, and that you receive an email that includes customer payment details.


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
