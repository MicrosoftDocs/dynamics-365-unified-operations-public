---
title: Set up rental templates (preview)
description: Set up rental templates for billing, charges, payment terms, fleet eligibility, customer assignments, movement automation, and purchase options.
author: jodahlMSFT
ms.author: jodahl
ms.reviewer: kamaybac
ms.search.form: RentalTemplate
ms.topic: how-to
ms.date: 10/23/2026
ai-usage: ai-assisted
ms.custom:
  - bap-template
---

# Set up rental templates (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

A *rental template* supplies reusable terms and defaults for rental quotations and contracts. Templates define billing scenarios, invoicing methods, miscellaneous charges, payment terms, price factors, and financial dimensions. They also control hourly and overtime billing, stand-down credits, insurance checks, refueling charges, quotation expiration, fleet item movement automation, and rental purchase option terms.

Create separate templates for agreement types or billing policies that need different defaults. Configure fleet type eligibility, customer assignments, and charge exemptions to control which fleet items, customers, and charges each template allows. This setup helps coordinators apply consistent terms without entering the same settings on every quotation or contract.

Before you configure templates, complete the setup described in [Configure prerequisites for rental management](set-up-rental-prerequisites.md). Create billing scenarios and invoice methods as described in [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md). Create the supporting records that your template needs, such as revenue categories, movement reason codes, and purchase option interest calculations. Learn more in [Set up rental reference data](set-up-rental-reference-data.md).

## Manage rental templates

To create, edit, or delete rental templates, go to **Rental management (Preview)** > **Setup** > **Rental templates**. From this page, you can do the following actions:

- To edit an existing template, edit its basic settings directly in the list, or open the template to make detailed changes.
- To edit fleet types, charge exemptions, or customer assignments, select the template and, on the Action Pane, open the **Template** tab and select the corresponding action.
- To delete a template, select it in the list and, on the Action Pane, select **Delete**.
- To create a template, on the Action Pane, select **New** and fill in the details described in the remaining sections of this article.

## Configure fleet type eligibility

Fleet type eligibility determines which fleet items, bulk fleet items, and attachments you can add to quotations and contracts created from a template. Availability opened from those documents lists only eligible fleet types.

To configure the fleet types and item types that a template allows, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental templates**.
1. Select the template. On the Action Pane, open the **Template** tab and select **Fleet type**.
1. Create, edit, or delete records as needed by using the actions on the Action Pane.
1. For each record that you're creating or editing, make the following settings:
    - **Fleet type** – Select a fleet type to allow on documents that use this template. Set this value when you create the row; you can't change it afterward.
    - **Fleet item, attachment, or all** – Select *Fleet item*, *Bulk fleet item*, *Attachment*, or *All* to specify which item types the row permits. To rent bulk fleet items, select *Bulk fleet item* or *All*.
    - **Contract type** – Select *All*, *Rent-to-rent*, or *Rental purchase option*. This field is visible only when **Rental purchase option transfer process** is enabled on the template.

1. Save your changes.

> [!IMPORTANT]
> A template with no fleet type rows allows no fleet items. Configure these rows for every template before you use it to create rental documents.

## Manage customer assignments

Customer assignments associate a rental template with specific customer accounts. To maintain them, select the template and, on the Action Pane, open the **Template** tab and select **Rental template customer assignments**.

You can also maintain these records at **Rental management (Preview)** > **Setup** > **Rental template customer assignments**. Each record pairs a customer account with a rental template.

## Configure miscellaneous charge exemptions

Miscellaneous charge exemptions prevent specific template charges from being added to a customer's rental quotations and contracts. Use them when a customer's negotiated terms exclude a charge that still applies to other customers.

Each exemption pairs one customer account with one rental template line. It doesn't exempt the customer from a fee type across all templates. For example, exempting a customer from one template's environmental fee doesn't exempt them from an environmental fee defined on another template.

To configure exemptions for charges on a template, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental templates**.
1. Select the template. On the Action Pane, open the **Template** tab and select **Miscellaneous charge exemptions**.
1. Create or delete exemption records as needed by using the actions on the Action Pane.
1. For each record that you're creating, make the following settings:
    - **Customer account** – Select the customer that is exempt from the charge.
    - **Rental template line** – Select the miscellaneous charge line from the template. Create a separate exemption record for each charge that the customer is exempt from.

1. Save your changes.

You can't edit either field on an existing exemption record. To change the customer or charge, delete the record and create a replacement.

## Work with the Lines view for rental templates

Use the **Lines** view to configure the template's main rental line and miscellaneous charge lines. The header supplies document-level defaults, while the line grid and line details define the charges that can accompany a rental.

To work with these settings, create or open a template from the **Rental templates** list and select the **Lines** view. On the Action Pane, select **Edit** if you need to change an existing template.

### The Rental template header FastTab

The **Rental template header** FastTab identifies the template and defines defaults for quotations and contracts created from it. These settings apply to the template as a whole, not to the miscellaneous charge selected in the line grid.

- The **Identification** field group identifies the template and the type of agreement it supports. Make the following settings in this group:
    - **Rental template** – Enter a unique identifier when you create the template. You can't change it afterward.
    - **Name** – Enter a descriptive name that helps coordinators choose the appropriate template.
    - **Contract type** – Select the agreement type, such as *Rental*, *Lease*, or *No-charge*. This setting determines the fleet item's agreement status when you activate a contract. You can't change it on an existing template.

- The **Number sequences** field group lets you use template-specific document numbering. Make the following settings in this group:
    - **Contract number sequence** – Select a number sequence for contracts created from this template. Leave it blank to use the contract number sequence on the **Rental parameters** page.
    - **Quotation number sequence** – Select a number sequence for quotations created from this template. Leave it blank to use the quotation number sequence on the **Rental parameters** page.

    Use template-specific sequences when different lines of business need separate contract and quotation numbering.

- The **Main line** field group defines the main rental line and its billing behavior. Every quotation and contract you create from the template gets a main line. The **Main line** settings decide how the system identifies that line and which revenue it posts to. Make the following settings in this group:
    - **Main line ID** – Enter the identifier to assign to main lines created from this template. This field is required. You can't add fleet items or rental classes to a quotation or contract without it.
    - **Name** – Enter the description to use for the main line.
    - **Revenue category** – Select the revenue category that determines the sales category used to invoice the main line. This field is required.
    - **Revenue category for bulk fleet items** – Select the revenue category to use for bulk fleet item lines. Set this field before you use the template to add bulk fleet items to a quotation or contract.
    - **Billing scenario** – Select the scenario that defines the available pricing periods and their sequence.
    - **Calendar** – Select the work calendar whose open days the system uses for calendar-based invoicing. You also need a calendar for calendar-based best rate calculation or an invoice method that invoices on a specific day.
    - **No fee** – Set to *Yes* to exclude the main line from fee calculation. The system selects this option for *No-charge* contracts.
    - **Hourly billing** – Set to *Yes* to bill by the hour instead of using the standard day, week, and month periods. This mode can suit smaller fleet items, such as generators or light towers. This setting is available for the *Rental* contract type. The billing scenario must include an hourly billing period, and you can't combine hourly billing with the rental purchase option transfer process.
    - **Hourly rate rounding** – Select *No*, *Up*, or *Down* to control rounding of the hours used for hourly billing. This setting rounds the hours, not the resulting amount.
    - **Approval required** – Set to *Yes* to require approval of overtime charges before invoicing. This setting is available when **Overtime billing method** isn't *End of contract*.
    - **Overtime billing method** – Select when to calculate overtime from service meter unit (SMU) readings: *End of contract*, *Period*, or *Last reading*. *End of contract* evaluates usage across the whole rental, so customers can balance heavy and light usage across months. *Period* calculates overtime for each invoice period. For example, a mining customer might prefer periodic overtime bills to one large charge at contract end. *Last reading* calculates overtime at the most recent SMU reading.
    - **Prorate overtime** – Set to *Yes* to derive the hourly overtime charge from the active rental rate and its allowed hours. Otherwise, the calculation uses the rental class's overtime rate.
    - **Prorate stand-down** – Set to *Yes* to prorate stand-down credits from the active rate on contracts without calendar-based invoicing. Otherwise, the calculation uses the base rate. For stand-down recorded in days, this setting also controls the hours deducted from the included SMU allowance.
    - **Notify user of suggested attachments and bulk fleet items** – Set to *Yes* to notify coordinators when they add a main line whose rental class has suggested attachments or bulk fleet items.

    Overtime billing requires a period code marked for overtime, and stand-down credits require a stand-down period code. Learn more in [Period code flags](set-up-billing-periods-scenarios.md#period-code-flags). Learn more about overtime approvals in [Handle overtime charges](invoice-rental-contracts.md#handle-overtime-charges).

    > [!IMPORTANT]
    > Enable **Prorate stand-down** for long-term rentals without calendar-based invoicing. Otherwise, a credit based on the daily rate can exceed the prorated value of the customer's monthly rental.

- The **Calendar-based invoicing** field group controls billing according to the template's work calendar. Make the following settings in this group:
    - **Calendar-based invoicing** – Set to *Yes* to invoice rental lines only for open days in the selected calendar. You must select a **Calendar**.
    - **Adjust first month** – Set to *Yes* to end the first monthly invoice period at month-end. This setting is editable when calendar-based invoicing is enabled. If the invoice method invoices on a specific day, the system sets this option automatically and ends the first period on that day instead. Use this setting to align monthly billing with month-end close.
    - **Prorate for calendar** – Set to *Yes* to prorate the active rental rate over the calendar's open days. Otherwise, calendar-based calculation uses the base rate.

- The **Finance information** field group supplies invoicing and payment defaults. Make the following settings in this group:
    - **Invoice method** – Select the method that determines the invoicing date of each invoice period.
    - **Currency** – Select the currency for quotations and contracts created from this template. Leave it blank to use the legal entity's accounting currency.
    - **Payment** – Select the default payment terms.

- The **Best rate calculation defaults** field group controls how the best rate calculation (BRC) evaluates rental duration and usage. Make the following settings in this group:
    - **Service meter unit calculation** – Select whether SMU calculation covers the full period or only the last period.
    - **Full period** – Set to *Yes* to evaluate the whole rental period. Set to *No* to evaluate only the part that hasn't been invoiced.
    - **Use calendar for best rate calculation** – Set to *Yes* to count days according to the template's work calendar during BRC. This setting is available only when a **Calendar** is selected.
    - **Use calendar for stand-down** – Set to *Yes* to use the template's work calendar for stand-down calculations. This setting is available only when a **Calendar** is selected.
    - **Calculate grace hours** – Set to *Yes* to let BRC exclude the last day when the rental ends within the price period's grace hours and this produces a lower charge.

- The **Default price factor values** field group supplies the price factors proposed on documents created from this template. Make the following settings in this group:
    - **Application** – Select the default application price factor.
    - **Shift** – Select the default shift price factor.
    - **Location** – Select the default location price factor.

Learn more about pricing periods and invoice methods in [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md). Learn more about pricing and price factors in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

### The Rental template lines FastTab

The **Rental template lines** FastTab defines miscellaneous charges that can accompany the main rental line, such as fuel or damage charges. These lines are charge definitions, not individual fleet items to rent. Common charge line types include the following:

- **Delivery/pickup freight** – A final invoice charge, so that pickup costs are billed when the work is done.
- **Environmental fee** – Typically 1.5% of the rental fee with a maximum cap.
- **Damage waiver** – Optional fire, theft, and vandalism coverage.
- **SMU-based charges** – Per-hour charges for tire wear, rental repair reserve, or other usage-based fees. Set **SMU based charge** on the template line, and use **Minimum hours** to guarantee a minimum charge.

To create a charge definition, select **Add line** on the FastTab's toolbar. Edit a line directly in the grid or select it to change additional settings on the **Line details** FastTab. To delete a selected line, select **Remove** on the toolbar.

For each line, make the following settings in the grid:

- **Rental template line** – Enter a unique identifier for the charge line. This field is required, and you can't change it after you create the line.
- **Name** – Enter a description that identifies the charge.
- **Revenue category** – Select the revenue category that determines the sales category used to invoice the charge. This field is required.
- **Amount** – Enter the proposed charge amount for a normal, amount-based charge. For percentage-based charges, use **Percent** instead.
- **Percent** – Enter the percentage to apply to the calculation base. This field is available for percentage-based charges. Set the calculation method and base on the **Line details** FastTab.
- **Maximum amount** – Enter a cap for a percentage-based charge. Enter *0* for no maximum. This field is available only for percentage-based charges. For example, to cap a 1.5% environmental fee at $500, enter *500* here and *1.5* in **Percent**.
- **Miscellaneous charge type** – Select whether the charge applies to the document header or a rental line, and whether it's recurring, once-only, or supplemental.
- **Final invoice** – Set to *Yes* to apply the charge only to the final invoice schedule. This setting is available only for once-only header or line charges that have **Default charge** set to *Yes*. For line charges, configure the rental classes that the charge applies to by using **Rental template line class rules**.
- **Default charge** – Set to *Yes* to propose adding this charge automatically to documents created from the template. You must select a **Miscellaneous charge type**. Customer charge exemptions and, for final-invoice line charges, class rules can prevent automatic addition.
- **Fee type** – Select the fee classification that identifies the charge to the corresponding rental process, such as fuel calculation.

#### Fee types and tax

The available fee types are *Transport*, *Fuel*, *Property tax*, *Loss waiver*, *Repair*, and *Environmental fee*. They also include *Fire-theft-vandalism waiver*, *Installation*, *After hours charge*, *Contingency fee*, *Other*, and *Other - roll up*.

The fee type classifies the charge; it doesn't determine its invoicing pattern or sales tax treatment. Some types also identify charges for specific processes. *Fuel* identifies the refueling charge, and *Fire-theft-vandalism waiver* identifies the insurance waiver charge. The insurance expiry check can add *Fire-theft-vandalism waiver* or *Loss waiver* charges. Learn more in [Run rental management periodic jobs](run-rental-periodic-jobs.md#run-the-insurance-expiry-check).

On active contracts, **Adjust miscellaneous charge** is unavailable for *Environmental fee* and *Fire-theft-vandalism waiver* charges.

Use *Property tax* for a charge that recovers personal property tax on rented fleet items from the customer. It's a rental charge, not the sales tax calculated on the document. It's priced, invoiced, and taxed like other miscellaneous charges. Learn more in [How tax groups are determined](understand-rental-financial-integration.md#how-tax-groups-are-determined).

#### Final-invoice class rules

For a final-invoice charge of type *Line - Once*, select **Rental template line class rules** on the toolbar. Use this page to specify which rental classes the charge applies to and how to add it:

- **Class relation type** – Select *Table* for one rental class, *Group* for a rental category, or *All* for all rental classes.
- **Class relation** – Select the rental class or category. Leave this field blank when **Class relation type** is *All*.
- **Add to final invoice** – Select *Required* to add the charge with the rental line and bill it on the final invoice. Select *Prompt* to offer the charge in the contract closing wizard.

The system checks for a class-specific rule first, then a category rule, and finally an *All* rule. Without a matching rule, it neither adds the final-invoice line charge automatically nor proposes it at closing. Customer charge exemptions still apply.

### The Line details FastTab

The **Line details** FastTab shows additional settings for the line selected on the **Rental template lines** FastTab. Select a line in the grid before you change these settings.

The **General** tab controls how to calculate the charge, attach it to a rental document, and handle specialized billing. It contains the following field groups:

- The **General** field group defines the charge description, revenue category, and calculation. Settings shared with the grid update the same charge definition. Make the following settings in this group:
    - **Name** – Enter the charge description.
    - **Normal or percentage** – Select *Normal* to use an amount, or *Percent* to calculate a percentage of a base amount. You can change this setting only for *Line - Once* and *Line - Recurring* charges. Other charge types use *Normal*.
    - **Calculation base** – For a percentage-based charge, select *Rental fee*, *Asking price*, or *Rental rate* to identify the amount to apply the percentage to.
    - **Revenue category** – Select the revenue category used to invoice the charge.
    - **Amount** – Enter the charge amount when **Normal or percentage** is *Normal*.
    - **Percent** – Enter a value from *0* through *100* when **Normal or percentage** is *Percent*.
    - **Maximum amount** – Enter the maximum calculated charge for a percentage-based line, or *0* for no maximum.

    Switching to *Percent* clears **Amount**. Switching to *Normal* clears **Percent** and **Maximum amount**.

- The **Relation setup** field group controls where the charge belongs and whether to add it by default. Make the following settings in this group:
    - **Default charge** – Set to *Yes* to propose automatic addition, subject to charge exemptions and applicable final-invoice class rules.
    - **Miscellaneous charge type** – Select a header-level or line-level charge and its recurring, once-only, or supplemental behavior.

- The **Other** field group holds fee classifications and damage-related options. Make the following settings in this group:
    - **Fee type** – Select the classification that the relevant rental process uses to identify this charge.
    - **No fee** – Set to *Yes* to exclude this line from fee calculation.
    - **Add damage charge to contract** – Set to *Yes* to add this charge once to a fleet item's contract line when damage is recorded on a fleet item movement. The amount comes from this template line. Only a *Line - Once* charge can use this setting, and only one line per template can have it enabled.
    - **No invoice on credit** – Set to *Yes* to exclude the charge when its main line produces a credit.
    - **Damage** – Set to *Yes* to use the miscellaneous charge to record damage on the contract. This setting is available only for line-level charges.

- The **SMU based charge** field group defines usage-based miscellaneous charges. Make the following settings in this group:
    - **SMU based charge** – Set to *Yes* to base the charge on SMU usage. This setting is available for *Line - Recurring* charges and *Line - Once* charges marked for the final invoice. Use an *End of period* invoice method to avoid having to adjust calculated values manually.
    - **Minimum hours** – Enter the minimum usage to bill for each period. The system bills actual usage when it exceeds this minimum. This field is available only when **SMU based charge** is set to *Yes*.

The **Financial dimensions** tab holds the **Default financial dimensions** for the selected template line. Select a value for each dimension that you need, such as a department or cost center. The available dimensions depend on your organization's financial dimension setup, so the fields can differ between environments.

Use **Options** > **Validate data integrity** to check the integrity of the dimension data.

## Work with the Header view for rental templates

Use the **Header** view to configure document-level defaults, movement automation, quotation expiration, financial dimensions, and rental purchase options. Unlike the **Lines** view, this view doesn't show the miscellaneous charge line grid.

To work with these settings, create or open a template from the **Rental templates** list and select the **Header** view. On the Action Pane, select **Edit** if you need to change an existing template.

Some fields appear in both views. They update the same template record, so changing a shared field in one view also changes it in the other.

### The General FastTab

The **General** FastTab identifies the template and defines operational defaults for contract activation, fleet item swaps, call-offs, insurance, and refueling. Use its field groups to decide which actions the system automates and which defaults coordinators can use.

- The **Overview** field group identifies the template and sets its payment terms. Make the following settings in this group:
    - **Rental template** – Enter the template's unique identifier when you create it. You can't change it afterward.
    - **Name** – Enter a descriptive name for the template.
    - **Payment** – Select the payment terms to apply to quotations and contracts created from this template. These terms determine the customer's payment due date.

- The **Number sequences** field group supplies template-specific document numbering. Make the following settings in this group:
    - **Contract number sequence** – Select the number sequence for contracts created from this template.
    - **Quotation number sequence** – Select the number sequence for quotations created from this template.

    Leave either field blank to use the corresponding number sequence on the **Rental parameters** page.

- The **Contract activation** field group controls movement creation and printing when a contract becomes active. Make the following settings in this group:
    - **Fleet item movement automation on contract activation** – Set to *Yes* to create and schedule outbound fleet item movements automatically on activation. The system skips fleet items that already have a qualifying movement.
    - **Fleet item movement reason for activation** – Select the reason code to assign to movements created during activation.
    - **Print contract** – Select *Never*, *Prompt*, or *Always* to control automatic printing during activation. *Prompt* asks whether to print during interactive activation. *Always* also enables automatic printing during noninteractive activation. The system doesn't automatically print the contract again if it already has a print date.

- The **Fleet item swap** field group supplies movement defaults for replacing a fleet item on an active contract. Make the following settings in this group:
    - **Fleet item movement automation on swap** – Select *No*, *Create*, or *Create then schedule* to control whether the swap process creates fleet item movements and schedules them.
    - **Fleet item movement reason for swap** – Select the reason code to assign to movements created for a swap.

- The **Call-offs** field group supplies movement defaults for ending a rental and arranging the fleet item's return. Make the following settings in this group:
    - **Fleet item movement automation on call-off** – Select *None*, *Create*, or *Create and schedule* as the default movement action in the call-off dialog.
    - **Fleet item movement reason for call-off** – Select the reason code to assign to movements created for a call-off.

- The **Insurance** field group controls the insurance check when you add a fleet item to a quotation or contract. Make the following setting in this group:
    - **Insurance validation** – Set to *Yes* to check the customer's physical damage insurance and link qualifying coverage or apply the configured waiver charge. Configure a line-level charge whose **Fee type** is *Fire-theft-vandalism waiver* and whose **Default charge** is set to *No*. The insurance process uses this charge when a waiver is required.

    Register the customer's physical damage insurance before you enable validation. Use blanket coverage for a policy that covers the fleet generally, or model- or serial-specific coverage for particular fleet items. Review **Policy expiration date** as part of this setup.

- The **Fuel parameters** field group controls refueling charges when you receive fleet items. Make the following settings in this group:
    - **Fuel calculation** – Set to *Yes* to calculate fuel charges from inbound fuel readings for fleet item models whose **Fuel type** is *Fuel*.
    - **Fuel price** – Enter the fuel price per unit of volume.
    - **Diesel calculation** – Set to *Yes* to calculate diesel charges from inbound fuel readings for fleet item models whose **Fuel type** is *Diesel*.
    - **Diesel price** – Enter the diesel price per unit of volume.

    Both calculations use a template line whose **Fee type** is *Fuel*. Configure that charge line before you use refueling charges.

- The **Address setup** field group controls job site registration during pickup location selection. Make the following setting in this group:
    - **Allow job site selection** – Set to *Yes* to let coordinators also register the customer's job site when they select a pickup fleet location.

Learn more about movements and scheduling in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md). Learn more about customer insurance and job sites in [Manage customer and prospect records for rental](manage-customer-prospect-records.md).

### The Main line FastTab

The **Main line** FastTab defines the main rental line's identity, revenue categories, billing scenario, calendar, and billing behavior. It contains the same fields as the **Main line** field group on the **Rental template header** FastTab in the **Lines** view.

Configure these shared settings in whichever view you prefer. Learn more about each field and its dependencies in [The Rental template header FastTab](#the-rental-template-header-fasttab).

### The Contract template FastTab

The **Contract template** FastTab sets the agreement type, currency, invoice timing, and a fleet item movement reason. Make the following settings:

- **Contract type** – Select the agreement type when you create the template. You can't change it afterward.
- **Currency** – Select the currency for quotations and contracts created from this template. Leave it blank to use the legal entity's accounting currency.
- **Invoice method** – Select the method that determines the invoicing date of each invoice period. If the method invoices on a specific day, select a **Calendar** on the **Main line** FastTab.
- **Fleet item movement reason** – Select the reason code that describes why fleet items are moved. Set the event-specific reasons for activation, swaps, and call-offs on the **General** FastTab.

**Contract type**, **Currency**, and **Invoice method** are also available in the **Lines** view.

### The Quotation FastTab

The **Quotation** FastTab defines the default and maximum validity of quotations created from this template. Both settings count days from **Expiration base** on the **Rental parameters** page, not necessarily from the date you create the quotation.

Make the following settings in the **Expiration** field group:

- **Default expiration date** – Enter the number of days from the expiration base to the expiry date proposed for a new quotation. Enter *0* to leave new quotations without an expiry date.
- **Maximum expiration date** – Enter the maximum number of days from the expiration base that users can specify for a quotation's expiry date. Enter *0* for no maximum.

### The Financial dimensions FastTab

The **Financial dimensions** FastTab holds the template-level **Default financial dimensions**. These values are separate from the dimensions you maintain for individual miscellaneous charge lines in the **Lines** view.

Select a value for each dimension that you need. Your organization's financial dimension setup determines the available fields. Use **Options** > **Validate data integrity** to check the integrity of the dimension data.

### The Rental purchase option parameters FastTab

The **Rental purchase option parameters** FastTab supplies purchase option terms and interest defaults for contracts created from this template. A rental purchase option (RPO) lets the customer apply a share of rental payments toward purchasing the fleet item.

- The **Rental purchase option** field group defines the template's purchase option settings. Make the following settings in this group:
    - **Contract rental purchase option** – Set to *Yes* to identify the template as intended for RPO contracts. The **Rental purchase option** setting on the contract determines whether that contract is an RPO contract.
    - **Rental purchase option transfer process** – Set to *Yes* to make **Initiate rental purchase option transfer** available on contracts that use this template. This action creates a transfer request for the contract's fleet items. You can't combine this setting with **Hourly billing**.
    - **Asking price as purchase price** – Set to *Yes* to copy a fleet item's asking price into the rental line's purchase price when the fleet item is added. Set to *No* to start the purchase price at *0*.
    - **Maximum term** – Enter the maximum number of price periods for the purchase option. After this term ends, generating invoice schedules puts the contract on hold.
    - **Minimum term** – Enter the minimum number of price periods for the purchase option. Users must confirm a call-off date or estimated return date that falls before this term ends.

    These term values become defaults on the contract. Keep the minimum term at or below the maximum term.

- The **Interest** field group defines how to calculate interest on the outstanding purchase balance. Make the following settings in this group:
    - **Interest type** – Select the method for determining the interest rate. *Fixed* uses the base interest percentage for the invoice period. *Prime plus* adds that percentage to the applicable prime rate.
    - **Rental purchase option interest calculations** – Select the named calculation that defines the day-count basis for interest. Without an interest calculation, the purchase option report doesn't calculate interest.
    - **Compound interest** – Set to *Yes* to add accrued interest to the declining balance when calculating subsequent interest.

Set the rent percentages and base interest percentages on the **Rental purchase option periods** FastTab. Learn more about the supporting calculation records and prime rates in [Set up rental purchase option interest](set-up-rental-reference-data.md#set-up-rental-purchase-option-interest).

### The Rental purchase option periods FastTab

The **Rental purchase option periods** FastTab defines the share of rent applied toward the purchase balance and the base interest percentage for each range of invoice periods. The system copies these rows to quotations and contracts created from the template.

Use the FastTab's toolbar to add or delete rows as needed, and edit percentages directly in the grid. For each row, make the following settings:

- **Percentage of rent to apply** – Enter the percentage of the rental fee that reduces the outstanding purchase balance.
- **Base interest percentage** – Enter the interest rate for the invoice periods in this range. For *Prime plus* interest, this percentage is added to the prime rate.
- **From** – Enter the number of the first invoice period that the row applies to.
- **To** – Enter the number of the last invoice period that the row applies to. Leave this field blank to apply the row to all later periods.

Period ranges must not overlap, and **To** can't be earlier than **From**. Set the range when you create the row; you can't edit its boundaries afterward. To change a range manually, delete the row and create a replacement.

When you add a later range, the system can close an existing open-ended range automatically. It sets the earlier row's **To** value to the period immediately before the later range begins.

## Related information

- [Set up rental reference data](set-up-rental-reference-data.md)
- [Configure rental parameters](configure-rental-parameters.md)
- [Set up billing periods and scenarios](set-up-billing-periods-scenarios.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Create rental quotations and contracts by using the rental cart](create-rental-quotations-contracts.md)
- [Invoice rental contracts](invoice-rental-contracts.md)
