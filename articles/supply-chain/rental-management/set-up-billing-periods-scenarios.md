---
title: Set up billing periods and scenarios (preview)
description: Learn how to set up the period codes, invoice methods, and billing scenarios that control how and when rental contracts are billed.
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

# Set up billing periods and scenarios (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Billing setup controls *how* a rental is priced over time (by the day, week, or month) and *when* invoices are generated. It's built from three masters that you configure under the **Rental management (Preview)** > **Setup** > **Periods** heading in the navigation pane. The following pages are available there:

- **Period codes** define the individual time-based pricing tiers (day, week, month, and special-purpose periods).
- **Invoice methods** define when invoices are generated relative to the billing period.
- **Billing scenarios** combine period codes into the billing rhythm and the rate card for a contract, and control how the rental escalates from one pricing tier to the next.

You then select a *billing scenario* and an *invoice method* on a rental template, which applies them to every contract that you create from that template. Complete the procedures described in this article before you finish the rental template setup in [Set up rental templates](set-up-rental-templates.md).

## What determines when a contract is invoiced

Three separate settings decide when a contract produces an invoice. Keep them apart when you set up billing and when you troubleshoot it.

| Setting | Where it's defined | What it controls |
|---|---|---|
| **Price period** | The billing scenario price line | The length of each billing chunk. A month period divides the rental into month-long chunks. |
| **Invoice method** | The rental template | The invoice date for each chunk—in advance, in arrears, or on a fixed day of the month. |
| **Invoice until** | The invoice generation dialog or the scheduled task | How far ahead a single run reaches. No invoice is created for a period that falls beyond this date. **Invoice until** on the **Invoicing** tab of the **Rental parameters** page caps the date that a run can use. |

A contract that's billed in arrears is invoiced when the billing period *ends* on or before the **Invoice until** date.

## Set up period codes

A *period code* is a single pricing tier—for example, a day, a week, or a 28-day month. You enter rates per period code, and billing scenarios reference period codes to build the escalating tier structure.

To set up period codes, go to **Rental management (Preview)** > **Setup** > **Periods** > **Period codes**.

### Period code fields

For each period code, configure the following fields:

- **Period** – A unique identifier for the period code.
- **Name** – A descriptive name for the period code.
- **Time unit** – The unit of time for the period. Options are *None*, *Year*, *Month*, *Week*, *Day*, and *Service meter unit*.
- **Invoice days** – The number of billable days in the period. The value must be greater than 0. For example, a 28-day month billed Monday through Friday has 20 invoice days.
- **Grace hours** – When the rental template has **Calculate grace hours** turned on, a return within this many hours past the rental's start time is billed one day less in the best rate calculation, if that's cheaper. For example, with 2 grace hours, a fleet item rented at 7:00 AM and returned by 9:00 AM the next day is charged for only one day.
- **Number** – The number of time units in the period (for example, *4* weeks, or *28* days).
- **Valid from** and **Valid to** – Optionally limit the dates on which this period's rates are shown in availability and rate overviews. They don't limit the pricing or invoicing of rental lines.
- **Display as** – Optional text that overrides how the period name is printed on rental invoice reports.

### Period code flags

Certain special-purpose period codes support specific billing features. On the period code, these features are identified by the **Base period**, **Overtime**, **Stand-down period**, and **Once** flags. You can set each of the **Base period**, **Overtime**, **Stand-down period**, and **Hourly billing** flags on only one period code. **Once** isn't restricted to a single period code.

| Flag | When to use | Description |
|---|---|---|
| **Once** | For one-time billing periods | When set to *Yes*, the full contract price for this period code is invoiced only once for the entire rental duration. Use it for periods that shouldn't repeat. Several period codes can have this flag set. |
| **Overtime** | For SMU or overtime billing | Set to *Yes* for the overtime billing period. The system posts overtime charges using the rates on this period. This period should use the *Service meter unit* time unit. Only one period code can have this flag set. |
| **Hourly billing** | For hourly billing periods | Set to *Yes* to designate this period as the hourly billing rate. It's valid only when **Time unit** is *None*. Only one period code can have this flag set. |
| **Base period** | For calendar-based invoicing, stand-down, and overtime allowances | Set to *Yes* for the base period. Supplies the day rate when calendar-based invoicing or stand-down isn't prorated, and the daily hours allowance for stand-down. It must be one day long, only one period code can be the base period, and billing scenarios must include it as a price line (sequence number *0* is enough). |
| **Stand-down period** | For stand-down credits | Set to *Yes* for the stand-down deduction period. The system calculates stand-down credits using the rates on this period.  Only one period code can have this flag set. |

### Rental period hours allowances

Rental period hours allowances define the equipment usage hours included in a rental period for each shift. Usage above the allowance is billed as overtime. For example, you might include 40 hours in a single-shift week and 80 hours in a double-shift week.

These allowances supply the default **Hours allowed** on rental rate lines for the matching period and shift. You can override the allowance on an individual rate line. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

To define the hours allowance for a period code, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Periods** > **Period codes**.
1. Select the period code to configure.
1. On the Action Pane, select **Hours allowed** to open the **Rental period hours allowances** page. This button is unavailable for period codes that have **Hourly billing** set to *Yes*.
1. Add a row and set the following fields:
    - **Shift** – Select the shift that the allowance applies to.
    - **Hours allowed** – Enter the equipment usage hours included in one rental period for that shift, before overtime charges apply.

1. Repeat for each shift that needs an allowance for this period code.

### Typical period code setup (28-day month or 4-week industry standard)

The following table shows a typical set of period codes for a rental business that bills on a 28-day month.

| Period code | Time unit | Invoice days | Flags |
|---|---|---|---|
| Day | Day | 1 | **Base period** = *Yes* |
| Week | Day | 5 (Monday-Friday billing) or 7 (7-day billing) | - |
| Month28 | Day | 20 (Monday-Friday billing) or 28 (7-day billing) | - |
| Overtime | Service meter unit | - | **Overtime** = *Yes* |
| Stand-down | - | - | **Stand-down period** = *Yes* |

## Set up invoice methods

An *invoice method* controls when the system generates an invoice relative to the billing period. A common rental industry setup is a *17-day frequency*—by around day 17, the accumulated charge for the period reaches the full monthly amount, so no further charges accrue until the next period. At that point the invoice total doesn't change, so rental businesses can invoice early to accelerate cash collection.

To set up invoice methods, go to **Rental management (Preview)** > **Setup** > **Periods** > **Invoice methods**.

For each invoice method, configure the following fields:

- **Invoice method** – A unique identifier for the invoice method.
- **Name** – A descriptive name for the invoice method.
- **In arrears** – When selected, the system calculates the invoice date from the end of each invoice period (in arrears). Otherwise, it calculates the date from the start of the period (in advance).
- **Number of days** – The number of days added to the start of each invoice period, or to its end when **In arrears** is selected, when setting the invoice date. A negative value invoices before that date.
- **Invoice on specific day** – When selected, the system generates invoices on a fixed day of the month instead of using the arrears or number-of-days logic.
- **Specific day to invoice** – The day of the month (0-31) on which monthly price periods end when **Invoice on specific day** is enabled. When set to *0*, a monthly period ends on the day before the day of the month that the contract started.

> [!NOTE]
> **Invoice on specific day** can't be combined with **In arrears** or **Number of days**. The system clears the conflicting fields. Price periods measured in months are invoiced on the specific day and other price periods on the last day of each invoice period. The rental template must have a **Calendar** assigned.

## Set up billing scenarios

A *billing scenario* does two jobs in a single table: it sets the *billing rhythm* (how often the contract produces an invoice) and it holds the *rate card* (what each period is worth). The **Sequence number** on each price line decides which of the two jobs that line does.

- A price line with a *sequence number of 1 or higher* produces the invoice schedule. The rental is divided into chunks of that period, and one invoice is created per chunk.
- A price line with a *sequence number of 0 provides a price only*. It never produces an invoice by itself. Its rate is carried on the contract so that it's available when a partial period has to be priced, such as when a fleet item is returned before the current period ends.

When a scenario has more than one price line with a sequence number, those lines form an ordered set of pricing tiers. The rental *escalates* from one tier to the next as it runs longer: billed by the day at first, then rolling up to weekly and then to monthly rates, so longer rentals are billed at progressively better rates.

To set up billing scenarios, go to **Rental management (Preview)** > **Setup** > **Periods** > **Rental billing scenarios**.

A billing scenario has a header and one or more price lines:

- The header has a unique **Billing scenario** ID and a descriptive **Name**.
- Each row on the **Price line** FastTab references a period code and controls the escalation. Make the following settings for each row:
    - **Price period** – The period code (day, week, month, and so on) for this tier.
    - **Sequence number** – Whether the line produces an invoice schedule, and in what order. The system bills the lowest sequence number above *0* first, and then moves to the next-highest when the current tier is exhausted. Sequence numbers above *0* must be unique within the scenario. Any number of price lines can share sequence number *0*, because those lines supply rates rather than invoices.
    - **Recurrence number** – How many times this tier is billed before the rental advances to the next tier in sequence. A recurrence value of *0* (or blank) means the tier is never closed by the invoice count, so it prices the rest of the rental. Unless invoicing should stop after a set number of periods, give the highest sequence number a recurrence of *0*.
    - **Grace days** – Free days for the recurring period. At the transition to the next tier, the next tier's start date is offset by the grace days, so the customer isn't charged for those days at the boundary. Grace days have no effect when the recurrence number is *0*.

### How the escalation works

When a contract is invoiced, the system applies the price line with the lowest sequence number and counts each invoice. When the number of invoices reaches the tier's **Recurrence number**, that tier is closed and the next sequence number's tier becomes active. A tier with a recurrence of *0* isn't closed by the invoice count, so it prices the remainder of the rental. It's still closed if you change the billing scenario on the contract: the change closes the active price line at the change date and activates the price line for the period that the scenario changed to.

Two points follow from this, and both are easy to miss:

- **A recurrence number of *0* on every price line means there's no escalation at all** – No tier is ever closed, so only the line with the lowest sequence number above *0* is ever billed. This is a valid and common setup. It bills the whole rental on one period, and the sequence-*0* lines supply the rates for partial periods.
- **Always leave the highest sequence number at a recurrence of *0*** – The last tier then keeps the contract line priced for the rest of the rental once every earlier tier is exhausted.

### Example: day-to-week-to-month escalation

Consider a billing scenario named *STANDARD* with these price lines:

| Sequence number | Price period | Recurrence number | Grace days |
|---|---|---|---|
| 1 | Day | 6 | 0 |
| 2 | Week | 3 | 0 |
| 3 | Month | 0 | 0 |

A contract on this scenario is billed as follows:

- **Days 1-6** – billed at the **daily** rate (6 daily invoices).
- **Next 3 weeks** – billed at the **weekly** rate.
- **Remainder of the rental** – billed at the **monthly** rate, indefinitely (recurrence *0*).

Because each tier is typically cheaper per day than the one before it, the effective rate falls as the rental gets longer.

### Example: single billing tier with supporting rate card

Many rental businesses invoice on one period throughout, and use the shorter periods only to price early returns. Consider a billing scenario named *MONTH* with these price lines:

| Sequence number | Price period | Recurrence number | Grace days |
|---|---|---|---|
| 0 | Day | 0 | 0 |
| 0 | Week | 0 | 0 |
| 0 | Overtime | 0 | 0 |
| 0 | Stand-down | 0 | 0 |
| 1 | Month | 0 | 0 |

A contract on this scenario is invoiced monthly for as long as it runs, because *Month* is the only price period that has a sequence number. The *Day* and *Week* lines never produce an invoice of their own, but their rates are carried on the contract. A fleet item that's returned after three weeks can therefore be priced as three weeks instead of as a full month.

Sequence-*0* lines have a second use. They're also what a running contract can switch to when you select **Change active period**. That command offers only the period codes that are already on the contract line, so the *Day* and *Week* lines in this example are what let you move a monthly contract to weekly or daily billing part-way through. Learn more in [Invoice rental contracts](invoice-rental-contracts.md#change-the-billing-period-on-a-running-contract).

### Example: hourly billing scenario

For fleet items charged by the hour (such as generators or light towers), create a billing scenario whose price line uses an *hourly-billing* period code (a period code with **Hourly billing** = *Yes* and **Time unit** = *None*). For an hourly-billing price line, the **Recurrence number** must be *1*.

## Apply the billing setup to a template

Period codes, invoice methods, and billing scenarios don't do anything on their own. You must apply them through a rental template. On the template, select the **Billing scenario** and the **Invoice method** that contracts based on that template should use. Learn more in [The Rental template header FastTab](set-up-rental-templates.md#the-rental-template-header-fasttab).

## Related information

- [Set up rental templates](set-up-rental-templates.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
