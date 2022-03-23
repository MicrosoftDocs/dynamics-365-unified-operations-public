---
# required metadata

title: Terminate schedule lines
description: This topic 
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

Modules > Advanced recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule line] > [select Revenue allocation]

Modules > Advanced recurring contract billing > Billing schedules > All or Active billing schedules > [select a billing schedule] > [select Revenue allocation]

This topic describes how to enter the revenue allocation parameters for a billing schedule. The revenue allocation can be set up and only edited when the billing schedule is created. When viewing this page for an active or terminated billing schedule, all values are read-only. 


## Specify Revenue Allocation

To specify the revenue allocation for a billing schedule, follow these steps: 
1. Select a billing schedule or a billing schedule line: 
   - From the  [All/Active Billing Schedules](BillSchedActiv.md) list, select a billing schedule
   - When you are in the [Billing Schedules](BillSched.md) page reviewing a specific billing schedule
2. Select **Revenue allocation**. 
3. Select the **MEA type**. 
4. Specify the **MEA number** and the **Deferred contract revenue account**. <br /> - If the **MEA type** is **Single**, the same **MEA number** and **Deferred contract revenue account** applies to each line. <br />   - If the **MEA type** is **Multiple**, you can apply a different **MEA number** and **Deferred contract revenue account** to each line. <br />  The MEA number can only be assigned to two or more items. In other words, a single line cannot have its own MEA number.
5. Select **Save**. 

## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**MEA type**|The multiple element arrangement (MEA) type for the transaction: <br />- **Multiple**:  Select this type when some line items   on the transaction are part of the MEA, or if more than one arrangement exists.<br />- **None**: Select this type for a standard  transaction without any revenue allocation.<br />- **Single**: Select this type when all items on the transaction are part of a single MEA. |
|**MEA number**|Displays the MEA number for a line. Available when **MEA Type** is **Multiple**. <br />When this value is empty, and you assign a MEA number, the **SSP Origin** and **Standalone Selling Price** are automatically updated based on the values from the **[Item Standalone Selling Price](../../AX_MERA/setup/ItmFairVal.md)** form. <br />Only the MEA numbers that are assigned to other lines in the sales order are available. <br />This field is read-only when the line has been billed. |
|**Deferred contract revenue account**|Specify the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created.<br /> Available when Advanced Recurring Contract Billing is installed and used. |
|**Line Grid**|
|**Item number**|Displays the value from the sales order.|
|**Frequency**|Displays the frequency for the revenue allocation: **Daily**, **Monthly**, **Quarterly**, **Semiannually**, or **Annually**. |
|**Quantity**|Displays the value from the sales order.|
|**Contract value**|Displays the contract value. |
|**MEA number**|Displays the MEA number for a line. Available when **MEA Type** is **Multiple**. <br />When this value is empty, and you assign a MEA number, the **SSP Origin** and **Standalone Selling Price** are automatically updated based on the values from the **[Item Standalone Selling Price](../../AX_MERA/setup/ItmFairVal.md)** form. <br />Only the MEA numbers that are assigned to other lines in the sales order are available. <br />If these values are not set up for the item, the values are from the <span href="../../AX_MERA/setup/Parameters.htm" class="gui">[MERA Parameters](../../AX_MERA/setup/Parameters.md)** form. | 
||Displays the standalone selling price origin for the line.<br />- **Amount**: The standalone selling price is  amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed.<br />- **Base sales price**: The standalone selling price is the same value as the base sales price of the item. <br />- **Invoice price**: The standalone selling price is the same value as the invoice price of the item. <br />- **Percent of item**: The standalone selling price is set by a percentage value and is calculated based on the price of the item.  When you select this option, specify the default percent. <br />- **Allocate residual amount**: The origin of the standalone selling price is calculated as follows: Total contract value of parent item - Total SSP of child items.  <br />If the calculated amount is a negative value, the amount is set to zero (0).   <br />Where: <br />![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:** This option can be selected by only one child item in the revenue split. <br />   - <span class="reference">Total Contract Value of Parent Item** is the net or billed amount<br />   - <span class="reference">Total SSP of child items** is the sum of the extended or contract standalone selling price of all child items, except for the child item that uses this SSP origin. <br />- **None**: The origin of the standalone selling price is based on the child items. This option applies to items that are defined as a parent item in a revenue split template. When **Revenue split** is selected, this option is automatically selected and cannot be changed. <br />- **Percent of parent invoice price**:  The origin of the standalone selling price is a percent of the invoice price of the parent item. You can change the default value.  Available only for child items in a revenue split template. <br />- **Percent of parent standard price**: The origin of the standalone selling price is a percent of the standard price of the parent item. You can change the default value. Available only for child items in a revenue split template. Default option for child items. <br />When the option for a child item is changed from percent of parent standard price to invoice price (or vice versa), the calculated values are also updated. |
|**Standalone selling price**|Displays the standalone selling price for the line in the transaction currency. <br />If is **Amount**, this value is manually entered. Otherwise, it is automatically calculated. |
|**Contract SSP**|Displays the contract standalone selling price. Read-only.|
|**Remaining contract revenue**|Displays the remaining revenue amount for the contract. This amount is the sum of all lines for which invoices have not yet been created. |
|**Total contract revenue**|Displays the total contract revenue amount for the line. This amount is the sum of all lines regardless of whether the invoice has been created or not. |
|**Deferred contract revenue account**|Specify the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created.<br /> Available when Advanced Recurring Contract Billing is installed and used. <br />The default value is from the header, but you can change the value for the line. |
|**Error**|Displays any errors associated with the revenue allocation. |
|**MEA number**|Displays the MEA number. |
|**Accrued amount**|Displays the total accrued revenue amount for the MEA number. |
|**Deferred contract revenue account**|Specify the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created.<br /> Available when Advanced Recurring Contract Billing is installed and used. <br />The default value is from the header, but you can change the value for the line. |


