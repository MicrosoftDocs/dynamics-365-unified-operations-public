---
title: Period charges
description: The charges feature in Microsoft Dynamics 365 Supply Chain Management has been extended with additional capabilities covering the ability to calculate additional charges periodically.  
author: Henrik Andersen
ms.author: henrikan
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/09/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Period charges

[!include [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](../includes/preview-banner.md)]

<!--KFM: Preview until 10.0.38 GA -->

The topic in this article provides information about **Period charges** which provide the ability to charge customers upon orders invoiced in a specific period that did not meet certain criteria. The feature supports setting up  period charge rules which identify such invoices and define applicable charges. Charges can be calculated upon minimum charge amount (for example: minimum delivery fee), minimum order quantity, or combination of both.

## Enable Period charges

In order to leverage period charges, enable the feature *Period charges* in feature management.

When this feature is enabled, new settings are available from accounts receivable parameters to control the period charge calculations. Also when this feature is enabled, changes are made to the  **Accounts receivable \> Invoices \> All free text invoice** Free text invoice details page to accommodate for free text invoices created for period charges. New page **Period charge rule** is added to **Accounts receivable \> Charges setup**, and new page **Calculate period charge** is added to **Accounts receivable \> Periodic tasks**.

## Working with Period charges

1. Go to **Accounts receivable \> Setup \> Accounts receivable parameters**.
1. Open the **Prices** tab.
1. On the **Charges** FastTab, make the following settings:
    - **Quantity threshold source** – Choose which types of lines to consider when calculating quantity-based period charge rules. Select *Sales order lines* to consider sales order line quantities (including cancelled sales order lines). Select *Invoice lines* to consider invoice line quantities instead. The general recommendation is to set this to *Invoice lines* unless the business requirements require otherwise.
    - **Site and warehouse source** – Choose where to match site and warehouse values set as selection criteria in period charge rules. Select *Invoice line* to match values set in individual invoice lines (in the `CustInvoiceTrans` table). Select *Sales order* to instead match values set in the sales order header (in the SalesTable table). The general recommendation is to set this to *Invoice line* unless the business requirements require otherwise.
    - **Required charge code match** – Set this value to No, if the period charge rule calculation for a line type monetary threshold or quantity threshold minimum amount does not require at least one invoice line charge matching the charge code on the rule line for a free text invoice line to be created. Set this value to Yes, if the period charge rule calculation for a line type monetary threshold or quantity threshold minimum amount requires at least one invoice line charge matching the charge code on the rule line for a free text invoice line to be created. The general recommendation is to set this to *Yes* unless the business requirements require otherwise.
    - **Extra batch helpers** – Enter a value to add batch helpers for load balancing when period charge calculation is run in a batch. Batch helpers are also referred to as threads.

### Set up period charge rule

Use this procedure to define period charge rules for customers, site and warehouse. Period charges are applied when you run calculate period charge batch for a period. You can define period charge rules for specific customer, site, or warehouse or for groups of customer, site, or warehouse. You can also define period charges that apply to all customers, site, or warehouse.

1. Go to **Accounts receivable \> Charges setup \> period charge rule**.
1. Click **New** to define a new period charge rule. Enter Name and description of the rule.
1. Select the date in **From invoice date** and **To invoice date** for which this period charge rule is valid.
1. Select an account in the **Account code** field from the following values:
    Table – Assign charges to a specific customer.
    Group – Assign charges to a miscellaneous charges group.
    All – Assign charges to all customers.
1. In the **Customer relation** field, select a specific customer if you selected Table, or select a customer charges group if you selected Group.
1. Select value in **Site**, keep it blank in case you want this rule to be applicable for all sites.
1. Select value in **Warehouse**, keep it blank in case you want this rule to be applicable for all warehouses.
1. Click **Add** button available under the Lines fast tab and configure the values as per the **Type** of the threshold.

#### Period charge rule explained

- **Name**: The name of the period charge rule.
- **Description**: A short description of the period charge rule.
- **From invoice date**: The invoice date from which this period charge rule is valid.
- **To invoice date**: The invoice date up to which this period charge rule is valid.
- **Account code**: The scope of customers to whom this period charge rule should apply. Select *Table* to apply the rule only to the customer selected in the *Customer relation* field. Select *All* to apply the rule to all customers.
- **Account relation**: If **Account code** is set to *Table*, then this field specifies the customer account that this period charge rule applies to. If **Account code** is set to *All*, then the rule will apply to all customers and this field will be blank.
- **Site**: The site where this period charge rule applies. If this field is blank, then the rule will apply to all sites. Whether this setting is applied to sales order header or invoice line is determined by the Site and warehouse source value. If a site is specified, then the current period charge rule will only apply to either customer invoice lines with this same site, or to invoice lines related to a sales order with this same site on the sales order header.
- **Warehouse**: The warehouse where this period charge rule applies. If this field is blank, then the rule will apply to all warehouses. Whether this setting is applied to sales order header or invoice line is determined by the Site and warehouse source value. If a warehouse is specified, then the current period charge rule will only apply to either customer invoice lines with this same warehouse, or to invoice lines related to a sales order with this same warehouse on the sales order header.
- **Type**: The type of period charge rule line. Select *Monetary threshold* to create a rule line that calculates the monetary value of qualifying charges, establishes minimum monetary thresholds for each charge type, and generates a free text invoice line that charges the shortfall for customers who don't meet the thresholds during the period. Select *Quantity threshold* to create a rule line that calculates the total sold quantity of qualifying items, establishes a minimum quantity threshold, and generates a free text invoice line with a fixed charge for customers who don't meet the threshold during the period. Select *Quantity threshold minimum amount* to create a rule line that includes both quantity and monetary thresholds.

Thresholds for all three types are transaction line based: Either based on line quantities (sales order line or invoice line) or line monetary values (charge line for invoice line)

- **Monetary threshold**: The monetary threshold at which a rule line applies. If the period charge calculation finds that the sum of qualifying line charges charged to a customer over the period is below this threshold, then the system will generate a free text invoice line with a charge equal to the shortfall.
- **Currency**: The currency for the **Monetary threshold** field value. This currency will also be used as a selection criterion, so a period charge rule line will only be evaluated against charge lines for invoice lines that use this same currency. The related free text invoice line generated for the customer will also use this currency.
- **Charge code**: The type of charge for which a period charge rule line applies (such as freight, installation, or handling).
- **Include debit charge amount only**: Controls which types of invoice line charges to include when calculating against the monetary threshold for a rule line. For rule lines where this check box is selected, the calculation will only include invoice line charges where the value is a debit (positive). For rule lines where this check box isn't selected, the calculation will include all invoice line charges, regardless of the value sign (debit/positive or credit/negative).
- **Quantity threshold**: The quantity threshold at which a rule line applies. If the period charge calculation finds that the total qualifying quantities ordered by a customer during the period is below this threshold, then the system will generate a free text invoice line with a charge equal to the charge amount specified by the rule line.
- **Unit**: The unit of measure used for the **Quantity threshold** field value. This unit of measure will also be used as a selection criterion, so a period charge rule line will only be evaluated against order or invoice line quantities that use either this same unit or another unit that can be converted to it using a conversion factor defined in the system.

Standard unit of measure rounding rules apply when unit of measure conversion is required.

- **Include debit quantity only**: Controls which types of sales order or invoice lines to include when calculating against the quantity threshold for a rule line. For rule lines where this check box is selected, the calculation will only include sales order or invoice lines where the value is a debit (positive). For rule lines where this check box isn't selected, the calculation will include sales order or all invoice lines, regardless of the value sign (debit/positive or credit/negative).
- **Charge amount**: The amount that a customer will be charged for a period for rule lines of type *Quantity threshold*, when the quantity threshold is not met for a rule line. This amount will appear as a fixed fee on the related free text invoice line for the relevant customer.
- **Currency for charge amount**: The currency used for the charge amount for rule lines of type *Quantity threshold*. This applies to the related free text invoice line and isn't used as a selection criterion.
- **Revenue account**: The revenue account that will be defaulted onto the free text invoice line created by a period charge rule line.
- **Description**: The description that will be defaulted on the related free text invoice line created by a rule.

### Calculate Period charge

After period charge rule setup is complete, use the Calculate Period charge page to calculate Period charge. Calculate period charge will create free text invoice if there will be shortfall between the configured threshold on Period charge rule setup and total charges/quantity processed on sales transactions for a period. Calculate period charge process can be executed from the UI or it can be configured as batch job.

- Click **Accounts receivable \> Periodic tasks \> Calculate period charge**

The following parameters are available on the page to control the period charge calculation.

- **Customer account**: Albeit the label states customer account, the account selected will be an invoice account to calculate period charges. Only invoices for this particular invoice account will be considered in the calculate period charges run. Leave this blank to calculate period charges for all accounts.  
- **Rule name**: Select a rule name to calculate period charges for that rule only. Leave this blank to calculate period charges for all rules.
- **From invoice date**. Select the first invoice date to include in the period charge calculation. If you are setting up a recurring job, you should leave this blank and use the **Max invoice age** setting instead.
- **To invoice date**: Select the last invoice date to consider in the period charge calculation. If you are setting up a recurring job, you should leave this blank and use the **Max invoice age** setting instead.
- **Max invoice age**: Specify the maximum age (in days) of invoices to include in the period charge calculation. The calculation will consider all invoice lines that are this old or younger on the day the calculation runs.
- **Days per free text invoice**: Specify the number of days to cover with each free text invoice generated by the period charge calculation.

### Example 1

In this scenario, the Period charge rule is setup with 100 USD monetary threshold freight charge applicable to all customers, all sites , and all warehouses and it is active with no expiration date. For customer US-001, multiple sales invoices are posted between 1-Jan-2022 to 10-Jan-2022 and total of 45 USD freight charge amount posted on multiple sales invoices between 1-Jan-2022 to 10-Jan-2022. For customer US-002, total of 105 USD freight charge amount posted on multiple sales invoices between 1-Jan-2022 to 10-Jan-2022.

1. User executes the **Calculate period charge** for all customers, for the period 1-Jan-2022 to 10-Jan-2022.

Result: A 55 USD monetary threshold free text invoice with one invoice line is created for US-001.

### Example 2

In this scenario, the Period charge rule is setup with 50 pcs. quantity threshold with minimum charge of 30 USD applicable to all customers, all sites, and all warehouses and it is active with no expiration date. For a customer US-001, multiple sales invoices are posted between 1-Jan-2022 to 10-Jan-2022 and total 23 pcs. invoiced quantities posted theses quantity sales transactions.

1. User executes the **Calculate period charge** for a customer US-001, for the period 1-Jan-2022 to 10-Jan-2022.

Result: A 30 USD quantity threshold free text invoice with one invoice line is created.

### Example 3

In this scenario, the Period charge rule is setup with 25 pcs. quantity threshold minimum amount and freight minimum charge of 20 USD applicable to all customers, all sites, and all warehouses and it is active with no expiration date. For a customer US-001, multiple sales invoices are posted between 1-Jan-2022 to 5-Jan-2022 and on these sales transactions total invoiced quantities is 15 pcs. and total freight charge amount posted is 15 USD.

1. User executes the **Calculate period charge** for customer US-001, for the period 1-Jan-2022 to 10-Jan-2022.

Result: 5 USD quantity threshold minimum amount free text invoice with one invoice line is created.

## Free text invoice

The Calculate period charge process creates one or more free text invoices when shortfalls are found. From the free text invoice details page, a **Line invoice base** page is added on the line action bar. The **Line invoice base** page is available only for a free text invoice created as a result of a period charge calculation. This page can be used to get insight into the basis upon which a specific free text invoice line was created.

1. Click Accounts  **Accounts receivable \> Invoices \> All free text invoices**
1. Select the free text invoice and click **Edit**.
1. Select free text invoice line, Click **Line invoice base**
1. On the **Period charge rule** line fast tab, detail of period charge rule applied on this free text line can be found.  
1. On the **Lines** fast tab, a summary of the invoice and sales order transactions included in the period charge evaluation for this free text line can be found.

To get more information about free text invoice, see Create a free text invoice.
