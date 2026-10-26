---
title: Change fleet item master data (preview)
description: Learn how to use the Setup changes actions to correct a fleet item's model, physical status, details, fleet type, and note.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: FLMFleetItemTable, FLMFleetItemChangePhysicalStatus
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Change fleet item master data (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

After a fleet item exists, you correct it through dedicated change actions rather than by editing the record directly. Those actions sit together in the **Setup changes** group on the Action Pane of the fleet item master, so you see all of them side by side. They look alike, but they aren't alike. One only rewrites a note, and another changes the physical status of every fleet item attached to the selected fleet item. Use this article to decide which change a fleet item's current state allows, and what else the change touches.

## Change a fleet item

Every change action follows the same pattern, regardless of which value you change.

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items**, and select a fleet item.
1. On the Action Pane, on the **Setup** tab, in the **Setup changes** group, select the change that you want.
1. Complete the fields in the dialog, and then select **OK**.

Each dialog writes immediately, except that **Serial number update** can create a transfer journal that you post yourself. There's no approval step and no undo.

> [!IMPORTANT]
> Before you make a change, note which changes can't be reversed:
>
> - **Change model** with **Change description** turned on replaces the fleet item name in *every* language, not only in your own.
> - **Change physical status** applies to every fleet item attached to the fleet item that you selected, not only to that fleet item.
> - **Update Not for sale** applies to every row that you marked, not only to the active row.

## Available changes and their effects

The following table lists each change action, when you can use it, and what it affects beyond the fleet item record itself.

| Action | When you can use it | What it changes beyond the fleet item record |
|---|---|---|
| **Change model** | Any time. A model is required. | Points the fleet item at another model and takes the **Not for sale** setting from it. With **Change description**, it also replaces the fleet item name in every language. |
| **Change physical status** | When the fleet item is *Available* or *Not available* and *In stock*, *Not available*, or *On hold*, or is on a *Rental*, *Lease*, or *No-charge* agreement and *In stock*, *Not available*, *On hold*, or *On job site*; always in the *Customer* fleet, and never for a bulk fleet item or in the *Canceled* fleet. A reason code is mandatory, and the new status can't be *None*. Only statuses that suit the current fleet type, agreement status, and physical status are offered. | Adjusts the agreement status and the availability status, and applies the same change to every attached fleet item. |
| **Change fleet item details** | Any time. No status check. | Nothing else. It writes the fleet item name for your language and the **Attachment** classification. |
| **Serial number update** | The fleet item must be serial tracked and received into inventory. The **Fleet item status** parameter, in the **Serial number update** group on the **Fleet items** tab of the rental parameters, sets how far: *Financial received* also requires the receipt to be invoiced, and *Financial and physical received* accepts a posted product receipt. The new serial number must be free, or you can select **Deactivate previous fleet item** to release it from fleet items in the *Customer* or *Canceled* fleet. | For the *Customer* and *Canceled* fleets, the inventory dimension is updated directly. For other fleet types, an unposted inventory transfer journal is created from the **Serial number update journal** on the **Rental parameters** page, which you must review and post. |
| **Change fleet type** | Only when the fleet item is in the *Canceled* fleet. For any other fleet type, the button is unavailable. The fleet item must have a **Customer**. | Moves the fleet item into the *Customer* fleet. |
| **Update location** | Only when the fleet item is *Available* and *In stock*, and no receipt for it is waiting to be invoiced. Requires the **Location update** journal name on the **Rental parameters** page and the **Location** dimension active in the product's storage dimension group. | Posts an inventory transfer journal within the same warehouse. The fleet item's address doesn't change. |
| **Change note** | Any time. A blank entry clears the note. | Stamps who last changed the note, and when. |
| **Update Not for sale** | Any time, on one or several selected fleet items. | Sets or clears the flag that blocks the fleet items from sales quotation lines and sales order lines. |

For a bulk fleet item, only **Change fleet item details**, **Change note**, and **Update Not for sale** are available.

## Descriptive changes

**Change model** re-points a fleet item at the correct model, for example, after the wrong model was selected at creation. The fleet item inherits **Not for sale** from the new model.

**Change fleet item details** covers what's easiest to get wrong at creation: the fleet item name, and whether the fleet item is an attachment such as a bucket or a set of forks. **Change note** replaces the free-text note and records who changed it and when.

## Changes that affect availability and physical state

**Change physical status** is the manual override for a status that posting normally sets. The reason code is mandatory, and the code that you select can hide the fleet item from the fleet item availability list. Setting *Not available* also sets the agreement status to *Not available* for fleet types other than *Customer*, and setting *In stock* restores a *Not available* agreement status to *Available*. Every attached fleet item receives the same physical status, reason code, and agreement status, so holding a fleet item also holds its attachments.

**Update location** moves a fleet item between locations inside its current warehouse and posts an inventory transfer journal. To re-bin several fleet items at once, use **Update location** on **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability** instead. That version accepts only *Available*, *In stock* fleet items in one warehouse. Learn more in [Configure inventory and location settings for rental management](configure-inventory-location-settings.md).

**Change fleet type** is the only way to bring a fleet item out of the *Canceled* fleet, for example, after a purchase order line was canceled by mistake. The target is always the *Customer* fleet, so the fleet item must have a customer.

## Changes that have accounting consequences

**Change rental amortization percentage** isn't in the **Setup changes** group. You find it on the **Functions** tab, in the **Fixed asset** group, and only when the fleet item's fixed asset has an open book in the current posting layer whose depreciation profile uses the *Revenue based* method. It sets a revenue-based depreciation percentage for that one fleet item, which changes the depreciation that posts with every future rental invoice for it. Enter a value between 0 and 100. Entering 0 deletes the fleet item specific percentage, so depreciation falls back to the depreciation profile. Learn more in [Understand rental management financial integration](understand-rental-financial-integration.md).

**Transfer ownership** also sits on the **Functions** tab, in the **Ownership** group, and it changes who owns a fleet item. It's available for a fleet item whose fleet type uses the *Customer* or *Manual* value tracking method, and not for a bulk fleet item. You enter the **To prospect account**, and the fleet item moves to that prospect and to the prospect's customer account, or to no customer account when the prospect has none. Nothing is posted. Learn more about prospects and the customer accounts behind them in [Manage customer and prospect records for rental](manage-customer-prospect-records.md).

**Update Not for sale** posts nothing, but it decides whether you can sell a fleet item. You can't add a fleet item marked as not for sale to a sales quotation or sales order line, whatever its agreement status and fleet type are.

## Related information

- [Manage fleet item master data](manage-equipment-master-data.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Configure inventory and location settings for rental management](configure-inventory-location-settings.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
