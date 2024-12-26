---
title: Period charges
description: Learn about about period charges, which let you charge customers when a collection of orders invoiced over a specified period failed to meet specific criteria.
author: AditiPattanaik
ms.author: adpattanaik
ms.topic: how-to
ms.date: 11/22/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Period charges

[!include [banner](../includes/banner.md)]

Period charges let you charge customers when a collection of orders that were invoiced over a specified period failed to meet specific criteria. The *Period charges* feature supports the setup of period charge rules that identify these invoices and define applicable charges. Charges can be calculated based on a minimum charge amount (such as minimum delivery fee), a minimum order quantity, or a combination of both.

The *Period charges* feature introduces the following changes to your system:

- Fields are added to the **Accounts receivable parameters** page to control the period charge calculations.
- Details are added to the **Free text invoice** details page to accommodate free text invoices that are created for period charges.
- A new page that's named **Period charge rule** is added under **Accounts receivable** \> **Charges setup** on the navigation pane.
- A new page that's named **Calculate period charge** is added under **Accounts receivable** \> **Periodic tasks** on the navigation pane.

## Prerequisites

Before you can use this feature, your system must meet the following requirements:

- You must be running Microsoft Dynamics 365 Supply Chain Management version 10.0.38 or later.
- The feature that's named *Period charges* must be turned on in [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md). (As of Supply Chain Management version 10.0.42, it's turned on by default)

## Configure period charges

The **Accounts receivable parameters** page provides several fields that control how period charge calculations work in your system. Follow these steps to configure them.

1. Go to **Accounts receivable** \> **Setup** \> **Accounts receivable parameters**.
1. On the **Prices** tab, on the **Charges** FastTab, set the following fields:

    - **Quantity threshold source** – Select one of the following values to specify which type of lines to consider when quantity-based period charge rules are calculated:

        - *Invoice lines* – Consider invoice line quantities. We recommend that you select this value unless specific business requirements demand otherwise.
        - *Sales order lines* – Consider sales order line quantities (including canceled sales order lines).

    - **Site and warehouse source** – Select one of the following values to specify where to match site and warehouse values that are set as selection criteria in period charge rules:

        - *Invoice line* – Match values that are set on individual invoice lines (in the `CustInvoiceTrans` table). We recommend that you select this value unless specific business requirements demand otherwise.
        - *Sales order* – Match values that are set on the sales order header (in the `SalesTable` table).

    - **Required charge code match** – Select whether period charge rule calculations for lines of the *Monetary threshold* or *Quantity threshold minimum amount* type require the creation of at least one invoice line charge that matches the charge code on the rule line for a free text invoice line. We recommend that you set this option to *Yes* unless specific business requirements demand otherwise.
    - **Extra batch helpers** – Enter the number of batch helpers (threads) to use for load balancing when period charge calculations are run in a batch.

## Manage period charge rules

Period charges are calculated and applied when you run the *Calculate period charge* batch job for a period. You can define period charge rules for a specific customer, site, or warehouse, or for groups of customers, sites, or warehouses. You can also define period charges that apply to all customers, sites, or warehouses. Follow these steps to create, edit, or delete a period charge rule.

1. Go to **Accounts receivable** \> **Charges setup** \> **Period charge rule**.
1. Follow one of these steps:

    - To add a new rule, select **New** on the Action Pane.
    - To edit an existing rule, select it in the list pane, and then select **Edit** on the Action Pane.
    - To delete an existing rule, select it in the list pane, and then select **Delete** on the Action Pane.

1. On the header of the new or selected rule, set the following fields:

    - **Name** – Enter a name for the rule.
    - **Description** – Enter a short description of the rule.
    - **From invoice date** – Select the first date when the rule is valid.
    - **To invoice date** – Select the last date when the rule is valid.
    - **Account code** – Select one of the following values to define the scope of customers (accounts) that the rule applies to:

        - *Table* – The rule applies only to the customer (account) that's selected in the **Account relation** field.
        - *All* – The rule applies to all customers (accounts).

    - **Account relation** – If you set the **Account code** field to *Table*, select the specific customer (account) that the rule applies to.
    - **Site** – Select the site where the rule applies. If the rule applies to all sites, leave this field blank. If you select a site, the rule applies only to customer invoice lines that have the same site or to invoice lines that are related to a sales order that has the same site on the sales order header.
    - **Warehouse** – Select the warehouse where the rule applies. If the rule applies to all warehouses, leave this field blank. If you select a warehouse, the rule applies only to customer invoice lines that have the same warehouse or to invoice lines that are related to a sales order that has the same warehouse on the sales order header.

1. On the **Lines** FastTab, use the buttons on the toolbar to add and remove rule lines as you require, to define the rule that you want to create. For each line, set the following fields:

    - **Type** – Select one of the following values to specify the type of charge that the rule line creates:

        - *Monetary threshold* – Calculate the monetary value of qualifying charges, establish a minimum monetary threshold for each charge type, and generate a free text invoice line that charges the shortfall to customers who don't meet the thresholds during the period.
        - *Quantity threshold* – Calculate the total purchased quantity of qualifying items, establish a minimum quantity threshold, and generate a free text invoice line that has a fixed charge for customers who don't meet the threshold during the period.
        - *Quantity threshold minimum amount* – Calculate a charge based on both quantity and monetary thresholds, and generate free text invoice lines as required.

        Thresholds for all three charge types are based on transaction lines. They're based on either line quantities (for sales order or invoice lines) or line monetary values (charge lines for invoice lines).

    - **Monetary threshold** – Enter the monetary threshold that the rule line applies at. If the period charge calculation determines that the sum of qualifying line charges that are charged to a customer over the period is below this threshold, the system generates a free text invoice line that has a charge that equals the shortfall.
    - **Currency** – Select the currency for the **Monetary threshold** field value. This currency is also used as a selection criterion. Therefore, a period charge rule line is evaluated only against charge lines for invoice lines that use the same currency. The related free text invoice line that's generated for the customer also uses this currency.
    - **Charge code** – Select the type of charge that the rule line applies to (such as freight, installation, or handling).
    - **Include debit charge amount only** – Control which types of invoice line charges are included in the calculation against the monetary threshold for a rule line. For rule lines where this checkbox is selected, the calculation includes only invoice line charges where the value is a debit (positive). For rule lines where this checkbox is cleared, the calculation includes all invoice line charges, regardless of the value sign (debit/positive or credit/negative).
    - **Quantity threshold** – Enter the quantity threshold that the line applies at. If the period charge calculation determines that the sum of qualifying quantities that a customer ordered during the period is below this threshold, the system generates a free text invoice line that has a charge that equals the charge amount that the rule line specifies.
    - **Unit** – Select the unit of measure for the **Quantity threshold** field value. This unit of measure is also used as a selection criterion. Therefore, a period charge rule line is evaluated only against order or invoice line quantities that use either the same unit or another unit that can be converted to it by using a conversion factor that's defined in the system. When unit of measure conversion is required, standard unit of measure rounding rules apply.
    - **Include debit quantity only** – Control which types of sales order or invoice lines are included in the calculation against the quantity threshold for a rule line. For rule lines where this checkbox is selected, the calculation includes only sales order or invoice lines where the value is a debit (positive). For rule lines where this checkbox is cleared, the calculation includes all sales order or invoice lines, regardless of the value sign (debit/positive or credit/negative).
    - **Charge amount** – The amount that a customer will be charged for a period for rule lines of the *Quantity threshold* type when the quantity threshold isn't met for a rule line. This amount appears as a fixed fee on the related free text invoice line for the relevant customer.
    - **Currency for charge amount** – The currency of the charge amount for rule lines of the *Quantity threshold* type. This currency applies to the related free text invoice line and isn't used as a selection criterion.
    - **Revenue account** – The revenue account that was entered on the free text invoice line that the rule line creates.

1. On the **Line details** FastTab, you can enter or view a description of the rule line that's currently selected on the **Lines** FastTab. This description is added to the related free text invoice lines that the rule line creates.

## Run and schedule period charge calculations

To calculate period charges and generate free text invoice lines for customers who don't meet the criteria that your period charge rules define, you must run the *Calculate period charge* batch job. You can manually run this batch job, or you can schedule it to run automatically on a recurring basis. Follow these steps to run or schedule the *Calculate period charge* job.

1. Go to **Accounts receivable** \> **Periodic tasks** \> **Calculate period charge**.
1. In the **Calculate period charge** dialog box, on the **Parameters** FastTab, set the following fields:

    - **Customer account** – Select the invoice account to calculate period charges for. Only invoices for this invoice account will be considered. To calculate period charges for all accounts, leave this field blank.
    - **Rule name** – To calculate charges only for a specific rule, select the name of that rule. To calculate period charges for all rules, leave this field blank.
    - **From invoice date** – Select the first invoice date to include in the period charge calculation. If you're setting up a recurring job, you should leave this blank and set the **Max invoice age** field instead.
    - **To invoice date** – Select the last invoice date to include in the period charge calculation. If you're setting up a recurring job, you should leave this field blank and set the **Max invoice age** field instead.
    - **Max invoice age** – Specify the maximum age (in days) of invoices to include in the period charge calculation. The calculation will consider all invoice lines that are this old or younger on the day when the calculation runs.
    - **Days per free text invoice** – Specify the number of days that are covered by each free text invoice that the period charge calculation generates.

1. On the **Run in the background** tab, set up the background options as usual for batch jobs in Supply Chain Management. If you want the job to run periodically, select the **Recurrence** link, and define the run schedule.
1. Select **OK** to run or schedule the job.

## Inspect free text invoices created by period charge calculations

The *Calculate period charge* job creates one or more free text invoices when shortfalls are found. Follow these steps to get more information about free text invoices that period charge calculations create.

1. Go to **Accounts receivable** \> **Invoices** \> **All free text invoices**.
1. Open the free text invoice that you want to inspect.
1. Select the free text invoice line that you want to inspect, and then, on the **Invoice lines** toolbar, select **Line invoice base**. (The **Line invoice base** page is visible only for free text invoices that are created as a result of a period charge calculation.)
1. Select the **Period charge rule line** FastTab to view details about the period charge rule that created the selected free text invoice line.
1. Select the **Lines** FastTab to view a summary of the invoice and sales order transactions that were included in the period charge evaluation for the selected free text invoice line.

For more information about free text invoices, see [Create a free text invoice](../../finance/accounts-receivable/create-free-text-invoice-new.md).

## Period charge rule example scenarios

This section provides examples that show how you might set up period charge rules.

### Example scenario 1

You have a period charge rule that establishes a monetary threshold freight charge of 100 US dollars (USD). It's applicable to all customers, sites, and warehouses, and has no expiration date.

- For customer US-001, multiple sales invoices are posted between January 1 and January 10, 2022. A total overall freight charge amount of 45 USD is posted on multiple sales invoices between January 1 and January 10, 2022.
- For customer US-002, a total overall freight charge amount of 105 USD is posted on multiple sales invoices between January 1 and January 10, 2022.

You now run the *Calculate period charge* batch job for all customers for the period from January 1 through January 10, 2022.

The result is a free text invoice that's generated for customer US-001. It has one invoice line for 55 USD.

### Example scenario 2

You have a period charge rule that establishes a quantity threshold of 50 pcs. and a minimum charge of 30 USD. It's applicable to all customers, sites, and warehouses, and has no expiration date.

For customer US-001, multiple sales invoices are posted between January 1 and January 10, 2022. The total overall quantity is 23 pcs.

You now run the *Calculate period charge* batch job for customer US-001 for the period from January 1 through January 10, 2022.

The result is a free text invoice that's generated for customer US-001. It has one invoice line for 30 USD.

### Example scenario 3

You have a period charge rule that establishes a quantity threshold of 25 pcs. and a minimum freight charge of 20 USD. It's applicable to all customers, sites, and warehouses, and has no expiration date.

For customer US-001, multiple sales invoices are posted between January 1 and January 5, 2022. The total overall quantity is 15 pcs., and the total overall freight charge is 15 USD.

You now run the *Calculate period charge* batch job for customer US-001 for the period from January 1 through January 10, 2022.

The result is a free text invoice that's generated for customer US-001. It has one invoice line for 5 USD.
