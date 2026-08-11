---
title: Create billing schedules
description: Learn about how to create, delete, and edit billing schedules, including step-by-step processes for creating billing schedules and removing line items.
author: twheeloc
ms.author: twheeloc
ms.topic: how-to
ms.date: 08/05/2026
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2021-11-05
ms.search.form:  
ms.dyn365.ops.version: 10.0.24
---

# Create billing schedules

[!include [banner](../includes/banner.md)]

On the **Billing schedule** page, you can create, delete, or edit billing schedules. You can also review the list of billing schedules. When you create a billing schedule, the billing group that you associate with the schedule determines the default values. Set up additional information on the **Recurring contract billing parameters** page.

## Create a billing schedule

To create a billing schedule, follow these steps:

1. On the **Billing schedule** page, select **New**.
1. In the **Create billing schedule** dialog box, in the **Billing schedule group** field, select a billing schedule group.
1. In the **Customer account** field, select a customer account.
1. In the **Start date** field, select the start date. In the **Number of periods** field, enter the number of periods. The **End date** field updates based on the number of periods that you enter. If you update the **Billing end date** field, the **Number of periods** field updates to **0**.
1. Select **OK**.
1. On the **Billing schedule** page, in the **General** tab, in the **Description** field, enter a description of the billing schedule.
1. In the **Milestone template** field, select a milestone template for **Milestone billing**.

Fields such as **Invoice account** and **Currency code** update with information from the customer.

The **Billing frequency** and **Billing interval** fields automatically set, based on the selected billing schedule group.

1. To create separate invoices, set the **Invoice separately** option to **Yes**.
1. To automatically renew a billing schedule after the final billing period, set the **Renew Automatically** option to **Yes**, and then set the **Lines to add per renewal** field.

The **Parameters** fields are automatically set, based on the values on the **Recurring contract billing parameters** page.

 1. To prorate the amount of a billing schedule, set the **Prorate partial periods** option to **Yes**.
 1. To align the billing schedule detail lines with the end of a month, set the **Align to month** option to **Yes**.
 1. In the **Contract start date** and **Contract end date** fields, enter the start and end dates of the contract. These dates are for information only.

The **Payment** field shows the customer payment information from the customer. When a line item is on hold or terminated, you can't change the payment information.

> [!NOTE]
> When you consolidate invoices by item, the value of the **Payment terms**, **Method**, and **Billing schedule** fields must match. Otherwise, you can't consolidate the invoices.

 1. On the **Address** tab, review and update the **Delivery address** and **Bill to address** fields.
 1. On the **Contact information** tab, associate an end user account with the billing schedule.
 1. In the **Contact info** fields, enter a contact, email address, and internet address.
 1. To track partner commission information, set the **Partner account** and **Partner commission rate** fields. These fields are for information only.
 1. On the **Total** tab, view the various totals that are calculated for the billing schedule.
 1. On the **Hold** tab, view audit information about when the billing schedule was put on hold and when the hold was removed.
 1. On the **Termination** tab, view a history of the terminations that were applied to or removed from the billing schedule.
 1. Select **Save**.
 1. On the **Billing schedule lines** FastTab, select **Add line**.
1. In the **Item number** field, select the item number. If the item that you add is a parent item in a revenue split, the lines automatically update with the child items. You can edit only the parent item in a revenue split. All child items are then updated accordingly.
1. In the **Item type** field, select the item type.
1. Update the start and end dates.
1. Before you create the invoices, you can change the billing frequency by updating the **Billing frequency** field. After you create the first invoice for the billing schedule, you can't change the billing frequency.
1. In the **Unit** field, select the unit of measure for the item.
1. In the **Pricing method** field, select the pricing method for the item.

The **Unit price** field automatically sets from inventory. However, you can update it if you change the pricing method to **Flat**.

## Remove a line item

To remove an item from a billing schedule, follow these steps:

1. On the **Billing schedule** page, in the **Schedule number** field, select the number of the billing schedule to edit.
1. On the **Billing schedule lines** FastTab, select the line to delete, and then select **Remove**.
1. Select **Save**.

## Generate a quotation from a billing schedule

To generate a quotation document from a billing schedule, follow these steps:

1. On the **Billing schedule** page, select the number of the billing schedule to edit.
1. On the **Billing schedule header** Action pane, select **Generate quotation**.
1. Fill in options on the **Sales quotation** page, such as **From date** and **To date**.
1. Select **Create**.

The rest of this article describes the actions and details that are available for lines on the **Billing schedule lines** FastTab.

## Billing schedule line actions

Use the buttons on the **Billing schedule lines** FastTab to apply actions to individual lines.

| Button | Description |
| -------- | ------------- |
| Add line | Add a line to the billing schedule. |
| Add from items list | Add multiple items to a billing schedule by selecting them in a list. |
| Remove | <p>Remove the selected line from the billing schedule.</p><p>For items that are part of a revenue split, you can remove only the parent item. All associated child items are then automatically removed.</p> |
| View billing detail | View the billing details. |
| Terminate | <p>Terminate the selected lines. This button is available only when the selected lines have a status of **Active**.</p><p>For items that are part of a revenue split, you can terminate only the parent item.</p> |
| Remove termination | <p>Remove the termination from the selected lines. This button is available only when the selected lines have a status of **Terminated**.</p><p>For items that are part of a revenue split, you can remove the termination only from the parent item.</p> |
| Place hold | <p>Select the details for putting the selected line on hold.</p><p>For items that are part of a revenue split, you can put only the parent item on hold.</p> |
| Remove hold | <p>Remove the hold from the selected line.</p><p>For items that are part of a revenue split, you can remove the hold only from the parent item.</p> |
| Escalation and discount | This button isn't available for items that are part of a revenue split, except parent items where the revenue split uses the **Zero amount** allocation method. |
| Deferrals | <p>Enter deferral options for the selected line.</p><p>This button isn't available for parent items in a revenue split.</p> |
| Milestone allocation | <p>Review and update the milestone allocation information for the selected line.</p><p>This button is available only when the billing schedule line item is a milestone item.</p> |
| Support and renewal | <p>Review and update the support and renewal information for the selected line.</p><p>This button is available only when the billing schedule line item is a support or renewal item.</p> |
| Display dimensions | Show or hide the dimension columns that appear in the **Billing schedule lines** grid. |
| Calculate unit price | <p>Calculate the unit price of the item, so that the customer can pay the contract amount in installments (for example, daily, monthly, quarterly, semiannually, or annually). You can select the contract price and price frequency.</p><p>You can view an audit trail of the changes: the old contract price and frequency, the new contract price and frequency, the user who made the change, and the date and time of the change.</p> |
| Alignment date | <p>Specify the alignment date for renewal items.</p><p>If you select an item group in the **Item group** field, all items use the alignment date of the first item in the item group in the billing schedule. If the **Item group** field is blank, you can specify an alignment date to use for all items.</p><p>This button is available only when the **Billing frequency** field is set to **Annual**.</p> |
| Unbilled revenue | <p>Set the item to use the unbilled revenue feature. You can then specify the unbilled revenue and unbilled discount accounts for the item.</p><p>This button is available only for items where the **Item type** field is set to **Standard**. It isn't available for existing billing schedules or for billing schedule lines where the invoice has already been created.</p> |
| Add revenue split child | <p>Select a child item to add to the sales order.</p><p>This button is available only for parent items in a revenue split.</p> |
| Advanced pricing options | Edit the pricing options for an item. |

## Billing schedule line details

When you select a line in the **Billing schedule lines** FastTab, you can view specific details for that line. The details appear in different tabs.

### General tab

The **General** tab provides the following information.

| Field or section | Description |
| ------------------ | ------------- |
| Usage | <p>This section provides information about usage items. It contains the following fields:</p><ul><li>**Usage identifier** – The identifier of the meter or usage item.</li><li>**Reading option** – The usage reading option: **Reading** or **Consumption**.</li><li>**Estimated consumption** – Specify the estimated consumption for a usage item that has periods where the invoice isn't created. On the **Billing detail** page, you can review the billing detail lines for the estimated consumption.</li></ul> |
| External references\* | This section contains the **External** and **Line number** fields, where you can specify external reference information. |
| Milestone | <p>This section provides information about milestone items. It contains the **Estimated completion date** field, which shows the item completion date.</p> |
| Text | A comment for the line. The text is translated to the default language of the customer or legal entity. |
| Item group | The item group for the line item. |
| Alignment date | The alignment date for the billing schedule. |

\* When you consolidate invoices by item on the **Generate invoice** page, the **External reference** fields must match. If even one character is different, the items aren't consolidated on the invoice. No validation checks are done on either field in the **External reference** section, and the value in the **Line number** field must be a positive integer.

### Address tab

The **Address** tab provides the following information.

| Field | Description |
|-------|-------------|
| Delivery address | <p>Select the delivery address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab.</p><p>When you change the address, you can select the following address options:</p><ul><li>**Addresses** – Select an address for the current customer.</li><li>**In use** – Select an address that is currently used for the current customer.</li><li>**Other address** – Select an address for any customer record.</li></ul><p>For items that use revenue splitting, you can only edit the address for the parent item. The address for the child items matches the address for the parent and can't be edited separately.</p> |
| Bill to address | <p>Select the bill-to address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab. You can change the address as you require, based on the purpose of the available addresses:</p><ul><li>If none of the addresses have a purpose of **Invoice**, the default bill-to address is the primary address for the customer, regardless of the purpose.</li><li>If one or more of the addresses have a purpose of **Invoice**, the default bill-to address is the address that you most recently entered.</li><li>If one or more of the addresses have a purpose of **Invoice**, and one of the invoice addresses is set as the primary address, the default bill-to address is the address that has a purpose of **Invoice** and is set as the primary address.</li><li>For items that use revenue splitting, you can only edit the address for the parent item. The address for the child items matches the address for the parent and can't be edited separately.</li></ul> |

### Product tab

The **Product** tab provides the following information.

| Field or section | Description |
|------------------|-------------|
| Storage dimensions | <p>This section shows the storage information for the item. It contains the **Serial number** field, which shows the serial number of the item.</p><p>The serial number comes from the initial sales order during the support and renewal process. For items that use revenue splitting, the serial number of the parent item is copied to all child items. The serial number is copied when you set the **Copy serial number** option to **Yes** on the **Recurring contract billing parameters** page.</p> |
| Product dimensions | The product details for the item. The values automatically update based on the **Variant number** value that you select for the billing schedule line. |

### Account tab

The **Account** tab provides the following information.

| Field | Description |
|-------|-------------|
| Main account | The main account that you create on the sales line. The default value comes from the sales order. This field can be blank. |
| Item financial dimensions | <p>The default financial dimension values, based on the customer and item record.</p><p>For items that use revenue splitting, the child items use the financial dimension values of the customer and item records, as described earlier. If you need to update the financial dimension values of child items, you can import the data entity.</p> |

### Renewals tab

The **Renewals** tab shows the following information.

| Field | Description |
|-------|-------------|
| Renew automatically | <p>A value that indicates whether the billing schedule line is automatically renewed for the next billing period:</p><ul><li>**Yes** – The billing schedule line is automatically renewed for the next billing period when you create an invoice.</li><li>**No** – The billing schedule line isn't automatically renewed. You must manually renew the billing schedule.</li></ul> |
| Lines to add per renewal | The number of lines to add to a billing schedule renewal. |

The **Renewals** tab also provides the following buttons.

| Button | Description |
| -------- | ------------- |
| Unbilled revenue journal entry audit | View all changes for items that use the unbilled revenue feature. |
| Add renewal term | Add a renewal term for the item. The start date of the new renewal term is the next date after the end date of the previous term. You can update the **Renewal end date**, **Deferral start date**, **Deferral end date**, **Item quantity**, and **Unit price** fields. |
| Modify renewal term | <p>Modify a renewal term. For the initial term, you can change the deferral start and end dates before the initial journal entry is created. For subsequent terms, the start date can't be changed. It's always the next date after the end of the previous term.</p><p>If a renewal term exists after the term that you're modifying, you can't change the dates. In this case, you can only update the **Quantity** and **Unit price** fields for the renewal item.</p><p>For example, three terms exist. <ul><li>The first term can't be changed because it already started.</li><li>For the second term, you can change only the quantity and unit price.</li><li>For the third term, you can change all values except the start date. Additionally, the **Schedule from template** option lets you create a deferral schedule that is based on the template for the unbilled revenue item. When you set this option to **Yes**, select the deferral template in the **Template** field, and change the deferral start and end dates as you require. Subsequent renewal terms use the same deferral template. However, you can change the deferral template.</p></li></ul> |

### Termination tab

The **Termination** tab shows the following information.

| Field | Description |
|-------|-------------|
| Termination date | The date when the billing schedule line is terminated. The default value comes from the **Termination date** field on the header. You can change the value as needed. |
| Termination type | The termination type. The default value comes from the **Termination type** field on the header. |

### Hold tab

If you use revenue and expense deferrals, the **Hold** tab shows the deferral date.

### Escalation and discount tab

The **Escalation and discount** tab provides the following information.

| Field | Description |
|-------|-------------|
| Escalation | <p>Select whether to allow escalations for the billing schedule line. When you create the billing schedule line, the system applies any escalation line from the header.</p><ul><li>**Yes** – You can apply escalations to the line. When you select this option, you can set up the escalations for the billing schedule lines on the **Escalation and discount** page.</li><li>**No** – You can't apply escalations to the line.</li></ul><p>The default setting is based on the **Billing schedule group** you select.</p> |

### Price changes tab

For lines that you change from **Standard** price to **Flat** price, the grid on the **Price changes** tab includes the following columns:

- Change date
- Changed by user
- Standard price
- Flat price
- Price update
