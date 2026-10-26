---
title: Ship and receive fleet items using fleet item movements (preview)
description: Learn how to use fleet item movements to ship fleet items to customers, receive returned fleet items, and track damage.
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

# Ship and receive fleet items using fleet item movements (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

A fleet item movement documents every physical movement of fleet items. When you post one, it updates the fleet item's fleet location and its physical and service statuses. The fleet item's inventory position and its fixed asset stay the same. Fleet item movements serve as the shipping and receiving paperwork for rental operations. They provide a complete history of fleet item condition, hours, and fuel at each movement point.

## Understand fleet item movement directions

Rental management uses four directions for fleet item movements:

- **Outbound** – Documents the shipment of fleet items from the fleet location to the customer's job site. The outbound fleet item movement typically captures the starting condition and hours.
- **Inbound** – Documents the return of fleet items. The inbound fleet item movement typically captures the ending condition, hours, and fuel level, and notes any damage that occurred during the rental.
- **Between job sites** – Documents the movement of fleet items between two customer job sites without returning to the fleet location.
- **Internal** – Documents the movement of fleet items between your own warehouses and fleet locations (for example, from branch A to branch B).

## Create an outbound fleet item movement

Typically, the system automatically creates fleet item movements when you activate a contract. The **Fleet item movement automation on contract activation** setting on the rental template controls this behavior. When it's enabled, activating a contract creates and schedules an outbound fleet item movement, unless one already exists. The rental coordinator can also manually create a fleet item movement. The operations staff then uses the fleet item movement as their checklist for preparing and loading the fleet item. <!-- They can also work it on a mobile device in the Dynamics 365 Supply Chain Management mobile app, which lists the fleet item movements that have the status *To be shipped*, *In transit*, or *To be picked*. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md). -->

To create an outbound fleet item movement manually, follow these steps:

1. Open the rental contract that contains the fleet item to ship.
1. Select **Create fleet item movement** on the Action Pane.
1. Make sure **Direction** is *Outbound*, select the fleet items to include in this shipment, and then select **OK**. You can ship all fleet items at once or ship them at different times. The system creates a separate fleet item movement for each pair of from and to locations.
1. Set the **Estimated delivery/pickup date and time** for the delivery.

### Schedule and ship the fleet item movement

A new fleet item movement has the status *Request*. Schedule it before the fleet items leave the fleet location, and then ship it.

1. Open the fleet item movement. On the Action Pane, in the **Posting** group, select **Schedule delivery/pickup** > **Schedule**.
1. Record the readings and complete the inspections, as described in the next section.
1. In the **Posting** group, select **Ship**.

Scheduling sets the status that the fleet item movement status setup defines for the direction and the *Schedule* action, such as *To be shipped* or *To be picked*. It applies the physical status and the service status from that row, generates the inspection checklist when checklists are enabled, and makes **Ship** the next step. Scheduling requires all of the following:

- A fleet item movement status setup row for the direction and the *Schedule* action.
- Every reading that the status setup row makes mandatory.
- Each fleet item on no other open fleet item movement.
- All of the fleet items in the same warehouse.
- Each fleet item in a fleet type that doesn't use the *Customer* value tracking method.
- A transit location on the fleet location that the fleet items move from. This requirement doesn't apply to a *Between job sites* fleet item movement. Learn more in [Configure inventory and location settings for rental management](configure-inventory-location-settings.md).

Shipping applies the same checks for the *Ship* action and sets the status from that row. It copies the **Service meter unit** and **Fuel level** readings to the fleet item on the contract line. It also makes **Receive** the next step when the setup defines one for the direction, and raises the action items that the row turns on.

A fleet item movement that's created automatically on contract activation is already scheduled, so it's ready to ship.

## Complete pre-shipment inspections

Before a fleet item leaves the fleet location, the operations staff must complete several inspection tasks on the outbound fleet item movement. <!-- The same tasks are available for each fleet item in the Dynamics 365 Supply Chain Management mobile app: the readings, the checklist, damage reports, and the service status. -->

Record pre-existing damage before the fleet item leaves. Learn more in [Document damage](#document-damage).

### Record hours and fuel

For a prime fleet item with a service meter, record the following readings before shipping. When you select **Service meter unit mandatory** or **Fuel mandatory** on the fleet item movement status setup row for the step, the reading is required before posting. This requirement applies to each fleet item that you ship or receive, unless its **Usage required** setting exempts it:

- **Service meter unit** – The current hour meter reading, with its **Capture date and time**. When you post the outbound fleet item movement, the system copies the reading to the fleet item on the contract line as **SMU when shipped out**, the baseline for measuring usage and overtime.
- **Fuel level** – The current fuel level. When you post the outbound fleet item movement, the system copies it to the fleet item on the contract line as **Start fuel**.

### Complete checklists

Fleet item models can include customizable checklists that operations staff must complete before shipping. Checklists help ensure that the fleet item is in proper working condition and that all required accessories are included.

Common checklist items include:

- Safety items present (fire extinguisher, warning lights, backup alarm)
- Fluid levels checked (oil, hydraulic, coolant)
- Tires or tracks inspected
- All attachments accounted for
- Fleet item cleaned and presentable

Complete the items on the **Checklist** tab of the line details. Each checklist item has one **Checked** check box and a free-text note. Record a problem in the note, or as a damage record, and then decide whether the fleet item can ship. A mandatory item that you don't check blocks posting until it's completed. You can check an item marked **Photo mandatory** only after you attach a JPG, JPEG, PNG, or HEIC image to it.

Set up checklist items for each fleet item model at **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item models** by selecting **Checklist items**, and make each item **Mandatory** or **Photo mandatory**. The system adds them to a fleet item movement when you schedule it, but only if you enable **Use checklist for shipping** or **Use checklist for receiving** on the **Fleet item movement** tab of rental parameters.

### Print inspection documents

Two documents are available on the Action Pane, in the **Print fleet item movement** group.

**Print fleet item movement** is available after the fleet item movement is scheduled. Use it as the delivery or pickup document. It carries the customer, the from and to addresses, the job site contact, and the note on the fleet item movement. For each fleet item, it carries the identification, the **Service meter unit**, **Secondary SMU**, and **Fuel level** readings, and the active damage that's recorded for it. It carries no checklist results, photos, or signature.

**Print inspection document** becomes available after the fleet item movement is completely shipped or received, and not for a canceled fleet item movement. Use it as the inspection record that the customer signs. It includes the customer and contact details, the from and to addresses, the actual delivery or pickup date and time, and who inspected the fleet items. For each fleet item, it includes the identification, the **Service meter unit** and **Fuel level** readings, and the checklist items with **Checked** and their notes. It also includes the photos that are attached to the checklist items and to the fleet item movement line<!--, including photos that are taken in the Dynamics 365 Supply Chain Management mobile app-->.

### Handle partial shipments

Sometimes, you can't ship all the fleet items on a fleet item movement at the same time. For example, all the fleet items on the rental contract don't fit in one shipment. In this situation, you can partially ship the fleet item movement.

To partially ship fleet items, select the lines that are ready, and then select **Partial ship**. The system does the following:

1. Ships the selected fleet items and updates their status.
1. Automatically creates a **new outbound fleet item movement** for the remaining fleet items.

You can process the companion fleet item movement later, when the remaining fleet items are ready.

## Use the fleet item movement scheduling view

The **Fleet item movement scheduling view** provides a real-time display of upcoming inbound and outbound fleet item movements, making it ideal for display on a monitor in the wash bay or shop area.

To access the scheduling view, go to **Rental management (Preview)** > **Common** > **Fleet item movements** > **Fleet item movement scheduling view**.

Operations staff use this view to:

- See what fleet items they need to prepare for outbound shipment and plan their prep work accordingly.
- Track inbound deliveries so they know when a fleet item is arriving and can prepare space at the fleet location.
- Filter by **Direction** and **Status**, or set **Scheduled filter** to *Scheduled* to show only fleet item movements that are requested, to be shipped, or to be picked.

## Receive fleet items with an inbound fleet item movement

Use an inbound fleet item movement to receive and inspect returned fleet items. A call-off can create the movement automatically. You can also create it manually from the rental contract: on the Action Pane, select **Create fleet item movement**, and set **Direction** to *Inbound*.

To receive fleet items with an inbound fleet item movement, follow these steps:

1. Open the inbound fleet item movement, and schedule it if it's still a request. You can configure the call-off to create and schedule the fleet item movement automatically in the rental template.
1. Record **Service meter unit** on each line. If you refuel the fleet item on return, enter the amount of fuel added in **Fuel level**.
1. Complete the return inspection checklist.
1. Document any new damage discovered during inspection. Compare with the outbound fleet item movement photos to distinguish pre-existing damage from new damage.
1. Select **Receive** to complete the inbound fleet item movement.

<!--
The operations staff can do the same on a mobile device in the Dynamics 365 Supply Chain Management mobile app, where an inbound fleet item movement that has the status *To be picked* or *In transit* offers **Receive**.
-->

When **Fuel calculation** or **Diesel calculation** is enabled on the contract and the rental template has a charge line with fee type *Fuel*, receiving creates a fuel charge. The system multiplies the amount added, recorded in **Fuel level**, by the contract's **Fuel price** or **Diesel price**, according to the fleet item model's fuel type. The rental template supplies the contract's default calculation settings and prices. A zero quantity or price doesn't create a fuel charge.

### Document damage

Document damage you find during return inspections on the inbound fleet item movement. Use the same procedure before shipment to record pre-existing damage on the outbound fleet item movement.

To document damage, follow these steps:

1. On the fleet item movement, go to the **Fleet item damages** tab in the line details section.
1. Select **New** to create a new damage record.
1. Select the required **Damage code** that classifies the damage, and optionally describe the damage and its location on the fleet item in **Note**.
1. Take a photo and attach it to the damage record. Photos provide evidence for comparing the fleet item's condition before and after the rental. <!-- In the Dynamics 365 Supply Chain Management mobile app, **Capture media** attaches photos or videos to the damage record. -->

> [!TIP]
> Always photograph pre-existing damage on outbound fleet item movements. When the fleet item comes back, you can compare the outbound and inbound photos to determine whether any new damage occurred during the rental.

### Follow up on damage

Each damage record stays active until you mark it as repaired. Use damage history to assign the follow-up work, record responsibility, and track repair charges.

To follow a damage record through to resolution, follow these steps:

1. Go to **Rental management (Preview)** > **Inquiries and reports** > **All damage history**.
1. Select the damage record and update the following fields as the case progresses:
    - **Assigned to** – Select the worker who follows up on the damage.
    - **Responsible customer / vendor** and **Responsible agreement** – Review who's responsible for the damage. Both default from the movement on which you recorded the damage. To attribute it to an earlier rental, select that rental's movement in **Responsible fleet item movement**.
    - **Damage decision** and **Recovery status** – Select the codes that describe your decision and the progress of cost recovery. Learn more about configuring these codes in [Set up reason codes](set-up-rental-reference-data.md#set-up-reason-codes).
    - **Customer responsibility** – Enter the part of the repair charge that the customer agreed to pay.
    - **Damage invoiced on** – Select the invoice that bills the damage.
    - **Damage invoiced amount** – Review the amount in accounting currency. Selecting an invoice fills this field from the invoice total. Update it manually if needed.

1. If the service team needs to inspect the fleet item and estimate the repair, select **Create work order request** on the Action Pane. Learn more in [Create a work order request](rental-management-overview.md#create-a-work-order-request).
1. When the repair is complete, select **Mark as repaired** on the Action Pane. The damage status changes to *Repaired*, and **Repaired on** records the date and time.
1. If more work is needed, select **Reopen damage** on the Action Pane. The status returns to *Active*, and the system clears **Repaired on**.
1. Save your changes.

### Handle partial receives

Sometimes, not all fleet items on a contract are returned at the same time. For example, a customer might return the prime fleet item but keep an attachment for a few more days.

To partially receive fleet items, select the lines that are being returned, and then select **Partial receive**. **Partial receive** is available only when the fleet item movement status setup has no *Ship* action for the fleet item movement's direction. The system does the following:

1. Receives the selected fleet items and updates their status.
1. Automatically creates a **new inbound fleet item movement** for the remaining fleet items.

When those remaining fleet items eventually return, the operations staff processes the companion fleet item movement to complete the receive.

> [!TIP]
> The partial receive process mirrors the partial ship process. In both cases, the system automatically creates a companion fleet item movement for the remaining fleet items, so nothing gets lost in the process.

## Resolve action items created by posting a fleet item movement

Shipping or receiving a fleet item can raise issues that you can't resolve immediately, such as damage found at handover, an unavailable customer signature, or a site that the driver couldn't access. Posting creates a *fleet item movement action item* for each issue: a follow-up task with an assigned owner and a status, so that you can track the issue to completion.

### Understand the four action item types

When you ship or receive, the system reads the fleet item movement status setup row for that direction and action, and raises only the types turned on for the row.

| Action item type | When it's raised |
|---|---|
| **Damaged** | One action item for each damage record already captured on the fleet item movement. If no damage was recorded, no action item is created. |
| **Delivery issue** | When **Delivery issue** is selected on the **Other** tab of the fleet item movement, for example for a wrong address, no site access, or a refused delivery. |
| **Customer signature unavailable** | When **Signature not available** is selected on the **Other** tab of the fleet item movement. |
| **Modify rent return** | Inbound fleet item movements only. The meter moved by no more than the **Modify rent return limit** in rental parameters, so a quick turn might be enough. |

<!--
> [!NOTE]
> In the public preview, the Dynamics 365 Supply Chain Management mobile app doesn't trigger **Delivery issue** or **Customer signature unavailable** action items. Record these conditions on the **Other** tab of the fleet item movement in Supply Chain Management.
-->

> [!NOTE]
> Record delivery issues and unavailable customer signatures on the **Other** tab of the fleet item movement in Supply Chain Management.

Each action item carries its type, a status of *Open* or *Resolved*, an assigned worker, a description, and links back to the fleet item movement and the fleet item.

### Find and close an action item

The **Rental management (Preview)** > **Common** > **Fleet item movement action items** node in the navigation pane includes three list pages:

- **All fleet item movement action items** – Every action item, open and resolved.
- **Fleet item movement action items** – Only the items that are still open. This is the team's working queue.
- **My fleet item movement action items** – Only the items assigned to you.

The **Fleet item movement action items workspace (Preview)**, at **Rental management (Preview)** > **Workspaces**, presents the same queue as counted tiles and lists, broken down by type and by whether items are open or assigned to you. It also links to the fleet item movement list, the scheduling view, the attachment replacement log, and fleet item availability.

To close an action item, follow these steps:

1. Open the action item from a list page or from the workspace.
1. Record what you found in the description. An action item can be edited only while it's open.
1. If the work belongs to another team, select **Reassign** and choose the worker who owns it.
1. Select **Resolve**. The status changes to *Resolved*, and the system stamps who resolved the item and when.

### Choose which action items to raise

Configure action items for each combination of direction and action at **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Fleet item movement status setup**. Each row turns the four types on or off, so an inbound receive can raise damage and quick-return items while an outbound ship raises only signature and delivery issue items. Each flag routes information that's already on the fleet item movement into a work queue.

### Classify the reason for a fleet item movement

A fleet item movement reason code records why a movement exists, so you can separate customer deliveries from contract activation, call-off, and swap movements in your reporting. Maintain the codes at **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Fleet item movement reason codes**. The system stamps the code on the fleet item movement automatically from the rental template, which holds four defaults: a general one, and one each for contract activation, call-off, and swap.

### Trace a posting, and unlock a blocked fleet item movement

Every posting writes a read-only journal row that records the fleet item movement, the status it moved to, and who posted it when. Open the journal from the fleet item movement, from the scheduling view, or at **Rental management (Preview)** > **Inquiries and reports** > **Fleet item movement journals**. Use it when a customer queries when a fleet item was shipped or returned.

A fleet item movement is locked while it's being posted, and the lock is released when the posting finishes. If an interrupted posting leaves it locked, the posting buttons stay unavailable for other users. Select **Unlock** on the Action Pane to release it. **Unlock** doesn't change a fleet item movement whose posting is still in progress.

## Handle modify rent returns (MRR)

A modify rent return (MRR) is an action item that flags fleet items returning from a short-term rental for potential quick-turn processing. When a fleet item returns after a brief period (for example, a weekend rental with only 8 hours of use), the system can automatically create an MRR record. The record alerts the service department or operations staff that a full service inspection might not be necessary.

Instead of the standard return-to-service workflow, the operations staff can perform a return-to-ready inspection and quickly move the fleet item back to *Ready* status, making it available for the next customer faster.

Inbound fleet item movement statuses trigger MRR action items. To enable MRR, configure the following:

1. Go to **Rental management (Preview)** > **Setup** > **Rental parameters** and on the **Fleet items** tab, on the **Fleet item movement** tab, specify the **Modify rent return limit**.
1. Go to **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Fleet item movement status setup**, select the row with **Direction** *Inbound* and **Action** *Receive*, and on the **Action items** tab, select **Modify rent return**.

You can monitor MRR actions in the **Fleet item movement action items workspace (Preview)**.

## Reviewing overtime approvals and meter readings

On fleet items that you bill by the hour, the meter reading you capture on a fleet item movement sets two values: the hours the customer owes over the allowance, and the asset life that usage-based depreciation consumes. An inaccurate reading affects customer billing and asset depreciation.

When usage exceeds the allowance on a contract line, the system creates an overtime approval record for the measured window. The **Overtime billing method** on the contract line decides which window to measure, and the **Overtime calculation** periodic job produces the records. Learn more in [Invoice rental contracts](invoice-rental-contracts.md#handle-overtime-charges).

Each record shows the start and end of the window, the meter values at each end, total usage, allowed hours, the overtime hours, the rate, and the calculated overtime fee. Allowed hours come from the hours allowance on the active price line and, unless the **Overtime billing method** is *Last reading*, are reduced by any stand-down hours already credited. Learn more in [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md).

To review overtime, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Rental contracts** > **Rental overtime approvals**.
1. Open the record, and use the link to the contract line if you need the rental context.
1. Accept the calculated fee, or enter a lower figure in **Modified overtime fee** if you give the customer a concession. This is the only field you can change. A value of zero invoices the calculated fee, so to waive the charge entirely, select **Cancel** instead of **Approve**.
1. Select **Approve**. The system writes a price line on the contract line, using the overtime period code and dated to the measured window, which then flows into the invoice.
1. To pull an approval back before it's invoiced, select **Cancel** or **Delete**. Both remove the price line while it's still active. **Delete** also releases the meter reading, so the next overtime calculation can create the record again; **Cancel** doesn't.

**Approval required** on the contract line determines whether a manager reviews the charge. When it's turned off, the record is created and approved in the same transaction. An empty queue doesn't mean the calculation didn't run. It usually means usage stayed within the allowance.

### Void an incorrect meter reading

A reading that you enter in error stays in the usage history until you void it. The system excludes a voided reading from usage, billing, and depreciation calculations. You can't edit or delete readings on the usage history page, so voiding is the only correction, and it can't be undone.

To void a meter reading, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet items**, and select the fleet item.
1. On the **Inquiries** tab, in the **Fleet item** group, select **Usage history** to open the **Fleet item usage historical entries** page.
1. Select the reading that you entered in error, and then select **Void reading**.
1. Confirm the prompt.

The system marks the reading **Void**, and the next reading is measured from the reading before the voided one, so cumulative usage stays continuous. When there's no later reading, the fleet item's latest reading falls back to the last reading that isn't void.

You can void a reading that depreciation uses after you undo that depreciation. If the depreciation journal isn't posted, delete the journal line or the journal. If it's posted, reverse the fixed asset transaction. Then select **Void reading**. After the reading is voided, that reversal can no longer be revoked, so recalculate and post depreciation for the period instead.

### Replace an hour meter

When you swap a physical meter or it rolls over, record the swap so cumulative usage stays continuous. The next fleet item movement, the overtime calculation, and usage-based depreciation all work from that figure.

To record a meter replacement, follow these steps:

1. Open the fleet item. On the **Setup** tab, in the **Service** group, select **Hour meter replacement**.
1. Select the **Hour meter replacement type**: *Main SMU* for the primary hour meter, or *Secondary SMU* for a second counter such as a drum or pump meter. The dialog shows the last known reading and its capture date for the meter you chose.
1. Enter the **Old meter SMU**, which is the reading on the old meter when you removed it, and its **Removal date and time**. The **Old meter SMU** can't be lower than the **Last SMU** shown in the dialog box.
1. Enter the **New meter SMU**, which is the reading on the new meter when you installed it, and its **Installation date and time**. The new meter doesn't have to start at zero, so the system correctly handles a refurbished or transferred meter.
1. Select **OK**.

The system writes two usage history rows, one closing the old meter and one opening the new one. It carries the difference forward into lifetime usage. It then measures a later reading against the continuous total rather than against the new meter's own count.

> [!IMPORTANT]
> The meter replacement dialog box checks the **Old meter SMU** against the **Last SMU**, and no other reading check applies. Check both readings before you select **OK**.

## Configure fleet item movement checklists

Define fleet item movement inspection checklists on the *fleet item model* record. You can create different checklist items for each combination of checklist action:

- **Action**: *Ship*, *Receive*, or *All*
- **Mandatory**: Whether the checklist item must be completed before the fleet item movement can be processed
- **Photo mandatory**: Whether a photo must be attached to the checklist item

Learn more about fleet item model setup in [Manage fleet item models](set-up-rental-reference-data.md#manage-fleet-item-models).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
- [Manage fleet item swaps, substitutions, and transfers](manage-equipment-swaps-substitutions-transfers.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
<!-- - [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md) -->
