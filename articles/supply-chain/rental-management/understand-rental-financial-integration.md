---
title: Understand rental management financial integration (preview)
description: Learn how rental management integrates with the general ledger, fixed assets, sales tax, and accounts receivable when you rent out fleet items.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form:
ms.topic: concept-article
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Understand rental management financial integration (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental management integrates with several financial modules in Dynamics 365 Finance and Supply Chain Management, including the general ledger, fixed assets, accounts receivable, and sales tax. This article describes the financial flow from purchasing fleet items through renting and invoicing them, and explains the key configuration that drives ledger postings, depreciation, and tax calculations.

This article is intended for finance teams and IT administrators who configure and maintain the financial aspects of the rental management system.

## Understand the fleet item lifecycle financial flow

The following sections describe the financial transactions at each stage of the fleet item lifecycle.

### Step 1 – Purchase fleet item

When you create and process a purchase order for a new fleet item:

1. **Product receipt** – The system creates:
    - An inventory transaction (purchase received).
    - A general ledger voucher for the receipt, if the item model group posts physical inventory.

1. **Vendor invoice** – The system creates:
    - A vendor invoice transaction.
    - A general ledger voucher that reverses the accrual and creates the vendor balance entry.

Rental management doesn't change these postings. The main accounts come from the standard inventory posting for the fleet item's item group. The item model group decides whether physical and financial inventory are posted to the ledger, as for any other stocked item.

<a name="transfer-from-new-to-rental"></a>

### Step 2 – Transfer from new fleet to rental fleet

When you transfer a fleet item from a fleet type whose **Value tracking method** is *Inventory* (such as *New*) to a fleet type whose value tracking method is *Fixed asset* (such as *Rental*):

1. The system creates a fixed asset for the fleet item, or reuses the fleet item's existing fixed asset. It uses the **Fixed asset group** and **Book** set on the **Posting configuration for fleet types** page for the target fleet type and the fleet item's item group. If there's no record for the item group, the record for all items is used. One of those records must exist for the target fleet type, and it must name a book.
1. The fixed asset ID comes from the number sequence of the fixed asset group, or from the fixed asset number sequence in the fixed assets parameters, and is otherwise the fleet item ID. A bulk fleet item always takes its ID from one of those number sequences. Learn more in [Configure prerequisites for rental management](set-up-rental-prerequisites.md#configure-fixed-asset-groups).
1. The system creates and posts an inventory journal of type *Fixed assets*, using the journal name in **Transfer request inventory asset journal** on the **Rental parameters** page. The journal issues the fleet item from inventory and posts a fixed asset *Acquisition* for the fleet item's posted inventory cost value. The fleet item must be in stock, so receive it into inventory before you run the transfer.
1. The inventory side of the voucher uses the item group's **Fixed asset issue** account, or its **Inventory issue** account if no fixed asset issue account is set up. When your sites are linked to a financial dimension, the new fixed asset takes the dimension value of the site where the fleet item is in stock. The fleet item's other financial dimensions don't change.

The **fixed asset posting profile** for the fixed asset's book determines the acquisition account used in the ledger entry.

### Step 3 – Create and activate a rental contract

When you create and activate a rental contract:

- The system populates contract lines from the rental template: the main rental fee plus any charge lines. A charge line applies either to the contract header or to a fleet item line, and it's recurring, once, or supplemental. That combination determines when the charge is invoiced.
- The system assigns the **sales tax groups**: it derives the sales tax group from the address that **Ship to** makes authoritative, and the item sales tax group from the line. Learn more in [How tax groups are determined](#how-tax-groups-are-determined).
- The system determines the **terms of payment** from a configurable hierarchy. Learn more in [Understand payment terms defaulting](#understand-payment-terms-defaulting).

### Step 4 – Generate and post rental invoices

Rental invoicing creates an *invoice schedule* from the contract, which then generates an ordinary *sales order* that you post. The standard Accounts receivable setup numbers the order and posts the invoice, so the customer balance, the invoice journal, and settlement behave as they do for any sales invoice.

1. **Generate invoice schedule** – Creates the schedule without any ledger postings. The schedule has header information (terms of payment, total amount, period, tax groups) and lines that mirror the contract lines.
1. **Generate sales order** – Creates the sales order for the invoice schedule.
1. **Post invoice** – Posts the sales order invoice, which creates:
    - Customer balance entries in accounts receivable.
    - Revenue postings for the main rental fee. When fleet items are active on the line, the system splits the revenue across them and posts each fleet item's share separately. Learn more in [Revenue posting for rental invoices](#revenue-posting-for-rental-invoices).
    - Revenue postings for supplemental charges such as freight (from inventory posting, using the sales category defined on the revenue category).
    - Sales tax transactions calculated from the sales tax group and item tax group.
    - **Revenue-based depreciation** for the fixed asset (if configured). Learn more in [Understand revenue-based depreciation](#understand-revenue-based-depreciation).

> [!NOTE]
> There's always a 1:1 relationship between an invoice schedule and a sales order. Invoice schedule lines match sales order lines in amounts, prices, sales categories, and tax information. The relationship holds through the full lifecycle, including credit notes.

### Step 5 – Transfer or sell the fleet item

When a fleet item leaves the rental fleet, the postings depend on where it goes:

- **To another *Fixed asset* fleet type** (for example, *Rental* to *Lease*) – When the fixed asset book changes, the system posts a *Fleet item transfer* transaction that moves the net book value to the target book.
- **To an *Inventory* fleet type** (for example, *Rental* to *Used*) – The system posts a fixed asset disposal for the net book value and receives the fleet item into inventory at the same value.
- **To a customer** – Sell the fleet item from an *Inventory* fleet type on a sales order. Posting the sales invoice posts revenue and cost of sale, as for any other stocked item.

Learn more in [Understand fleet transfer financial impact](#understand-fleet-transfer-financial-impact) and [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md).

## How tax groups are determined

Every rental document line carries two values that decide how it's taxed: a **sales tax group**, which follows the place that you deliver the rental to, and an **item sales tax group**, which follows what you rent out. The system sets both automatically, you can override both, and both flow unchanged into the invoice schedule and then into the sales order that posts the invoice.

### The sales tax group follows the ship-to address

The sales tax group on the header comes from whichever address the **Ship to** rule makes authoritative, not from the customer record alone:

| **Ship to** | Sales tax group is taken from |
|---|---|
| **Job site** | The tax group registered on the job site's location. |
| **Pickup fleet location** | The tax group registered on the location of the delivery address. |
| **Address** or **Customer** | The tax group on the customer account. |

This factor matters wherever tax is charged at the destination rather than at the seller's address. A contract delivered to a job site in another jurisdiction is taxed for that jurisdiction, and it changes as soon as **Ship to** or the job site changes. Learn more about the rule itself in [Set where the delivery goes](create-rental-quotations-contracts.md#set-where-the-delivery-goes).

When the header sales tax group changes, the system copies it to every line **except** lines that have **Use separate address** turned on. Those lines keep their own tax group.

A line that uses a separate address derives its own sales tax group from its own **Ship to** value, and it does so for only two of the four values:

- **Job site** and **Pickup fleet location** set the line's sales tax group from that address.
- **Address** and **Customer** change the line's address but leave its sales tax group as it was.

So a separate-address line that you switch to *Customer* keeps the tax group that it was last given. Check the line's tax group after you change its address rule.

### The item sales tax group follows the line

The system resolves the item sales tax group in this order, and the first value that exists wins:

1. **The prime line it's attached to.** An attachment line takes the item sales tax group of the fleet item line that it belongs to, so an attachment is always taxed like the fleet item that it goes out with.
1. **The rental class** on the line, if that class has an item sales tax group.
1. **The revenue category** on the line.

The system resolves the value when you create the line, and again whenever you change the line's **Rental class** or **Revenue category**.

> [!IMPORTANT]
> Changing the rental class or the item sales tax group on a prime line also sets the item sales tax group on its attachment lines that aren't closed, so that each attachment is taxed like its prime. Closed lines aren't affected.

### Tax is calculated at today's rate

When the system calculates tax for display on a quotation or a contract, it looks up the tax rate as of **the current date**, not the invoicing date and not the dates of the rental period. On a contract that spans a rate change, the amount shown before the invoice is raised can differ from the amount that posts. The posted invoice is taxed by the sales order that it's raised on, in the standard way.

### Where you can review the calculated tax

The system shows sales tax at these points, in addition to the posted invoice:

- The **Quotation summary** and **Contract summary** steps of the rental cart.
- The contract closing wizard, on the **Review contract closing information** step, alongside the rental fee and overtime charges. Learn more in [Close a contract with the closing wizard](call-off-close-rental-contracts.md#close-a-contract-with-the-closing-wizard).
- The best rate calculation, which prices a recalculation with tax as well as net and offers a **Tax details** breakdown. Learn more in [See the sales tax on a rate estimate](call-off-close-rental-contracts.md#see-the-sales-tax-on-a-rate-estimate).
- A pro forma invoice, which calculates tax without posting anything. Learn more in [Generate pro forma invoices](#generate-pro-forma-invoices).

## Understand how ledger accounts are determined

Rental management doesn't have a separate posting profile for fleet items. Each fleet item transaction posts through the standard posting setup of the module that creates it:

| Transaction | Where the ledger accounts come from |
|---|---|
| Purchase product receipt and vendor invoice | The inventory posting for the fleet item's item group, as for any other stocked item. |
| Fleet transfer from an *Inventory* fleet type to a *Fixed asset* fleet type | The item group's **Fixed asset issue** account (or its **Inventory issue** account) for the inventory side, and the acquisition account of the fixed asset posting profile for the fixed asset side. |
| Fleet transfer from a *Fixed asset* fleet type to an *Inventory* fleet type | A *Disposal - sale* fixed asset transaction that uses the posting profile in the fixed assets parameters. The inventory movement that receives the fleet item uses the disposal's offset account. |
| Fleet transfer between two *Fixed asset* fleet types | When the fixed asset moves to a different book, the **Fleet item transfer** posting type on the fixed asset posting profile that's selected as **Transfer posting profile** on the **Rental parameters** page. A change of only the fixed asset group can instead be reversed and reposted with the posting profile of the fixed asset's book. Learn more in [Understand fleet transfer financial impact](#understand-fleet-transfer-financial-impact). |
| Rental invoice revenue | The sales order revenue account that inventory posting assigns to the sales category of the line's revenue category. |
| Revenue-based depreciation | The fixed asset posting profile of the fleet item's asset book. |
| Sales invoice for a fleet item that's still tracked as a fixed asset | A fixed asset disposal that uses the fixed asset posting profile that's selected as **Asset posting profile** on the **Rental parameters** page. A credit note for the invoice reverses the disposal. Fleet item availability doesn't let you add a fleet item in a *Fixed asset* fleet type to a sales order, so you normally transfer it to an *Inventory* fleet type before you sell it. Learn more in [Sell fleet items from the rental fleet](sell-equipment-from-rental-fleet.md). |

A fleet transfer assigns the fixed asset group and book set up on the **Posting configuration for fleet types** page for the target fleet type and the fleet item's item group. That page holds a fleet type, an item code and item group, a fixed asset group, and a book. It doesn't hold ledger accounts. Learn more in [Configure posting for fleet types](configure-inventory-location-settings.md#configure-posting-for-fleet-types).

### Revenue posting for rental invoices

Revenue for each rental invoice line follows the revenue category on the line:

1. Each line, including the main rental line, has a **Revenue category**.
1. Each revenue category has a **sales category** assigned to it. The invoice schedule line takes that sales category, and so does the sales order line that posts the invoice.
1. The sales category determines the revenue account: the **Revenue** account on the **Sales order** tab of inventory posting (**Inventory management** > **Setup** > **Posting** > **Posting**), with **Item code** set to *Category*.

When fleet items are active on the main rental line, the system splits the line amount across those fleet items when it creates the invoice schedule line. Each fleet item's share is based on its revenue percentage on the line, prorated for the days that the fleet item was on the line in the invoice period. The invoice then posts one revenue entry for each fleet item's share, instead of one entry for the whole line, so revenue-based depreciation and utilization follow the fleet item.

This setup means the main rental fee and supplemental charges can post to different revenue accounts, giving finance teams granular control over revenue recognition.

## Understand revenue-based depreciation

When a rental invoice posts, the system can automatically calculate and post fixed asset depreciation from the invoiced revenue. Configure it as follows:

1. On the book at **Fixed assets** > **Setup** > **Books**, assign a depreciation profile that uses the **Revenue based** method. The system reads the method from the depreciation profile on the book setup, not from the profile on the individual fixed asset's book.
1. Enter the **Revenue based depreciation percentage** on the fixed asset's book (for example, 90%). If you leave it blank, the percentage from the book's depreciation profile is used instead.
1. When you post a rental invoice, the system multiplies that percentage by the revenue split amount allocated to the fleet item, not by the invoice total, and posts the result as depreciation on the fixed asset. Because the calculation follows the revenue split, a fleet item that you swap mid-contract depreciates only on the revenue that's allocated to it.

The depreciation is limited to the remaining net book value, unless the fixed asset's book is set to allow a negative net book value. A fleet item whose net book value is already zero, for example because its acquisition was never posted, gets no depreciation.

The **fixed asset posting profile** determines the depreciation main account, using the asset group, book, and depreciation transaction type.

### Book requirements at invoice posting

Each fleet item that receives revenue from a posted rental invoice, and whose fleet type has the **Value tracking method** set to *Fixed asset*, is checked when the invoice posts. The check runs whether or not the book is revenue based:

- The fleet item must have a fixed asset.
- Unless all of the fixed asset's books are closed, exactly one of them must be *Open* and use a book whose **Posting layer** is *Current* and that has a depreciation profile.

The system posts revenue-based depreciation only to that one book, and only when its depreciation profile uses the **Revenue based** method.

> [!NOTE]
> An asset book that uses the **Revenue based** method is excluded from the standard depreciation proposal, and a proposal that includes it creates no depreciation for that book. Revenue-based assets depreciate only when rental invoices post.

## Understand SMU-based depreciation

SMU-based depreciation reduces the value of a fleet item by the hours that it runs, instead of by elapsed time or by invoiced revenue. The system multiplies the service meter units (SMU) that are reported on the fleet item's usage history by a depreciation rate per hour, and it stops depreciating when the asset reaches its residual value.

This method suits fleet items whose wear follows usage rather than the calendar, such as generators, compactors, and aerial work platforms.

### Configure SMU-based depreciation

The setup spans both the depreciation profile and the asset group book, so complete the following steps in order.

1. On the depreciation profile, set the **Method** to *SMU based*.
1. Optionally, enter a **Day** on the depreciation profile. This value is the day of the month that determines the last day of each depreciation period, so that depreciation periods can follow a rental billing cycle instead of the calendar month end. Enter a value from 1 through 31.
1. On the asset group book setup, enter the **SMU useful life** (the useful life of the fleet item, in hours) and the **Residual value %** (the residual value as a percentage of the total acquisition cost). Asset books that are created from this setup inherit both values.
1. On the asset book, review the inherited values. To use a different percentage for a single fleet item, set **Override %** to *Yes*, and then enter the **Residual value %** for that book.

From this setup, the system derives the two amounts that drive the calculation.

| Field | How it's determined |
|---|---|
| **Residual value** | The total cost of the fleet item multiplied by the **Residual value %**. |
| **Depreciation rate per hour** | The rate that's applied to each reported hour. |

> [!IMPORTANT]
> **SMU useful life** is required on every book whose depreciation profile uses an SMU-based method.

### Run SMU-based depreciation

Unlike revenue-based depreciation, SMU-based depreciation runs through the standard fixed asset depreciation proposal. For each period, the system multiplies the hours that are reported on the fleet item's usage history by the **Depreciation rate per hour**. It then limits the result so that the net book value never falls below the **Residual value**.

Hours that are depreciated are marked **Used for depreciation** on the fleet item's usage history, so the same hours are depreciated only once.

To review the result, go to **Fixed assets** > **Inquiries and reports** > **SMU based depreciation** > **SMU based - Fixed asset transactions**. For each transaction, the inquiry shows the **Hours used**, the **Total hours used** up to the transaction date, and the **Net book value (SMU based)** after the transaction.

> [!NOTE]
> The SMU readings on a fleet item's usage history must not decrease, because a decrease would make a period's depreciation negative. Correct the usage history before you run the proposal.
>
> Before you void a meter reading that depreciation uses, delete its line from the unposted depreciation journal or reverse the posted fixed asset transaction, and then recalculate and post depreciation for the period.

## Use standard depreciation methods

Rental management adds the **Revenue based** and **SMU based** methods to the standard set. It doesn't remove or replace any of the other methods. Every depreciation method that Finance supports remains available for fleet items. You select the method on the depreciation profile in the usual way.

| Method | Depreciation is driven by |
|---|---|
| **Straight line service life** | The service life of the asset, in equal amounts per period. |
| **Straight line life remaining** | The remaining service life, recalculated from the remaining net book value. |
| **Reducing balance** | A fixed percentage of the remaining net book value. |
| **200%, 175%, 150%, and 125% reducing balance** | An accelerated percentage of the remaining net book value. |
| **Manual** | Percentages that you enter for each interval. |
| **Factor** | A factor that produces a progressive or digressive schedule. |
| **Consumption** | Units of consumption that you record against the asset. |
| **Revenue based** | The revenue that's invoiced for the fleet item. Added by rental management. |
| **SMU based** | The hours that the fleet item runs, taken from its usage history. Added by rental management. |

Learn more about the standard methods, and about the depreciation conventions that determine how the first and last periods are calculated, in [Depreciation methods and conventions](../../finance/fixed-assets/depreciation-methods-conventions.md).

> [!TIP]
> **Consumption** and **SMU based** both depreciate by usage, but they take that usage from different places. Consumption depreciation uses units that you record against the fixed asset. SMU-based depreciation uses the meter readings that are already captured on the fleet item's usage history, so no separate entry is needed.

A fleet item can move to a different depreciation method when you transfer it to a fleet type that uses a different book. The fleet transfer moves the asset out of the source book and into the target book. Learn more in [Understand fleet transfer financial impact](#understand-fleet-transfer-financial-impact).

## Understand payment terms defaulting

A configurable hierarchy on the **Rental parameters** page determines the terms of payment on a rental contract:

1. Go to **Rental management (Preview)** > **Setup** > **Rental parameters**, open the **Other** tab, and then open **Payment terms defaulting**.
1. Move **Customer** and **Rental template** from **Options** into **Selected defaulting sequence** in the order they should be checked. The system doesn't use sources that aren't in the sequence.

The system checks each source in order and uses the first one that has a value defined:

| Source | Description |
|---|---|
| **Customer** | The terms of payment on the invoice customer's account. |
| **Rental template** | The terms of payment on the rental template. |

This hierarchy lets you set customer-specific payment terms and fall back to the template default. The terms of payment also set the due date of the posted invoice. However, if you turn on **Due date from schedule** at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Invoicing** tab, the invoice takes the due date that's carried on the invoice schedule instead.

## Generate pro forma invoices

A pro forma invoice calculates and displays invoice amounts (including sales tax) without creating any transactions in the system. Pro forma invoices are useful for sharing with customers whose accounting departments need to align purchase orders with expected rental charges before you generate the actual invoice.

To generate a pro forma invoice, follow these steps:

1. Open the rental contract.
1. Select **Proforma** on the Action Pane.
1. Set **Invoice until** to a date past the invoice method threshold—for example, past day 17 for a 17-day invoice method.
1. Leave **Print** selected. It's always selected for a pro forma.
1. Select **OK** to generate the pro forma report.

The pro forma calculates sales tax by using the tax groups already defined on the contract, but it doesn't create any invoice schedules, sales orders, or ledger entries.

## Record payment deposits on rental contracts

You can record a customer payment deposit during the contract creation process or on a contract that already exists, in cash, by check, or by credit card. This record is useful when a customer provides a deposit to secure the contract.

To record a deposit, follow these steps:

1. Turn on **Use cash register** at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Cash register** tab, and make sure that your user is linked to a worker.
1. In the contract creation wizard, on the **Contract summary** step, under **Down payment**, select **Add payment**. On a contract that already exists, select **Add payments** in the **Payments** group on the **Rental** tab of the Action Pane.
1. In the **Enter customer payment information** dialog, select the **Payment method** and enter the **Payment amount**. Select **Prepay** when the payment is collected now. In the **Payment information** group, enter a **Payment reference**, such as a check number, and a **Description**.
1. Select **Submit**. A card payment that's marked **Prepay** is charged, and its journal is created and posted for you. A card payment that isn't marked **Prepay** is only authorized, and no journal is created until the payment is captured.

Payments are collected per person and per day. Submitting a payment adds a line to the open customer payment journal of your worker, for today's date and the selected method of payment, and creates that journal when none exists. Each employee therefore has one journal per day and method of payment to reconcile. A journal name must be available, either on the method of payment in the cash register payment setup or as **Default cash register journal name** on the **Cash register** tab of the rental parameters. The person who collects the payment must also be linked to a worker.

The journal that's created is a cash register journal. The system fills in its cash register fields and keeps the link back to the rental contract, so you don't record either yourself.

After the journal is created, you can post it and auto settle it against future rental invoices by using the standard customer payment settlement process.

### Capture an authorized credit card payment

You capture an authorized card payment from the contract, in full or in parts.

1. On the rental contract, on the **Rental** tab of the Action Pane, in the **Payments** group, select **View payment details**. The **Customer payments** page opens for the contract and lists each payment with its method, amount, and status.
1. Select a credit card payment whose status is *Authorized*, and then select **Credit card** > **Capture**.
1. In **Capture payment**, check the **Authorization balance**, and then enter the **Capture amount**. It defaults to the most that you can capture: the lower of the authorization balance and the part of the payment amount that isn't captured yet.
1. Select **Capture**.

Each capture posts its own customer payment journal against the contract. While an authorization balance remains, the payment stays *Authorized* and you can capture again, and it becomes *Paid* when the captured total reaches the payment amount. Repeated partial captures need a payment connector that supports incremental capture. **Credit card** > **Void** releases an authorization while nothing is captured.

### Review and delete payments on a contract

The **Payments** group also includes **View journal details**, which opens **Payment journal details**. That page lists the customer payment journal lines registered for the contract and shows whether they're posted. To remove a payment that you entered by mistake, select its line and then select **Delete payment**. This option is available only while the line's journal isn't posted.

## Handle invoice schedule credit notes

When you need to correct a posted rental invoice, create a credit note from the invoice schedule rather than from the sales order.

To create a credit note, follow these steps:

1. On the rental contract, open **Invoice schedules**.
1. Select the invoiced schedule that you want to credit. You can only credit the latest uncredited schedule on the contract.
1. On the **Invoice schedule** tab, in the **Credit** group, select **Credit note**, or select **Partial credit note** and change the quantity or unit price on its lines before you post.
1. If **Reason code for credit** is turned on on the **Rental parameters** page, select a reason code.
1. The system creates a new invoice schedule entry with negative amounts and a *Credit* type indicator.
1. Generate and post the credit. The system creates a corresponding credit sales order.

After crediting, you can regenerate the invoice schedule for the same period with corrected data.

> [!NOTE]
> An invoiced schedule can't be deleted. Credit it, and then recreate it. Delete schedules newest first, because a schedule can't be deleted while a later schedule exists on the contract. A schedule whose sales order is already generated can't be deleted either; select **Delete** > **Sales order** to delete the sales order and return the schedule to *Open* first.

## Use financial dimensions on rental documents

Use financial dimensions to classify accounting entries, for example by department or cost center. Dimension values form part of the ledger account and support financial reporting. Use financial tags for additional transaction references, such as a rental contract or job site reference, that you want to analyze without adding another ledger account segment. A financial tag doesn't select the main account.

Configure financial dimensions, their values, and the account structures for your legal entity by using the standard Finance setup. On rental quotations, contracts, and invoice schedules, review the **Financial dimensions** in the header details and line details. Learn more in [Financial dimensions](../../finance/general-ledger/financial-dimensions.md).

### Understand dimension defaults

- The rental quotation or contract header takes its default financial dimensions from the customer.
- When you add a fleet item and create a rental line, the system keeps dimension values already on the line, then fills remaining values from the document header and the fleet item, in that order. Standard rules for linked dimensions still apply.
- You can copy a change to header dimensions to existing lines when you confirm the corresponding header-to-line update. Review the resulting line values, especially where a line needs a different accounting classification.
- The invoice schedule takes header dimensions from the rental document header and line dimensions from the corresponding rental lines.

For example, suppose a new line has no dimension values yet, the rental header has **Department** set to *Rental*, and the fleet item has **Cost center** set to *Branch 01*. The line can take both values. If the fleet item also has a different **Department**, the header value takes precedence over that fleet item value, subject to the configured linked-dimension rules.

### Review dimensions before posting

Before you post an invoice schedule, review its header and line dimensions. For a line whose revenue is divided among fleet items, open **Revenue split** and review the dimensions on those rows too. These values provide the accounting context for the revenue entries and any revenue-based depreciation that the invoice posts for each fleet item.

Changes to an unposted document don't change entries that are already posted. Use the invoice schedule credit process for accounting corrections, as described in **Handle invoice schedule credit notes** in this article.

## Use financial tags on rental documents

When you configure financial tags for the legal entity, a **Financial tags** tab appears in the following places:

- The header details and the line details of rental quotations and contracts
- The header details and the line details of **Invoice schedules**
- **Miscellaneous charges** lines
- The **Revenue split** page

The rental process carries the tags that you enter there to the documents that it creates:

- The invoice posting
- The revenue split and revenue-based depreciation postings
- The fixed asset postings and the fleet transfer journals
- The Fire-Theft-Vandalism Waiver charges
- The quotation journals

A reversal or a cancellation keeps the tag of the transaction that it corrects. Changing the tag on a contract line or an invoice schedule line also updates the unposted sales tax records, so the sales tax transactions carry the same tag. A deposit that you enter from the contract stamps its tag on the customer payment journal line.

The rental contract and quotation header and line entities expose the financial tag, so an integration can set it.

### Set up financial tags

Set up tags separately for each legal entity where you use rental documents.

1. In **Feature management**, make sure **Financial tags** is enabled. For the sales orders used to invoice rental contracts, also enable **Enable financial tags for sales order invoicing**. If you use tags on fleet item purchase orders, enable **Enable financial tags for purchase order invoicing**.
1. Open **General ledger parameters**, select **Financial tags**, and define the delimiter before you create tags. Choose a character that isn't used in your tag values.
1. Go to **General ledger** > **Chart of accounts** > **Financial tags** > **Financial tags**. Select **New**, enter a label, and choose the **Value type**. For example, create a tag named *RentalReference* with the value type *Text*.
1. Select **Activate** to make the tag available for transaction entry.

Learn more about value types, lists, and legal-entity configuration in [Financial tags](../../finance/general-ledger/financial-tag.md).

### Follow tag values through the rental workflow

Enter the common tag values on the rental quotation or contract header before adding fleet item lines.

- New main fleet item lines inherit the header's tag values.
- Attached lines inherit the tag values of their parent line. When a line is split into separate fleet item lines, the split lines retain the original line's tags.
- Invoice schedule headers and lines take the tags from their corresponding rental document headers and lines.

These inherited tag values are copied as one set. They are separate from the financial dimension defaults described above. Review the **Financial tags** on each line and enter any line-specific values before creating the invoice schedule. After changing a header value, also review any lines that already exist.

### Example: trace a rental reference to the posted invoice

To follow a reference through a rental invoice, follow these steps:

1. Create and activate the *RentalReference* tag as described earlier.
1. On a rental contract, open the header **Financial tags** and enter *JOB100* for **RentalReference**.
1. Add a main fleet item line and an attached line. Review their **Financial tags**. They inherit *JOB100*. If a line needs a different reference, enter that value on the line.
1. Create the invoice schedule and review the **Financial tags** on its header, lines, and any **Revenue split** rows before posting.
1. Post the invoice, and then review its accounting entries on **Voucher transactions**. Check the tag values on the relevant revenue entries. Header and line values can differ, so review the entry that corresponds to the line you're tracing.

Tags appear as separate columns on the posted accounting entries and can be used for filtering and detailed analysis. Use financial dimensions for dimension-based financial statements and trial balances. Learn more in [Differences between financial tags and financial dimensions](../../finance/general-ledger/financial-tag-financial-dimension.md).

## Understand fleet transfer financial impact

What a fleet transfer posts depends on the value tracking methods of the source and target fleet types. Learn more about the supported combinations in [Supported fleet transfers](configure-inventory-location-settings.md#supported-fleet-transfers).

- **From *Inventory* to *Fixed asset*** (for example, *New* to *Rental*) – The system creates the fixed asset and posts its acquisition, as described in [Step 2 – Transfer from new fleet to rental fleet](#transfer-from-new-to-rental).
- **From *Fixed asset* to *Inventory*** (for example, *Rental* to *Used*) – The system posts a fixed asset journal with a *Disposal - sale* line for the net book value of the fleet item's open book. The journal name comes from **Transfer journal** on the **Fixed assets** tab of the rental parameters. It then posts an inventory movement journal, using **Transfer request movement journal**, that receives the fleet item at the same value into the warehouse that's specified on the transfer request. The movement journal's offset account is the disposal line's offset account.
- **Between two *Fixed asset* fleet types** (for example, *Rental* to *Lease*) – The system compares the fixed asset group and book set up on the **Posting configuration for fleet types** page for the target fleet type with the fixed asset's current group and open book:
    - If neither the book nor the group changes, the system doesn't post fixed asset transactions, except for a bulk fleet item. A bulk fleet item holds one fixed asset per fleet type, so the system always posts it into the target fleet type's book, and the group-only reversal option doesn't apply to it.
    - If the book changes, the system posts a *Fleet item transfer* transaction that moves the net book value out of the source book and into the target book, which can use a different depreciation profile. The transferred amounts are summarized, unless **Transfer with details** is set to *Yes* on the **Rental parameters** page, which moves the balances at the transaction type level.
    - If only the group changes, and **Reversal when only fixed asset group changes** is set to *Yes* on the **Rental parameters** page, the fixed asset transactions are reversed for the old group and posted again for the new group. If it's set to *No*, the change is posted in the same way as a change of both the book and the group.

The *Fleet item transfer* transaction uses the fixed asset posting profile that's selected as **Transfer posting profile** on the **Rental parameters** page. That profile needs an offset account for the **Fleet item transfer** posting type. All of these transactions post on the transfer date. When **Transfer on system date** is turned on on the **Rental parameters** page, that date is the current date. When it's turned off, you enter the transfer date as you complete the transfer.

If the source book carries posted depreciation and the target fleet type's book is set not to calculate depreciation, the system asks whether to continue and transfer the previously posted depreciation. If you answer no, the fleet transfer is canceled.

Fleet transfer rules define which fleet-to-fleet transfers are allowed. To configure transfer rules, go to **Rental management (Preview)** > **Setup** > **Transfers** > **Transfer rules**.

Rental businesses can therefore change depreciation methods when a fleet item moves between fleet types—for example, straight line service life depreciation in the rental fleet changing to SMU-based depreciation in the lease fleet. Learn more in [Use standard depreciation methods](#use-standard-depreciation-methods).

## Related information

- [Rental management overview](rental-management-overview.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Add fleet items to the rental fleet](add-equipment-to-rental-fleet.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
