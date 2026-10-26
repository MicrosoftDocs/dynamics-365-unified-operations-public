---
title: Manage fleet item swaps, substitutions, and transfers (preview)
description: Learn how to swap fleet items before and during a rental, substitute different-sized fleet items, and transfer fleet items between locations.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage fleet item swaps, substitutions, and transfers (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

During the life of a rental contract, you might need to change or replace fleet items, or move them between locations. Rental management supports several scenarios for managing these changes, including pre-shipment swaps, on-site swaps, substitutions, and transfers.

## Swap a fleet item before shipping

A pre-shipment swap occurs when you change a fleet item *before* it ships to the customer. This change is common when the originally reserved fleet item becomes unavailable (for example, it needs service) and you assign an equivalent fleet item instead.

To swap a fleet item before shipping, follow these steps:

1. Open the rental contract.
1. Select the contract line with the fleet item you want to swap.
1. Select **Swap** under **Fleet item**.
1. Select the replacement fleet item. The lookup isn't limited to the same rental class. The replacement's service status must be something other than *Hard down*.
1. Check **Date**, which is today by default, and optionally select a **Swap reason code**. Select **Move attachments** if the attachments should move to the new fleet item, and then select **OK**.

The system checks rental class conformity separately, through the **Check on swap** rental parameter. When that parameter is set to *Hold*, the swap goes through, the mismatch is recorded as a rental class exception, and the whole contract is put on hold with the reason *Fleet item/class mismatch*.

A pre-shipment swap is transparent to the customer—the contract terms, rates, and dates remain the same. Only the specific serial number changes. The system records every swap in **Swap history**, which you open from the **Inquiries** tab of the contract.

## Swap a fleet item on site

An on-site swap (also called a fleet item exchange) occurs when you replace a fleet item *while the customer is using it*. This swap is common when a fleet item breaks down and the customer needs a working replacement delivered immediately.

An on-site swap involves two fleet item movements:

- An *inbound fleet item movement* to pick up the original fleet item from the job site.
- An *outbound fleet item movement* to deliver the replacement fleet item to the job site.

You can create the fleet item movements manually, or set **Fleet item movement automation on swap** on the rental template to *Create* or *Create then schedule*. On an active contract, the swap dialog includes a check box, selected by default, that creates both fleet item movements. This option is available only when the latest fleet item movement for the original fleet item is a completed outbound one.

> [!NOTE]
> During an on-site swap, rental charges continue to accrue. The swap itself is a single transaction on the contract. The system closes the original fleet item on the contract line effective the day before the **Date** that you enter in the swap dialog, and adds the replacement to the same line effective the swap date. Delivery of the replacement isn't what moves it. The swap date can't be earlier than today, and it can't be later than the invoice-until date on the line.

Before you swap, post or delete every invoice schedule that isn't invoiced for the contract line, for an attachment linked to it, or for a charge line under it. The same requirement applies when you remove a fleet item from a line. Learn more in [Call off and close rental contracts](call-off-close-rental-contracts.md#remove-a-fleet-item-from-a-contract-line).

## Substitute a fleet item at a different rate

A swap changes which fleet item the customer gets. A substitution changes what the customer is renting: **Substitute** replaces the *rental class* on a line, and the system reprices the line for the new rental class. For example, a customer ordered a 19-foot scissor lift, but you can only offer a 26-foot lift.

**Substitute** is available on an active main line that came from a rental template line. On a contract, it's available only while the contract status is *Created* or *Approved*. After the contract is active, use a swap instead. On a quotation, it's available until the quotation is *Confirmed*, *Lost*, or *Canceled*.

To create a substitution, follow these steps:

1. Open the rental quotation or contract.
1. Select the main line that you want to substitute.
1. Select **Substitute**.
1. In **Select the new rental class**, select the **Rental class** that replaces the current one. You can select any rental class, but it must be different from the current one.
1. Select **OK**.

When you select **OK**, the system does the following:

- It records the substitution as a rental class exception, with the original rental class, the new rental class, and the reason *Substitute*. To review the exceptions, go to **Rental management (Preview)** > **Inquiries and reports** > **History** > **Rental class exceptions**.
- It changes the rental class on the line.
- It reprices the line for the new rental class, looking up rates and discounts again. When no rate exists for the new rental class, the line takes the amount from the rental template line.
- It updates the item sales tax group on the line.
- If **Hold on substitute** is enabled in rental parameters, it puts the quotation or contract on hold with the reason *Substitution*, so that someone reviews the change. To release a contract from hold, approve it.

Substitute doesn't change the fleet item on the line. A fleet item that's already assigned stays on the line even if it doesn't belong to the new rental class, and the rental class check at activation (**Check on active**) can then report a mismatch. Assign a fleet item from the new rental class after you substitute.

Because the line is repriced, the customer pays the rate for the new rental class by default. Use that when the customer agrees to pay for the larger fleet item. To provide the larger fleet item at the originally contracted rate as a goodwill gesture, change the price on the line after the substitution. The system checks a price reduction against the rate override limits, and it can put the document on hold. Learn more in [Set up rate override limits](set-up-rental-rates-discounts.md#set-up-rate-override-limits).

## Transfer fleet items between your fleet locations

To move fleet items between your own fleet locations, create an internal fleet item movement from fleet item availability.

To transfer fleet items, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability**.
1. Select the fleet items to move. They must all be at the same fleet location, and their fleet types must use the *Fixed asset*, *Inventory*, or *Manual* value tracking method.
1. Select **Create fleet item movement**. **Direction** is set to *Internal*, and you can't change it.
1. Select **OK**. The system leaves out fleet items whose agreement status is *Not available*.
1. Open the fleet item movement, set the **To** fleet location and the **Estimated delivery/pickup date and time**, and then schedule, ship, and receive it.

Scheduling requires a transit location on the fleet location that the fleet items move from. Shipping puts the fleet items at that transit location, and receiving puts them at the destination fleet location. Learn more in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).

An internal fleet item movement changes the fleet item's fleet location, not the inventory location that the fleet item is stocked at. To change that, use **Update location** on the fleet item, which posts an inventory transfer journal. Learn more in [Change fleet item master data](change-fleet-item-master-data.md).

Moving a fleet item to a different fleet is a fleet transfer, not a fleet item movement. Learn more in [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
- [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md)
