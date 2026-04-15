---
title: Business events and Microsoft Power Automate
description: This article provides information about the business events that are available for consumption in Microsoft Power Automate using the connector.
author: Sunil-Garg
ms.author: sunilg
ms.topic: upgrade-and-migration-article
ms.date: 04/08/2026
# ms.custom: [used by loc for topics migrated from the wiki]
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global for most topics. Set Country/Region name for localizations 
ms.search.validFrom: Platform update 27
# ms.search.form:  [Operations AOT form name to tie this article to]
ms.dyn365.ops.version: 2019-6-30 

---

# Business events and Microsoft Power Automate

[!include[banner](../../includes/banner.md)]

This article explains how to configure and consume a business event from a Microsoft Power Automate endpoint by using the **When a Business Event occurs** trigger of the finance and operations connector.

This article shows how to perform the following tasks:

- Create a new flow in Power Automate.
- Trigger a business event.

The steps in this article show how to use the finance and operations connector. However, you can also apply these steps to the process of creating flows in Power Automate for finance and operations apps business events and data events in the Microsoft Dataverse connector. For more information about finance and operations apps business events and data events that have the **When an action is performed** and **When a row is added, modified, or deleted** triggers in the Dataverse connector, see [Business events in Microsoft Power Automate](../business-events-flow.md).

## Create a new flow in Power Automate

1. Sign in to Power Automate portal.

1. Select an existing environment where you have the permissions needed to create a Power Automate resource. The default environment is open to all companies.

1. Select **New \> Create from blank**.

1. Search for **Dynamics 365 Finance** and select the connector.

1. You see a trigger named **When a Business Event occurs**. Select this trigger.

1. Select your environment instance, category, event name, and legal entity.
    > [!TIP]
    > Take advantage of the auto-complete that Power Automate provides by entering only part of the environment instance URL or part of the event name.

    :::image type="content" source="../../media/BEF-Howto-Flow-04.png" alt-text="Screenshot of Microsoft Power Automate business event trigger.":::

1. Select the **New Step** button to add a new action.

1. Search for the **Parse JSON** data operation. This step is needed to parse the message with the schema of the data contract.

    :::image type="content" source="../../media/BEF-Howto-Flow-06.png" alt-text="Screenshot of Parse JSON action.":::

1. Select the content field of **Parse Json** action, then the **Body** output from the previous step appears as an option. Select **Body**.

    :::image type="content" source="../../media/BEF-Howto-Flow-07.png" alt-text="Screenshot of Parse JSON input.":::

1. Enter the schema of the contract. Because the app provides only a sample payload, you can use the Power Automate capability to generate a schema from a payload. Select an event in the catalog (for example, Customer Payment) and select the **Download schema** link. This action downloads a text file. Open the text file and copy the content.

    :::image type="content" source="../../media/BEF-Howto-Flow-08.png" alt-text="Screenshot of event payload.":::

1. Go back to Power Automate and select the **Use sample payload to generate schema** link. Paste your text file content and select **Done**.

    :::image type="content" source="../../media/BEF-Howto-Flow-09.png" alt-text="Screenshot of Parse JSON schema input.":::

1. Depending on the quality of your sample payload, the generator might not be able to distinguish between an integer and a real number. This distinction isn't clear if the real number is provided as a whole number in the sample payload. Review your generated schema and check if you need to change an "integer" into "number". In JSON, a "number" data type means real number.

    :::image type="content" source="../../media/BEF-Howto-Flow-10.png" alt-text="Screenshot of JSON data types.":::

1. Choose another final action to consume the business event content. For instance, you can send an email (or post a text message to Teams) to notify the customer about payment details. Search for the **Send email** action, and then sign in to your Microsoft 365 account.

1. Fill in the message with the required fields.

     :::image type="content" source="../../media/BEF-Howto-Flow-12.png" alt-text="Screenshot of Microsoft Power Automate send email action.":::

1. Save the flow.

## Trigger a business event

Power Automate can automatically configure the application for you. After you save your flow, it creates an endpoint, then it activates the business event. There's no remaining configuration step apart from verifying that the endpoint is correctly configured before triggering an event.

1. Sign in to the client.

1. Go to **System Administration \> Setup \> Business Events**.

1. Select **Endpoints**.

1. Verify that a new endpoint is created with a GUID appended in the name.

    :::image type="content" source="../../media/BEF-Howto-Flow-13.png" alt-text="Screenshot of Microsoft Power Automate business event GUID.":::

1. If you check the **Active events** tab, you can also verify that **Payment Posted** is activated for legal entity GBSI.

    :::image type="content" source="../../media/BEF-Howto-Flow-14.png" alt-text="Screenshot of active business events.":::

1. The final step is to trigger the business event of a posted customer payment and check whether the flow runs and you receive an email with customer payment details.

## Troubleshooting a flow

Here are some troubleshooting suggestions:

- Power Automate provides a full history of runs to help determine what might be wrong with a failing flow.
- When reviewing a failed run, carefully review the inputs and outputs of trigger and action blocks.
- After you make changes to the flow, go to the latest run or a particular run, and select **Resubmit** the inputs to run the flow again.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
