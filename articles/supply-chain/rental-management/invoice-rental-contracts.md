---
title: Invoice rental contracts (preview)
description: Learn how to generate periodic invoices for rental contracts, change the billing period, create credit notes, and handle prorated charges.
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

# Invoice rental contracts (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental invoicing can be periodic—the system generates invoices on a recurring schedule throughout the rental period rather than once at the end. The billing scenario on each contract line sets the billing periods, and the invoice method and proration settings on the contract's rental template set when each period is invoiced and how partial periods are charged.

## Understand billing cycles

A billing scenario controls how the system calculates rental charges for each invoice period. The most common billing scenario in the rental industry uses a 28-day month, which divides the year into 13 equal periods rather than using calendar months. This approach simplifies proration and avoids the complexity of months with different lengths. The system supports flexible billing cycles, including calendar-based billing.

### Invoice generation timing

The **Invoice method** on the rental template sets the invoicing date of each period: **Number of days** after the period starts, or after it ends when **In arrears** is selected. A common setting in the rental industry is 17 days into a 28-day period. By around day 17, the accumulated charge for the period reaches the full monthly amount, so no further charges accrue until the next period, and the invoice total doesn't change. By generating the invoice at this point, rental businesses get the invoice to the customer as early as possible—a critical concern because construction customers typically take 60-90 days to pay.

Other timing options include:

- **Invoice on specific day** – Each invoice period ends on the day of the month that's set in **Specific day to invoice** (for example, the 15th), so the customer is billed on a predictable date. **Number of days** isn't used.
- **In arrears** – The invoice is created at the end of the period.

### Grace hours

Grace hours provide a window before the next billing period starts. For example, if grace hours are set to 2 and a customer rents a fleet item at 7:00 AM, the customer can return it by 9:00 AM the next day and be charged for only one day. If grace hours are disabled, or the customer returns after the grace window, the customer is charged for the next period.

You define grace hours on the billing period codes and activate them with **Calculate grace hours**, in the **Best rate calculation defaults** group on the rental template. The best rate calculation can then leave out the last day when the rental ends inside the grace hours of the price period.

Learn more about billing scenarios in [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md).

## Generate periodic invoices

The system typically generates rental invoices at the start of each billing period (invoiced in advance) or at the end of each period (invoiced in arrears), depending on **In arrears** on the invoice method.

On a template that uses **Calendar-based invoicing**, first select **Calendar-based invoice** > **Generate line calendar journal** on the contract. Invoice schedules can't be generated until every active main line has calendar calculation journal lines.

To generate rental invoices, follow these steps:

1. Go to the contract and, in the **Post invoice schedules** group on the Action Pane, select **Generate**.
1. In **Invoice until**, enter the date by which invoice periods must be due. It defaults to today.
1. Select **OK** to create the invoice schedules.

You can also select **Generate and post** to create and post the invoice in one step, or **Proforma** to preview the amounts first.

The system creates one invoice per billing period. Each invoice includes:

- Rental charges for the prime fleet item, attachments, and bulk fleet items
- Miscellaneous charges (delivery fees, environmental charges, damage waivers)
- Any prorated charges for mid-period starts or ends
- Fuel and usage charges, if applicable

Go to the contract. On the Action Pane, open the **Inquiries** tab and, from the **Invoice** group, select **Invoice schedules** to review and post the generated invoices. On an invoice schedule, you can open the **Sales order** that carries the invoice, the posted **Invoice journal**, and the **Ledger transaction** for its voucher.

You can also run invoice generation and posting as periodic (batch) jobs:

- **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Generate invoice schedules**
- **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Generate invoice schedules and invoices**
- **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Post invoice schedules**

Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).

> [!NOTE]
> **Post invoice schedules** first creates the sales order for any schedule that's still in *Open* status, and then posts the invoice. It isn't limited to posting orders that already exist.

## Change the billing period on a running contract

**Change active period** switches the billing period that a contract is invoiced on, mid-rental, from the next invoice onward. Use it when the billing rhythm you agreed at contract creation stops fitting partway through and you don't want to close the contract and open a new one. Typical cases:

- **Cash or COD customers** – The contract was written on the standard monthly rhythm, but the customer settles at the counter and wants to be billed daily or weekly instead.
- **A short extension** – After a full month, the customer needs the fleet item for one more week. Switching to weekly for the final cycle bills the week the customer used, rather than a second full month.
- **A weekend rental billed upfront** – The coordinator moves the contract to the daily period and invoices the two or three days before the fleet item leaves the yard.

The command applies to **all main lines of the contract at once**. There's no per-line toggle. It's available only while the contract is *Active*, and only on a template that doesn't use hourly billing. It isn't offered on quotations. The paired **Reverse period change** undoes it.

### Make sure the period is available to switch to

The **New period** lookup offers only the period codes that already exist as a price on *every* main line of the contract, so the switch you want has to be set up before the contract is written. Those prices are copied from the contract's billing scenario when the line is created, which means a scenario that carries only a monthly price line leaves you with nothing to switch to.

To keep daily and weekly switches open, give the billing scenario day and week price lines with a sequence number of *0*. Sequence-*0* lines never produce an invoice of their own, so they don't change the contract's invoicing rhythm, but they put the rate on the line—which is what both **Change active period** and an early return need. Learn more in [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md).

Hourly billing, once, overtime, and stand-down period codes are never offered, even when they're on the line.

### Change the period

When the period you want is available on every main line, you can make the switch. Clear the documents that belong to the period you're leaving first.

1. Open the *Active* contract.
1. Post or delete any invoice schedule that's still in *Open* or *Ordered* status, because the period it was created for is about to move.
1. Delete any open (not yet invoiced) stand-down records. Register them again after the change.
1. On the Action Pane, in the **Update** group, select **Change active period**.
1. In **New period**, select the period code to bill on from now on.
1. Select **OK**.

If overtime is billed by period and the latest period has no overtime approval record, you're asked to confirm before the change goes through. Check that there's no unbilled overtime for the last invoicing period before you continue.

### What the change does

The change closes the active period on the date it was invoiced to, and the new period takes over from the following day. The change doesn't affect invoices that were already generated, and the next invoice the contract produces uses the new period. Along with the main lines:

- **Recurring miscellaneous charges follow the contract.** Environmental fees, damage waivers, and other recurring charges move to the new period, so they keep arriving once per cycle rather than at the old rhythm.
- **The next invoice due date is recalculated** from the end of the last invoiced period, using the length of the new period.
- **Stand-down prices are reactivated** for the window the new period covers.
- **Calendar journal lines are regenerated** on templates that use calendar-based invoicing.
- **Service meter (SMU) based charges are reset.** Charge dates and minimum hours are recalculated for the new period length.

### Reverse a period change

**Reverse period change** sits next to **Change active period** in the **Update** group. It runs immediately, with no dialog, and puts every main line back on the period it used before the last change.

Reverse a period change while all of the following are true:

- The new period isn't invoiced. If it is, create and post a credit note first.
- No open stand-down records exist.
- Overtime isn't calculated for the latest period of the contract.

**Reverse period change** is the only way back. After a contract bills on a period and moves off it, **Change active period** doesn't return it to that period, so use **Reverse period change** for a contract that was switched from monthly to weekly and then invoiced weekly.

## Create credit notes

When you need to adjust a previously issued invoice, work from the invoice schedule. The **Credit** group offers three commands, on both the header and the line:

- **Credit note** – Reverses the entire original invoice schedule. Use this when you need to reissue the entire invoice (for example, if a fleet item was invoiced at the wrong rate). Only a full credit note taken from the header reopens the related calendar journal and stand-down records.
- **Partial credit note** – Credits part of the original schedule. Use this command for stand-down credits, rate adjustments, or other partial corrections.
- **Invoice copy** – Copies the invoice schedule to a new *Open* schedule on the **Invoicing date** that you enter. **Invert sign** is selected by default and makes the copy credit the original; clear it to reissue an identical invoice, for example when the original was sent to the wrong invoice account. **Invoice copy** opens its own dialog and doesn't reopen the calendar journal or the stand-down records.

Two rules apply before any credit is created:

- Credit the most recent invoice schedule on the contract first. A full credit note is available while no later schedule on the contract is still uncredited.
- Invoice an open credit note on the contract before you create another credit note.

To create a credit note, follow these steps:

1. Go to the contract. On the Action Pane, open the **Inquiries** tab and, from the **Invoice** group, select **Invoice schedules**. Then select the schedule you want to credit.
1. Select **Credit** > **Credit note** or **Credit** > **Partial credit note**, on the header or on a line.
1. For a partial credit note taken from the header, set **Valid from** and **Valid to**. Both dates are mandatory, and both must fall inside the original invoicing period. They're recorded on the credit lines as the credited period. For a partial credit note taken from a line, the selected line is the scope and no dates are requested.
1. Select a **Reason code**. The code is mandatory.
1. Select **OK** to create the credit schedule.
1. For a partial credit note, open the new credit schedule and, on each line, change **Quantity** or **Unit price** so that **Price** is the amount that you want to credit. The sign can't be changed.
1. Post the credit schedule.

The credit dialog opens only when **Reason code for credit** is enabled in rental parameters. When that parameter is disabled, no dialog appears. The system creates the credit directly, and the credit lines keep the dates of the original lines.

You can issue repeated partial credits against the same invoice, up to but not beyond the value of the original invoice. A partial credit that would take the total credited beyond that value can't be created.

After you create a credit note, you can generate a corrected invoice with the adjusted amounts.

> [!NOTE]
> The system maintains a complete audit trail linking credit notes to their original invoices, so you can always trace adjustments back to the original billing.

## Resolve invoicing failures and correct a posted period

An unattended invoicing run doesn't stop at the first failure. When a contract can't be processed, the job records the failure against that contract and continues with the next one. You can view the details on the **Rental invoicing batch job exceptions** page.

### Find contracts that weren't invoiced

Go to **Rental management (Preview)** > **Periodic jobs** > **Invoicing** > **Rental invoicing batch job exceptions**. Each row represents one contract from one run and shows **Processed**, **Job caption** (the caption of the batch job that wrote it), **Exception**, **Rental document ID**, **Invoice schedule ID**, **Invoicing date**, and **Reason**. **Processed** is the only field you can edit; the job writes everything else.

> [!IMPORTANT]
> Only batch runs that you start from the **Periodic jobs** menu populate this page. Also, only the following batch runs populate this page: *Generate invoice schedules*, *Generate invoice schedules and invoices*, and *Post invoice schedules*. Invoicing that you start from a contract or from the **Invoice schedules** page doesn't write anything here. A pro forma run doesn't write anything here either. Review the results of interactive invoicing at the time you run it.

### Distinguish errors from warnings

The **Exception** column shows which kind of exception the job recorded:

- **Error** – Schedule creation or posting failed. The contract wasn't invoiced, and **Reason** holds the detail that the job recorded. Review these rows first.
- **Warning** – The step finished, but the run produced a warning. The contract was invoiced, and the row is recorded so that you can verify the result.

### Review the captured infolog

Each row stores the infolog that the run produced for that contract or schedule. Select **Log** to replay it into the client infolog and see the full detail behind the single line in **Reason**. Select the value in **Invoice schedule ID** to open the invoice schedules for the contract, or select the contract number to open contract details.

### Process the exception list

To clear the overnight exceptions, follow these steps:

1. Clear the **Processed** filter above the list, so the page shows only the rows that still need attention.
1. For each row, read **Reason** and select **Log** for the detail.
1. Use the jump from the row to open the contract or the invoice schedule, and fix the cause. Typical causes are a missing ledger account for the revenue split, a customer on credit hold, and a contract line with no price.
1. Regenerate the invoice from the contract, or leave the contract for the next scheduled run.
1. Select **Processed** on the row.

The log isn't purged automatically. Keep **Processed** up to date so that the page remains usable.

### Correct a period that's already posted

After you post an invoice, you can't delete the schedule. Use the commands in the **Credit** group on the invoice schedule to make corrections:

- **Credit note** reverses the whole schedule, for a period that you billed at the wrong rate or against the wrong customer.
- **Partial credit note** credits part of it. Reduce **Quantity** or **Unit price** on the credit lines to the amount that you want to credit—three stand-down days out of a posted 28-day period, for example—before you post it.
- **Invoice copy**, with **Invert sign** cleared, reissues the same schedule for an invoice that was correct but was sent to the wrong invoice account.

After the credit is created, generate the corrected invoice for the period. If you need the sales order for a schedule without invoicing it yet, select **Generate order** on the invoice schedule.

Learn more about the three commands in [Create credit notes](#create-credit-notes), and about the sequence in which credits and schedules can be created and deleted in [Understand the invoice schedule](#understand-the-invoice-schedule).

## Handle prorated charges

Proration applies when a rental period doesn't align neatly with the billing cycle. Common proration scenarios include:

- **Mid-period start** – A fleet item ships in the middle of a billing period. The first invoice is prorated for the partial period.
- **Mid-period return** – The customer returns a fleet item in the middle of a billing period. The final invoice is prorated for the partial period.
- **Stand-down days** – Days when the customer isn't using the fleet item (for example, weather or venue closures). These days are credited against the current billing period. Learn more in [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md).

Set proration on the rental template, not on the billing scenario. A template that uses **Calendar-based invoicing** counts the open days of the work **Calendar** that you select. Learn more in [The Rental template header FastTab](set-up-rental-templates.md#the-rental-template-header-fasttab).

## Review calendar calculation journals

On a template that uses **Calendar-based invoicing**, each main line is billed from a calendar calculation journal. The journal holds one row per price period, with the start and end dates, the number of days, the invoice amount, and the stand-down days and amount.

Generate the rows from the contract in the **Calendar-based invoice** group: **Generate line calendar journal** creates them period by period for every active main line, up to the **Generate until** date that you enter. **Calendar-based summary** shows the calendar-based amounts of the main lines, net of stand-down. The amounts are zero until the rows are generated.

Review and adjust the rows on the line, on the **Calendar-based invoicing** tab. **Add** appends the next price period, and **Remove** deletes rows, starting with the last one. You can delete only a row with the **Calendar journal status** *Created*. The status moves to *Invoice schedule* when the row reaches an invoice schedule, and then to *Invoiced*, or to *Credit scheduled* when it's credited. **Final period** marks the last period of the line, and **Credit** marks a row that was created to credit an already invoiced period because the fleet item came back early.

Two periodic jobs maintain the rows. **Update calendar calculation journals** recalculates the working days and amounts of rows that aren't on an invoice schedule yet, from the work calendar of the rental template. **Delete calendar calculation journals** removes rows in a date range for closed rental contracts and for lost or confirmed rental quotations. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md).

When you extend the estimated return date on the header, the prompt that cascades the change to the lines offers to update the calendar calculation journals.

## Handle overtime charges

When a customer uses a fleet item for more hours than their shift agreement allows, the system creates an overtime approval record and bills the excess. The **Overtime billing method** on the contract line decides which window is measured:

- *Period* – Overtime is evaluated for each invoicing cycle when *Overtime calculation* runs, either as the periodic job or as **Overtime** > **Overtime calculation** on the contract. Generating invoice schedules also evaluates it, but only on lines where **Approval required** is cleared.
- *Last reading* – Overtime is evaluated up to the most recent meter reading.
- *End of contract* – No overtime line is created on the periodic invoices, and the whole contract's usage is settled once during contract closing. The exception is a calendar-based invoicing template, where service meter unit (SMU) lines are still created every period.

The start and end values are the lifetime SMU figures on the fleet item usage history rows inside the window, not the raw readings taken on the outbound and inbound fleet item movements. Unless the overtime billing method is *Last reading*, the allowed hours for the window are reduced by the stand-down hours registered on the line. A fleet item that stood down therefore doesn't accrue overtime for hours that the customer was already credited for. Learn more in [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md).

For example, a customer rents a fleet item for one week on a single-shift agreement that allows 40 hours. When the usage history for the window shows 51 hours of use, the system calculates overtime for the 11 extra hours at the configured hourly rate.

Whether anyone reviews the charge depends on **Approval required** on the contract line. When that flag is cleared, the system creates and approves the record in the same transaction, and writes the price line without review. No record is created when usage is inside the allowance, so an empty list means there was no overtime rather than a job that didn't run. Review pending records at **Rental management (Preview)** > **Common** > **Rental contracts** > **Rental overtime approvals**.

Overtime settings are configured in the rental template. Learn more in [The Rental template header FastTab](set-up-rental-templates.md#the-rental-template-header-fasttab).

## Record hours on an hourly billing line

On a template that uses **Hourly billing**, a line is billed for the hours that you record on it rather than for a period. The commands are on the line, under **Rental document line hours**.

Select **Calculation** to open **Rental document line hours**, where you enter the **Start date/time** and **End date/time** of the window, the **Hours**, and the **Hourly rate**. The page also shows the **Call-off date and time** and any **Additional hours**, and an **Invoicing** group with the **Invoiced amount** and the amount that's still to be invoiced. Select **OK** to register the hours on the line.

**Calculation** is available while the contract is *Created*, *Approved*, *Printed*, or *Active* and no invoice schedule is open, and while the line either has no hours recorded yet or has an open hours record and is called off. Select **Reverse calculation** to reverse the hourly billing calculations of the line; it's available while an hours record and an active price exist.

The billing scenario of the line needs a period code that's marked for hourly billing. Learn more in [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md).

## Handle late returns

When a customer keeps a fleet item past the agreed return date, you can bill the extra time. The process for handling a late return is as follows:

1. The rental coordinator creates the call-off and sets **Call-off date and time** to when the customer finished using the fleet item.
1. The system recalculates the rental period based on the updated dates.
1. During contract closing, the system recalculates the totals for the full actual rental duration. On a standard template, the best rate calculation (BRC) evaluates that duration and determines the optimal rate. For example, a fleet item originally planned for one day but kept for five days might be charged at the weekly rate. Templates that use calendar-based invoicing or hourly billing use their own totals calculation instead, and the best rate controls are disabled for hourly billing. Learn more in [Call off and close rental contracts](call-off-close-rental-contracts.md).

<!--
> [!TIP]
> Wait until the operations staff receives the fleet item and logs the ending hours and fuel, on the fleet item movement or on a mobile device, before generating the final invoice. This way you can include all charges (fuel, overtime, damage) on one final invoice rather than creating a supplemental invoice. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md).
-->

> [!TIP]
> Wait until the operations staff receives the fleet item and logs the ending hours and fuel on the fleet item movement before generating the final invoice. This way you can include all charges (fuel, overtime, damage) on one final invoice rather than creating a supplemental invoice.

## Create supplemental invoices

After a contract is closed and the final invoice is generated, you might discover additional charges that need to be billed—for example, damage found during a post-delivery inspection, extra freight costs, or repairs.

To create a supplemental invoice, follow these steps:

1. Open the closed rental contract.
1. On the Action Pane, in the **Update** group, select **Status** > **Reopen**. The contract status changes to *Reopened*.
1. Select **Miscellaneous charge** > **Supplemental** on the header, or **Add miscellaneous charge** > **Supplemental** on a line, and enter the extra charge (for example, *Damage repair - front window handles: $500*). On a reopened contract, the recurring and once charge commands are disabled, so a supplemental charge is the only kind you can add. Only a supplemental charge gets its own invoice schedule; a once charge would be folded into an existing schedule instead.
1. In the **Post invoice schedules** group, select **Generate**. The system creates an off-cycle invoice schedule that isn't linked to a regular billing period.
1. Post the invoice.
1. Select **Status** > **Close** to close the contract again.

The off-cycle invoice appears in the contract's invoice history alongside the regular periodic invoices and the final invoice, which provides a complete billing audit trail.

## Handle revenue split for the prime fleet item and attachments

A line can carry a prime fleet item (for example, a skid steer) plus attachments (a bucket and forks). The amount of each invoice schedule line is then split across those fleet items, so that revenue, revenue-based depreciation, and utilization follow the individual fleet item.

Each fleet item's share is its **Revenue percentage** on the line, prorated for the days that it was on the line inside the invoice period. **Revenue percentage** starts at 100. When **Use package** is enabled on the **Rental parameters** page, it comes from the rental class package lines instead, and a fleet item that replaces another in a swap inherits the percentage of the one that it replaced.

Set the percentages on the contract line, in **Fleet item** > **Attachment handling** or in **Fleet item** > **Fleet item**. **Attachment handling** doesn't close until the percentages of the active fleet items total 100, and **Fleet item** is editable when you open it from the line.

The revenue account for each share is the **Sales revenue** account that inventory posting assigns to the sales category of the line's revenue category and to the invoice customer. Learn more in [Understand rental management financial integration](understand-rental-financial-integration.md).

Select **Split revenue to attachments** on the **Rental parameters** page, in the **Adding fleet items to rental quotation or contract** group. The system then adds up the rental revenue of a prime fleet item and of the attachments attached to it, and divides it equally among them when invoice schedules are created. Miscellaneous charges that are calculated as a percentage of the rental fee of those lines follow the split amounts, up to their maximum amount. Credit invoice schedules aren't split, and the setting can't be combined with **Use package**.

## Understand the invoice schedule

When the system generates a rental invoice, it first creates an *invoice schedule* that represents the billing for a specific period. The invoice schedule serves as an intermediate step between the contract and the posted invoice.

The invoice schedule has:

- **Header** – Contains the **Customer account**, **Invoice customer**, **Terms of payment**, **Invoicing date**, **Period number** and **Period name**, and **Sales tax group**. The header **Total** is the sum of the line prices, and the header is linked to a single sales order.
- **Lines** – Mirror the contract lines. Each line has a **Revenue category** value that drives the **Sales category** used for GL posting, plus **Sales tax group**, **Item sales tax group**, **Unit price**, and **Price**. The tax groups follow the contract line. Each line becomes a sales order line that carries a sales category instead of an item number, so a rental invoice posts customer, revenue, and tax entries and leaves inventory untouched.

To review how a line's amount is divided across the fleet items on it, select the line on the **Invoice schedule lines** tab, and then select **Revenue split**. The page lists one row per fleet item, with the **Fleet item**, **Main account**, **Debit**, and **Credit**, plus the currency, the transaction text, financial dimensions, and, on the **Credited** tab, whether the row is credited. You can't add or delete rows. Until the schedule is *Invoiced*, you can correct the amounts and the financial dimensions in the details pane; the rows total the line's **Price**, so keep that total when you change an amount. After the schedule is invoiced, the page is read-only. A credit note copies every uncredited row with negated amounts, so the reversal reaches the same fleet items and accounts.

The invoice schedule goes through the following statuses:

| Status | Description |
|---|---|
| *Open* | Generated, but no sales order exists yet. You can review, modify, or delete it. |
| *Ordered* | A sales order exists for the schedule, but the invoice isn't posted yet. |
| *Invoiced* | The sales order invoice is posted. |

> [!NOTE]
> You can delete only an *Open* schedule. To remove an *Ordered* schedule, first select **Delete** > **Sales order** on it, which deletes its sales order and returns the schedule to *Open*. Schedules must be deleted newest first: a schedule can't be deleted while a later schedule on the same contract hasn't been invoiced, and a credit schedule can't be deleted while a newer non-credit schedule carries the same invoicing date.

Learn more about how invoice postings affect the general ledger, including revenue account determination and revenue-based depreciation in [Understand rental management financial integration](understand-rental-financial-integration.md).

## Generate pro forma invoices

A pro forma invoice calculates and displays invoice amounts (including sales tax) without creating any transactions in the system. Pro forma invoices are useful for sharing with customers whose accounting departments need to align purchase orders with expected rental charges before the actual invoice is generated.

To generate a pro forma invoice, follow these steps:

1. Open the rental contract.
1. Select **Proforma** on the Action Pane.
1. In **Invoice until**, enter the date up to which to calculate the charges. **Print** is already selected.
1. Select **OK** to generate the pro forma report.

The pro forma calculates sales tax by using the tax groups defined on the contract and doesn't post any invoice or ledger entries. No invoice schedule or sales order remains afterwards.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
- [Handle stand-down credits and concessions](handle-stand-down-credits-concessions.md)
- [Set up rental templates](set-up-rental-templates.md)
- [Configure rental parameters](configure-rental-parameters.md)
