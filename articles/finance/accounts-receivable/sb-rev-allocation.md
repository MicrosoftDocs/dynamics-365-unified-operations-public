---
# required metadata

title: Revenue allocation 
description: This topic explains how to use revenue allocation in Subscription billing.
author: JodiChristiansen
ms.date: 11/04/2021
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

# Revenue allocation

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule line] > [select Revenue allocation]

Modules > Subscription billing > Recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule] > [select Revenue allocation]

This topic describes how to enter the revenue allocation parameters for a billing schedule. The revenue allocation can be set up and only edited when the billing schedule is created. When viewing this page for an active or terminated billing schedule, all values are read-only. 


## Specify revenue allocation on a billing schedule

To specify the revenue allocation for a billing schedule, follow these steps: 
1. Select a billing schedule or a billing schedule line from **All/Active Billing Schedules** list.
2. Select **Revenue allocation** from the Revenue allocation tab at the top of the page. 
3. Select the **Multiple element arrangement type**. 
4. Specify the **Multiple element arrangement number** and the **Deferred contract revenue account**. If the **Multiple element arrangement type** is **Single**, the same **Multiple element arrangement number** and **Deferred contract revenue account** applies to each line. If the **Multiple element arrangement type** is **Multiple**, you can apply a different **Multiple element arrangement number** and **Deferred contract revenue account** to each line. The multiple element arrangement number can only be assigned to two or more items. In other words, a single line cannot have its own multiple element arrangement number.
5. Select **Save**. 

### Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**Multiple element arrangement type**|The multiple element arrangement (MEA) type for the transaction: <br />- **Multiple**:  Select this type when some line items   on the transaction are part of the multiple element arrangement, or if more than one arrangement exists.<br />- **None**: Select this type for a standard transaction without any revenue allocation.<br />- **Single**: Select this type when all items on the transaction are part of a single multiple element arrangement. |
|**Multiple element arrangement number**|Displays the multiple element arrangement number for a line. Available when **Multiple element arrangement type** is **Multiple**. <br />When this value is empty, and you assign a multiple element arrangement number, the **Standalone selling price origin** and **Standalone selling price** are automatically updated based on the values from the **Item standalone selling price** form. Only the multiple element arrangement numbers that are assigned to other lines in the sales order are available. This field is read-only when the line has been billed. |
|**Deferred contract revenue account**|Specify the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created. Available when Recurring contract billing is installed and used. |
|**Lines**|
|**Variant number**|Displays the value from the sales order.|
|**Item number**|Displays the value from the sales order.|
|**Billing frequency**|Displays the frequency for the revenue allocation: **Daily**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**. |
|**Quantity**|Displays the value from the sales order.|
|**Contract value**|Displays the contract value. |
|**Multiple element arrangement number**|Displays the multiple element arrangement number for a line. Available when **Multiple element arrangement type** is **Multiple**. When this value is empty, and you assign a multiple element arrangement number, the **Standalone selling price origin** and **Standalone selling price** are automatically updated based on the values from the **Item standalone selling price** page. Only the multiple element arrangement numbers that are assigned to other lines in the sales order are available. If these values are not set up for the item, the values are from the **Multiple element revenue allocation parameters** page. | 
|**Standalone selling price origin**|Displays the standalone selling price origin for the line.<br />- **Amount**: The standalone selling price is the amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed.<br />- **Base sales price**: The standalone selling price is the same value as the base sales price of the item. <br />- **Invoice price**: The standalone selling price is the same value as the invoice price of the item. <br />- **Percent of item**: The standalone selling price is set by a percentage value and is calculated based on the price of the item.  When you select this option, specify the default percent. <br />- **Allocate residual amount**: The origin of the standalone selling price is calculated as follows: Total contract value of parent item - Total standalone selling price of child items.  <br />If the calculated amount is a negative value, the amount is set to zero (0).   <br />Where: <br />**Note:** This option can be selected by only one child item in the revenue split. <br />**Total contract value of parent item** is the net or billed amount<br />**Total standalone selling price of child items** is the sum of the extended or contract standalone selling price of all child items, except for the child item that uses this standalone selling price origin. <br />**None**: The origin of the standalone selling price is based on the child items. This option applies to items that are defined as a parent item in a revenue split template. When **Revenue split** is selected, this option is automatically selected and cannot be changed. <br />**Percent of parent invoice price**: The origin of the standalone selling price is a percent of the invoice price of the parent item. You can change the default value.  Available only for child items in a revenue split template. <br />**Percent of parent standard price**: The origin of the standalone selling price is a percent of the standard price of the parent item. You can change the default value. Available only for child items in a revenue split template. Default option for child items. <br />When the option for a child item is changed from percent of parent standard price to invoice price (or vice versa), the calculated values are also updated. |
|**Standalone selling price**|Displays the standalone selling price for the line in the transaction currency. <br />If it is **Amount**, this value is manually entered. Otherwise, it is automatically calculated. |
|**Contract Standalone selling price**|Displays the contract standalone selling price. Read-only.|
|**Remaining contract revenue**|Displays the remaining revenue amount for the contract. This amount is the sum of all lines for which invoices have not yet been created. |
|**Total contract revenue**|Displays the total contract revenue amount for the line. This amount is the sum of all lines regardless of whether the invoice has been created or not. |
|**Deferred contract revenue account**|Specify the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created.<br /> Available when Recurring contract billing is enabled and used. <br />The default value is from the header, but you can change the value for the line. |
|**Error**|Displays any errors associated with the revenue allocation. |

## Revenue allocation on a sales order

To use the revenue allocation functionality on a sales order do the following:
1. On the **All sales orders** page, create a sales order with items. 
1. In the **Invoice** tab, select **Revenue allocation** under  **Revenue allocation**. 
1. Select the **Multiple element arrangement type** and **Multiple element arrangement number**.   
If the **Multiple element arrangement type** is **Multiple**, select the lines you want and click **Apply to selected**. 
1. Select **Save**.
1. Save the invoice and process it when you are ready. 

If you use Revenue and expense deferrals, the deferral schedule is automatically created. The deferral schedule can be viewed in **All deferral schedules**.

