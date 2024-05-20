---
title: Note integration
description: Learn about the integration of note data in dual-write, including an outline on creating a note in a customer engagement app.
author: RamaKrishnamoorthy
ms.author: ramasri
ms.topic: conceptual
ms.custom: 
  - bap-template
ms.date: 05/20/2024
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: global
ms.search.validFrom: 2020-01-06
---

# Note integration

[!include [banner](../../../finance/includes/banner.md)]

During business processes, Microsoft Dynamics 365 users often gather information about their customers. This information is recorded as activities and notes. This article describes the integration of note data in dual-write.

Customer information can be classified in the following ways:

+ **Actionable information that a Dynamics 365 user handles on behalf of a customer** – For example, Contoso (a Dynamics 365 user) is conducting a game show. One of Contoso's customers (a customer) wants to attend the game show. The customer asks a Contoso employee to book a slot in the game show for them. The booking occurs in Contoso's event attendee's calendar.
+ **Actionable information for a Dynamics 365 user** – For example, a customer who is purchasing a Surface unit enters special instructions that indicate that the device should be gift wrapped before delivery. These instructions are actionable information that should be handled by the Contoso employee who is responsible for packaging.
+ **Nonactionable information** – For example, a customer visits the Contoso store and, during their conversation with a store associate, expresses interest in *Halo* games and gaming accessories. The store associate makes a note of this information. The product recommendations engine then uses it to make recommendations to the customer.

In general, actionable information is captured as *activities* in finance and operations apps and customer engagement apps. Nonactionable information is captured as *notes* in finance and operations apps, and as *annotations* in customer engagement apps.

> [!TIP]
> Although notes are intended for nonactionable information, the apps won't prevent you from using them to store and handle actionable information if you want to use them in that way.

Microsoft is currently releasing functionality for note integration. (Functionality for activity integration will release later.) Note integration is available for customers, vendors, sales orders, and purchase orders.

## Create a note in a customer engagement app

To create a note in a customer engagement app and then sync it to a finance and operations app, follow these steps.

1. In the customer engagement app, open the account record for a customer.
2. In the **Timeline** pane, select the plus sign (**+**), and then select **Note** to create a note.

    ![Creating a note in the customer engagement app.](../../dev-itpro/data-entities/dual-write/media/notes-ce-1.png)

3. Enter a title and description, and then select **Add note**.

    ![Entering a title and description.](../../dev-itpro/data-entities/dual-write/media/notes-ce-2.png)

    The new note is added to the customer timeline.

    ![New note on the customer timeline.](../../dev-itpro/data-entities/dual-write/media/notes-ce-3.png)

4. Sign in to the finance and operations app, and open the same customer record. Notice that the **Attachments** button (paperclip symbol) in the upper-right corner indicates that the record has an attachment.

    ![Notification about an attachment.](../../dev-itpro/data-entities/dual-write/media/notes-ce-4.png)

5. Select the **Attachments** button to open the **Attachments** page. You should find the note that you created in the customer engagement app.

    ![Note from the customer engagement app.](../../dev-itpro/data-entities/dual-write/media/notes-ce-5.png)

Any updates to the note are synced back and forth between the finance and operations app and the customer engagement app.

## Create a note in a finance and operations app

You can also create a note in a finance and operations app, and it will sync to a customer engagement app.

To create a note in a finance and operations app and then sync it to a customer engagement app, follow these steps.

1. In the finance and operations app, on the **Attachments** page, select **New** \> **Note**.

    ![Creating a note in the finance and operations app.](../../dev-itpro/data-entities/dual-write/media/notes-fo-1.png)

2. Enter a title and a brief set of instructions, and then select **Save**.

    ![Entering a title and instructions.](../../dev-itpro/data-entities/dual-write/media/notes-fo-2.png)

3. In the customer engagement app, update the record. You should find the new note on the timeline.

    ![New note on the timeline in the customer engagement app.](../../dev-itpro/data-entities/dual-write/media/notes-fo-3.png)

You can classify a note as either internal, or external.

- In the finance and operations app, on the **Attachments** page, open the note, and then, in the **Restriction** field, select **Internal** or **External**.

    ![Restriction field.](../../dev-itpro/data-entities/dual-write/media/notes-fo-4.png)

You can also create a URL.

1. In the finance and operations app, on the **Attachments** page, select **New** \> **URL**.
2. Enter a title and the URL.
3. In the **Restriction** field, select **Internal** or **External**.

    ![Creating a URL in the finance and operations app.](../../dev-itpro/data-entities/dual-write/media/notes-fo-5.png)

4. Select **Save**.

    Because customer engagement apps don't have a URL type, the URL is integrated with dual-write as a note.

    ![URL appearing as a note in the customer engagement app.](../../dev-itpro/data-entities/dual-write/media/notes-ce-6.png)

> [!NOTE]
> File attachments aren't supported.

## Templates

Note integration includes a collection of table maps that work together during data interaction, as shown in the following table.

> [!NOTE]
> These templates are compatible with live sync only, and currently do not support initial sync.

| Finance and operations app | Customer engagement app | Description |
|----------------------------|-------------------------|-------------|
| [Customer Attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#230) | Annotations | Businesses that use plain text and URLs to capture customer-specific information (for both organizations and persons). |
| [Vendor document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#231) | Annotations | Businesses that use plain text and URLs to capture vendor-specific information (for both organizations and persons). |
| [Sales order header document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#229) | Annotations | Businesses that use plain text and URLs to capture sales order–specific information. |
| [Purchase order header document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#232) | Annotations | Businesses that use plain text and URLs to capture purchase order–specific information. |

## Limitations

Once you install the notes solution, you can't uninstall it. 

For more information, see [Dual-write mapping reference](../../dev-itpro/data-entities/dual-write/mapping-reference.md).

