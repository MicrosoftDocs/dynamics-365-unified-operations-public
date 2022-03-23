---
# required metadata

title: Multiple element revenue allocation parameters
description: This topic describes how to set up the parameters for Multiple element revenue allocation in Subscription billing.
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
# Multiple element revenue allocation 

Multiple element revenue allocation allows you to set up different templates to calculate and allocate revenue across multiple items. This can help you meet ASC 606 and/or IFRS 15 compliance.

## Multiple element revenue allocation parameters

Use the **Multiple element revenue allocation parameters** page to set up the parameters for Multiple element revenue allocation. 

### Standalone selling price origin
 
**Standalone selling price origin** determines where the standalone selling price comes from. You can update this value on the **Item Standalone Selling Price** page and on the transaction. The standalone selling price is based on one of the following options:
|Field        | Description           |
| :------------- |:-------------| 
|**Amount** | The standalone selling price is an amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed. |
|**Base sales price** |The standalone selling price is the same value as the base sales price of the item.|
|**Invoice price** |The standalone selling price is the same value as the invoice price of the item.|
|**Percent of item**| The standalone selling price is set by a percentage value and is calculated based on the price of the item.  When you select this option, specify the default percent.| 
|**Allocate residual amount** |The origin of the standalone selling price is calculated as follows: Total contract value of parent item - Total Standalone selling price of child items.|

 
If the calculated amount is a negative value, the amount is set to zero (0) where: 
|Field        | Description           |
| :------------- |:-------------| 
|**Total Contract Value of Parent Item**| The net or billed amount.| 
|**Total Standalone selling price of child items**| The sum of the extended or contract standalone selling price of all child items, except for the child item that uses this Standalone selling price origin. **Note:** This option can be selected by only one child item in the revenue split. |
|**None** |The origin of the standalone selling price is based on the child items. This option applies to items that are defined as a parent item in a revenue split template. When **Revenue split** is selected, this option is automatically selected and cannot be changed. | 
|**Percent of parent invoice price** | The origin of the standalone selling price is a percent of the invoice price of the parent item. You can change the default value. Available only for child items in a revenue split template. | 
|**Percent of parent standard price** |The origin of the standalone selling price is a percent of the standard price of the parent item. You can change the default value. Available only for child items in a revenue split template. Default option for child items. When the option for a child item is changed from percent of parent standard price to invoice price (or vice versa), the calculated values are also updated.|  
 
### Account for revenue allocation rounding differences

**Account for revenue allocation rounding differences** is the account used for recording any rounding adjustments to a contract revenue amount. Available when Recurring contract billing is being used. 

##  Item Standalone Selling Price

Use the **Item standalone selling price** page to specify the origin and standalone selling price of an item. The values specified on this page are used as the default values on the **Revenue allocation** page in Multiple element revenue allocation and Recurring contract billing. 

### Specify item standalone selling price

To specify the standalone price for an item, follow these steps: 
1. Select the **Standlone selling price origin**.
   * If **Standalone selling price origin** is **Percent of item**, specify the **Percent**.
   * If **Standalone selling price origin** is **Amount**, specify the **Standalone selling price**. 
2. For each item you want to add in the **List**, select **Add**.
3. Select the **Item code** and **Item relation**. For items where the **Revenue split** check box is cleared, the item code-item relation combination that you select must be unique. 
4. If needed, change the **Standalone selling price origin**, **Standalone selling price**, or **Percent** from the default values. 
5. For each parent item you want to add in the **List**, select **Add**.
6. Select the **Item code** and **Item relation**.
7. Select the **Revenue split** check box. 
8. Select the **Item relation**. The list is updated with the parent item and all child items. 
9. If needed for the child items, change the **Standalong selling price origin**, **Percent of parent standard price**, **Percent of parent invoice price**, or **Allocate residual amount** from the default values.
10. To add several items at one time, select **Add items**.
11. Update the query to select the range of items that you want to add. 
12. Select **OK**, review the list of items that you added, and select **OK**.   

### Fields

This page contains the following fields: 

| Field        | Description           |
| :------------- |:-------------| 
| **Standalone selling price origin**     | Select the origin of the standalone selling price:  <br /> - **Amount**: The standalone selling price is amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed. <br /> - **Base sales price**: The standalone selling price is the same value as the base sales price of the item.  <br /> - **Invoice price**: The standalone selling price is the same value as the invoice price of the item.  <br /> - **Percent of item**: The standalone selling price is set by a percentage value and is calculated based on the price of the item. When you select this option, specify the default percent.     |  
| **Standalone selling price**	  | Specify the standalone selling price of the item. Available when **Standalone selling price origin** is **Amount**.       |   
| **Percent**     | Specify the percent of the standalone selling price. Available when **Standalone selling price origin** is **Percent of item**, **Percent of parent invoice price**, or **Percent of parent standard price**.       |  
| **Revenue split**     | Indicates that a line uses revenue splitting:<br /> - **Selected**: Only items that have a revenue split template set up can be selected in **Item relation**.  You can select this check box only for parent items of a revenue split template. <br /> - **Cleared**: Indicates that the item is a standard item that does not use revenue split. |
| **Relationship**	  | Displays an icon to indicate that the item is a parent or child item in a revenue split.       |   
| **Item code**     | Select the item code: **Table** or **Group**. <br />When **Revenue split** is selected, this option is set to **Table** and cannot be changed.|  
| **Item relation**	  | Select an item number. <br />When **Revenue split** is selected, only items that are parent items that have a **revenue splitting template** set up are available. When the parent item is selected, the list is automatically updated with the child items for the parent item.       |   
| **Standalone selling price origin**     | Select the origin of the standalone selling price: <br /> - **Amount**: The standalone selling price is amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed. <br /> - **Base sales price**: The standalone selling price is the same value as the base sales price of the item. <br /> - **Invoice price**: The standalone selling price is the same value as the invoice price of the item. <br /> - **Percent of item**: The standalone selling price is set by a percentage value and is calculated based on the price of the item. When you select this option, specify the default percent. <br /> - **Allocate residual amount**: The origin of the standalone selling price is calculated as follows: Total contract value of parent item - Total standalone selling price of child items. <br />If the calculated amount is a negative value, the amount is set to zero (0) where: <br /> - **Total Contract Value of Parent Item** is the net or billed amount <br /> - **Total standalone selling price of child items** is the sum of the extended or contract standalone selling price of all child items, except for the child item that uses this standalone selling price origin. <br />**Note:** This option can be selected by only one child item in the revenue split. <br /> - **None**: The origin of the standalone selling price is based on the child items. This option applies to items that are defined as a parent item in a revenue split template. When **Revenue split** is selected, this option is automatically selected and cannot be changed.  <br /> - **Percent of parent invoice price**: The origin of the standalone selling price is a percent of the invoice price of the parent item. You can change the default value. Available only for child items in a revenue split template. <br /> - **Percent of parent standard price**: The origin of the standalone selling price is a percent of the standard price of the parent item. You can change the default value. Available only for child items in a revenue split template. Default option for child items. When the option for a child item is changed from percent of parent standard price to invoice price (or vice versa), the calculated values are also updated.        |  
| **Standalone selling price**	  | Specify the standalone selling price of the item. Available when **Standalone selling price origin** is **Amount**.       |   
| **Percent**	  | Specify the percent of the standalone selling price. Available when **Standalone selling price origin** is **Percent of item**, **Percent of parent invoice price**, or **Percent of parent standard price**.       |   
| **Parent item**	  | Displays the item number for the parent item. For child items in a revenue split, displays the item number of the parent item.       |   


## MEA templates

Use the **MEA templates** page to create and edit multiple element arrangement (MEA) template ID’s. These IDs are used on the **Revenue allocation** page to group items together.

### Create Template

Set up an MEA template: 
1. Select **New**. 
1. Enter a unique **MEA template ID** and **Description**. 
1. Select the **Deferred contract revenue account**. This is the account you want to use for journal entries when a multiple element arrangement (MEA) contract invoice is created. Available when Recurring contract billing is enabled and used. 
1. Select **Save**.





