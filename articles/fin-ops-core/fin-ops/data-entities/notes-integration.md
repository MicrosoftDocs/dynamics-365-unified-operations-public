---
title: Note integration
description: Learn about the integration of note data in dual-write, including an outline on creating a note in a customer engagement app.
author: RamaKrishnamoorthy
ms.author: johnmichalak
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 01/21/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: global
ms.search.validFrom: 2020-01-06
---

# Note integration

[!include [banner](../../../finance/includes/banner.md)]

During business processes, Microsoft Dynamics 365 users often gather information about their customers. They record this information as activities and notes. This article describes the integration of note data in dual-write.

You can classify customer information in the following ways:

+ **Actionable information that a Dynamics 365 user handles on behalf of a customer** – For example, Contoso (a Dynamics 365 user) is conducting a game show. One of Contoso's customers (a customer) wants to attend the game show. The customer asks a Contoso employee to book a slot in the game show for them. The booking occurs in Contoso's event attendee's calendar.
+ **Actionable information for a Dynamics 365 user** – For example, a customer who is purchasing a Surface unit enters special instructions that indicate that the device should be gift wrapped before delivery. These instructions are actionable information that should be handled by the Contoso employee who is responsible for packaging.
+ **Nonactionable information** – For example, a customer visits the Contoso store and, during their conversation with a store associate, expresses interest in *Halo* games and gaming accessories. The store associate makes a note of this information. The product recommendations engine then uses it to make recommendations to the customer.

In general, you capture actionable information as *activities* in finance and operations apps and customer engagement apps. You capture nonactionable information as *notes* in finance and operations apps, and as *annotations* in customer engagement apps.

> [!TIP]
> Although you intend to use notes for nonactionable information, the apps don't prevent you from using them to store and handle actionable information if you want to use them in that way.

Microsoft is currently releasing functionality for note integration. Note integration is available for customers, vendors, sales orders, and purchase orders.

## Create a note in a customer engagement app

To create a note in a customer engagement app and then sync it to a finance and operations app, follow these steps:

1. In the customer engagement app, open the account record for a customer.
1. In the **Timeline** pane, select the plus sign (**+**), and then select **Note** to create a note.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-1.png" alt-text="Screenshot of creating a note in the customer engagement app.":::

1. Enter a title and description, and then select **Add note**.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-2.png" alt-text="Screenshot of entering a title and description for a note.":::

    The new note is added to the customer timeline.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-3.png" alt-text="Screenshot of new note on the customer timeline.":::

1. Sign in to the finance and operations app, and open the same customer record. Notice that the **Attachments** button (paperclip symbol) in the upper-right corner indicates that the record has an attachment.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-4.png" alt-text="Screenshot of notification about an attachment.":::

1. Select the **Attachments** button to open the **Attachments** page. You should find the note that you created in the customer engagement app.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-5.png" alt-text="Screenshot of note from the customer engagement app.":::

Any updates to the note sync back and forth between the finance and operations app and the customer engagement app.

## Create a note in a finance and operations app

You can also create a note in a finance and operations app, and it syncs to a customer engagement app.

To create a note in a finance and operations app and then sync it to a customer engagement app, follow these steps:

1. In the finance and operations app, on the **Attachments** page, select **New** \> **Note**.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-fo-1.png" alt-text="Screenshot of creating a note in the finance and operations app.":::

1. Enter a title and a brief set of instructions, and then select **Save**.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-fo-2.png" alt-text="Screenshot of entering a title and instructions.":::

1. In the customer engagement app, update the record. You should find the new note on the timeline.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-fo-3.png" alt-text="Screenshot of new note on the timeline in the customer engagement app.":::

You can classify a note as either internal or external.

- In the finance and operations app, on the **Attachments** page, open the note. In the **Restriction** field, select **Internal** or **External**.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-fo-4.png" alt-text="Screenshot of Restriction field.":::

You can also create a URL.

1. In the finance and operations app, on the **Attachments** page, select **New** \> **URL**.
1. Enter a title and the URL.
1. In the **Restriction** field, select **Internal** or **External**.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-fo-5.png" alt-text="Screenshot of creating a URL in the finance and operations app.":::

1. Select **Save**.

    Because customer engagement apps don't have a URL type, dual-write integrates the URL as a note.

    :::image type="content" source="../../dev-itpro/data-entities/dual-write/media/notes-ce-6.png" alt-text="Screenshot of URL appearing as a note in the customer engagement app.":::

> [!NOTE]
> File attachments aren't supported.

## Templates

Note integration includes a collection of table maps that work together during data interaction, as shown in the following table.

> [!NOTE]
> These templates are compatible with live sync only, and currently don't support initial sync.

| Finance and operations app | Customer engagement app | Description |
|----------------------------|-------------------------|-------------|
| [Customer Attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#230) | Annotations | Businesses that use plain text and URLs to capture customer-specific information (for both organizations and persons). |
| [Vendor document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#231) | Annotations | Businesses that use plain text and URLs to capture vendor-specific information (for both organizations and persons). |
| [Sales order header document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#229) | Annotations | Businesses that use plain text and URLs to capture sales order–specific information. |
| [Purchase order header document attachments](../../dev-itpro/data-entities/dual-write/mapping-reference.md#232) | Annotations | Businesses that use plain text and URLs to capture purchase order–specific information. |

## Limitations

You can't uninstall the notes solution after you install it. 

For more information, see [Dual-write mapping reference](../../dev-itpro/data-entities/dual-write/mapping-reference.md).

