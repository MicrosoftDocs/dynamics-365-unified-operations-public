---
# required metadata

title: Create billing schedules
description: This article explains how to create, delete, and edit billing schedules.
author: JodiChristiansen
ms.date: 01/30/2023
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Create billing schedules

[!include [banner](../includes/banner.md)]

On the **Billing schedule** page, you can create, delete, or edit billing schedules. You can also review the list of billing schedules. When you create a billing schedule, the default values for it are determined by the billing group that is associated with it. Additional information is set up on the **Recurring contract billing parameters** page.

## Create a billing schedule

To create a billing schedule, follow these steps.

1. On the **Billing schedule** page, select **New**.
2. In the **Create billing schedule** dialog box, in the **Billing schedule group** field, select a billing schedule group.
3. In the **Customer account** field, select a customer account.
4. In the **Start date** field, select the start date, and then, in the **Number of periods** field, enter the number of periods. The **End date** field is updated based on the number of periods that you enter. If you update the **Billing end date** field, the **Number of periods** field is updated to **0** (zero).
5. Select **OK**.
6. On the **Billing schedule** page, in the **General** tab, in the **Description** field, enter a description of the billing schedule.
7. In the **Milestone template** field, select a milestone template for **Milestone billing**.

Fields such as **Invoice account** and **Currency code** are updated with information from the customer.

The **Billing frequency** and **Billing interval** fields are automatically set, based on the selected billing schedule group.

8. To create separate invoices, set the **Invoice separately** option to **Yes**.
9. To automatically renew a billing schedule after the final billing period, set the **Renew Automatically** option to **Yes**, and then set the **Lines to add per renewal** field.

The **Parameters** fields are automatically set, based on the values on the **Recurring contract billing parameters** page.

10. To prorate the amount of a billing schedule, set the **Prorate partial periods** option to **Yes**.
11. To align the billing schedule detail lines with the end of a month, set the **Align to month** option to **Yes**.
12. In the **Contract start date** and **Contract end date** fields, enter the start and end dates of the contract. These dates are for information only.

The **Payment** field shows the customer payment information from the customer. When a line item is on hold or terminated, the payment information can't be changed.

> [!NOTE]
> When you consolidate invoices by item, the value of the **Payment terms**, **Method**, and **Billing schedule** fields must match. Otherwise, the invoices can't be consolidated.

13. On the **Address** tab, you can review and update the **Delivery address** and **Bill to address** fields.
14. On the **Contact information** tab, you can associate an end user account with the billing schedule.
15. In the **Contact info** fields, you can enter a contact, email address, and internet address.
16. To track partner commission information, set the **Partner account** and **Partner commission rate** fields. These fields are for information only.
17. On the **Total** tab, you can view the various totals that have been calculated for the billing schedule.
18. On the **Hold** tab, you can view audit information about when the billing schedule was put on hold when the hold was removed.
19. On the **Termination** tab, you can view a history of the terminations that were applied to or removed from the billing schedule.
20. Select **Save**.
21. On the **Billing schedule lines** FastTab, select **Add line**.
22. In the **Item number** field, select the item number. If the item that is added is a parent item in a revenue split, the lines are automatically updated with the child items. You can edit only the parent item in a revenue split. All child items are then updated accordingly.
23. In the **Item type** field, select the item type.
24. Update the start and end dates.
25. Before the invoices are created, you can change the billing frequency by updating the **Billing frequency** field. After the first invoice for the billing schedule is created, the billing frequency can't be changed.
26. In the **Unit** field, select the unit of measure for the item.
27. In the **Pricing method** field, select the pricing method for the item.

The **Unit price** field is automatically set from inventory. However, you can update it if you change the pricing method to **Flat**.

## Remove a line item

To remove an item from a billing schedule, follow these steps.

1. On the **Billing schedule** page, in the **Schedule number** field, select the number of the billing schedule to edit.
2. On the **Billing schedule lines** FastTab, select the line to delete, and then select **Remove**.
3. Select **Save**.

## Generate a quotation from a billing schedule

To generate a quotation document from a billing schedule, follow these steps.

1. On the **Billing schedule** page, select the number of the billing schedule to edit.
2. On the **Billing schedule header** Action pane, select **Generate quotation**.
3. Fill in options on the **Sales quotation** page, such as **From date** and **To date**.
4. Click **Create**.

The rest of this article describes the actions and details that are available for lines on the **Billing schedule lines** FastTab.

## Billing schedule line actions

The buttons on the **Billing schedule lines** FastTab let you apply actions to individual lines.

| Button | Description |
|--------|-------------|
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

When you select a line in the **Billing schedule lines** FastTab, you can view specific details for that line. Those details are divided among different tabs.

### General tab

The following information is available on the **General** tab.

| Field or section | Description |
|------------------|-------------|
| Usage | <p>This section provides information about usage items. It contains the following fields:</p><ul><li>**Usage identifier** – The identifier of the meter or usage item.</li><li>**Reading option** – The usage reading option: **Reading** or **Consumption**.</li><li>**Estimated consumption** – Specify the estimated consumption for a usage item that has periods where the invoice hasn't been created. On the **Billing detail** page, you can review the billing detail lines for the estimated consumption.</li></ul> |
| External references\* | This section contains the **External** and **Line number** fields, where you can specify external reference information. |
| Milestone | <p>This section provides information about milestone items. It contains the **Estimated completion date** field, which shows the item completion date.</li></ul> |
| Text | A comment for the line. The text is translated to the default language of the customer or legal entity. |
| Item group | The item group for the line item. |
| Alignment date | The alignment date for the billing schedule. |

\* When you consolidate invoices by item on the **Generate invoice** page, the **External reference** fields must match. If even one character is different, the items won't be consolidated on the invoice. No validation checks are done on either field in the **External reference** section, and the value in the **Line number** field must be a positive integer.

### Address tab

The following information is available on the **Address** tab.

| Field | Description |
|-------|-------------|
| Delivery address | <p>Select the delivery address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab.</p><p>When you change the address, you can select the following address options:</p><ul><li>**Addresses** – Select an address for the current customer.</li><li>**In use** – Select an address that is currently used for the current customer.</li><li>**Other address** – Select an address for any customer record.</li></ul><p>For items that use revenue splitting, only the address for the parent item can be edited. The address for the child items matches the address for the parent and can't be edited separately.</p> |
| Bill to address | <p>Select the bill-to address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab. You can change the address as you require, based on the purpose of the available addresses:</p><ul><li>If none of the addresses have a purpose of **Invoice**, the default bill-to address is the primary address for the customer, regardless of the purpose.</li><li>If one or more of the addresses have a purpose of **Invoice**, the default bill-to address is the address that was most recently entered.</li><li>If one or more of the addresses have a purpose of **Invoice**, and one of the invoice addresses is set as the primary address, the default bill-to address is the address that has a purpose of **Invoice** and is set as the primary address.</li><li>For items that use revenue splitting, only the address for the parent item can be edited. The address for the child items matches the address for the parent and can't be edited separately.</li></ul> |

### Product tab

The following information is available on the **Product** tab.

| Field or section | Description |
|------------------|-------------|
| Storage dimensions | <p>This section shows the storage information for the item. It contains the **Serial number** field, which shows the serial number of the item.</p><p>The serial number is copied from the initial sales order during the support and renewal process. For items that use revenue splitting, the serial number of the parent item is copied to all child items. The serial number is copied when the **Copy serial number** option is set to **Yes** on the **Recurring contract billing parameters** page.</li></ul> |
| Product dimensions | The product details for the item and the values are automatically updated, based on the **Variant number** value that is selected for the billing schedule line. |

### Account tab

The following information is available on the **Account** tab.

| Field | Description |
|-------|-------------|
| Main account | The main account that is created on the sales line. The default value is from the sales order. This field can be blank. |
| Item financial dimensions | <p>The default financial dimension values, based on the customer and item record.</p><p>For items that use revenue splitting, the child items use the financial dimension values of the customer and item records, as described earlier. If you must update the financial dimension values of child items, you can import the data entity.</p> |

### Renewals tab

The following information is available on the **Renewals** tab.

| Field | Description |
|-------|-------------|
| Renew automatically | <p>A value that indicates whether the billing schedule line is automatically renewed for the next billing period:</p><ul><li>**Yes** – The billing schedule line is automatically renewed for the next billing period when you create an invoice.</li><li>**No** – The billing schedule line isn't automatically renewed. You must manually renew the billing schedule.</li></ul> |
| Lines to add per renewal | The number of lines to add to a billing schedule renewal. |

Additionally, the following buttons are available on the **Renewals** tab.

| Button | Description |
|--------|-------------|
| Unbilled revenue journal entry audit | View all changes for items that use the unbilled revenue feature. |
| Add renewal term | Add a renewal term for the item. The start date of the new renewal term is the next date after the end date of the previous term. The **Renewal end date**, **Deferral start date**, **Deferral end date**, **Item quantity**, and **Unit price** fields can be updated. |
| Modify renewal term | <p>Modify a renewal term. For the initial term, you can change the deferral start and end dates before the initial journal entry is created. For subsequent terms, the start date can't be changed. It's always the next date after the end of the previous term.</p><p>If a renewal term exists after the term that you're modifying, the dates of the term can't be changed. In this case, only the **Quantity** and **Unit price** fields for the renewal item can be updated.</p><p>For example, three terms exist. <ul><li>The first term can't be changed because it has already started.</li><li>For the second term, only the quantity and unit price can be changed.</li><li>For the third term, all values except the start date can be changed. Additionally, the **Schedule from template** option lets you create a deferral schedule that is based on the template for the unbilled revenue item. When this option is set to **Yes**, select the deferral template in the **Template** field, and change the deferral start and end dates as you require. Subsequent renewal terms use the same deferral template. However, the deferral template can be changed.</p></li></ul> |

### Termination tab

The following information is available on the **Termination** tab.

| Field | Description |
|-------|-------------|
| Termination date | The date when the billing schedule line is terminated. The default value is from the **Termination date** field on the header. You can change the value as you require. |
| Termination type | The termination type. The default value is from the **Termination type** field on the header. |

### Hold tab

If revenue and expense deferrals are used, the **Hold** tab shows the deferral date.

### Escalation and discount tab

The following information is available on the **Escalation and discount** tab.

| Field | Description |
|-------|-------------|
| Escalation | <p>Select whether escalations are allowed for the billing schedule line. Any escalation line from the header is applied when the billing schedule line is created.</p><ul><li>**Yes** – Escalations can be applied to the line. When this option is selected, you can set up the escalations for the billing schedule lines on the **Escalation and discount** page.</li><li>**No** – Escalations can't be applied to the line.</li></ul><p>The default setting is based on the **Billing schedule group** selected.</p> |

### Price changes tab

For lines that are changed from **Standard** price to **Flat** price, the grid on **Price changes** tab includes the following columns:

- Change date
- Changed by user
- Standard price
- Flat price
- Price update
