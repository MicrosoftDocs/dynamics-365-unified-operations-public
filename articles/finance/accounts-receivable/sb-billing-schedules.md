---
# required metadata

title: Billing schedule overview
description: This topic explains how to create, delete, or edit billing schedules. 
author: JodiChristiansen
ms.date: 02/09/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: jchrist
ms.search.validFrom: 2021-11-05
ms.dyn365.ops.version: 10.0.24

---

# Billing schedule overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

On the **Billing schedule page**, you can create, delete, or edit billing schedules as well as review a list of billing schedules.
When you create a billing schedule, the default values for the billing schedule are determined by the billing group associated with the billing schedule. Additional information is set up on the **Recurring Contract Billing Parameters** page.  

## Creating a billing schedule

To create a billing schedule, follow these steps:
1. Select **New**. 
2. On the **Create billing schedule** page, select a **Billing schedule group**.  
3. Select a **Customer account**. 
4. Select the **Start date** and type the **Number of periods**. The **End date** will be updated based on the number of periods specified. If the **Billing end date** is updated the **Number of periods** changes to 0. 
5. Click **OK**. 
6. On the **General** tab, enter a **Description** for the billing schedule.
7. Select a **Milestone template** for **Milestone billing**. 
8. Fields are updated with information from the customer such as **Invoice account** and **Currency code**.  
9. The **Billing frequency** and **Billing interval** default from the **Billing schedule group**. 
10. If you want to create separate invoices, set **Invoice separately** to **Yes**.
11. To automatically renew a billing schedule after the final billing period, set **Renew Automatically** to **Yes** and specify the **Lines to add per renewal**.
12. The **Parameters** default from **Recurring contract billing parameters**. 
13. Set **Prorate partial periods** to **Yes** to prorate the amount of a billing schedule.  
14. Set **Align to month** to **Yes** to align the billing schedule detail lines to the end of a month.
15. Enter the **Contract start date** and **Contract end date**. These dates are for information only.
16. **Payment** displays the customer payment information and are from the customer. When a line item is on hold or terminated, the payment information cannot be changed.

>[Note:]
> When consolidating invoices by item, the values for payment terms, method, and schedule are considered and must match for the invoices to be consolidated. 

17. Click the **Address** tab to view and update the **Deliveray address** and the **Bill to address**. 
18. In the **Contact information** tab associate the **End user account** to a billing schedule. 
19. In the **Contact info** fields, you can enter a **Contact**, **Email**, and **Internet address**. 
20. To track partner commission information, specify the **Partner account** and **Partner commission rate**. These fields are informational.
21. Click the **Total** tab to view various totals calculated for the billing schedule. 
22. Select the **Hold** tab to view audit information of when the billing schedule was put on hold or the hold removed.
23. Select the **Termination** tab to view a history of the terminations that were applied or removed to the billing schedule.
24. Select **Save**.
25. In the **Billing schedule lines**, click **Add line**. 
26. Select the **Item number**.  If the item you add is a parent item in a revenue split, the lines are automatically updated with the child items. You can only edit the parent item in a revenue split, and all child items are updated accordingly. 
27. Select the **Item type**. 
28. Edit the start and end dates. 
29. Before the invoices are created, the **Billing frequency** can be changed. After the first invoice for the billing schedule is created, the billing frequency cannot be edited.
30. Select the **Unit** of measure for the item and the **Pricing method**. 
31. The **Unit price** defaults from inventory but can be updated if the pricing method is changed to **Flat**.


## Removing a line item

To remove an item from a billing schedule, follow these steps: 
1. In the list of all billing schedules, select the **Schedule number** of the billing schedule that you want to edit. 
2. In the FastTab, select the line you want to delete, and select **Remove**. 
3. Select **Save**. 


### Actions

>[Note:]
> The **Billing schedule lines** actions can be applied to one line at a time. 


|Action|Description|
|:-----|:-----|
|**Add line**|Adds a new line to the billing schedule. |
|**Add from items list**| Select multiple items to add to a billing schedule. 
|**Remove**|Removes the selected line from the billing schedule. <br />For items that are part of a revenue split, you can only remove the parent item, which also removes all associated child items. |
|**View billing detail**|View the billing details. |
|**Terminate**|This is only available when the selected lines have a status of **Active**. For revenue split items, you can terminate only the parent item. |
|**Remove termination**|You can remove the termination on billing schedule lines that have a status of **Terminated**. For revenue split items, you can remove the terminiation from the parent item. |
|**Place hold**|Select the details of putting a billing schedule line on hold. <br />For revenue split items, you can put the parent item on hold. |
|**Remove hold**|Allows you to remove a hold on a billing schedule line. <br />For revenue split items, you can remove the hold from the parent item. |
|**Escalation and discount**|Opens the **Escalation and discount** page.<br />Not available for items that are part of a revenue split, except for parent items where the revenue split uses the **Zero amount** allocation method. |
|**Deferrals**|You can enter the deferral options for the schedule line. <br />This button is not available for parent items in a revenue split. |
|**Milestone allocation**|You can view and update the milestone allocation information for the line.<br />This applies when the billing schedule line item is a milestone item. |
|**Support and renewal**|You can view and edit the support and renewal information for the line. <br />This is available when the billing schedule line item is a support or renewal item. |
|**Display dimensions**|You can show or hide the dimension columns that appear on the **Billing schedule lines** list. |
|**Calculate unit price**|You can select the **Contract price** and **Price frequency**. The unit price of the item is calculated so that the customer can pay the contract amount installments, such as daily, monthly, quarterly, semiannually, or annually.<br />You can view an **Audit trail** of the changes: old contract price and frequency, new contract price and frequency, user who made the change, and the date and time of the change. |
|**Alignment date**|You can specify the **Alignment date** for renewal items. <br />If you choose an **Item group**, all items use the alignment date of the first item in the item group in the billing schedule.  <br />If the **Item group** is empty, you can specify an **Alignment date** to use for all items. <br />The **Alignment date** works only when the billing frequency is annual. |
|**Unbilled revenue**|You can set the item to use the unbilled revenue feature and then specify the unbilled revenue and unbilled discount accounts for the item.  <br />This is only available for items where **Item type** is **Standard**. <br />**Unbilled revenue** is not available for existing billing schedules or for billing schedule lines in which the invoice has already been created. |
|**Add revenue split child**|You can select a child item to add to the sales order. <br />Available only for parent items of a revenue split. |
|**Advanced pricing options**|You can edit the pricing options for an item. |

## Line details

When you select a line in the **Billing Schedule Lines** FastTab, you can view specific details for the selected line. 

|Field|Description|
|:-----|:-----|
|**General tab**|
|**Usage**|Provides information for usage items: <br /> **Usage identifier**: Displays the identifier for the meter or usage item. <br /> **Reading option**: Displays the usage reading option: **Reading** or **Consumption**. <br /> **Estimated consumption**: Specify the estimated consumption for a usage item that have periods where the invoice has not been created. You can review the billing detail lines for the estimated consumption on the **Billing Detail** page. |
|**External references**\*|You can specify external reference information in the **External** and **Line number** fields. |
|**Milestone**|Provides information for milestone items:  <br />**Estimated completion date**: Displays the item completion date. |
|**Text**|Displays comment for the line. <br />This text is translated to the default language of the customer or legal entity. |
|**Item group**|Displays the item group for the line item and is not editable. |
|**Alignment date**|The alignment date for the billing schedule. |
|**Address tab**|
|**Delivery address**|Select the delivery address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab. <br />When you change the address, you can select the following address options: <br />**Addresses**: Select an address for the current customer. <br />**In use**: Select an address that is currently used for the current customer. <br />**Other address**: Select an address for any customer record. <br />For items that use revenue splitting, only the address for the parent item can be edited. The address for the child items(s) is the same as the parent and cannot be edited separately. |
|**Bill to address**|Select the bill-to address for the line item. The default delivery address is the primary delivery address from the **Address** FastTab. You can change the address as needed based on the purpose of the available addresses: <br />If none of the addresses have a purpose of **Invoice**, the default bill-to address is the primary address for the customer regardless of the purpose. <br />If one or more of the addresses have a purpose of **Invoice**, the default bill-to address is the address that was entered most recently. <br />If one or more of the addresses have a purpose of **Invoice** and one of the invoice addresses is set as the primary address, the default bill-to address is the address that has the purpose of invoice and primary. <br />For items that use revenue splitting, only the address for the parent item can be edited. The address for the child items(s) is the same as the parent and cannot be edited separately. |
|**Product tab**|
|**Storage dimensions**|Displays the storage information for the item:<br />**Serial number**: Displays the serial number for the item. The serial number is copied from the initial sales order during the support and renewal process. For items that use revenue splitting, the serial number for the parent item is copied to all child items. The serial number is copied when **Copy serial number** is **Yes** on the **Recurring contract billing parameters** page. |
|**Product dimensions**|Displays the product details for the item and the values are automatically updated based on the **Variant number** selected for the billing schedule line. |
|**Account tab**|
|**Main account**|Displays the main account that is created on the sales line. The default value is from the sales order. However, this field can be empty. |
|**Item financial dimensions**|Displays the default financial dimension values based on the customer and item record. <br />For items that use revenue splitting, the financial dimension values for child items use the financial dimension values of the customer and item records as described earlier. If needed, you can import the data entity to update the financial dimension values of child items. |
|**Renewals tab**|
|**Renew automatically**|Displays whether the billing schedule line automatically renews for the next billing period: <br />**Yes**: The billing schedule line is automatically renewed for the next billing period when you create an invoice.  <br />**No**: The billing schedule line is not automatically renewed. You must manually renew the billing schedule. |
|**Lines to add per renewal**|Displays the number of lines to add to a billing schedule renewal. |
|**Termination tab**|
|**Termination date**|Displays the date on which the billing schedule line is terminated. The default value is from the **Termination date** in the header, but you can change it. |
|**Termination type**|Displays the termination type. The default value is from the **Termination type** in the header, but you can change it. |
|**Hold tab**|Deferral date (only if Revenue and  Expense Deferrals is used)|
|**Escalation and discount tab**|
|**Escalation**|Select to allow escalations for the billing schedule line. Any escalation line from the header are rolled down when the billing schedule line is created:<br />**Yes**: Escalations can be applied to the line. <br />When this option is selected, you can set up the escalations for the billing schedule lines on the **Escalation and discount** page. <br />**No**: Escalations cannot be applied to the line. <br /> The default setting is based on the **Billing schedule group** selected, but you can change it. |
|**Price changes tab**|Displays the following columns for lines changed from standard to flat price: <br />**Change date**<br />**Changed by user**<br />**Standard price**<br />**Flat price**<br />**Price update** |

\*When consolidating invoices by item on  **Generate Invoice**, the external reference information must be exactly the same. If the information is not identical (e.g., even if one character is different), the items will not be consolidated on the invoice. 
- No validation checks are performed on either of these fields.
- The **Line number** must be a positive integer. 

#### Buttons

The **Renewals** tab has the following buttons: 

|Button|Description|
|:-----|:-----|
|**Renewals tab**|  |
|**Unbilled revenue journal entry audit**|You can view all changes for items that use the unbilled revenue feature. |
|**Add renewal term**|You can add a renewal term for the item. The start date of the new renewal term is the next date after the end date of the previous term, and it cannot be changed. You can change the renewal end date, the deferral start and end dates, the item quantity, and unit price. <br />The dialog also includes the **Calculate unit price** button. |
|**Modify renewal term**|You can modify a renewal term. For the initial term, you can change the deferral start and end dates prior to creating the initial journal entry. For subsequent terms, the start date cannot be changed and is the next date after the end of the previous term. <br />If a renewal term exists after the term you are modifying, the dates of the term cannot be changed. In this case, you can change only the quantity and unit price for the renewal item. 

For example, three terms exist. The first term cannot be changed because it has already started. For the second term, only the quantity and unit price can be changed. For the third term, all values can be changed, except the start date. Additionally, the **Schedule from template** option allows you to create a deferral schedule based on the template for the unbilled revenue item. When this option is **Yes**, select the deferral **Template** and change the deferral start and end dates as needed. Subsequent renewal terms use the same deferral template, which can be changed. |

