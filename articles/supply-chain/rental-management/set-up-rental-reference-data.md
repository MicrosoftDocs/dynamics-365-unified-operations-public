---
title: Set up rental reference data (preview)
description: Set up rental reference data for fleet classification, movements, reservations, revenue posting, depreciation, and purchase option interest.
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

# Set up rental reference data (preview)

[!INCLUDE [banner](../includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

Rental reference data provides the classifications, codes, and supporting setup records that rental operations use. Configure these records to organize your fleet, control movement processing, and support consistent reservations, billing, and financial posting.

This setup includes rental classes and categories, fleet item models, attachment compatibility rules, inspection checklists, movement statuses, and reason codes. Financial setup includes journal assignments, revenue categories, depreciation profiles, and rental purchase option interest. Other records control availability summaries, reservations, charge exemptions, and notice to owner tracking.

Complete the standard component setup described in [Configure prerequisites for rental management](set-up-rental-prerequisites.md) before you configure rental reference data. Configure reusable document defaults separately, as described in [Set up rental templates](set-up-rental-templates.md). For legal entity-wide rules and per-user defaults, learn more in [Configure rental parameters](configure-rental-parameters.md).

## Configure released products for fleet items

Each released product used as a fleet item needs additional configuration (inventory dimension groups, item model group, the **Fleet item** setting, model, and rental class). Learn more about that setup, and about the rest of the inventory configuration, in [Configure inventory and location settings](configure-inventory-location-settings.md#configure-released-products-for-rental).

## Configure posting journals

Rental management uses journals to post revenue splits, fleet transfers, location changes, and serial number corrections. Assign journal names on the **Rental parameters** page so that each process uses the appropriate journal type and posting defaults.

Before you assign journal names, create them as described in [Configure journal names](set-up-rental-prerequisites.md#configure-journal-names). This procedure selects existing journal names; it doesn't create new ones.

To assign the journal names for rental posting, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Rental parameters**.
1. Open the **General** tab and set the following fields:
    - **Revenue split posting journal** – Select a ledger journal name of type *Daily* for revenue split processing.
    - **Transfer request movement journal** – Select an inventory journal name of type *Movement* for transfers that return a fleet item from a fleet type tracked as a fixed asset to one tracked as inventory.
    - **Transfer request inventory asset journal** – Select an inventory journal name of type *Fixed assets* for transfers from a fleet type tracked as inventory to one tracked as a fixed asset, such as from *New* to *Rental*.

1. Open the **Fleet items** tab and set the following fields:
    - **Location update** – Select an inventory journal name of type *Transfer* for the **Update location** action, which moves a fleet item between locations within its current warehouse.
    - **Serial number update journal** – Select an inventory journal name of type *Transfer* for corrections to a fleet item's serial number.

1. Open the **Fixed assets** tab and set **Transfer journal** to a ledger journal name of type *Post fixed assets*. The system uses this journal for fixed asset transactions when a fleet item transfers out of a fleet type whose **Value tracking method** is *Fixed asset*.
1. Save your changes.

## Configure fleet item movement statuses

Fleet item movement statuses define the processing steps for each type of fleet item movement. Each status drives a physical status for the fleet item and can trigger mandatory data collection or action items. <!-- Shipping and receiving in the Dynamics 365 Supply Chain Management mobile app uses the same setup. Posting from a mobile device applies the same physical status, readings, inspection, service status update, and action items. Learn more in [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md). -->

To configure the statuses, required checks, and follow-up actions for a fleet item movement step, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Fleet item movement status setup**.
1. Create, edit, or delete records as needed by using the buttons on the Action Pane.

1. For a record that you're creating or editing, review the following fields in the header. Set these values when you create a record; you can't change them on an existing record.
    - **Direction** – Select the movement direction that this setup applies to, such as *Outbound* or *Inbound*.
    - **Action** – Select the processing step to configure, such as *Schedule*, *Ship*, or *Receive*.

    Each record must have a unique combination of **Direction** and **Action**.

1. On the **General** FastTab, make the following settings:
    - **Status** – Select the status to assign to the fleet item movement when the action is posted, such as *In transit* or *Received*.
    - **Physical status** – Select the physical status to assign to the fleet items on the movement when the action is posted. Don't select *Ordered*. You can select *Delivered* only for outbound movements, and *In stock* only for inbound or internal movements.
    - **Fuel mandatory** – Set to *Yes* to require fuel readings when fleet items are shipped or received at this step.
    - **Service meter unit mandatory** – Set to *Yes* to require service meter unit (SMU) readings when fleet items are shipped or received at this step.
    - **Inspection mandatory** – Set to *Yes* to require inspection to be completed before the step is processed.
    - **Update service status** – Set to *Yes* to update the fleet items' service status when the action is posted.
    - **Service status** – Select the service status to assign to the fleet items. This field is available only when **Update service status** is set to *Yes*.

    **Fuel mandatory** and **Service meter unit mandatory** are both qualified by **Usage required** on the fleet item. A fleet item whose **Usage required** value is *No* is exempt, and an attachment is exempt unless **Usage required** is *Yes*. A reading of *0* counts as recorded. Learn more in [Configure inventory and location settings for rental management](configure-inventory-location-settings.md).

1. On the **Action items** FastTab, make the following settings to create follow-up action items when the *Ship* or *Receive* action is posted. These settings don't require or block processing.
    - **Damage** – Set to *Yes* to create a *Damaged* action item for each damage recorded on the movement.
    - **Delivery issue** – Set to *Yes* to create a *Delivery issue* action item when a delivery issue is recorded on the movement.
    - **Customer signature** – Set to *Yes* to create a *Customer signature unavailable* action item when **Signature not available** is selected on the movement's **Other** tab. A signature isn't required to complete the step.
    - **Modify rent return** – Set to *Yes* to create a *Modify rent return* action item for qualifying inbound returns. The SMU usage since shipment must be at or below **Modify rent return limit** on the **Rental parameters** page.

    <!--
    > [!NOTE]
    > In the public preview, the Dynamics 365 Supply Chain Management mobile app doesn't trigger **Delivery issue** or **Customer signature unavailable** action items. Record these conditions on the **Other** tab of the fleet item movement in Supply Chain Management.
    -->

    > [!NOTE]
    > Record delivery issues and unavailable customer signatures on the **Other** tab of the fleet item movement in Supply Chain Management.

1. Save your changes.

## Set up rental classes and categories

Use rental categories and classes to organize your fleet for reporting, pricing, and availability searches. Rental categories provide high-level groupings, while rental classes group fleet items that share the same rental rates.

Rental document lines identify the rental class a customer rents, rather than a specific fleet item. For example, a customer can rent from the *Medium CTL* class without choosing a particular model or serialized asset. The following table shows how categories, classes, and fleet item models or assets fit together:

| Level | Example | Description |
|---|---|---|
| Rental category | Compact track loader (CTL) | High-level grouping for reporting. |
| Rental class | Medium CTL | The pricing unit—all fleet items in a class share the same rates. |
| Fleet item model or Asset | CTL model A, CTL model B | Individual models and serialized assets. |

One place where rental categories and classes are useful is the *rental availability summary*. This summary allows you to quickly see which categories and classes of fleet items are available for rental, helping you manage inventory and plan for customer demand. This view is helpful when a customer needs, for example, a medium skid steer but doesn't care which specific make or model they get. To open the rental availability summary, go to **Rental management (Preview)** > **Common** > **Fleet items** > **Fleet item availability summary**.

### Set up rental categories

Rental categories are the top-level grouping in the hierarchy, used for reporting and filtering. Create categories before rental classes, because classes reference categories.

To set up rental categories, go to **Rental management (Preview)** > **Setup** > **Rental categories**. For each category, assign a **Category ID** and a **Name**.

### Set up rental classes

To set up rental classes, go to **Rental management (Preview)** > **Setup** > **Rental classes**.

Each class lists the fleet items that belong to it, with the **Default** flag showing which of them treat this class as their home class. You can also maintain this membership from the other side, on the fleet item. A fleet item can belong to several classes, so this list isn't limited to fleet items whose default class is the current one. Learn more in [Manage fleet item master data](manage-equipment-master-data.md#assign-a-fleet-item-to-more-than-one-rental-class).

For class-based pricing and packages, follow [Set up book rates](set-up-rental-rates-discounts.md#set-up-book-rates), [Set up discounts](set-up-rental-rates-discounts.md#set-up-discounts), and [Set up rental packages](set-up-rental-rates-discounts.md#set-up-rental-packages).

<!-- KFM: A great deal of functionality isn't being described here, including all settings, packages, rate table, and discount  -->

### Suggested attachments and bulk fleet items

*Suggested attachments* and *suggested bulk fleet items* are related fleet items or consumables that customers commonly rent together with the main fleet item. You maintain the suggestions by grouping rental classes, but you don't maintain them on the **Rental classes** page. Set them up by using the pages listed under **Rental management (Preview)** > **Setup** > **Validity rules and suggestions** in the navigator:

- **Suggested attachments by class** – Map which attachment rental classes belong with a prime rental class. Select the prime class, and then move classes between **Attachments available** and **Attachments selected for class**.
- **Suggested bulk fleet items by class** – Map which bulk fleet item rental classes belong with a prime rental class. Select the prime class, and then move classes between **Available bulk fleet items** and **Selected bulk fleet items**. The available list shows the released products whose **Fleet item type** is *Bulk fleet item*.

When a coordinator adds a main line for a relevant class to a contract, and the template has **Notify user of suggested attachments and bulk fleet items** enabled, the system prompts the coordinator to review the suggestions. This process helps ensure that you don't miss complementary items (for example, a bucket with an excavator, or fuel with a generator).

### Fleet item features

Use *fleet item features* to define descriptive attributes (for example, capacity, attachment type, or fuel type) that you can assign to fleet items and use to refine availability searches. To set up features, go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item features**.

## Set up revenue categories

Revenue categories link rental template charge lines to standard sales categories and tax item groups for financial posting. You need to create them before you can configure template lines.

To set up revenue categories, go to **Rental management (Preview)** > **Setup** > **Revenue categories**.

For each revenue category, configure:

- **Revenue category ID** – A unique identifier.
- **Name** – A descriptive name, such as *Rental revenue*, *Damage waiver*, or *Environmental fee*.
- **Valid from / Valid to** – Optional date range for the category.
- **Sales category** – The standard sales category that this rental revenue maps to. This category drives account determination through the sales category hierarchy.
- **Tax item group** – The item sales tax group used when this category is invoiced.

> [!NOTE]
> You must create the sales category hierarchy before you create revenue categories. Learn more in [Configure prerequisites for rental management](set-up-rental-prerequisites.md).

## Set up rental purchase option interest

Rental purchase option contracts charge interest on the outstanding purchase balance. Two setup pages hold the figures that the rental template points to.

To set up an interest calculation, go to **Rental management (Preview)** > **Setup** > **Rental purchase options** > **Rental purchase option interest calculations**. For each calculation, set:

- **Name** – The name of the interest calculation.
- **Interest calculation basis** – The numerator of the day-count fraction. The daily rate is the interest rate times this value, divided by the interest divisor.
- **Interest divisor** – The number of days that the yearly interest rate is divided by to give a daily rate. Use *365* for an actual year, or *360* for a 360-day year.

To maintain the prime rates, go to **Rental management (Preview)** > **Setup** > **Rental purchase options** > **Rental purchase option prime interest rates**, and add a row for each **Effective date** with its **Prime interest rate %**. The system uses these rates when the template's **Interest type** is *Prime plus*.

Select the interest calculation on the rental template, and set the percentages per band of periods on the template's **Rental purchase option periods** FastTab in the **Header** view. The rental purchase option report uses these figures to calculate the interest charge and the pay-off amount. Learn more in [Work with the Header view for rental templates](set-up-rental-templates.md#work-with-the-header-view-for-rental-templates).

## Set up physical statuses for availability summary

The rental availability summary combines each fleet item's agreement status with the *physical statuses for availability* setup. A fleet item whose physical status isn't listed here is left out of the summary altogether, so list every physical status that your fleet uses.

To configure physical statuses for the availability summary, go to **Rental management (Preview)** > **Setup** > **Physical statuses for rental availability summary**.

Create a record for each physical status you use, and select **Available in summary** on the statuses whose available fleet items should count as available. On a listed status that has **Available in summary** cleared, available fleet items count as *Not available* instead. Typically, you select **Available in summary** for statuses such as *In stock* and *Ready*, and clear it for statuses such as *In shop* or *Sold*.

## Set up reason codes

Reason and damage codes standardize how you record rental events, explain adjustments, and track damage resolution. The following table lists the setup pages and the purpose of each code type. The examples illustrate codes you might define; choose values that fit your organization's processes.

| Reason code type | Navigation path | Description |
|---|---|---|
| Fleet item movement reason codes | **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Fleet item movement reason codes** | Identify why a fleet item movement is created, such as contract activation, a swap, or a call-off. The system assigns codes from the rental template, which holds a general default and separate defaults for activation, swaps, and call-offs. |
| Canceled call-off reason codes | **Rental management (Preview)** > **Setup** > **Canceled call-off reason codes** | Explain why an active call-off is canceled, for example, because the customer extends the rental. A reason is required when you cancel an active call-off. Use stand-down reason codes instead for temporary rental interruptions. |
| Fleet item status reason codes | **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item status reason codes** | Explain physical status changes and record the reason on physical transactions. Codes marked **Fleet item movement replacement** are available for attachment replacement. Codes marked **Show on availability** cause affected fleet items to appear in availability. The code marked *Canceled* is assigned to fleet items that are canceled because their purchase order line is deleted; only one reason code can have this setting. |
| Stand-down reason codes | **Rental management (Preview)** > **Setup** > **Stand-down reason codes** | Explain an interruption that qualifies for a stand-down credit, such as bad weather or a breakdown. A reason is required when you register a stand-down. |
| Swap reason codes | **Rental management (Preview)** > **Setup** > **Swap reason codes** | Explain why one fleet item is swapped for another, such as a mechanical failure or a customer request for a replacement. |
| Credit reason codes | **Rental management (Preview)** > **Setup** > **Credit reason codes** | Explain why a rental invoice schedule is credited, such as a billing correction. A reason is mandatory when **Reason code for credit** is enabled on the **Rental parameters** page. |
| Damage codes | **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Damage codes** | Classify damage to a fleet item, such as a dent or a broken light. A damage code is required when damage is registered. <!-- These codes are also available when staff report damage in the Dynamics 365 Supply Chain Management mobile app. --> |
| Damage decision codes | **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Damage decision codes** | Record the decision about reported damage, such as *Repair* or *Scrap*. The code documents the decision; it doesn't determine invoicing. |
| Damage recovery statuses | **Rental management (Preview)** > **Setup** > **Fleet item movements** > **Damage recovery statuses** | Track progress in recovering damage costs from the responsible customer or vendor, for example, *Awaiting payment* or *Recovered*. These statuses track recovery; they don't trigger invoicing. |

> [!NOTE]
> There's no separate replace attachment reason code page. The reasons offered when you replace an attachment on a fleet item movement are *fleet item status reason codes* that have **Item movement replacement** enabled. Set them up as described in the table.

## Set up reservations

The reservation feature lets customers or rental staff request fleet items before a contract is created. Reservation setup has three parts: **Reservation types**, **Reservation requests**, and **Reservations**. The **Reservation requests** and **Reservations** pages also include linked **Fleet types** setup.

### Set up reservation types

*Reservation types* define the categories of reservations, such as *Standard* or *Priority*.

To set up reservation types, go to **Rental management (Preview)** > **Setup** > **Reservations** > **Reservation types**. For each type, assign a **Type** ID and a **Description**.

### Set up reservation requests

The *reservation requests* setup defines which fleet items you can request and the limits that apply to each reservation type. It also controls whether you can request a rental class or model before choosing individual fleet items.

To configure the request limits, selection rules, and eligible fleet types for a reservation type, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Reservations** > **Reservation requests**.
1. Create, edit, or delete records as needed by using the actions on the Action Pane.
1. For a record that you're creating, select the **Reservation type** in the header. Create one setup record per reservation type. You can't change the reservation type on an existing record.
1. On the **General** FastTab, make the following settings:
    - **Maximum requests per fleet item** – Enter the maximum number of active requests with overlapping dates that can include the same fleet item.
    - **Maximum requests per model or class** – Enter the maximum total quantity requested for any one model or rental class by requests of this type. This limit counts quantities, not just request records. Enter *0* for no limit.
    - **Control by number of fleet items** – Set to *Yes* to add a request-count check based on the number of fleet items in the requested item's fleet type. Set to *No* to skip this check.
    - **Maximum length** – Enter the maximum request duration in days, or *0* for no limit. This field is unavailable when **Open end date** is set to *Yes*.
    - **Expiry time** – Enter the number of days to add to the request's start date to calculate its expiry date. Enter *0* to leave the request without an expiry date.
    - **Model allowed** – Set to *Yes* to let a request specify a fleet item model. Clear the model and assign individual fleet items before you convert the request to a reservation.
    - **Class allowed** – Set to *Yes* to let a request specify a rental class instead of individual fleet items. Assign individual fleet items before you convert the request to a reservation.
    - **Open end date** – Set to *Yes* for requests without an end date. Users can't enter an end date, and the maximum length doesn't apply. Set to *No* to allow an end date and apply **Maximum length**.

1. On the **Fleet types** FastTab, configure which fleet types requests of this reservation type can include. On the FastTab's toolbar, select **Add line** to add a row or **Remove** to delete a selected row. For each row, make the following setting:
    - **Fleet type** – Select an allowed fleet type. Add a separate row for each fleet type that you want to allow. To change an existing row's fleet type, remove the row and add a replacement.

    > [!IMPORTANT]
    > If you leave the **Fleet types** FastTab empty, you can't add individual fleet items to requests of this type. Configure fleet type eligibility for confirmed reservations separately on the **Reservations** setup page.

1. Save your changes.

### Reservation settings

The *reservation setup* controls confirmed reservations for individual fleet items, whether you create them directly or convert reservation requests. Use it to set duration and advance-booking limits, protect reserved items from conflicting documents, and choose which rental or sales documents reservations can create.

To configure the limits, document rules, and eligible fleet types for a reservation type, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Reservations** > **Reservations**.
1. Create, edit, or delete records as needed by using the actions on the Action Pane.
1. For a record that you're creating, select the **Reservation type** in the header. Create one setup record per reservation type. You can't change the reservation type on an existing record.
1. On the **General** FastTab, configure the following groups of settings.

    In the **Reservation** group, define the reservation's duration, expiry, and booking requirements:

    - **Maximum length** – Enter the maximum reservation duration in days. This field is unavailable when **Open end date** is set to *Yes*.
    - **Expiry time** – Enter the number of days to add to the reservation's start date to calculate its expiry date. Requests that you convert to reservations keep their request expiry date.
    - **Time window** – Enter the maximum number of days from today to the reservation's start date. For example, enter *30* to allow reservations that start within the next 30 days. Enter *0* to allow any start date.
    - **Opportunity required** – Set to *Yes* to require an opportunity in the **Create reservation** dialog. Reservation requests don't require one.

    In the **Sales reservation** group, make the following setting:

    - **Open end date** – Set to *Yes* for reservations without an end date. Users can't enter an end date, and the maximum length doesn't apply. Set to *No* to allow an end date and apply **Maximum length**.

    In the **Stop rules** group, choose which document types can't use a reserved fleet item when an enabled validation rule finds a conflict. Set an option to *Yes* to apply that stop rule, or *No* to skip it:

    - **Stop sales quotation** – Block the reserved fleet item from use on a sales quotation when a conflict exists.
    - **Stop sales order** – Block the reserved fleet item from use on a sales order when a conflict exists.
    - **Stop rental quotation** – Block the reserved fleet item from use on a rental quotation when a conflict exists.
    - **Stop rental contract** – Block the reserved fleet item from use on a rental contract when a conflict exists.

    In the **Validation rules** group, define which differences between the reservation and a document count as a conflict:

    - **User validation** – Set to *Yes* to check that the document and reservation have the same responsible worker. A different worker triggers the applicable stop rule. This setting compares responsible workers, not signed-in users.
    - **Customer validation** – Set to *Yes* to check that the document and reservation have the same customer. A different customer triggers the applicable stop rule. Set to *No* to ignore customer differences in this check.

    If both validation options are *Yes*, both the customer and responsible worker must match to avoid a conflict. If both are *No*, these stop rules don't block use of the reserved fleet item.

    In the **Conversion** group, choose which documents you can create from a reservation and whether to copy its dates:

    - **Convert to rental quotation** – Set to *Yes* to enable creation of a rental quotation from the reservation.
    - **Convert to rental contract** – Set to *Yes* to enable creation of a rental contract from the reservation.
    - **Convert to sales quotation** – Set to *Yes* to enable creation of a sales quotation from the reservation.
    - **Convert to sales order** – Set to *Yes* to enable creation of a sales order from the reservation.
    - **Copy start date** – Set to *Yes* to copy the reservation's start date to the rental quotation or contract.
    - **Copy end date** – Set to *Yes* to use the reservation's end date as the estimated return date of the rental quotation or contract.

    The date-copy settings apply only to rental quotations and contracts, not sales documents. To edit these settings, enable **Convert to rental quotation**, **Convert to rental contract**, or both.

1. On the **Fleet types** FastTab, configure which fleet types confirmed reservations of this reservation type can include. On the FastTab's toolbar, select **Add line** to add a row or **Remove** to delete a selected row. For each row, make the following setting:
    - **Fleet type** – Select an allowed fleet type. Add a separate row for each fleet type that you want to allow. To change an existing row's fleet type, remove the row and add a replacement.

    > [!IMPORTANT]
    > If you leave the **Fleet types** FastTab empty, you can't assign fleet items to confirmed reservations of this type. This list is separate from the list on the **Reservation requests** setup page. When you convert a request, its fleet items must also meet the confirmed reservation's fleet type rules.

1. Save your changes.

## Manage fleet item models

*Fleet item models* describe the makes and models in your fleet and hold settings that individual fleet items share. Use them to maintain manufacturer and fuel information, organize models into groups, and propose defaults when you create fleet items. For each model, you can also define compatible attachments, suggest attachments for rental, and prepare shipping and receiving inspection checklists.

### Set up fleet item model records

Create a model record for each manufacturer and model combination that you use. Fleet items read shared attributes, such as fuel type and group code, from their model. Other settings provide defaults that you can change when you create an individual fleet item.

Before you start, create the manufacturers that you need at **Rental management (Preview)** > **Setup** > **Fleet items** > **Manufacturers**. If you want to group models, also create group codes at **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item group codes**.

To maintain the model's identification, shared settings, and creation defaults, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item models**.
1. Create, edit, or delete records as needed by using the actions on the Action Pane.
1. For a record that you're creating, make the following settings in the header:
    - **Manufacturer** – Select the manufacturer of the model.
    - **Model** – Enter the model identifier. The combination of manufacturer and model must be unique, so different manufacturers can use the same model identifier.

    You can't change either field on an existing record.

1. On the **General** FastTab, make the following settings:
    - **Description** – Enter a meaningful description of the model, such as its equipment type and distinguishing specifications.
    - **Group code** – Select a group to organize related models for reporting and attachment validity rules. For example, group all compact track loaders together regardless of manufacturer, or group models by product family.

1. On the **Insurance** FastTab, review the model-level price fields. These fields don't set rental rates. Learn more about rental pricing in [Set up rental rates and discounts](set-up-rental-rates-discounts.md).

    - In the **Insurance charges** group, maintain the amount fields for each date range and for service meter units (SMUs).
    - In the **Insurance charges percentage** group, maintain the corresponding percentage fields.

    <!-- TODO: PM input needed – Confirm the intended use of the model's Insurance amount and percentage fields, including the percentage base and how amounts and percentages interact. The form exposes these fields, but no production calculation reading them was found in the checked RentalManagement source. Don't infer an insurance calculation from the captions. -->

1. On the **Miscellaneous** FastTab, make the following settings:
    - **Attachment** – Set to *Yes* if this model represents an attachment, such as a bucket or forks. Set to *No* for a prime fleet item model.
    - **Attached to** – Select the prime fleet item model that this attachment model is intended to attach to. This model reference doesn't pair individual fleet items. Configure permitted combinations as described in [Configure attachment validity rules](#configure-attachment-validity-rules).
    - **Vendor family** – Enter the vendor's family designation for the model, if applicable. This value is descriptive, not a vendor account selection.
    - **Notice to owner exempt** – Set to *Yes* to exempt fleet items of this model from notice to owner tracking. Learn more in [Configure notice to owner (NTO) tracking](#configure-notice-to-owner-nto-tracking).
    - **Fuel type** – Select *Fuel*, *Diesel*, or *None*. This setting determines which fuel calculation applies when you receive a fleet item. Fuel and diesel charges also require the corresponding calculation and refuel prices on the rental template. Select *None* for a model that doesn't use either fuel type.
    - **Not for sale (default)** – Set to *Yes* to propose **Not for sale** when you create fleet items of this model. Set to *No* to leave that flag cleared by default. You can change the proposed value before you create the fleet item.
    - **Eligible for service** – Set to *Yes* to make new fleet items eligible for service in Field Service by default. Set to *No* to leave that flag cleared by default. You can change the proposed value when you create a fleet item.

1. Save your changes.

Learn more about using models when you create and maintain individual fleet items in [Manage fleet item master data](manage-equipment-master-data.md).

### Configure attachment validity rules

*Attachment validity rules* define which attachment models or groups can connect to a prime fleet item model or group. Use them to prevent incompatible pairings when attachment validation is enabled and to identify attachments that rental coordinators should offer.

For example, skid steers and their attachments can have different hydraulic flow requirements. You can restrict a high-flow attachment, such as a concrete grinder, to compatible high-flow models instead of allowing it on a standard-flow model.

To define permitted attachments and rental suggestions for a model, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item models**.
1. Select the model that you want to configure.
1. On the Action Pane, select **Attachment validity rules**. The page opens for the selected model.
1. In the **Validity rule setup** FastTab that contains the model lists, configure individual attachment models:
    - **Attachable models** – Review the models that the selected prime model allows. To add a model, select it in **Not attachable models** and then, on that list's toolbar, select **Add**. To remove a rule, select its row in **Attachable models** and then, on that list's toolbar, select **Remove**.
    - **Suggested for rental** – Set to *Yes* on an allowed model's row to suggest its attachments when you rent out the prime fleet item. Set to *No* to keep the compatibility rule without using it for suggestions.

1. In the **Validity rule setup** FastTab that contains the group lists, configure attachment groups. The settings here work the same as they do for the other **Validity rule setup** FastTab.

1. Save your changes.

Rules can match a model or group on either side: model-to-model, model-to-group, group-to-model, or group-to-group. A group-to-group rule can replace many individual model rules. To maintain rules for a prime group, open **Attachment validity rules** from the Action Pane on **Fleet item group codes**. You can also maintain the full list at **Rental management (Preview)** > **Setup** > **Validity rules and suggestions** > **Attachment validity rules**.

> [!IMPORTANT]
> Model and group rules are additive. Removing an individual model rule doesn't prohibit a pairing if another applicable group rule still allows it.

To enforce the rules when you pair fleet items, select **Attachment validation** in the attachment builder. That check box takes its default from **Default attachment validation** on the **Rental parameters** page. Learn more about pairing fleet items and using suggestions in [Manage attachments and bulk fleet items](manage-rental-attachments.md).

### Configure fleet item movement checklist items

Model-specific checklists give operations staff consistent inspection instructions when they ship or receive fleet items. You can require completion, photographic evidence, or both. Typical checklist items include safety equipment verification, fluid level checks, tire and track inspection, and damage documentation.

The system copies these items to fleet item movements when you schedule them. Checklist generation requires **Use checklist for shipping**, **Use checklist for receiving**, or both on the **Fleet item movement** tab of **Rental parameters**. The movement's direction must also have a movement status configured for the corresponding *Ship* or *Receive* action. Learn more in [Configure rental parameters](configure-rental-parameters.md).

To prepare the inspection items for a model before you schedule fleet item movements, follow these steps:

1. Go to **Rental management (Preview)** > **Setup** > **Fleet items** > **Fleet item models**.
1. Select the model that you want to configure.
1. On the Action Pane, select **Checklist items**.
1. Create, edit, or delete records as needed by using the actions on the Action Pane.
1. For each checklist item, make the following settings:
    - **Checklist item** – Enter a short name for the check, such as *Hydraulic fluid level* or *Photograph existing damage*. The name and action together identify an item within the model's checklist.
    - **Description** – Enter instructions that explain what the inspector must check or record. This text appears with the checklist item during inspection.
    - **Action** – Select *Ship* for checks before shipping, *Receive* for checks when receiving, or *All* for both. When both actions are enabled for a movement, *All* creates a separate checklist entry for each action.
    - **Mandatory** – Set to *Yes* to block posting of the corresponding ship or receive action until the inspector marks this item as **Checked**. Set to *No* for an optional check.
    - **Photo mandatory** – Set to *Yes* to require at least one JPG, JPEG, PNG, or HEIC image before the inspector can mark the item as **Checked**. A video doesn't satisfy this requirement. Set to *No* to allow confirmation without a photo.

    You can't change **Checklist item** or **Action** after you save a record. To change either value, delete the record and add a replacement.

    > [!IMPORTANT]
    > To require a photo before posting, set both **Mandatory** and **Photo mandatory** to *Yes*. **Photo mandatory** alone prevents checking an item without a photo, but it doesn't require the inspector to complete an optional item.

1. Save your changes.

Changes to the model's checklist don't automatically rewrite checklist entries already copied to a movement. Configure the model's checklist before you schedule movements that need those checks. Learn more about completing inspections in [Ship and receive fleet items using fleet item movements](ship-receive-rental-equipment.md#complete-checklists)<!-- and [Use the Dynamics 365 Supply Chain Management mobile app](use-rental-mobile-app.md)-->.

## Set up depreciation profiles

*Depreciation profiles* control how the system calculates depreciation for rental fleet assets. Common depreciation methods include the following:

- **Revenue based** – When a rental invoice is posted, the system calculates depreciation as a configured percentage of the revenue allocated to the fleet item and automatically posts it as asset depreciation. For example, if you set the percentage to 90%, the system posts 90% of the revenue allocated to the fleet item on each invoice as depreciation.
- **Straight line** – Depreciates the asset evenly over a fixed period (configured in the depreciation profile). This method is common for attachments such as buckets and forks.
- **SMU based** – Depreciates the asset based on actual service meter usage. The system multiplies the hours recorded on the fleet item's usage history for each period by the **Depreciation rate per hour** that you configure on the asset book. Depreciation stops when the asset reaches its configured residual value.

You configure depreciation profiles in the standard fixed asset setup. When a fleet item is transferred to a fleet type whose **Value tracking method** is *Fixed asset*, the system automatically creates the fixed asset. It assigns the fixed asset group and book specified on the **Posting configuration for fleet types** page for the target fleet type.

Learn more about how ledger accounts are determined, how revenue-based and SMU-based depreciation work, the full list of standard methods, and other financial aspects in [Understand rental management financial integration](understand-rental-financial-integration.md).

## Configure miscellaneous charge exemptions

You can exempt specific customers from charges for specific miscellaneous line items on rental contracts. This exemption is common when a customer negotiates that certain charges, such as environmental fees, don't apply to their contracts.

To configure exemptions, go to **Rental management (Preview)** > **Setup** > **Miscellaneous charge exemptions**. You can also maintain exemptions from a rental template. Learn more in [Configure miscellaneous charge exemptions](set-up-rental-templates.md#configure-miscellaneous-charge-exemptions).

## Configure notice to owner (NTO) tracking

In certain jurisdictions, particularly some US states, rental companies must notify the property owner when a fleet item is delivered to a job site. This notification is required to preserve lien rights in case of non-payment.

There's nothing to configure on the **Notice to owner** page itself. It's a register that the system fills in for rental contracts. Open it from **Rental management (Preview)** > **Setup** > **Notice to owner**. The system fills in the ship date and start date when you ship the first fleet item on the contract to the job site. You manually record the filing number, filing date, and filing status on each row. The feature doesn't calculate deadlines and doesn't raise alerts.

You configure the two exemptions that keep a row from being created:

- **Notice to owner exempt** on the customer record.
- **Notice to owner exempt** on the fleet item model.

## Related information

- [Configure rental parameters](configure-rental-parameters.md)
- [Set up rental templates](set-up-rental-templates.md)
- [Configure inventory and location settings for rental management](configure-inventory-location-settings.md)
- [Manage fleet item master data](manage-equipment-master-data.md)
- [Set up rental rates and discounts](set-up-rental-rates-discounts.md)
- [Understand rental management financial integration](understand-rental-financial-integration.md)
