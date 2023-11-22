---
title: Period charges (preview)
description: Period charges let you charge customers when a collection of orders invoiced over a specified period failed to meet certain criteria. The feature supports setting up  period charge rules that identify such invoices and define applicable charges.
author: Henrikan
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/22/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Period charges (preview)

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

*Period charges* let you charge customers when a collection of orders invoiced over a specified period failed to meet certain criteria. The feature supports setting up  period charge rules that identify such invoices and define applicable charges. Charges can be calculated based on a minimum charge amount (such as minimum delivery fee), minimum order quantity, or a combination of both.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

To use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management 10.0.38 or later.
- The feature that is named *Period charges* must be turned on in [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

The *Period charges* feature introduces the following changes to your system:

- Settings are added to the **Accounts receivable parameters** page to control the period charge calculations.
- Details are added to the  **Free text invoice** details page to accommodate free text invoices created for period charges.
- A new page called **Period charge rule** is added under **Accounts receivable \> Charges setup** in the navigation pane.
- A new page called **Calculate period charge** is added under **Accounts receivable \> Periodic tasks** in the navigation pane.

## Configure period charges

The **Accounts receivable parameters** page provides several settings that control how period charge calculations work on your system. Follow these steps to configure them.

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. Expand the **Charges** FastTab and make the following settings:
    - **Quantity threshold source** – Choose which types of lines to consider when calculating quantity-based period charge rules. Select one of the following options:
        - *Invoice lines* – Consider invoice line quantities. We recommend using this option unless you have specific business requirements that demand otherwise.
        - *Sales order lines* – Consider sales order line quantities (including canceled sales order lines).
    - **Site and warehouse source** – Choose where to match site and warehouse values set as selection criteria in period charge rules. Select one of the following options:
        - *Invoice line* – Match values set in individual invoice lines (in the `CustInvoiceTrans` table). We recommend using this option unless you have specific business requirements that demand otherwise.
        - *Sales order* – Match values set in the sales order header (in the `SalesTable` table).
    - **Required charge code match** – Choose whether or not period charge rule calculations for lines of type *Monetary threshold* or *Quantity threshold minimum amount* require the creation of at least one invoice line charge that matches the charge code on the rule line for a free text invoice line.  We recommend setting this to *Yes* unless you have specific business requirements that demand otherwise.
    - **Extra batch helpers** – Enter the number batch helpers (threads) to use for load balancing when period charge calculations are run in batch.

## Manage period charge rules

Period charges are calculated and applied when you run the *Calculate Period charge* batch job for a period. You can define period charge rules for a specific customer, site, or warehouse or for groups of customers, sites, or warehouses. You can also define period charges that apply to all customers, sites, or warehouses. Follow these steps to create, edit, or delete a period charge rule.

1. Go to **Accounts receivable \> Charges setup \> Period charge rule**.
1. Follow one of these steps:
    - To add a new rule, select **New** on the Action Pane.
    - To edit an existing rule, select it on the list pane and then select **Edit** on the Action Pane.
    - To delete and, select it on the list pane and then select **Delete** on the Action Pane.

1. Make the following settings in the header of the new or selected rule:
    - **Name** – Enter a name for the rule.
    - **Description** – Enter a short description of the rule.
    - **From invoice date** – Select the first date on which this period charge rule is valid.
    - **To invoice date** – Select the last date on which this period charge rule is valid.
    - **Account code** – Set the scope of customers (accounts) for which the rule applies. Choose one of the following values:
        - *Table* – The rule applies only to the customer (account) selected in the **Account relation** field.
        - *All* – The rule applies to all customers (accounts).
    - **Account relation** – If you set **Account code** to *Table*, then select the specific customer (account) to which the rule applies.
    - **Site** – Select the site where the rule applies. Leave this field blank to apply this rule to all sites. If a site is specified, then this period charge rule will only apply to either customer invoice lines with this same site, or to invoice lines related to a sales order with this same site on the sales order header.
    - **Warehouse** – Select the Warehouse where the rule applies. Leave this field blank to apply this rule to all Warehouses. If a warehouse is specified, then the current period charge rule will only apply to either customer invoice lines with this same warehouse, or to invoice lines related to a sales order with this same warehouse on the sales order header.

1. On the **Lines** FastTab, use the toolbar buttons to add and remove rule lines as needed to define the rule you want to create. Make the following settings for each line:

    - **Type** – Choose the type of charge the rule line creates. Choose one of the following values:
        - *Monetary threshold* – Calculates the monetary value of qualifying charges, establishes a minimum monetary thresholds for each charge type, and generates a free text invoice line that charges the shortfall for customers who don't meet the thresholds during the period.
        - *Quantity threshold* – Calculates the total purchased quantity of qualifying items, establishes a minimum quantity threshold, and generates a free text invoice line with a fixed charge for customers who don't meet the threshold during the period.
        - *Quantity threshold minimum amount* – Calculates charge based on both quantity and monetary thresholds and generates free text invoice lines as needed.

        Thresholds for all three types are based on transaction lines They're based on either line quantities (for sales order or invoice lines) or line monetary values (charge lines for invoice lines).

    - **Monetary threshold** – Enter the monetary threshold at which the rule line applies. If the period charge calculation finds that the sum of qualifying line charges charged to a customer over the period is below this threshold, then the system generates a free text invoice line with a charge equal to the shortfall.
    - **Currency** – Select the currency for the **Monetary threshold** field value. This currency will also be used as a selection criterion, so a period charge rule line will only be evaluated against charge lines for invoice lines that use this same currency. The related free text invoice line generated for the customer will also use this currency.
    - **Charge code** – Select the type of charge for which the rule line applies (such as freight, installation, or handling).
    - **Include debit charge amount only** – Controls which types of invoice line charges to include when calculating against the monetary threshold for a rule line. For rule lines where this check box is selected, the calculation will only include invoice line charges where the value is a debit (positive). For rule lines where this check box isn't selected, the calculation will include all invoice line charges, regardless of the value sign (debit/positive or credit/negative).
    - **Quantity threshold** – Enter the quantity threshold at which the line applies. If the period charge calculation finds that the total qualifying quantities ordered by a customer during the period are below this threshold, then the system will generate a free text invoice line with a charge equal to the charge amount specified by the rule line.
    - **Unit** – Select the unit of measure used for the **Quantity threshold** field value. This unit of measure will also be used as a selection criterion, so a period charge rule line will only be evaluated against order or invoice line quantities that use either this same unit or another unit that can be converted to it using a conversion factor defined in the system. Standard unit of measure rounding rules apply when unit of measure conversion is required.
    - **Include debit quantity only** – Controls which types of sales order or invoice lines to include when calculating against the quantity threshold for a rule line. For rule lines where this check box is selected, the calculation will only include sales order or invoice lines where the value is a debit (positive). For rule lines where this check box isn't selected, the calculation will include sales order or all invoice lines, regardless of the value sign (debit/positive or credit/negative).
    - **Charge amount** – The amount that a customer will be charged for a period for rule lines of **Type** *Quantity threshold*, when the quantity threshold isn't met for a rule line. This amount will appear as a fixed fee on the related free text invoice line for the relevant customer.
    - **Currency for charge amount** – The currency used for the charge amount for rule lines of **Type** *Quantity threshold*. This applies to the related free text invoice line and isn't used as a selection criterion.
    - **Revenue account** – The revenue account entered onto the free text invoice line created by the rule line.

1. On the **Line details** FastTab, you can add or read a **Description** for the rule line currently selected on the **Lines** FastTab. This description is added to the related free text invoice lines created by the rule line.

## Run and schedule period charge calculations

To calculate period charges and generate free text invoice lines for customers who don't meet the criteria defined by your period charge rules, you must run the *Calculate period charge* batch job. You can run this batch job manually or you can schedule it to run automatically on a recurring basis. Follow these steps to run or schedule the *Calculate period charge* job.

1. Go to **Accounts receivable \> Periodic tasks \> Calculate period charge**.
1. The **Calculate period charge** dialog opens. Make the following settings on the **Parameters** FastTab:
    - **Customer account** – Select the invoice account to calculate period charges for. Only invoices for this invoice account will be considered. Leave this field blank to calculate period charges for all accounts.  
    - **Rule name** – To only calculate charges for a specific rule, select that rule name here. Leave this field blank to calculate period charges for all rules.
    - **From invoice date** – Select the first invoice date to include in the period charge calculation. If you're setting up a recurring job, you should leave this blank and use the **Max invoice age** setting instead.
    - **To invoice date** – Select the last invoice date to consider in the period charge calculation. If you're setting up a recurring job, you should leave this field blank and use the **Max invoice age** setting instead.
    - **Max invoice age** – Specify the maximum age (in days) of invoices to include in the period charge calculation. The calculation will consider all invoice lines that are this old or younger on the day the calculation runs.
    - **Days per free text invoice** – Specify the number of days to cover with each free text invoice generated by the period charge calculation.
1. Expand the **Run in the background** tab and set up the background options as usual for batch jobs in Supply Chain Management. If you want to run the job periodically, select the **Recurrence** link and establish the run schedule.
1. Select **OK** to run or schedule the job.

## Inspect free text invoices created by period charge calculations

The *Calculate period charge* job creates one or more free text invoices when shortfalls are found. Follow these steps to get more information about free text invoices that were created by period charge calculations.

1. Go to  **Accounts receivable \> Invoices \> All free text invoices**.
1. Open the free text invoice you want to inspect.
1. Select the free text invoice line you want to inspect and then select **Line invoice base** from the **Invoice lines** toolbar. (The **Line invoice base** page is only visible for free text invoices created as a result of a period charge calculation.)
1. Expand the **Period charge rule** line FastTab to see details about the period charge rule that created this free text invoice line.  
1. Expand the **Lines** FastTab to see a summary of the invoice and sales order transactions included in the period charge evaluation for this free text invoice line.

For more information about free text invoice, see [Create a free text invoice](../../finance/accounts-receivable/create-free-text-invoice-new.md).

## Period charge rule example scenarios

This section provides a few examples of how you might set up period charge rules.

### Example scenario 1

You have a period charge rule that establishes a 100 USD monetary threshold freight charge that applies to all customers, sites, and warehouses with no expiration date.

- For customer US-001, multiple sales invoices are posted between 1-Jan-2022 and 10-Jan-2022 and a total overall freight charge amount of 45 USD is posted on multiple sales invoices between 1-Jan-2022 and 10-Jan-2022.
- For customer US-002, a total overall freight charge amount of 105 USD is posted on multiple sales invoices between 1-Jan-2022 to 10-Jan-2022.

Now you run the *Calculate period charge* batch job for all customers for the period 1-Jan-2022 to 10-Jan-2022.

The result is a free text invoice generated for customer US-001 with one invoice line for 55 USD.

### Example scenario 2

You have a period charge rule that establishes a 50 pcs. quantity threshold with minimum charge of 30 USD applicable to all customers, sites, and warehouses with no expiration date.

For customer US-001, multiple sales invoices are posted between 1-Jan-2022 to 10-Jan-2022 with a total overall quantity of 23 pcs.

Now you run the *Calculate period charge* batch job for customer US-001 for the period 1-Jan-2022 to 10-Jan-2022.

The result is a free text invoice generated for customer US-001 with one invoice line for 30 USD.

### Example scenario 3

You have a period charge rule that establishes a 25 pcs. quantity threshold and a minimum freight charge of 20 USD applicable to all customers, sites, and warehouses with no expiration date.

For customer US-001, multiple sales invoices are posted between 1-Jan-2022 to 5-Jan-2022 with a total overall quantity of 15 pcs. and a total overall freight charge of 15 USD.

Now you run the *Calculate period charge* batch job for customer US-001 for the period 1-Jan-2022 to 10-Jan-2022.

The result is a free text invoice generated for customer US-001 with one invoice line for 5 USD.
