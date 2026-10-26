---
title: Run rental management periodic jobs (preview)
description: Learn how to configure and run the periodic batch jobs for rental invoicing, insurance expiry checks, utilization, and carrying cost.
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

# Run rental management periodic jobs (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental management includes several periodic batch jobs that automate routine tasks such as invoice generation, insurance monitoring, reservation cleanup, and utilization calculations. This article describes the available periodic jobs, how to configure them, and the recommended scheduling patterns that rental businesses use.

To access periodic jobs, go to **Rental management (Preview)** > **Periodic jobs**. The invoicing jobs and the invoicing exception list are in the **Invoicing** submenu, and the rate priority job is in the **Rates and discounts** submenu.

## Generate and post invoice schedules

The invoice schedule batch jobs are the most important periodic jobs in rental management. They automate the billing cycle so that rental coordinators can focus on reviewing invoices rather than manually identifying which contracts need to bill.

### Recommended billing workflow

Most rental businesses use a two-phase nightly batch process:

1. **Nightly generate** – The *Generate invoice schedules* batch job runs each night, identifying all active contracts where the invoice method threshold is met (for example, 17 days into the rental period). The job creates invoice schedules without posting any transactions.
1. **Daytime review** – During the next business day, the rental team reviews the generated invoice schedules. They verify purchase order numbers, check rates, and delete or adjust any schedules that need correction.
1. **Nightly post** – Before the next generate job runs, the **Post invoice schedules** batch job creates sales orders for any schedules still in *Open* status and then posts the customer invoices for *Ordered* schedules.

Some rental businesses prefer a more conservative approach where users manually post each invoice after review. Other rental businesses that are confident in their billing practices combine generate and post into a single nightly run using the *Generate invoice schedules and invoices* job.

> [!IMPORTANT]
> Review **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Rental invoicing batch job exceptions** daily to confirm that all contracts were invoiced. Learn more in [Invoice rental contracts](invoice-rental-contracts.md#resolve-invoicing-failures-and-correct-a-posted-period).

### Invoice exemptions

The jobs process rental contracts whose status is *Active*. To leave specific contracts out of a run, filter them out under **Records to include** in the job dialog, and invoice them from the contract instead. Customer-level miscellaneous charge exemptions are configured separately at **Rental management (Preview)** > **Setup** > **Miscellaneous charge exemptions**.

## Run the insurance expiry check

The insurance expiry check identifies physical damage insurance policies that are about to expire, so you can follow up with the customer before coverage lapses. It reads the customer insurance certificates that are registered at **Rental management (Preview)** > **Setup** > **Insurance**. Learn more in [Manage customer and prospect records for rental](manage-customer-prospect-records.md).

To run the insurance expiry check, follow these steps:

1. Go to **Rental management (Preview)** > **Periodic jobs** > **Insurance expiry check**.
1. Set the **Expiry time** parameter, in days. This value defaults from the value configured in rental parameters (for example, 30 days). The job finds open physical damage insurance that expires within this window, measured from today's date, and sets those insurance records to *Expiry logged*.
1. Set **Add miscellaneous charge**, which is selected by default. When it's selected, the job adds the *Fire-Theft-Vandalism Waiver* or *Loss waiver* charge from the rental template to contract lines whose insurance expires within the **Expiry time**.

> [!TIP]
> Most rental businesses clear **Add miscellaneous charge**. They prefer to run the expiry check, review the results, follow up with the customer to request updated insurance documentation, and only add the damage waiver charge if the customer doesn't respond within a reasonable period.

After you run the job, review the insurance expiry log at **Accounts receivable** > **Inquiries and reports** > **Payments** > **Insurance expiry log** to see which contracts have customers with expiring insurance and follow up accordingly.

## Manage reservation and quotation expiry

Two batch jobs at **Rental management (Preview)** > **Periodic jobs** help keep the reservation and quotation lists clean:

- **Reservation expiry** – Sets active reservations whose expiry date has passed to *Expired*, freeing up the reserved fleet item for other deals.
- **Update expiring quotations** – Sets quotations to an *Expired* status. The job affects only quotations in *Sent* status, and it uses today's date plus the **Days** value that you enter in the job dialog, so a positive value expires quotations before they actually lapse. The sales team can then review expired quotations and flag them as lost if the customer didn't convert.

Schedule both jobs to run daily so that coordinators and sales representatives always work with current reservation and quotation data.

## Calculate overtime

When you calculate overtime charges monthly (common for high-value fleet items on long-running engagements), use the overtime calculation batch job at **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Overtime calculation**. The same calculation is available as **Overtime calculation** on the rental contract Action Pane, where it's narrowed to that one contract.

The job evaluates customer usage for the billing period by comparing the allowed shift hours against the actual service meter readings. If a customer exceeds the allowed hours, the system calculates the overtime charge that appears on the next cycle bill. The job processes the main lines of active contracts. Unless the rental template uses calendar-based invoicing, it skips called-off lines and lines whose **Overtime billing method** is *End of contract*.

Whether the calculated overtime is reviewed is decided per contract line by **Approval required**. When it's cleared, the overtime is approved and priced without review. Usage that stays inside the allowance creates no record, so only exceeded allowances reach the approval list. The approval list is at **Rental management (Preview)** > **Common** > **Rental contracts** > **Rental overtime approvals**.

## Calculate utilization

Several batch jobs at **Rental management (Preview)** > **Periodic jobs** maintain the utilization metrics that rental managers use to monitor fleet performance:

| Batch job | Description |
|---|---|
| *Calculate fleet item utilization* | Aggregates the utilization transactions into a summary row for each fleet item and calculates time and financial utilization. It processes only fleet items in fleet types whose **Value tracking method** is *Fixed asset*, and it always calculates as of the current date. |
| *Generate utilization transactions* | Backfills utilization transactions for invoiced revenue-split records that don't have one yet. Transactions are normally written when the rental invoice is posted. It processes fleet items in fleet types whose **Value tracking method** is *Fixed asset*, *Inventory*, or *Manual*. |
| *Update utilization transactions* | Sets invoiced days to zero on utilization transactions whose period code is an overtime or a stand-down period, so that those lines don't inflate time utilization. Run it after you flag a period code as an overtime or a stand-down period, and after the **Revenue split for swapped fleet item** job. |
| *Delete utilization transactions* | Deletes the utilization summary and the utilization transactions of fleet items in fleet types whose **Value tracking method** is *Manual* or *Customer*, when the fleet item hasn't changed fleet type for more than a year. Deleted data isn't regenerated. |

Schedule the generate and calculate jobs to run at least daily so that utilization dashboards and the fleet item availability summary reflect current data. Extract the history you want to keep before you schedule the delete job. Learn more in [Track rental fleet utilization](track-rental-fleet-utilization.md).

## Update rental rates and fleet item data

Find the *Update rates, prices and ages on fleet item* batch job at **Rental management (Preview)** > **Periodic jobs** > **Fleet item** > **Update rates, prices and ages on fleet item**. It refreshes the rate, price, and age fields on every fleet item in a fleet type whose **Value tracking method** is *Fixed asset*, *Inventory*, or *Manual*, and it writes:

- **Rental age** and **Inventory age**, in months, counted from the fleet item's transfer date and received date.
- The default daily, weekly, monthly, and monthly calendar rates. These rates come from the rate for all customers of the fleet item's default rental class, with the default price factors from the rental parameters, for rate lines and period codes that are valid today.
- The **Asking price**, taken from the sales price of the fleet item's product. The asking price is the base for percentage charges that are calculated on it, and for rental purchase options.

**Fleet item availability** shows these values. The rate columns appear there only when **Rates in fleet item availability** is turned on at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Rates and discounts** tab, on the **Default price factor values** page.

Run the job after you post a trade agreement journal or change rental rates. To maintain the sales prices that the asking price comes from, open a price/discount journal and select **Maintain fleet item prices/discounts** on the lines toolbar. That command copies existing trade agreement lines into the journal, filtered by manufacturer, fleet type, or fleet item type.

### Update rate priority

One more rate job sits in its own submenu at **Rental management (Preview)** > **Periodic jobs** > **Rates and discounts**.

| Batch job | Description |
|---|---|
| *Update priority* | Recalculates the **Priority** on rental rates, discounts, or both, which determines the order in which rates are matched. |

The lowest priority value is matched first. Select *All*, *Rate*, or *Discount* in the job dialog to choose which records to restamp. Run the job after you change the sorting values on the **Rental parameters** page. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

### Update rental class definitions

Use the *Rental class change* batch job at **Rental management (Preview)** > **Periodic jobs** > **Rental class change** to replace one rental class with another, for example when you deprecate an old rental class. The job updates every fleet item that has the class as its default class, and every rental class definition line that refers to it, so you don't need to update each fleet item record yourself.

## Calculate carrying cost

Some rental businesses calculate the carrying cost of their rental fleet—the cost of the capital invested in the fleet. The *Calculate carrying cost* batch job processes every fleet item in the fleet types you select whose asset book has **Carrying cost** selected and a status of *Open*. It doesn't look at utilization or at whether the fleet item is on rent.

### Set up the carrying cost calculation

Go to **Rental management (Preview)** > **Setup** > **Rental parameters** and open the **Carrying cost** tab.

| Field | Description |
|---|---|
| **Carrying cost %** and **Per** | The rate, and the unit that it's expressed in: *Year*, *Month*, or *Day*. |
| **Calculation frequency** | The length of the period that each calculation covers: *Month*, *Year*, *Fiscal year*, or *Fiscal period*. The fiscal options follow the legal entity's fiscal calendar. |
| **Journal name** | The fixed asset journal name that the carrying cost journal is created in. |
| **Transaction text** | The text that's written on the journal lines. |
| **Transaction type** | *Acquisition*, *Acquisition adjustment*, *Revaluation*, *Write-up adjustment*, or *Write-down adjustment*. It sets the fixed asset transaction type, and the offset account that comes with it. |

Then select **Carrying cost** on each fixed asset book that should carry the cost.

### Run the calculation

Go to **Rental management (Preview)** > **Periodic jobs** > **Calculate carrying cost**. The **Fleet types** group has one check box for each fleet type whose **Value tracking method** is *Fixed asset*. Select the ones to include, and the job processes them whether you run it now or in the background. **Posting date** is the date of the fixed asset journal lines that the calculation creates. Set **Posting** to *Proposal* to create the journal for review, or to *Post* to post it as well.

For each fixed asset book that's *Open* and has **Carrying cost** selected, the amount is the net book value at the end of the period multiplied by the rate, converted to the length of the period. It's prorated from the asset's first transaction date when that date falls inside the period. The job skips a book that already has a carrying cost line for the period, so running it again for the same period adds nothing.

## Manage revenue split for swapped fleet item

When you exchange a fleet item mid-contract, you need to reallocate the revenue from that billing period between the two fleet items for depreciation. For example, fleet item A is on-site for two weeks before you swap it for fleet item B. The *Revenue split for swapped fleet item* batch job at **Rental management (Preview)** > **Periodic jobs** > **Revenue split for swapped fleet item** does that reallocation. It splits the revenue, the utilization, and the revenue-based depreciation of the invoiced period between the two fleet items, and posts the correction to the ledger.

The job requires the *Revenue split voucher for swapped fleet item* number sequence. Fleet items tracked as fixed assets must meet the fixed asset book requirements that apply at invoice posting, and none of their books can be sold or scrapped. Learn more in [Understand rental management financial integration](understand-rental-financial-integration.md#book-requirements-at-invoice-posting).

## Job site expiration

You can expire job sites when they're no longer active (for example, a data center construction project that's complete). Run the *Job site expiration* batch job at **Rental management (Preview)** > **Periodic jobs** > **Job site expiration**. The dialog asks for a date, which is mandatory, and optionally for a customer account that limits the run.

A job site is expired only when no rental document on it has a blank end date and the latest end date across its documents is earlier than the date that you enter. Job sites that were never used on a rental document are reported rather than expired.

You can also expire a job site manually by setting the **Expired** toggle on the job site record. Expiring inactive job sites keeps the job site list manageable for rental coordinators.

## Delete stand-down records

The *Delete stand-down records* batch job at **Rental management (Preview)** > **Periodic jobs** > **Delete stand-down records** deletes historical stand-down records. It reaches only rental contracts that are *Closed*, and within those, only the stand-down periods whose From and To dates both fall inside the **From date** and **To date** that you enter in the dialog.

## Maintain calendar calculation journals

Two jobs at **Rental management (Preview)** > **Periodic jobs** maintain the calendar calculation journals that calendar-based invoicing builds. Both reach only rental documents whose rental template uses calendar-based invoicing. Each dialog takes a **From date** and a **To date** – leave **To date** blank for no upper limit—and **Records to include** narrows the run by rental template or rental ID.

| Batch job | Description |
|---|---|
| *Update calendar calculation journals* | Recalculates the working days and the amounts of journal lines that aren't on an invoice schedule yet, from the work calendar on the rental template. It reaches rental contracts with a status of *Created* or *Active*, and rental quotations with a status of *Created* or *Sent*. Run it after you change a work calendar, for example to add holidays. |
| *Delete calendar calculation journals* | Deletes journal lines whose start and end dates both fall inside the dates that you enter, for rental contracts with a status of *Closed* and rental quotations with a status of *Lost* or *Confirmed*. Use it to purge history. |

## Related information

- [Rental management overview](rental-management-overview.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
- [Manage customer and prospect records for rental](manage-customer-prospect-records.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Track rental fleet utilization](track-rental-fleet-utilization.md)
