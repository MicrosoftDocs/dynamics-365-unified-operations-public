---
title: Create rental quotations and contracts by using the rental cart (preview)
description: Learn how to use the rental cart to create rental quotations and contracts, move them through their statuses, and add miscellaneous charges.
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

# Create rental quotations and contracts by using the rental cart (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

The **Rental cart** is a guided process for creating rental quotations and contracts. It starts with a dialog where you set dates and a rental template, then continues through a creation wizard that collects customer information, miscellaneous charges, and a summary before finalizing the document.

## Create a rental quotation by using the rental cart

To create a rental quotation by using the rental cart, follow these steps:

1. Go to **Rental management (Preview)** > **Workspaces** > **Rental management workspace (Preview)** and select **Rental cart**.
1. In the **Rental cart** dialog, set the following fields:
   - **Start date/time** – The date and time when the rental period begins.
   - **Estimated return** – The date and time when the customer expects to return the fleet item.
   - **Rental template** – Determines the billing scenario, pricing structure, and default terms. Learn more in [Manage rental templates](set-up-rental-templates.md#manage-rental-templates).
1. Add or remove rental classes as needed. When you open **Rental cart** from **Fleet item availability**, the dialog lists the fleet items that you marked instead, and you can remove any of them.
1. Select **Rental quotation creation** to open the wizard.
1. On the **Customer information** step, select the customer or prospect. Enter the delivery address and contact information.
1. On the **Miscellaneous charges** step, review and add any applicable fees such as delivery, environmental, or damage waiver charges. You configure the defaulted fees on the rental template.
1. On the **Quotation summary** step, review the fleet item charges, miscellaneous charges, and sales tax. Optionally, add bulk fleet items or a header-level discount.
1. On the **Finalize** step, choose one of the following actions to complete the process:
   - **Open quotation** – Opens the new quotation so you can review or make further changes.
   - **Send quotation** – Opens a layout dialog where you enter the expiry date. When you confirm it, the quotation moves to *Sent* and the layout is printed. The quotation isn't emailed to the customer automatically.

To create a rental contract directly (rather than a quotation), follow the same steps but select **Rental contract creation** in step 4. On the **Finalize** step, you can choose to **Open contract**, **Activate contract**, or **Print contract**.

> [!NOTE]
> An activated contract is ready for shipping and invoicing. If you plan to ship the fleet item immediately, select **Activate contract** on the **Finalize** step. A contract in *Created* (draft) status can't be invoiced.

When you activate a contract, the outbound fleet item movement can be created and scheduled automatically. The **Fleet item movement automation on contract activation** setting on the rental template controls this behavior. When it's enabled, activating a contract automatically creates and schedules the outbound fleet item movement, unless one already exists. Learn more in [The General FastTab](set-up-rental-templates.md#the-general-fasttab).

## Select a rental template for a customer

The **Rental template** lookup initially lists the templates linked to the selected customer. To use another template, switch the lookup to show all templates and select the template that you want. When you save the quotation or contract for the customer, the system automatically creates the customer-template link if it doesn't already exist. This process makes the template easier to find on later documents for that customer. Learn more in [Link rental templates to customers](manage-customer-prospect-records.md#link-rental-templates-to-customers).

## Add job site information

You can associate fleet items with a job site. A job site represents the location where you deliver and use the fleet item. Job sites have the following characteristics:

- **One-to-many customer relationship** – Multiple customers can share the same job site. This relationship is common on large construction projects where several subcontractors work at the same location.
- **Address and notes** – The job site includes a delivery address and optional notes to help delivery drivers find the exact location. After you enter the address, you can also record its **Latitude** and **Longitude**, and fleet item movements to and from the job site show them next to the address.
- **Contact information** – You can assign site contacts.

To add a job site, enter the job site information during the rental cart process or add it directly on the contract form. If the job site already exists in the system, you can search for it. The job site lookup lists the job sites that are linked to the customer or prospect. To select a job site that's linked only to other customers, such as a site that several subcontractors share, set **Show job sites** to *All*.

Learn more about managing job sites, including linking multiple customers and expiring inactive sites, in [Manage customer and prospect records for rental](manage-customer-prospect-records.md).

## Assign sales representatives

You can associate a sales taker with a rental contract for commission management and other reporting. Set the **Sales taker** in the **Responsible** group on the **Setup** tab of the document header. It defaults to the worker who creates the quotation or contract, and it's copied to the sales order that invoicing creates.

## Contract header: statuses, holds, ship-to, and printing

A quotation and a contract are the same header record with a different document type. On a contract, the contract status decides what you can still change. Activation is the gate: before it you shape the contract, after it you run and bill it.

### What each status allows

The following table shows which actions are available in each contract status.

| Action | Created or Approved | Printed | Active | On hold | Reopened |
|---|---|---|---|---|---|
| Add fleet items or bulk fleet items, or apply a header discount | Yes | No | No | No | No |
| Copy contract | Yes | Yes | Yes | No | No |
| Create a fleet item movement | Yes | Yes | Yes | No | No |
| Add a recurring or once miscellaneous charge | Yes | No | Yes | Yes | No |
| Add a supplemental miscellaneous charge | Yes | No | Yes | Yes | Yes |
| Create a pro forma invoice schedule | Yes | Yes | Yes | Yes | Yes |
| Create or post an invoice schedule | No | No | Yes | No | Yes |
| Run the contract closing wizard | No | No | Yes | No | Yes |
| **Change active period** and **Reverse period change** | No | No | Yes | No | No |
| Register a stand-down | No | No | Yes | No | No |
| Swap a fleet item | Yes | Yes | Yes | Yes | No |
| Remove a fleet item from a line | No | No | Yes | No | No |
| Create a sales order or a purchase order | Yes | Yes | Yes | No | Yes |
| Edit the header fields | Yes | Yes | Yes | No | Yes |

Three qualifications apply. **Copy contract** creates a new contract with new dates and the same active fleet items, but only on No-charge contract templates. **Change active period** and **Reverse period change** also require a template that doesn't use hourly billing, and they're explained in [Invoice rental contracts](invoice-rental-contracts.md#change-the-billing-period-on-a-running-contract). Nothing in the table is available after a contract is *Closed*, *Canceled*, or *Rejected*.

### Move a contract through its statuses

Use the contract closing wizard as the standard way to close an active rental contract. On the Action Pane, select **Contract closing** to review final charges and complete billing. Learn more in [Close a contract with the closing wizard](call-off-close-rental-contracts.md#close-a-contract-with-the-closing-wizard).

Use the status commands on the Action Pane. Print is available from *Created* and *Approved*, and activation from *Created*, *Printed*, and *Approved*. You can send a contract back to *Created* from *Printed* and *Active*, and cancel from *Created*, *Printed*, *Active*, *Approved*, and *On hold*. You can close from *Active*, *Reopened*, and *Rejected*, reopen from *Closed*, approve from *On hold* and *Rejected*, and reject from *On hold*.

While a contract is *Active* and carries an invoice schedule that isn't posted, every status command is unavailable. Post or delete the schedule first.

Reopening a closed contract sets the status to *Reopened*, which is a distinct status from *Active*, for corrections and supplemental charges only. After corrections and posting, use the status commands on the Action Pane to return the contract directly to *Closed*. Reopening isn't a way to extend a rental: the commands that change how a running contract bills, **Change active period** and **Reverse period change**, are offered only while the contract is *Active*.

### Why a contract is on hold

No command puts a contract on hold. The system applies the status, together with one of the following reasons:

- A manual change
- A rate override
- A missing rental class
- An approval
- Past due
- A credit limit
- A fleet item and class mismatch
- A substitution
- An applied dynamic price
- Passing the rental purchase option maximum term date

While a contract is on hold, the header is read-only, and invoice schedule creation, invoice posting, and the contract closing wizard are blocked. Pro forma invoice schedules and miscellaneous charges still work, so you can keep pricing the bill while the block is investigated.

To release a hold, approve the contract. The status becomes *Approved*, the pre-activation editing surface reopens, and you activate the contract again to resume billing. Approval is deliberately unavailable when the last status change reason was a credit limit or past due, so clear the customer's credit position first. Rejecting an on-hold contract sets it to *Rejected*, from which you can close the contract or approve it.

### Set where the delivery goes

**Ship to** on the header is the rule that decides which address is authoritative on the document. The same field appears on each line, next to **Use separate address**. Set it to one of the following values:

- **Address** – Deliver to the delivery address that you enter on the document.
- **Customer** – Deliver to the customer's registered address.
- **Job site** – Deliver to a registered job site.
- **Pickup fleet location** – The customer collects from a fleet location, which becomes the fulfillment point.

Changing **Ship to** clears the fields that no longer apply and refills the address. **Job site** clears the delivery address and the pickup fleet location. **Pickup fleet location** clears the delivery address and the job site, and fills in the pickup location. **Address** and **Customer** clear all three.

The rule also works in reverse. Entering a job site sets **Ship to** to *Job site*, choosing a pickup fleet location sets it to *Pickup fleet location*, and editing the delivery address sets it to *Address*. The exception is a rental template that has **Allow job site selection** turned on, which is the one case where a job site and a pickup fleet location can coexist on a document that's set to *Pickup fleet location*.

The delivery name follows the same rule: the customer name, the job site name, the fleet location description, or the address description. When the contract raises a sales order or a sales quotation, the value converts to the ship-to rule on that document, so a job site rental stays a job site sale.

**Ship to** also decides how the document is taxed. The sales tax group is taken from the address that the rule makes authoritative: the job site's location, the location of the delivery address, or the customer account. Changing the rule, or changing the job site, can therefore change the tax that's charged. Learn more in [How tax groups are determined](understand-rental-financial-integration.md#how-tax-groups-are-determined).

### Fields that printing locks

Printing a contract writes a rental document journal: a snapshot of the document, its lines and prices, and the fleet items with their start meter readings and asking prices. The live contract stays editable; the snapshot doesn't change. The system also writes snapshots when you send a quotation, when activation prints the contract, and when a fleet item swap reprints it. Open **Rental document journals** from the contract to reprint any earlier version. That snapshot, not the live contract, settles a dispute.

Printing also stamps the print date and moves the contract to *Printed*, where you can no longer add fleet items, bulk fleet items, header discounts, or miscellaneous charges. Return the contract to *Created* to keep editing it, or activate it.

### Cascade header changes to the lines

When you save a header change on a document that already has lines, the header-to-line update settings on the **Rental parameters** page determine whether the change is copied automatically, prompts you, or isn't copied. The settings cover changes such as the delivery address, the tax group, financial dimensions, and the estimated return date. Depending on your settings, the system also asks about updating all line addresses, retaining prices, and updating calendar calculation journals. Answer the **Retain prices** question with care: letting the cascade search for rates again can overwrite a price that you negotiated on a line. Learn more about **Update document lines** in [General FastTab of the General tab](configure-rental-parameters.md#general-fasttab-of-the-general-tab).

### Apply a header discount and trace converted documents

To reduce every active main line at once, select **Add discount** in the **Discount** group on the **Contract** tab (**Quotation** on a quotation), and enter the percentage. The value is kept as the **Header discount percentage** on the header and is applied to the main lines after their own line discounts, so the two compound. **Add discount** is available on a contract that's *Created* or *Approved*, on a quotation that's *Created*, *Sent*, or *Won*, and on the summary step of the rental cart. A reduction that goes beyond the rate override limits puts the document on hold.

On the **Other** tab of the header, the **Conversion** group shows **Converted from** and **Converted to**. They're written when a quotation is converted or a document is copied, and you can select either one to open the linked document.

## Miscellaneous charges: Once, Recurring, and Supplemental

Miscellaneous charges are the non-fleet item fees that you bill with a rental: delivery and pickup, environmental charges, road permits, cleaning, fuel, damage waiver and insurance charges, and damage found after a return. The command that you use determines which invoice the fee appears on, so select the command that matches how the charge is billed. For example, a delivery fee billed once, a damage waiver billed monthly, and a damage charge raised after the final invoice each use a different command.

### Add a charge to the whole contract

Header charges apply to the contract as a whole, so use them for fees that aren't tied to a single fleet item.

1. Open the rental contract or quotation.
1. On the Action Pane, on the **Contract** tab (**Quotation** on a quotation), select **Miscellaneous charge**, and then select one of the following commands:
   - **Once** – A fee that's billed one time, no matter how many billing periods the rental spans. A header once charge is placed on the final invoice of the run rather than on every period. Use it for delivery, pickup, permits, cleaning, or fuel.
   - **Recurring** – A fee that's added again to every invoice schedule that the contract generates, so it appears on every cycle bill without being entered again. Use it for an environmental fee, a damage waiver, or an admin charge.
   - **Supplemental** – A fee that gets its own invoice schedule, stamped as supplemental and outside the normal period sequence, so it produces an off-cycle invoice. **Invoice from** is set to today.
1. Complete the new charge line in the **Lines** grid, including the quantity and the unit price.

A supplemental charge lets you bill a customer after the final invoice: reopen the closed contract, add the supplemental charge, generate the invoice, and close the contract again. On a contract in *Reopened* status, **Recurring** and **Once** are unavailable at both the header and the line, so only **Supplemental** remains.

### Add a charge to one fleet item line

Line charges apply only to the fleet item on the line that you select.

1. Open the rental contract or quotation, and then select a main line. The commands are unavailable when the selected line is itself a charge line.
1. On the **Contract line** FastTab (**Quotation line** on a quotation), select **Add miscellaneous charge**, and then select **Recurring**, **Supplemental**, or **Once**.

The system creates a line charge under the main line it belongs to, so it follows that fleet item:

- **Recurring** takes the same period boundaries as the main line's own recurring prices, so it bills on that line's cadence.
- **Once** is billed on the last invoice for that line.
- **Supplemental** is valid for a single day and gets its invoice schedule immediately, flagged as supplemental, so it invoices off-cycle instead of waiting for the next periodic run.

To review the charges that belong to the selected line in a separate form, select **Miscellaneous charges**.

The **Miscellaneous charge** and **Add miscellaneous charge** menus are available when the contract is *Created*, *Approved*, *Active*, *On hold*, or *Reopened*. They're unavailable while the contract is *Printed*, and after it's *Closed*, *Canceled*, or *Rejected*.

### Correct the unit price of a charge

Use **Adjust miscellaneous charge** on the **Contract line** FastTab to change the unit price of a charge that isn't invoiced yet, such as a renegotiated delivery fee. Enter the new unit price. The new price applies to the periods that aren't invoiced yet, and invoiced periods and stand-down periods are left untouched. The rate override check doesn't run, so the correction can't put the contract on hold.

**Adjust miscellaneous charge** is available only when the contract status is *Active* and the selected line is a charge line whose fee type is neither **Environmental fee** nor **Fire-Theft-Vandalism Waiver**. It isn't available on quotations. The same dialog is available from the miscellaneous charges step of the rental cart, so you can price the proposed fees before the document exists.

### Charges added automatically by the rental template

Charge definitions come from the rental template lines, which carry the fee type, the amount or the percentage with its maximum amount, and the calculation base. Three settings decide whether a charge reaches the contract by itself:

- **Default charge** adds the charge automatically when a fleet item or a rental class is added to the document.
- A **Miscellaneous charge exemption** for the customer account suppresses the charge.
- **Final invoice** restricts a once charge to the final invoice. What happens then depends on **Add to final invoice** on the **Rental template line class rules** for the rental class or category of the line. *Required* adds the charge automatically, and *Prompt* offers it on the contract closing wizard as a charge that you select. Clearing a prompted charge on the wizard removes the line again.

Two more template line settings shape the result: **No fee** keeps the line out of the fee calculation, and **No invoice on credit** suppresses the charge when the main line produces a credit instead of a bill.

Learn more in [The Rental template lines FastTab](set-up-rental-templates.md#the-rental-template-lines-fasttab) and [Invoice rental contracts](invoice-rental-contracts.md).

## Add bulk fleet items to a contract

Bulk fleet items are non-serialized accessories such as hoses, safety vests, strainers, or cables that you rent alongside prime fleet items. The system tracks bulk fleet items by quantity rather than by serial number.

Before you start, ensure that the contract's rental template has a **Revenue category for bulk fleet items**, because every bulk fleet item line takes that revenue category.

To add bulk fleet items to a contract, follow these steps:

1. Open the rental contract or rental quotation.
1. On the Action Pane, on the **General** tab, in the **Bulk fleet items** group, select **Bulk fleet items availability**. **Fleet item availability** opens with the **Fleet item type** filter fixed to *Bulk fleet item*.
1. Select the **Marked** check box for each bulk fleet item that the customer needs, and then enter the **Quantity to add**. The quantity starts at 1 and can't exceed the quantity in stock.
1. In the **Add** group, select **Add to contract** (**Add to quotation** on a quotation). The system adds each marked bulk fleet item to the document as a new line.
1. Adjust pricing as needed. For example, some rental businesses include safety vests at no charge as a courtesy to the customer but charge for unreturned bulk fleet items.

The page lists the fleet items whose **Fleet item type** is *Bulk fleet item*, together with the quantity that each one holds per fleet type. You can add a bulk fleet item only when it has a default rental class and the rental template allows its fleet type.

After you save a bulk fleet item line, you can't change its quantity. To rent more, add another line from **Bulk fleet items availability**.

## Move a quotation through its statuses

A quotation has its own status: *Created*, *Sent*, *Confirmed*, *Won*, *Lost*, *Canceled*, *Expired*, or *On hold*. Use the commands on the Action Pane, on the **Quotation** tab, in the **Update** group, under **Status** to move it.

| Command | Available from | What it does |
|---|---|---|
| **Send** | *Created*, *Sent*, *Expired*, *Won* | Opens the layout dialog. When you confirm it, the quotation moves to *Sent*, the print date is stamped, the quotation journal is written, and the layout is printed. |
| **Win** | *Created*, *Sent* | Sets the status to *Won*. |
| **Confirm** | *Created*, *Sent*, *Expired*, *Won* | Opens the conversion dialog, creates the rental contract in *Created* status, marks a linked opportunity as won, and moves linked reservations to the contract. |
| **Lost** | *Created*, *Sent*, *Expired*, *Won* | Asks for a reason, removes the fleet items from the lines, sets a linked opportunity to lost, and cancels the linked active reservations. |
| **Cancel** | *Created*, *Sent*, *Expired*, *Won* | Does the same as **Lost**, and also deletes the calendar calculation journals. |
| **Approve** | *On hold* | Releases the hold. |

The system sets *On hold* itself when a rate override goes beyond its limit or a dynamic price is applied. The **Update expiring quotations** periodic job moves *Sent* quotations whose expiry date has passed to *Expired*. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).

After a quotation is *Canceled* or *Lost*, its header is read-only.

## Create a contract from a quotation

After the customer accepts the quotation, you can convert it to a rental contract. Converting a quotation to a contract preserves all the information from the quotation, including fleet item selections, rates, and job site details.

To create a contract from a quotation, follow these steps:

1. Open the quotation.
1. On the Action Pane, on the **Quotation** tab, in the **Update** group, select **Status** > **Confirm**. In the dialog that opens, check the customer, rental template, dates, and delivery details for the contract, and then select **OK**.
1. Review the contract details and make any necessary adjustments.
1. Select **Activate** to activate the contract. An activated contract is ready for invoicing.

> [!IMPORTANT]
> You must activate a contract before you can generate invoices.

### Copy a quotation or contract

**Copy quotation** and **Copy contract** are in the **Copy** group on the **General** tab.

**Copy quotation** runs without a dialog and creates a new quotation in *Created* status with a new ID. It's available while the quotation is *Created*, *Sent*, *Confirmed*, *Expired*, or *Won*. A line whose fleet item has the physical status *Not available* or *On hold* isn't copied.

**Copy contract** is available only on a contract that uses a no-charge template, while the contract is *Created*, *Approved*, *Printed*, or *Active*. It opens the create document dialog, where you set the new contract's customer, dates, and delivery details, creates the contract with the active fleet items of the original, and then asks whether to close the original contract.

## Work with prospects

A prospect is a potential customer who doesn't yet have a full customer account. Rental management supports creating quotations for prospects, which is useful for the following scenarios:

- Walk-in customers requesting a quick quote
- Events where you capture leads
- Referrals that aren't set up as full accounts

When a prospect accepts a quotation, convert the prospect to a customer before you confirm the quotation. Confirmation creates the contract for the customer account that's linked to the prospect, so that account must exist first. Learn more in [Set up rental templates](set-up-rental-templates.md).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Reserve fleet items](reserve-rental-equipment.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Set up rental templates](set-up-rental-templates.md)
- [Configure rental parameters](configure-rental-parameters.md)
