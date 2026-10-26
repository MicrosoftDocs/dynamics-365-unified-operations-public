---
title: Track rental fleet utilization (preview)
description: Learn how rental management calculates time and financial utilization for fleet items, where to view it, and how to configure utilization periods.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: FLMFleetItemUtilization
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Track rental fleet utilization (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Utilization measures how effectively you use your rental fleet. Rental management calculates utilization for each fleet item and lets you view it by rental class and rental category, so you can identify underperforming assets and make informed decisions about your fleet.

## Understand utilization types

Rental management calculates two types of utilization for each fleet item.

| Type | What it measures | How it's calculated |
|---|---|---|
| **Time utilization** | How much of the reporting period the fleet item was earning rental revenue. | Invoiced days in the period, divided by the number of days in the period, expressed as a percentage. |
| **Financial utilization** | How much revenue the fleet item generated relative to its cost. | Revenue realized in the period, divided by the fleet item's acquisition value, expressed as a percentage. |

The system calculates both types for each of the configurable utilization periods and for the fleet item's whole life (the *Life* period).

## View fleet item utilization

To view utilization for your fleet, go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item utilization**.

The **Rental utilization** page lists each fleet item with the following information:

- **Fleet item** – The fleet item number.
- **Default rental class** – The fleet item's default rental class.
- **Rental category** – The rental category of the fleet item's default rental class.
- **Financial - [period]** and **Financial life** – Financial utilization for each configured period and for the fleet item's whole life.
- **Time - [period]** and **Time life** – Time utilization for each configured period and for the fleet item's whole life.

To review the underlying records that make up a fleet item's utilization, select **Utilization transactions**.

You can also open the utilization view for a specific fleet item from the fleet item master: open the fleet item record and select **Fleet item utilization**. The fleet item master also shows **Actual days in rental** and **Accumulated days in rental** for the fleet item.

## View utilization on the availability summary

The **Rental availability summary** can display time and financial utilization columns alongside availability counts, so you can weigh utilization when you decide which fleet items to rent. To access it, go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability summary**.

The summary shows the financial and time utilization columns for the selected utilization period. To switch between the configured periods and *Life*, select **Display details** and change **Utilization period**.

The **Utilization on availability** user setting controls whether utilization columns appear on the **Fleet item availability** and **Rental availability summary** screens. Learn more in [Show utilization on availability screens](#show-utilization-on-availability-screens).

## Configure utilization periods

The system calculates utilization for up to four rolling reporting periods plus the fleet item's whole life. You define the periods in rental parameters.

To configure utilization periods, go to **Rental management (Preview)** > **Setup** > **Rental parameters** and open the **General** tab. In the **Rental utilization** section, configure the following settings:

| Setting | Description |
|---|---|
| **Utilization period 1** through **Utilization period 4** | The number of days in each rolling reporting period, counted back from the date on which utilization is calculated. Enter a number of days for each of the four periods. For example, *30*, *60*, *90*, and *180*. |
| **Default utilization period** | The period shown by default on the rental availability summary. Options are *Utilization period 1* through *4*, or *Life*. |
| **Utilization from acquisition** | When enabled, a configured period that's longer than the number of days the fleet item has spent in asset fleets is shortened to that number of days. This prevents recently acquired fleet items from appearing artificially underutilized. |

> [!NOTE]
> The **Time utilization reference period** and **Financial utilization reference period** settings on the **Dynamic pricing** tab are separate. They tell dynamic pricing which utilization figure (a specific period or *Life*) to use when it suggests rates. Learn more in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

## Show utilization on availability screens

The **Utilization on availability** setting controls whether the **Fleet item availability** and **Rental availability summary** screens show financial and time utilization. It's a per-user setting, so each worker can choose whether to see utilization figures.

An administrator configures this setting per user on the **Rental user setups** tab at **Rental management (Preview)** > **Setup** > **Rental parameters**. When the setting is disabled for a user, that user's availability screens hide the utilization columns, and **Utilization period** isn't available in **Display details**.

## Run utilization periodic jobs

A set of periodic batch jobs maintains the utilization figures. Schedule them to run regularly so that the utilization inquiry and the availability summary reflect current data. To access them, go to **Rental management (Preview)** > **Periodic jobs**.

| Batch job | Description |
|---|---|
| **Generate utilization transactions** | Back-fills utilization transactions for invoiced revenue-split records that don't have one yet. Invoice posting normally writes the transactions, so this job only fills gaps. It processes fleet items in fleet types whose **Value tracking method** is *Fixed asset*, *Inventory*, or *Manual*. |
| **Calculate fleet item utilization** | Calculates time and financial utilization for each fleet item from the utilization transactions, and updates the utilization summary. |
| **Update utilization transactions** | Sets invoiced days to zero on overtime and stand-down lines, so that those lines don't distort time utilization. Run it after you flag a period code for overtime or stand-down, to correct transactions that already exist. The correction is permanent. |
| **Delete utilization transactions** | Removes the utilization figures for fleet items that moved to a fleet type whose **Value tracking method** is *Manual* or *Customer* more than a year ago. Those fleet items no longer appear on the **Rental utilization** page. |

A typical schedule generates and calculates utilization daily, so that dashboards and the availability summary stay current.

## How utilization is calculated

When you post rental invoices and run the utilization jobs, the system builds utilization from invoiced rental activity:

1. Posting a rental invoice records the fleet item's invoiced revenue and invoiced days as utilization transactions. Each one takes its ID from the **Utilization transaction** number sequence on the **Number sequences** tab of **Rental management (Preview)** > **Setup** > **Rental parameters**, so set that number sequence up before you post rental invoices.
1. The **Calculate fleet item utilization** job aggregates those transactions per fleet item and computes, for each configured period and for life:
   - **Time utilization** = invoiced days in the period, divided by the days in the period, multiplied by 100.
   - **Financial utilization** = revenue in the period, divided by the fleet item's acquisition value, multiplied by 100.

For the *Life* period, the number of days used is the total number of days the fleet item has spent in the asset fleets. That total is the accumulated days in rental plus the current stint, when the fleet item is in a fleet. When **Utilization from acquisition** is enabled, a configured period that's longer than that same days-in-asset-fleets figure is shortened to it.

## Conditions that affect utilization results

Utilization results depend on correctly configured data. Two conditions determine whether a fleet item produces a figure. If a fleet item shows no utilization, check these conditions in order.

### Utilization is a fixed asset measure

**Calculate fleet item utilization** processes only fleet items that have a fixed asset and that belong to a fleet type whose **Value tracking method** is *Fixed asset*. The job never aggregates fleet items in fleet types set to *Inventory*, *Manual*, *Customer*, or *Canceled*, so it publishes no utilization for them. Set the **Value tracking method** of the fleet types that hold rentable fleet items to *Fixed asset* before you rely on any figure. A fleet item gets its fixed asset when it's transferred into such a fleet type, with the fixed asset group and book from the **Posting configuration for fleet types** page. Learn more in [Configure posting for fleet types](configure-inventory-location-settings.md#configure-posting-for-fleet-types).

### A fleet item needs a resolvable asset book

Financial utilization divides realized revenue by the acquisition value on the fleet item's asset book, so each fleet item needs a fixed asset with a book. The calculation takes the fleet item's open book. If there's no open book, it falls back to a closed book in the *Current* posting layer. When several of those exist, it uses the book set up on the **Posting configuration for fleet types** page for the fleet item's fleet type and item group. A fleet item that's missing from the **Rental utilization** page altogether, rather than showing zeros, indicates a missing fixed asset or asset book rather than an idle fleet item.

### What the figures include

Two more rules shape the numbers once these conditions are met:

- Revenue and invoiced days reach utilization only after you post the rental invoice schedule and it reaches *Invoiced* status, so utilization lags invoicing rather than the rental itself. The system converts revenue to the accounting currency at the invoicing date, which lets you compare branches on one basis.
- A credit note contributes negative revenue and negative invoiced days, and lines billed under a period code flagged for overtime or stand-down contribute revenue but zero days. Strong revenue with low time utilization is often that combination rather than a data error.

The calculation always runs as of the current date, and it counts only utilization transactions whose invoicing date is on or before that date. The invoicing date comes from the invoice schedule, so revenue from a schedule that's posted ahead of its invoicing date doesn't count until that date. There's no as-of date in the dialog, so you can't recalculate an earlier month.

### Audit a disputed figure

To trace a percentage back to the invoices that produced it, follow these steps:

1. Go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item utilization** and select the fleet item.
1. Select **Utilization transactions**. Each row names the invoicing date, the billing period code, the rental class, the contract, the revenue, and the invoiced days.
1. On a row, select the **Invoice schedule line** to open the rental invoice schedule that produced it.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Check fleet item availability and select fleet items](check-equipment-availability.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Run rental management periodic jobs](run-rental-periodic-jobs.md)
