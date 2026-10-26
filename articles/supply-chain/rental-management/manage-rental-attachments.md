---
title: Manage attachments and bulk fleet items (preview)
description: Learn how to pair attachments to fleet items, add attachment and bulk fleet item lines to rental documents, and set up validity rules.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: FLMFleetItemAttachmentBuilder, RentalAttachmentBuilder, RentalAttachmentRule, RentalClassAttachmentSuggestion, RentalClassBulkFleetItemSuggestion
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Manage attachments and bulk fleet items (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

An attachment is a fleet item, such as a bucket or a breaker, that operates attached to a prime fleet item. A bulk fleet item is a non-serialized fleet item, such as a hose, a cable, or a strainer, that you rent by quantity rather than by serial number.

**Attachment handling** opens a different **Attachment builder** depending on where you start. From a fleet item, it pairs the attachment to a prime fleet item. From a rental document line, it creates the line that bills the attachment.

## Choose the right Attachment builder

The following table compares the two builders, so that you can tell which one you need.

| | Attachment builder on the fleet item | Attachment builder on the rental line |
|---|---|---|
| **Where you start** | A fleet item record | A line on a rental contract or quotation |
| **What it changes** | The **Attached to** value on the attachment fleet item, permanently and for every future rental | A child document line under the prime line, so the attachment is priced and billed on this document |
| **What constrains it** | Attachment validity rules, when **Attachment validation** is selected, and rental contracts: a fleet item that's on a rental contract is changed on that contract instead | Document and line status, and a revenue split that totals 100 |
| **Use it when** | You pair a fleet item before shipping | The customer needs the attachment on this rental |

## Pair an attachment to a prime fleet item

Pairing sets the **Attached to** value on the attachment fleet item, so the attachment stays with the prime fleet item on every future rental.

> [!TIP]
> Use fleet-item pairing primarily when attaching or removing an attachment requires significant effort. For quick-coupler attachments that you can easily remove, usually keep the fleet items unpaired and add the attachment as a billable rental line instead.

To pair an attachment to a prime fleet item, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items**, and select the prime fleet item.
1. On the Action Pane, in the **Builder** group, select **Attachment handling**.
1. Select **Attachment validation** to enforce attachment validity rules while you work. The **Default attachment validation** parameter sets the check box, and you can clear it for this session.
1. On the **Attachments** tab, drag an attachment onto the prime fleet item in the tree, or select the attachment and select **Add**. Select **Save** to apply the change.
1. If active reservations or linked quotations reference the fleet item, the **Update attachment on rental reservation and quotation** rental parameter decides whether they're updated: *Never*, *Prompt* (you confirm the change), or *Always*. A fleet item that's part of a package on a quotation isn't updated, so adjust that quotation manually.

The system logs every connection and disconnection in **Attachment history** on the fleet item. Learn more in [Manage fleet item master data](manage-equipment-master-data.md).

## Add an attachment as a billable line

When a customer needs an attachment for one rental only, add it to the rental document instead of pairing it to the fleet item.

1. Open a rental contract or a rental quotation.
1. Select the line that carries the prime fleet item.
1. On the **Contract line** FastTab (**Quotation line** on a quotation), select **Fleet item** > **Attachment handling**. The button is available while a contract is *Created* or *Approved*, and while a quotation is *Created*, *Sent*, or *Won*. The line status must be *Active*.
1. Add the attachment to the prime line. The system creates a child line and links it to the prime line, so the attachment is priced, invoiced, and shipped with its parent.
1. Set **Date** to the date the attachment is registered as swapped or removed.
1. Set **Update attached to** if the physical pairing changes too. When it's enabled, the **Attached to** value on the attachment fleet item is updated, so the master record changes with the document. When it's disabled, only the document changes.
1. Check the revenue percentages before you close the form. They must total 100, and each percentage is that fleet item's share of the amount invoiced for the line. Learn more in [Invoice rental contracts](invoice-rental-contracts.md#handle-revenue-split-for-the-prime-fleet-item-and-attachments).

Bulk fleet items are always separate document lines with a quantity. Learn more in [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md#add-bulk-fleet-items-to-a-contract).

## Set up validity rules and suggestions

Three setup pages sit under **Rental management (Preview)** > **Setup** > **Validity rules and suggestions**.

- **Attachment validity rules** define which attachments can be connected to which prime fleet items. A rule pairs a **Model** or a **Group code** on the prime side with an **Attachment model** or an **Attachment group code** on the attachment side, so one group-to-group rule can replace a cross product of models. Rules work on models and group codes, not on rental classes. Select a model or group, then move entries between **Attachable models** and **Not attachable models**, or between **Attachable groups** and **Not attachable groups**. Set **Suggested for rental** on the rules that should also drive the suggestion indicator on a document line. The page is also reachable from a fleet item model and from a fleet item group code.
- **Suggested attachments by class** records which attachment rental classes belong with a prime rental class. Select the prime class, then move classes between **Attachments available** and **Attachments selected for class**.
- **Suggested bulk fleet items by class** follows the same pattern for bulk fleet items, by using **Available bulk fleet items** and **Selected bulk fleet items**. The available list shows the released products whose **Fleet item type** is *Bulk fleet item*.

## Act on suggestions on a quotation or contract line

The suggestions produce two indicator columns on the document lines, one for attachments and one for bulk fleet items. The indicators have the following meanings:

- A green check – At least one suggested fleet item is on the document.
- A yellow exclamation – Suggestions exist, but none of them is on the document yet.
- A red cross – There's nothing to suggest for the line.

After a fleet item is assigned to the line, the attachment indicator follows the attachment validity rules marked **Suggested for rental** instead of the class suggestions.

To create attachment lines from a suggestion, select the line, and then select **Suggested attachments**. Select the classes the customer needs in the dialog, and confirm. The system creates the child attachment lines automatically. The dialog opens while the line has no active fleet item. When a fleet item is already assigned, **Suggested attachments** opens **Fleet item availability** instead, filtered to the attachments that the validity rules marked **Suggested for rental** allow for that fleet item's model.

To add suggested bulk fleet items, select the line, and then select **Fleet item** > **Suggested bulk fleet items**. **Fleet item availability** opens with only the bulk fleet items that are suggested for the line's rental class. Mark the bulk fleet items, enter the **Quantity to add** for each, and then select **Add to contract line** or **Add to quotation line** to add them as lines under the selected line.

The **Notify user of suggested attachments and bulk fleet items** setting on the rental template decides whether a notification appears when you add a main line that has suggestions. Learn more in [The Rental template header FastTab](set-up-rental-templates.md#the-rental-template-header-fasttab).

## Related information

- [Manage fleet item master data](manage-equipment-master-data.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Reserve fleet items](reserve-rental-equipment.md)
- [Sell accessories and consumables](sell-accessories-consumables.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
