---
# required metadata

title: Consume business events with Microsoft Flow
description: This topics provides information about the business events that are available for consumption in Microsoft Flow via the Finance and Operations connector.
author: ibenbouzid
manager: AnnBe
ms.date: 07/02/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations, Core
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global for most topics. Set Country/Region name for localizations
# ms.search.industry: 
ms.author: imbenbou
ms.search.validFrom: Platform update 27
ms.dyn365.ops.version: 2019-6-30 

---

# Consume business events with Microsoft Flow

[!include[banner](../../includes/banner.md)]

This topic provides steps detailing how to configure and consume a Microsoft Dynamics 365 for Finance and Operations business event from a Microsoft Flow endpoint.

This topic shows how to perform the following tasks:

-   Create a new Microsoft Flow.
-   Trigger a business event.

## Create a new Microsoft Flow

1.  Sign in to Microsoft Flow portal.

2.  Select an existing environment where you have the permissions needed to create a flow resource. The default environment is open to all companies.

3.  Select **New \> Create from blank**.

4.  Search for **Dynamics 365 for Finance and Operations** and select the connector.
     
5.  You will notice a trigger for Finance and Operations named **When a Business Event occurs**. Select this trigger.

6.  Select your environment instance, category, event name, and legal entity.

    <img src="../../media/BEF-Howto-Flow-04.png" width="50%">

7.  Select the **New Step** button to add a new action.

8.  Search for the **Parse JSON** data operation. This step is needed to parse the message with the schema of the data contract provided by Finance and Operations.

    <img src="../../media/BEF-Howto-Flow-06.png" width="50%">

9.  Select the content field of **Parse Json** action, then the **Body** output from the previous step should appear as an option. Select **Body**.

    <img src="../../media/BEF-Howto-Flow-07.png" width="50%">

10. Enter the schema of the contract received from Finance and Operations. Because Finance and Operations provides only a sample payload you can use the Microsoft Flow capability to generate a schema from a payload. Go back to Finance and Operations, select an event in the catalog (for example, Customer Payment) and select the **Download schema** link. This will download a text file. Open the text file and copy the content.

    <img src="../../media/BEF-Howto-Flow-08.png" width="50%">

11. Go Back to Microsoft Flow and select the **Use sample payload to generate schema** link. Paste your text file content and select **Done**.

    <img src="../../media/BEF-Howto-Flow-09.png" width="70%">

12. Depending on the quality of your sample payload, your generator will not recognize an integer from a real number. This is true if the real number is provided as a whole number in the sample payload. Review your generated schema and check if you need to change an “integer” into “number”. (In JSON, a “number” data type means real number).

    <img src="../../media/BEF-Howto-Flow-10.png" width="100%">

13.  Choose another final action to consume the business event content. For instance, you can send an email (or post a text message to Teams) to notify the customer about payment details. Search for the **Send email** action, then sign in to your Office 365 account.

14.  Fill in the message with the required fields.

   <img src="../../media/BEF-Howto-Flow-12.png" width="70%">

15. Save Flow.

## Trigger a Business Event

Microsoft Flow can configure Finance and Operations automatically for you. After you save your Flow it creates an endpoint in Finance and Operations, then it activates the business event for you. There is no remaining configuration step in Finance and Operations apart from verifying that the endpoint has been correctly configured before triggering an event.

1. Sign in to the Finance and Operations client.

2.  Go to **System Administration \> Setup \> System Parameters**.

3.  Select the **Business events** tab.

4.  Select **Business events**.

5.  Click **Endpoints**.

6.  Verify that a new endpoint has been created with a GUID appended in the name.

    <img src="../../media/BEF-Howto-Flow-13.png" width="100%">

7.  If you check the **Active events** tab you can also verify that “**Payment Posted**” is activated for legal entity GBSI.

    <img src="../../media/BEF-Howto-Flow-14.png" width="100%">

8.  The final step is to trigger the business event of a posted customer payment and check whether the Flow runs and you receive an email with customer payment details.
