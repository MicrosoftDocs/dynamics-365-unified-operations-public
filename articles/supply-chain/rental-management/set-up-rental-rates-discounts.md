---
title: Set up rental rates and discounts (preview)
description: Learn how to configure rental rate tables, customer-specific pricing, rental packages, and discount limits with manager approval workflows.
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

# Set up rental rates and discounts (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental rates determine how much you charge customers for fleet items. You structure rates by rental class (a grouping of similar fleet item types) and match them by customer or rental rate group, rental class or rental category, period code, currency, and the price factors that you switch on. The system also supports discounts and rate override limits.

## Understand rental rate structure

Organize rental rates by *rental class* rather than by individual fleet item. A rental class groups fleet items of similar size and capability. This approach simplifies rate management because you maintain one set of rates per class instead of per fleet item.

> [!NOTE]
> Before you set up rates, create your rental categories and rental classes. You define rates per rental class. Learn more in [Set up rental classes and categories](set-up-rental-reference-data.md#set-up-rental-classes-and-categories).

Manage rates and discounts from two places:

- **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rates** – A global list of all rate records. Use this page for bulk rate maintenance. **Rental discounts** on the same menu opens the same page filtered to discount records.
- **Rental management (Preview)** > **Setup** > **Rental classes** – Open a rental class and select **Rate table** or **Discount** to manage the rates or discounts for that class.

## How a rate is selected, imported, and re-sorted

Each price line on a quotation or contract line is priced on its own. The system looks for the first rate record that matches the line, ordered by **Priority**, and copies the rate amount and the hours allowed onto the price line. It then repeats the search against the discount records and applies the discount that it finds. Understanding both steps lets you predict the amount that you quote a customer.

### What a rate record must match

A rate record has a header, which is the matching key, and one or more rate lines, which carry the dated amounts. Both parts must match the contract line:

- On the rate line, the **Period** must be the period code being priced, and the **Currency** must be the currency of the document. Rate amounts aren't converted between currencies, so maintain a rate line in each currency that you quote in.
- On the rate line, the system evaluates **From date** and **To date** against the **invoice-from date of the contract line**, not against today's date. Future-dated rates therefore take effect for the billing periods that fall inside their validity, and re-dating a contract can change the price.
- On the header, **Account code** must be *All*, or **Account relation** must be the customer or the customer's rate group. Discounts use the customer's discount group instead of the rate group.
- On the header, **Class code** must be *All*, or **Class relation** must be the rental class of the line, or the *rental category* that the class belongs to. Rates are maintained per rental class, so a rate matches on its own class. Discounts are maintained for one rental class, a rental category, or all classes, so one discount record can cover a whole family of classes.
- On the header, each price factor that's in use (**Application**, **Shift**, or **Location**) must either be empty on the rate record or equal the value on the contract line. An empty price factor matches any value, so it acts as a wildcard.

### How Priority decides which record wins

**Priority** is a read-only number on the rate record. The system takes the **first** matching record in ascending Priority order, so the **lowest** Priority wins. You never type the value. The system calculates it from the sorting values at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Rates and discounts** tab. The calculation is a base value, plus a value for the account code (a specific account, a group, or all accounts), plus a value for each price factor that's switched on but left empty on the record. All of the sorting values are *0* in a new legal entity, so set them before you create rates.

To set them, go to **Rental management (Preview)** > **Setup** > **Rental parameters**, open the **Rates and discounts** tab, and then open the **Sorting** page. Give the more specific records the lower values.

| Group | Fields |
|---|---|
| **Base** | **Sorting base** – the starting value of every calculated Priority. |
| **Account code** | **Sorting table account**, **Sorting group account**, and **Sorting all account** – added when the account code is a specific account, a group, or all accounts. |
| **Class code** | **Sorting table class**, **Sorting group class**, and **Sorting all class** – added to a discount in the same way, for its class code. |
| **Rate** | **Sorting rate application**, **Sorting rate shift**, and **Sorting rate location** – added to a rate for each price factor that's switched on but left empty on the record. |
| **Discount** | **Sorting discount application**, **Sorting discount shift**, and **Sorting discount location** – the same values for discounts. |

For example, consider a **Sorting base** of *10*, account values of *0*, *1*, and *2*, and rate price factor values of *2*. A rate for a named customer with every price factor filled in scores *10*, and a rate for all customers with none of them filled in scores *18*. The first one wins.

For discount records, the class code also contributes to Priority, through the **Sorting table class**, **Sorting group class**, and **Sorting all class** values. Rate records always apply to one rental class, so the class code doesn't contribute to their Priority.

The system recalculates Priority when you save a rate record from the rate page. If you change the sorting values on the **Rental parameters** page, existing records keep their previous Priority until you recalculate them.

### Import rates and update the priority

You can also create rates and discounts by using a data management import. The **Rental rate headers** entity, together with **Rental rate lines**, exposes **Priority** as the evaluation order, so an imported file can carry the value to use.

> [!IMPORTANT]
> After you import rates or discounts, run **Rental management (Preview)** > **Periodic jobs** > **Rates and discounts** > **Update priority**, so that every imported record is evaluated in the right order. A record with a low **Priority** outranks records with a higher one.

Run **Update priority** again after any change to the sorting values. Select *All*, *Rate*, or *Discount* to choose which records are restamped.

You can also recalculate from the rate page. On the **Rate** tab (the **Discount** tab on **Rental discounts**), in the **Update** group, select **Sorting**, and then select **Selected** for the current record or **All** for every rate and discount in the legal entity.

### How the discount is applied to the rate

After the system finds the rate, the discount search runs against the discount records by using the same matching rules. The system then applies the discount to the rate amount in this fixed order:

1. The system subtracts the **Discount amount**.
1. It reduces the result by the line **Discount percentage**.
1. It reduces that result by the header discount percentage.

The two percentages **compound**. They aren't added together. A 10 percent line discount followed by a 10 percent header discount leaves 81 percent of the amount, not 80 percent.

The price line also records where the rate came from, so you can answer a price question later without re-running the search. *Default* means that a rate for all customers matched (the book rate) or that no rate was found. *Customer group* means that the customer's rental rate group matched, and *Customer* means that a named account matched.

## Set up book rates

Book rates (also called list rates or retail rates) are the standard published rates for a rental class.

To set up book rates, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rates**.
1. Select **New**. A number sequence assigns the **Rate ID**.
1. Set the **Account code** to *All* so that the rate applies to every customer.
1. Select the rental class in **Class** (in the **Class relation** group). On a rate record, **Class code** is set automatically and can't be edited. You can change it only on a discount record.
1. Add a rate line for each **Period** code (day, week, month, and so on). On each line, enter the **Rate**, the **Currency**, and optionally the **Hours allowed** (the usage hours included in the rate period; usage beyond this threshold is billed as overtime). **Hours allowed** defaults from the rental period hours allowance for the period and the rate's shift, so you enter it only to override that value.
1. Set **From date** and **To date** on each line. You can future-date rates for annual rate maintenance—for example, set up new rates in the fall that take effect on January 1 without affecting current pricing.
1. Select **Save**.

> [!NOTE]
> After you save a rate record, you can't edit its key fields (account code and relation, class relation, price factors, and type). To correct a key, create a new record.

## Change rates in bulk

The rate page changes many rates at once. Select the rate records first, and then use the commands on the **Rate** tab (the **Discount** tab on **Rental discounts**).

- In the **Update** group, select **Modify rate** (**Modify discount** on a discount). In the dialog, select the **Period** and the **Currency**, set a **From date** and a **To date**, and enter either a **Change by amount** or a **Change by percentage**. For each selected record, the command takes the rate line for that currency and period that's valid today, sets its dates to the dialog dates, and changes the amount. A preview lists the current and the new rate. Select **OK** to apply it, or **Cancel** to leave the rates as they are.
- In the **Rounding** group, select **Round now** to round the rate on the line that's valid today for the currency and period that you choose. It shows the same kind of preview first. **Rounding setup** opens the rounding parameters.

Set the rounding options at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Rates and discounts** tab, on the **Rounding** page. **Rounding rule** is the number that a rate is rounded to, **Rounding method** is *Normal*, *Downward*, or *Rounding-up*, and **Automatic rounding** selects **Apply rounding** by default in the **Modify** dialog.

> [!IMPORTANT]
> **Modify rate** changes the rate line that's valid today, so it doesn't keep the previous amount. When the current rate has to stay in force until a future date, add a new dated rate line instead.

## Set up customer-specific rates

You can negotiate and store special rates for individual customers or groups of customers.

### Individual customer rates

To create rates for a specific customer, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rates**.
1. Select **New**.
1. Set the **Account code** to *Table*, and set the **Account relation** to the customer.
1. Select the rental class in **Class relation**.
1. Add a rate line for each **Period** code with the negotiated **Rate**.
1. Select **Save**.

When you add this customer to a contract, the system automatically applies their customer-specific rates instead of the book rates.

### Rental rate group rates

To simplify rate management for customers who share the same pricing (for example, a group of pipeline contractors), assign them to a shared **Rate group** and set rates at the group level.

Create rate groups and discount groups at **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rate groups**. Each group has a **Type** of *Rate* or *Discount*: a customer's **Rental rate group** must be a *Rate* group, and the **Rental discount group** must be a *Discount* group. This page is separate from the **Dynamic price rate groups** tier table on the **Dynamic pricing** tab of the rental parameters.

To set up rate group rates, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rate groups**, create the group, and set **Type** to *Rate*.
1. On each customer record, on the **Setup** FastTab, in the **Rental rate and discount** group, select the group in **Rental rate group**. Rates match on the **Rental rate group** and discounts match on the **Rental discount group**, so a customer can sit in one tier for rates and a different tier for discounts.
1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental rates**, select **New**, set the **Account code** to *Group*, and set the **Account relation** to the rate group.
1. Select the rental class in **Class relation**.
1. Add a rate line for each **Period** code with the group rate.
1. Select **Save**.

Rate groups make maintenance easier—when you need to adjust rates for all pipeline customers, you update one record instead of many.

## Configure application-based rates

Rental rates can vary based on the application where the fleet item is used. A fleet item used in harsh environments experiences more wear, which justifies higher rates.

Applications are *price factors* that you define at **Rental management (Preview)** > **Setup** > **Rental rates** > **Price factors**, where each record has an ID, a name, and a **Price factor type** of *Application*, *Shift*, or *Location*. Your list can therefore differ from the examples in this article.

The system uses a price factor in pricing only when you switch it on at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Rates and discounts** tab, with **Rates by application** and **Discount by application**.

> [!IMPORTANT]
> Switching on **Rates by application**, **Rates by shift**, or **Rates by location** makes that price factor mandatory on rate records and on every quotation or contract line that has a rental class. You must enter it before you can save such a line or activate a contract that has one. The **Discount by** settings make the price factor mandatory on discount records only. Switch on only the price factors that your rate book uses.

To set up application-based rates, create a rate record for the rental class and select the applicable **Application**. Common applications include:

- **Standard** – Normal operating conditions.
- **Salt water** – Coastal or marine environments with corrosive conditions.
- **Industrial** – Heavy industrial applications with high dust or chemical exposure.

Each application can have its own day, week, and month rates.

## Configure shift-based rates

Rates can also vary based on the operating shift, which reflects how many hours per day the fleet item is used.

Shifts, like applications, are price factors, and you switch them on with **Rates by shift** and **Discount by shift** on the **Rates and discounts** tab of the rental parameters. To set up shift-based rates, create rate records for each shift type:

- **Single shift** – Standard 8-hour operation (the default).
- **Double shift** – Two operators running the fleet item during extended hours.
- **Continuous (24/7)** – Round-the-clock operation, common for generators during disaster relief or construction projects with tight deadlines.

You can combine shift-based and application-based rates by creating separate records for each combination (for example, salt water + double shift).

## Set up rental packages

A rental package groups a prime fleet item with its attachments into a single rate structure. This structure is an alternative to pricing each fleet item individually.

For example, instead of pricing a skid steer at $4,500/month and a bucket at $500/month separately, you can create a package that prices the combination at a specific rate.

To set up a rental package, turn on **Use package** at **Rental management (Preview)** > **Setup** > **Rental parameters**, on the **Fleet items** tab, under **Adding fleet items to rental quotation or contract**, and then follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental classes** and select or create the class that represents the package. The page lists package classes only after you select **Package view**.
1. Set the **Package** flag on the class.
1. In the **Rental class definition** grid, add a line for each component class—for example, one medium skid steer class plus one skid steer bucket class.
1. Set the quantity for each component. For example, you might create a package with one skid steer, one bucket, and two forks. To accept any number of fleet items from a component class, select **Any** instead.
1. Set a **Revenue percentage** on each component line. When the package has more than one component line, the percentages must total 100. For example, 80 on the prime fleet item and 20 on the attachment splits the revenue 80/20, which drives revenue-based depreciation and utilization for each fleet item.
1. Set up rates for the package class using the same rate structure (day, week, and month rates with customer, application, and shift options).

> [!TIP]
> While packages offer pricing flexibility, maintaining rates at the individual rental class level is often easier for long-term system maintenance. Use packages when customers request bundled pricing.

## Location price factors

A **Location** price factor works like the application and shift price factors. Switch it on with **Rates by location** and **Discount by location**, and then select it on the quotation or contract line. The value defaults from the rental template's default price factor values, or from **Default location** on the **Rental parameters** page.

## Configure dynamic pricing

Dynamic pricing automatically suggests rate adjustments based on market conditions such as fleet utilization, inventory levels, and customer history. Unlike static rates, dynamic pricing responds to real-time demand.

To configure dynamic pricing, go to **Rental management (Preview)** > **Setup** > **Rental parameters** and open the **Dynamic pricing** tab.

### Enable and control dynamic pricing

- **Activate dynamic pricing** – Turns the feature on or off.
- **Allow price decrease** and **Allow price increase** – Control whether the system can suggest downward adjustments, upward adjustments, or both.
- **Approval required** – When enabled, applying a suggested dynamic price puts the quotation or contract *On hold* until it's approved.
- **Inventory level by fleet location** – Whether the system evaluates inventory at the fleet (rental) location level rather than the company level.

### Configure pricing parameters

Tune the dynamic pricing parameters to your fleet size and market. The same percentages don't work for a small rental business with a few fleet items per class and a large one with dozens.

You configure dynamic pricing through several tables, each defining adjustment percentages for a driver. In the five tier tables, each row applies its **Percentage** to the values from **From** to **To**, inclusive; the ranges in a table can't overlap, and a value that falls outside every range contributes 0%:

| Section | Description |
|---|---|
| **Dynamic price inventory level tiers** | Adjustments based on how many fleet items of the rental class are available. Each band contributes the signed percentage that you configure, so you decide whether scarcity raises or lowers the suggestion. |
| **Dynamic price reservations tiers** | Adjustments based on the number of active reservations, at the reservation stage, for the rental class on the line. |
| **Dynamic price time utilization tiers** | Adjustments based on the percentage of time fleet items are on rent, over a **Time utilization reference period**. |
| **Dynamic price financial utilization tiers** | Adjustments based on revenue performance, over a **Financial utilization reference period**. |
| **Dynamic price past contract tiers** | Adjustments based on past rental contract patterns, with a configurable **Reference date**. |
| **Dynamic price rate groups** | Different adjustments for specific rate groups. |
| **Dynamic price period limits** | Per **Period code**, the **Maximum increase percentage** and **Maximum decrease percentage** that cap the suggested adjustment. Enter the maximum decrease as a negative percentage; a period code without a limit gets no adjustment. |

> [!NOTE]
> Dynamic pricing suggestions apply only to rental classes that aren't packages.

### Apply a dynamic price suggestion

The six drivers each contribute a signed percentage. The system **sums** them into a calculated percentage, and then clamps that result with the **Maximum increase percentage** and **Maximum decrease percentage** defined for the period code. The suggested amount is the base rate, which is the amount on the line's active price line, adjusted by the resulting percentage.

To use a suggestion, select a main line on a quotation or a contract and select **Dynamic pricing** > **Dynamic price suggestion** on the lines toolbar. The dialog lists the drivers, the percentages, and the suggested amount. Select **Apply** to use it, or **Close** to discard it. There's no field for changing the suggested amount before you apply it.

Applying a suggestion updates **every** price line of the document line, not only the active period. If **Approval required** is enabled, the quotation or contract is put *On hold* with the reason *Dynamic price applied*.

To back a suggestion out, select **Revert to base price** on the line. The line returns to the rate and discount that the price search finds for the line's invoice-from date, not to the amount that it carried before the adjustment.

## Set up discounts

Discounts let you offer reduced rates for specific customers or rate groups. The system stores discounts as separate discount records, and matches them to a contract line the same way it matches rates.

To set up discounts, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rental discounts**. This action opens the rental rate page filtered to discount records.
1. Select **New**.
1. Set the **Account code** (and, for a specific account or group, the **Account relation**). Discounts match on the customer's **Rental discount group** (a rental rate group whose **Type** is *Discount*), not on the **Rental rate group**.
1. Set the **Class code** and **Class relation**. On a discount record, you can set the class code to *Table* (one rental class), *Group* (a rental category), or *All* (all classes).
1. Add a line for each **Period** code and enter a **Discount percentage** or a **Discount amount**. For example:
    - Day: 5% discount
    - Week: 10% discount
    - Month: 15% discount
1. Select **Save**.

When you add the customer to a contract, the system automatically applies the matching discount. Learn more about the order in which a discount amount, a line percentage, and a header percentage are applied in [How the discount is applied to the rate](#how-the-discount-is-applied-to-the-rate).

## Set up rate override limits

To prevent excessive discounting, set maximum override limits per rental class and period code. When a price reduction on a quotation or contract exceeds the limit, the system puts the document *On hold* with the reason *Rate override*. A user with the **Rental manager** role approves a held document, because that role includes contract approval.

To configure rate override limits, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental rates** > **Rate overrides**.
1. Select the **Period** (required) and, optionally, the **Rental class**. A record without a rental class is the default limit for that period code, and the system uses it whenever no class-specific record exists.
1. Enter the **Allowed amount** and the **Allowed percentage** that a price can be reduced before the system holds the document. A value of 0 means no limit for that measure. For example:
    - Day: **Allowed percentage** 5%, **Allowed amount** $10
    - Week: **Allowed percentage** 10%, **Allowed amount** $25
    - Month: **Allowed percentage** 15%, **Allowed amount** $50

Keep these behaviors in mind when you plan the limits:

- If no limit record exists for a period code, the system doesn't hold anything, except for customers that have **Fixed rate** set.
- The system treats a customer whose customer record has the **Fixed rate** flag set as zero tolerance. The system holds any price reduction on that customer's documents, whatever the limits say. You can still enter the price, but the system places the document on hold.
- Price **increases** aren't checked on a standard template.
- On a template that uses calendar-based invoicing, the system checks the limits against the header discount percentage instead of the line price change.

## Related information

- [Rental management overview](rental-management-overview.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Call off and close rental contracts](call-off-close-rental-contracts.md)
