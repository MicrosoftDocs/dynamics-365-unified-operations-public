---
title: Configure rental parameters (preview)
description: Learn how to configure rental parameters for rental operations, financial processing, reporting, and user defaults.
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

# Configure rental parameters (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental parameters control behavior across the rental management module in a legal entity. Use them to establish business rules, validation checks, and defaults for daily rental operations and financial processing.

These settings govern how you create, assign, move, and reserve fleet items, including attachment handling and shipping and receiving checks. They also control pricing and discounts, dynamic price suggestions, invoicing, payment recording, fixed asset transactions, and carrying cost calculations. Other settings define utilization reporting periods, status colors, and number sequences.

Per-user settings define default warehouses, fleet locations, rental templates, reservation types, and availability views. They also control whether users can manage other users' reservations.

For supporting setup records, learn more in [Set up rental reference data](set-up-rental-reference-data.md). For reusable document defaults, learn more in [Set up rental templates](set-up-rental-templates.md).

## Open the Rental parameters page

To configure rental parameters, go to **Rental management (Preview)** > **Setup** > **Rental parameters**.

The rental parameters page is organized into tabs. This article describes how to work with each of them.

<a name="general-tab"></a>

## General tab

The **General** tab contains settings that apply to the overall rental management module, including best rate calculation defaults, quotation expiration, and utilization settings. It provides the FastTabs and settings described in the following subsections.

### General FastTab of the General tab

The **General** FastTab controls quotation expiration, whether reserved fleet items can be quoted, and defaults for best rate calculations and posting journals. Make the following settings:

- **Expiration base** – Select the date from which to count the rental template's **Default expiration date** and **Maximum expiration date** values. Select *System date* to count from the current system date, or *Start date* to count from the rental's start date. Learn more in [The Quotation FastTab](set-up-rental-templates.md#the-quotation-fasttab). **Expiration time in days** on the **Other** tab is separate: it controls when a quotation appears in the workspace's **Expiring quotations** tile.
- **Reserved fleet item can be quoted** – Set to *Yes* to allow a fleet item reserved on a sales order, or owned by a customer, to be added to a sales quotation. Set to *No* to block it. When you quote a fleet item that's reserved on a sales order, the system warns you about that order. Fleet item reservations still apply.
- **Period** – In the **Best rate calculation defaults** group, select the period code to assign to price lines created by the best rate calculation. This setting identifies the resulting price line's period; it doesn't replace the billing scenario's pricing tiers. Learn more in [Best rate calculation, end to end](call-off-close-rental-contracts.md#best-rate-calculation-end-to-end).
- **Transfer request movement journal** – Select an inventory journal name of type *Movement* for fleet transfers from fixed assets back to inventory.
- **Transfer request inventory asset journal** – Select an inventory journal name of type *Fixed assets* for fleet transfers from inventory to fixed assets.
- **Revenue split posting journal** – Select a ledger journal name of type *Daily* for revenue split processing.

Create the journal names before you select them here. Learn more in [Configure posting journals](set-up-rental-reference-data.md#configure-posting-journals).

On the **General** FastTab's toolbar, select **Update document lines** to configure what happens when a user changes a rental quotation or contract header. For each field shown in the dialog, choose one of the following behaviors:

- *Never* – Don't apply the header change to document lines.
- *Always* – Apply the header change to document lines automatically.
- *Prompt* – Ask the user whether to apply the header change to document lines.

These rules cover fields such as dates, delivery address, sales tax group, and financial dimensions. Confirm the dialog to save the rules. This command configures subsequent header-to-line updates; it doesn't immediately update existing documents.

### Rental utilization FastTab

The **Rental utilization** FastTab defines the reporting periods for time and financial utilization and the default period shown in the rental availability summary. Make the following settings:

- **Utilization period 1** through **Utilization period 4** – Enter the number of days in each rolling reporting period, counted back from the utilization calculation date. For example, enter *30*, *60*, *90*, and *180* to compare short-term and longer-term performance.
- **Default utilization period** – Select the period to show initially in the rental availability summary. Choose one of **Utilization period 1** through **Utilization period 4**, or *Life* for the fleet item's whole life.
- **Utilization from acquisition** – Set to *Yes* to shorten a reporting period when the fleet item has spent fewer days in asset fleets than the configured period. This setting avoids treating days before acquisition as unused rental capacity. Set to *No* to use the full configured reporting period.

Learn more about the calculations, availability display, and jobs that maintain the figures in [Track rental fleet utilization](track-rental-fleet-utilization.md).

> [!NOTE]
> **Time utilization reference period** and **Financial utilization reference period** are on the **Dynamic pricing** tab, not this FastTab. Each selects which utilization period, or *Life*, dynamic pricing uses for its corresponding rate adjustment. Learn more in [Dynamic pricing tab](#dynamic-pricing-tab).

<a name="fleet-items-tab"></a>

## Fleet items tab

The **Fleet items** tab controls how you create fleet items, assign them to rental documents, validate their use, and process transfers and movements. It provides the FastTabs and settings described in the following subsections.

### General FastTab of the Fleet items tab

The **General** FastTab defines defaults for fleet item creation, attachment handling, fleet transfers, and serial number corrections. Make the following settings:

- **Fleet item ID creation** – Select *With serial number* to require a serial number before **Create fleet item** is available on purchase order lines and movement journal lines. Select *Without serial number* to create the fleet item first and record its serial number later. Learn more in [Enter serial numbers when fleet items arrive](add-equipment-to-rental-fleet.md#enter-serial-numbers-when-fleet-items-arrive).
- **Serial number update** – Set to *Yes* to use **Serial number update** to change serial numbers on open purchase order lines that have fleet items. This action updates both the purchase order line and its fleet item, instead of letting users edit the line's serial number directly.
- **Location update** – Select an inventory journal name of type *Transfer* for the fleet item's **Update location** action. This action changes its inventory location within the current warehouse, not its fleet location.
- **Default attachment validation** – Set to *Yes* to select **Attachment validation** by default in the attachment builder. When that validation is selected, an attachment validity rule must allow the combination of the prime fleet item and attachment models.
- **Bar code setup** – Select the bar code setup to propose when users create bar codes from a fleet item.
- **Transfer on system date** – Set to *Yes* to use the current system date as the transfer and posting date for fleet transfers. Set to *No* to let the user specify the transfer date when completing the transfer.
- **Transfer attachments** – Set to *Yes* to select a prime fleet item's attachments automatically when you select it for a fleet transfer request. This setting concerns transfers between fleet types, not shipments to customers.
- **Transfer with details** – Set to *Yes* to transfer fixed asset balances by transaction type when transferring between fleet types tracked as fixed assets. Set to *No* to transfer summarized acquisition and depreciation amounts.
- **Clear disposal date** – Set to *Yes* to clear the asset book's **Disposal date** when a transfer between fixed-asset fleet types generates a disposal. Set to *No* to retain the transfer date as the disposal date.
- **Reversal when only fixed asset group changes** – Set to *Yes* to reverse and repost transactions in the new fixed asset group when the book stays the same. Set to *No* to use disposal and reacquisition instead. This reversal option doesn't apply to bulk fleet items.
- **Asset posting profile** – Select the fixed asset posting profile for fleet item purchase and sales order transactions. This profile determines the fixed asset ledger accounts; it isn't the mapping of fleet types to fixed asset groups and books.
- **Fleet item status** – In the **Serial number update** group, select the receipt status required before correcting a stocked fleet item's serial number. Select *Financial received* to require an invoiced receipt, or *Financial and physical received* to also accept a posted product receipt.
- **Serial number update journal** – Select an inventory journal name of type *Transfer* for corrections to stocked fleet items' serial numbers. This setting is separate from the **Serial number update** switch for purchase order lines.
- **Blank ID removes link** – Set to *Yes* to remove a purchase order line's fleet item link when the user confirms **Attach to fleet item** with a blank fleet item ID. Set to *No* to leave the existing link unchanged in that case.

Learn more about journal assignments in [Configure posting journals](set-up-rental-reference-data.md#configure-posting-journals), and about serial number and inventory location changes in [Change fleet item master data](change-fleet-item-master-data.md).

Fleet transfers change a fleet item's fleet type and can create accounting transactions. Learn more in [Transfer fleet items between fleet types](add-equipment-to-rental-fleet.md#transfer-fleet-items-between-fleet-types) and [Configure fleet types](configure-inventory-location-settings.md#configure-fleet-types).

### Adding fleet items to rental quotation or contract FastTab

The **Adding fleet items to rental quotation or contract** FastTab controls fleet item sharing and how prime fleet items and attachments are priced together. Make the following settings:

- **Fleet item on multiple rentals** – Select *Not allowed* to reject assignments when the fleet item is already assigned to another rental document. Select *Allow only on quotation* to permit sharing involving a quotation, but not to add an item on one contract to another contract. Select *Allowed* to permit sharing on both quotations and contracts. Permitted sharing prompts the user to confirm the existing assignment; it doesn't make the fleet item physically available for overlapping rentals.
- **Use package** – Set to *Yes* to price a prime fleet item and its attachments as a rental package. Define the component classes, quantities, and revenue percentages on the package's rental class. Learn more in [Set up rental packages](set-up-rental-rates-discounts.md#set-up-rental-packages).
- **Split revenue to attachments** – Set to *Yes* to divide rental revenue equally among the prime fleet item and its attachments when invoice schedules are created. Use this option when you want equal revenue allocation without configuring package component percentages.

You can't enable **Use package** and **Split revenue to attachments** together. Turn off one before you turn on the other.

No-fee main lines are an exception to the sharing restriction: they can share a fleet item already on a contract after confirmation, even with *Not allowed*.

<a name="fleet-item-validation"></a>

### Fleet item validation FastTab

The **Fleet item validation** FastTab controls how the system handles rental class mismatches, missing fleet items, and changes that need review. Make the following settings:

- **Check on active** – Select how to handle a fleet item that doesn't belong to the line's rental class when you activate the rental contract.
- **Check on assign** – Select how to handle a rental class mismatch when you assign a fleet item to a quotation or contract line.
- **Check on swap** – Select how to handle a rental class mismatch when you swap the fleet item on a contract line.
- **Validate attachment removal** – Set to *Yes* to prevent removal of an attachment in the attachment builder opened from a fleet item while either the attachment or its prime fleet item is on a rental contract. Set to *No* to skip this contract check.
- **Hold on substitute** – Set to *Yes* to put the quotation or contract on hold with the reason *Substitution* when you substitute a line's rental class. The substitution changes the class and reprices the line immediately; the hold requires review before the document proceeds.
- **Fleet item validation** – Select *Warning* to allow contract activation with a warning when a main line has neither a fleet item nor a bulk fleet item. Select *Error* to block activation until a fleet item is assigned.
- **Sales order validation** – Select how to handle a fleet item on an active rental contract when adding it to a sales order or sales quotation from **Fleet item availability**. Select *None* to skip this check, *Prompt* to request confirmation, or *Error* to block the action. This setting doesn't override other sales eligibility checks.

For **Check on active**, **Check on assign**, and **Check on swap**, choose *None* to skip the rental class check. Choose *Log* to record a rental class exception and allow the action, or *Error* to reject the mismatch. Choose *Hold* to record the exception and put the document on hold with the reason *Fleet item/class mismatch*.

Rental class validation is separate from service status restrictions and fleet item availability. Learn more in [Check fleet item availability and select fleet items](check-equipment-availability.md). For the difference between swapping a fleet item and substituting its rental class, learn more in [Manage fleet item swaps, substitutions, and transfers](manage-equipment-swaps-substitutions-transfers.md).

### Fleet item movement FastTab

The **Fleet item movement** FastTab controls checks for outbound shipments and inbound returns, inspection checklists, meter readings, and inspection document text. Make the following settings:

- **Outbound fleet item movement validation** – Select *Warning* to allow contract activation with a warning when fleet items aren't covered by an outbound fleet item movement. Select *Error* to block activation until the missing assignments or movements are corrected.
- **Inbound fleet item movement validation** – Select how to handle fleet items that have movement records but aren't received on a completed inbound movement when closing a contract or a line on its final invoice. Select *No* to skip the check, *Warning* to warn and continue, or *Error* to block closing.
- **Control on rental inbound fleet item movement** – Set to *Yes* to require that a fleet item on a rental contract is returned on an inbound movement for that contract.
- **Use checklist for shipping** – Set to *Yes* to generate the fleet item model's shipping checklist on fleet item movements. Checklist generation also requires a fleet item movement status configured for the *Ship* action.
- **Use checklist for receiving** – Set to *Yes* to generate the fleet item model's receiving checklist on fleet item movements. Checklist generation also requires a fleet item movement status configured for the *Receive* action. Only checklist items marked **Mandatory** block processing when they're incomplete. <!-- Operations staff can complete the generated checklist on the mobile app's **Inspection** page. --> Learn more in <!-- [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md) and --> [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md).
- **Secondary SMU control** – Set to *Yes* to block movement posting when a secondary service meter unit (SMU) reading is lower than the latest secondary reading. Set to *No* to ask for confirmation and allow posting if the user accepts. A primary **Service meter unit** reading below **Last SMU** blocks posting regardless of this setting.
- **Modify rent return limit** – Enter the maximum SMU usage between shipment and return that qualifies for a modify rent return action item. The system compares the difference between the readings, not the absolute return reading. Action item creation also requires **Modify rent return** on the applicable inbound movement status setup row.
- **Activate terms and conditions** – Set to *Yes* to enter terms and conditions for the inspection document. Setting it to *No* clears the text.
- **Terms and conditions** – Enter the text to print on the fleet item movement inspection document.

### Replace attachment FastTab

The **Replace attachment** FastTab controls which replacement attachments you can select on a fleet item movement. Use these settings to decide whether replacements must match the original attachment's location and fleet type:

- **Different location on attachment replacement** – Set to *Yes* to allow a replacement from another location within the same warehouse. Set to *No* to require the same location.
- **Different fleet type on attachment replacement** – Set to *Yes* to allow a replacement with a different fleet type. Set to *No* to require the same fleet type.

### Package match icons FastTab

The **Package match icons** FastTab defines the visual indicators for package matching on the **Rates and classes** page. These indicators help users distinguish how closely the fleet item and attachments match a package's component classes.

To configure the indicators, select each matching category in turn and choose its **Icon**. Configure the exact-match, possible-match, and no-match categories. The preview shows the selected icon; changing it affects the indicator, not the package matching rules.

### Fleet item documentation FastTab

The **Fleet item documentation** FastTab defines the attachment type used for fleet item pictures and the icon that identifies them. Make the following settings here:

- **Picture type** – Select the document attachment type used for fleet item pictures.
- **Picture icon** – Select the icon that indicates a picture attachment of that type.

### Fleet item inventory inquiry FastTab

The **Fleet item inventory inquiry** FastTab controls which fleet item agreement statuses the inventory inquiry excludes. Use it to leave out statuses that aren't relevant to your inventory review.

In **Excluded fleet item agreement statuses**, add the statuses that the inquiry should omit. Remove a status from the excluded list to include it again. This list filters the inquiry; it doesn't change the fleet items' agreement statuses.

## Invoicing tab

The **Invoicing** tab controls invoice schedule date limits, payment due dates, the start dates of new rental fee lines, and credit note reason requirements. These settings apply across rental contracts in the current legal entity. Make the following settings:

- **Invoice until** – Enter the latest date that users can specify as **Invoice until** or **Fixed invoice date** when generating invoice schedules. Leave it blank to impose no date limit. This setting is a validation limit, not a default billing date or a contract end date.
- **Due date from schedule** – Set to *Yes* to calculate a schedule's payment due date from its invoicing date and terms of payment, and carry that due date to the customer invoice. Set to *No* to calculate the due date from the current system date and terms of payment when posting. If the schedule has no due date, posting uses the payment terms calculation even when this setting is *Yes*. Use *Yes* when generating a schedule in advance shouldn't shift the payment deadline to the date you eventually post it.
- **Update start date on rental fee line** – Set to *Yes* to start a new rental fee line on the day after the latest invoice schedule period that isn't credited. This setting prevents a newly added fee from starting in a period already covered by a schedule. Set to *No* to copy the parent rental line's start date instead. The parent line's start date also applies when no qualifying schedule period exists or the contract is reopened, regardless of this setting.
- **Reason code for credit** – Set to *Yes* to require a **Reason code** when creating a full or partial credit note from an invoice schedule. The credit dialog opens so that the user can select the code before proceeding. Set to *No* to create the credit without that dialog or a required reason code.

Learn more about generating schedules and crediting invoices in [Invoice rental contracts](invoice-rental-contracts.md). For how payment terms default onto rental documents, learn more in [Understand payment terms defaulting](understand-rental-financial-integration.md#understand-payment-terms-defaulting).

## Cash register tab

The **Cash register** tab controls payment recording on rental contracts, including deposits collected before invoicing. Recorded payments go into customer payment journals for reconciliation and posting. On the **General** FastTab, make the following settings:

- **Use cash register** – Set to *Yes* to let rental coordinators record payments directly on rental contracts. The user who collects a payment must be linked to a worker.
- **Default cash register journal name** – Select the payment journal name to use when the selected method of payment doesn't have its own journal name in the cash register payment setup. Ensure that a journal name is available from one of these sources; otherwise, payment recording can fail.

Learn more in [Record payment deposits on rental contracts](understand-rental-financial-integration.md#record-payment-deposits-on-rental-contracts).

## Fixed assets tab

The **Fixed assets** tab controls whether contract activation updates fixed asset depreciation start dates. It also defines the journal and posting profile for fixed asset transactions generated by fleet transfers. On the **Rental** FastTab, make the following settings:

- **Depreciation start by contract** – Set to *Yes* to update eligible fleet item asset books' **Depreciation start date** to the rental contract's start date when you activate the contract. Only open books without posted depreciation transactions are updated. Books that use *Straight line service life* or *Straight line life remaining* are excluded. Set to *No* to leave the depreciation start dates unchanged during contract activation. This setting doesn't select the depreciation method or post depreciation.
- **Transfer journal** – Select a ledger journal name of type *Post fixed assets* for the fixed asset transactions generated when a fleet item transfers out of a fleet type whose **Value tracking method** is *Fixed asset*. The journal is used both for transfers to another fixed-asset fleet type and for transfers back to inventory. Create the journal name before selecting it here. Learn more in [Configure posting journals](set-up-rental-reference-data.md#configure-posting-journals).
- **Transfer posting profile** – Select the fixed asset posting profile for transfers between fleet types tracked as fixed assets. Configure an offset account for the *Fleet item transfer* transaction type in that profile; the transfer fails if the account is missing. Transfers from fixed assets back to inventory use the default posting profile from the fixed asset parameters instead.

<!-- TODO: PM input needed: The Depreciation start by contract tooltip says depreciation starts when the contract is invoiced. RentalDocumentStatusChange_Contract_Active.updateDeprStartDateOnAssetBook updates the start date during activation, subject to the book and method conditions documented above. Confirm the intended behavior and correct the tooltip. -->

The **Transfer posting profile** determines ledger accounts. It doesn't replace **Posting configuration for fleet types**, which assigns fixed asset groups and books. Learn more in [Configure posting for fleet types](configure-inventory-location-settings.md#configure-posting-for-fleet-types) and [Understand fleet transfer financial impact](understand-rental-financial-integration.md#understand-fleet-transfer-financial-impact).

For how depreciation amounts are calculated and posted, learn more in [Set up depreciation profiles](set-up-rental-reference-data.md#set-up-depreciation-profiles).

## Rates and discounts tab

The **Rates and discounts** tab controls default price factors, factor-specific rate and discount setup, search priorities, and rounding during rate maintenance. Configure these settings to determine which prices users start with and which rate or discount takes precedence when several records match. These parameters don't create the rate and discount records themselves.

### Default price factor values FastTab

The **Default price factor values** FastTab provides default values for pricing new main rental lines and displaying rates in fleet item availability. It also controls whether changing an invoice-from date triggers a new price search. Make the following settings:

- **Default application** – Select the application price factor to use on a new main rental line when its rental template doesn't specify one.
- **Default shift** – Select the shift price factor to use on a new main rental line when its rental template doesn't specify one.
- **Default location** – Select the fallback location price factor for new main rental lines. The system first uses the price factor assigned to the pickup fleet location, then the rental template's default, and finally this value. This field selects a price factor, not a warehouse or fleet location.
- **Rates in fleet item availability** – Set to *Yes* to show rental rate columns in fleet item availability, using the default price factors configured here. Set to *No* to hide those columns; this setting doesn't disable pricing on rental documents.
- **Retain prices** – Select what happens to prices on a main rental line when its **Invoice from** date changes, either directly or through a header update. Select *Never* to run a new price search, *Prompt* to ask whether to keep the current prices, or *Always* to keep them.

### Rate FastTab

The **Rate** FastTab lets you maintain different rental rates for different applications, shifts, and locations. Enabling a factor makes its field editable and required on rental rate records. It also requires that factor on main rental lines. Make the following settings:

- **Rates by application** – Set to *Yes* to maintain rates by application, such as different types of equipment use.
- **Rates by shift** – Set to *Yes* to maintain rates by shift. This lets the rate reflect how intensively the equipment is used.
- **Rates by location** – Set to *Yes* to maintain location-specific rates. Assign location price factors to pickup fleet locations to support different rates at different branches.

Learn more about the records that these settings apply to in [Understand rental rate structure](set-up-rental-rates-discounts.md#understand-rental-rate-structure).

### Discount FastTab

The **Discount** FastTab enables factor-specific discounts independently of the rate settings. For example, you can maintain rates by shift without maintaining separate discounts by shift. Enabling a factor makes its field editable and required on rental discount records. Make the following settings:

- **Discount by application** – Set to *Yes* to maintain separate discounts for different application price factors.
- **Discount by shift** – Set to *Yes* to maintain separate discounts for different shift price factors.
- **Discount by location** – Set to *Yes* to maintain separate discounts for different location price factors. A location price factor is required on main rental lines when either this setting or **Rates by location** is enabled.

### Sorting FastTab

The **Sorting** FastTab defines the values that the system adds together to calculate each rate or discount record's **Priority**. The matching record with the lowest total wins. Choose values that give your preferred combinations lower totals, rather than relying on records with equal priorities.

Make the following settings:

- **Sorting base** – Enter the starting value for every rate and discount's priority. Because the system adds the same base to every record, changing it alone doesn't change their relative order.
- **Sorting table class**, **Sorting group class**, and **Sorting all class** – Enter the additions for discounts that apply to a specific rental class, a rental category, or all classes, respectively. These values don't contribute to rate priorities, because rates apply to a specific rental class.
- **Sorting table account**, **Sorting group account**, and **Sorting all account** – Enter the additions for a specific customer, a customer group, or all customers, respectively. Group matching uses the customer's rental rate group for rates and rental discount group for discounts.
- **Sorting rate application**, **Sorting rate shift**, and **Sorting rate location** – Enter the addition for each factor that's enabled for rates but left blank on a rate record. Positive values give these less-specific records a lower preference than otherwise equivalent records with the factor filled in.
- **Sorting discount application**, **Sorting discount shift**, and **Sorting discount location** – Enter the corresponding additions for factors that are enabled for discounts but left blank on a discount record.

After changing the sorting values, run **Rental management (Preview)** > **Periodic jobs** > **Rates and discounts** > **Update priority**. Existing records keep their previous priority until it's recalculated. Learn more, including a worked example, in [How priority decides which record wins](set-up-rental-rates-discounts.md#how-priority-decides-which-record-wins).

### Rounding FastTab

The **Rounding** FastTab defines how rate maintenance rounds stored rate amounts. These settings apply when you use **Round now** or apply rounding in **Modify rate**. They don't automatically round every price calculated on a rental contract. Make the following settings:

- **Rounding rule** – Enter the increment to round rates to. For example, enter *0.05* to round to multiples of five hundredths, or *1.00* to round to whole currency units.
- **Rounding method** – Select *Normal* to round to the nearest increment, *Downward* to round down, or *Rounding-up* to round up.
- **Automatic rounding** – Set to *Yes* to select **Apply rounding** by default in the **Modify rate** dialog. Set to *No* to leave that option cleared by default. Users can change the option for each modification.

Learn more about updating and rounding existing rates in [Change rates in bulk](set-up-rental-rates-discounts.md#change-rates-in-bulk).

## Dynamic pricing tab

The **Dynamic pricing** tab defines rules for suggesting adjustments to rental quotation and contract prices. Use it to reflect fleet availability, utilization, reservation demand, and customer history in a suggestion that users review before applying. You control which adjustments are allowed, how much each factor contributes, and the maximum change for each rental period.

### Dynamic pricing FastTab

The **Dynamic pricing** FastTab enables price suggestions and sets the controls that apply across the adjustment rules. Make the following settings:

- **Activate dynamic pricing** – Set to *Yes* to let users calculate and apply dynamic price suggestions on rental quotation and contract lines. Set to *No* to disable these suggestions.
- **Allow price decrease** – Set to *Yes* to permit suggestions that lower the price, subject to the period's maximum decrease. Set to *No* to prevent users from applying a suggestion with a negative calculated adjustment.
- **Allow price increase** – Set to *Yes* to permit suggestions that raise the price, subject to the period's maximum increase. Set to *No* to prevent users from applying a suggestion with a positive calculated adjustment.
- **Approval required** – Set to *Yes* to put the quotation or contract on hold when a user applies a suggestion. The document must be approved before it can proceed, but this setting doesn't route it to an approver.
- **Inventory level by fleet location** – Set to *Yes* to count available fleet items only at the fleet location on the quotation or contract header. Set to *No* to count them across the legal entity. In both cases, the count includes only the line's rental class and fleet types whose **Value tracking method** is *Fixed asset*.

### Other dynamic price FastTabs

The remaining FastTabs define the percentages that contribute to a suggestion and the limits on their combined effect. The FastTabs match a measured value to a **From**–**To** range and contribute that range's **Percentage**. Use non-overlapping ranges, with **From** no greater than **To**. Both endpoints are included, and a value outside all ranges contributes no adjustment.

Positive percentages raise the price, and negative percentages lower it. The system adds the contributions together, then applies the limits for the price line's period code. Configure each FastTab as follows:

- **Dynamic price inventory level tiers** – Define adjustments by the number of available fleet items in the rental class, not by an inventory percentage. The count follows the **Inventory level by fleet location** setting.
- **Dynamic price reservations tiers** – Define adjustments by the number of active reservation lines for fleet items in the rental class. Only reservations at the reservation stage and fleet types tracked as fixed assets contribute.
- **Dynamic price time utilization tiers** – Define adjustments by the rental class's average time utilization percentage. Select a **Time utilization reference period** to choose the utilization period used for that average.
- **Dynamic price financial utilization tiers** – Define adjustments by the rental class's average financial utilization percentage. Select a **Financial utilization reference period** independently of the time utilization period.
- **Dynamic price past contract tiers** – Define adjustments by the number of other rental contracts for the customer. Set **Reference date** to choose the contract start-date cutoff. The count excludes the current document and isn't limited to completed contracts.
- **Dynamic price rate groups** – Assign an adjustment **Percentage** to each customer rental rate group. Unlike the tier FastTabs, this FastTab matches the customer's assigned group rather than a numeric range.
- **Dynamic price period limits** – Set **Maximum decrease percentage** and **Maximum increase percentage** for each **Period code**. Enter the maximum decrease as a negative percentage. A period code without a limit record gets no adjustment.

Learn more about calculating and applying suggestions in [Configure dynamic pricing](set-up-rental-rates-discounts.md#configure-dynamic-pricing).

## Color tab

The **Color** tab defines background colors that help users recognize statuses in rental document grids. On the **Color setup** FastTab, select a color for each status in the following field groups:

- **Contract** – Colors for rental contract statuses.
- **Quotation** – Colors for rental quotation statuses.

These settings change only the visual highlighting. They don't change document statuses or the rules for processing them.

## Other tab

The **Other** tab brings together settings for insurance expiry checks, fee-line presentation, payment terms, workspace reminders, and reservations. Use these settings to establish defaults for supporting processes and keep reservations aligned with changes to quotations and fleet item attachments.

Configure the following settings on their respective FastTabs:

- **Expiry time** on the **Insurance** FastTab – Enter the default number of days ahead to check for expiring physical damage insurance policies. The *Insurance expiry check* periodic job proposes this value when you run it.
- **Streamlined miscellaneous charges** on the **Design** FastTab – Set to *Yes* to hide miscellaneous charges from the document lines and add or review a rental line's charges on the **Miscellaneous charges** page instead. Set to *No* to show the charges in the document lines.
- **Expiration time in days** on the **Workspace** FastTab – Enter how many days before expiry a quotation should appear in the **Expiring quotations** tile on the rental management workspace.

On the **Payment terms defaulting** FastTab, arrange the sources in **Selected defaulting sequence** in the order the system should check them. A new quotation or contract uses the first source with payment terms defined. Sources outside the sequence aren't used. Learn more in [Understand payment terms defaulting](understand-rental-financial-integration.md#understand-payment-terms-defaulting).

The **Reservations** FastTab controls customer requirements and how changes to quotations or fleet item attachments affect linked reservations. Make the following settings here:

- **Customer for reservation** – Set to *Yes* to require a customer account when creating a fleet item reservation. Set to *No* to allow reservations without a customer.
- **Cancel reservation behind rental quotation** – Select whether to cancel a linked reservation when its rental quotation is lost or canceled.
- **Cancel reservation behind sales quotation** – Select whether to cancel a linked reservation when its sales quotation is lost or canceled.
- **Update attachment on rental reservation and quotation** – Select whether attachments added to or removed from a fleet item should also be added to or removed from its active rental reservations and linked rental quotations.

For the cancellation and attachment-update settings, select *Never* to leave the linked records unchanged, *Prompt* to ask the user, or *Always* to update them automatically.

## Carrying cost tab

Carrying cost represents the cost of the capital invested in your rental fleet. The **Carrying cost** tab holds the rate and posting settings that the *Calculate carrying cost* periodic job uses. The job calculates a cost for each eligible fixed asset book, whether or not the fleet item is on rent. Make the following settings on the **Carrying cost** FastTab:

- **Carrying cost %** – Enter the percentage to apply to the asset book's net book value at the end of the calculation period. The rate applies for the unit selected in **Per**.
- **Per** – Select whether the percentage applies per *Year*, *Month*, or *Day*. This rate unit is separate from the calculation window selected in **Calculation frequency**.
- **Calculation frequency** – Select the period that each calculation covers: *Month*, *Year*, *Fiscal year*, or *Fiscal period*. The fiscal options use the legal entity's fiscal calendar. This setting defines the calculation window; it doesn't schedule the job.
- **Journal name** – Select a ledger journal name of type *Post fixed assets* for the journal that the job creates.
- **Transaction text** – Enter the text to include on the generated fixed asset journal lines.
- **Transaction type** – Select the fixed asset transaction type for carrying cost: *Acquisition*, *Acquisition adjustment*, *Revaluation*, *Write-up adjustment*, or *Write-down adjustment*. Ensure that the asset book's posting profile has the appropriate account setup for that type. The job uses the selected type when deriving the journal line's offset account.

Select **Carrying cost** on each fixed asset book that should be included. The job processes only open books for fleet items in the selected fleet types whose **Value tracking method** is *Fixed asset*. Learn more about running the calculation and choosing whether to create a proposal or post the journal in [Calculate carrying cost](run-rental-periodic-jobs.md#calculate-carrying-cost).

<a name="rental-workers"></a>

## Rental user setups tab

Worker settings define each user's default warehouse, fleet location, rental template, and availability view. They also control whether the user can manage other users' reservations. Each row applies to one user. Make the following settings for each user:

- **User ID** – Select the user that you're configuring. A new row defaults to your own user ID, so change it if you're configuring another user.
- **Warehouse** – Select the default warehouse for sales orders, sales quotations, and purchase orders that the user creates. The system also proposes the warehouse's site.
- **Fleet location** – Select the default fleet location for new rental quotations and contracts. The system also proposes it as the pickup fleet location on headers, lines, and creation dialogs.
- **Auto site population** – Set to *Yes* to automatically fill in the selected warehouse's site when the user removes a fleet item.
- **Rental template** – Select the default template for new rental quotations and contracts, including those created from the rental cart and the class cart.
- **Reservation type** – Select the default reservation type to propose when the user creates a fleet item reservation.
- **Manage all reservations** – Set to *Yes* to let the user edit, delete, cancel, and convert active reservations that other users created. Set to *No* to limit the user to their own reservations.
- **Show all on fleet item availability** – Set to *Yes* to select **Show all** by default when the user opens fleet item availability from the menu. Set to *No* to initially exclude fleet items that are reserved, on a sales order, on a rental contract, or on order.
- **Fleet item types in availability view** – Select the default **Fleet item type** filter for fleet item availability: *Fleet item*, *Bulk fleet item*, *Attachment*, or *All*.
- **Utilization on availability** – Set to *Yes* to show financial and time utilization on fleet item availability and the rental availability summary. Set to *No* to hide the utilization columns.

Learn more about the availability settings in [Check fleet item availability and select fleet items](check-equipment-availability.md) and [Track rental fleet utilization](track-rental-fleet-utilization.md).

## Number sequences tab

The **Number sequences** tab lists every number sequence that rental management uses in this legal entity, and shows the number sequence code assigned to each one. The records numbered here include the following:

- Rental contracts
- Rental quotations
- Fleet item movements
- Call-off documents
- Invoice schedules
- Transfer requests
- Fleet item reservations
- Fleet items
- Rental rates
- Insurance records
- Utilization transactions
- Fleet item damage history
- The vouchers that the *Revenue split for swapped fleet item* periodic job posts

## Related information

- [Set up rental reference data](set-up-rental-reference-data.md)
- [Set up rental templates](set-up-rental-templates.md)
- [Configure prerequisites for rental management](set-up-rental-prerequisites.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Track rental fleet utilization](track-rental-fleet-utilization.md)
- [Run rental management periodic jobs](run-rental-periodic-jobs.md)
