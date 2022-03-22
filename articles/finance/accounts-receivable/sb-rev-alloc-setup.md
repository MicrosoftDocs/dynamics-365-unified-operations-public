---
# required metadata

title: Multiple element revenue allocation parameters
description: This topicdescribes how to set up the parameters for Multiple element revenue allocation in Subscription billing.
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
# Multiple Element Revenue Allocation Parameters

Modules > Subscription billing > Multiple element revenue allocation > Setup > Multiple element revenue allocation parameters
<div>

Use this page to set up the parameters for Multiple Element Revenue Allocation. 




| Field        | Description           |
| :------------- |:-------------| 
| **Account for revenue allocation rounding differences**     | Select the account you want to use for recording any rounding adjustments to a contract revenue amount. Available when Recurring contract billing is enabled and used.       |  
| **Standalone selling price origin**	  | Determines where the standalone selling price is from. You can override this value on the **Item Standalone Selling Price** page and on the transaction. The standalone selling price is based on one of the following options: <br />* **Amount**: The standalone selling price is an amount greater than zero (0) that you set. The amount is converted between the functional and originating currencies as needed. <br />* **Base sales price**: The standalone selling price is the same value as the base sales price of the item. <br />* **Invoice price**: The standalone selling price is the same value as the invoice price of the item. <br /> * **Percent of item**: The standalone selling price is set by a percentage value and is calculated based on the price of the item.  When you select this option, specify the default percent. <br />* **Allocate residual amount**: The origin of the standalone selling price is calculated as follows: Total contract value of parent item - Total SSP of child items. <br />If the calculated amount is a negative value, the amount is set to zero (0). <br />Where: <br />- **Total Contract Value of Parent Item** is the net or billed amount <br />- **Total SSP of child items** is the sum of the extended or contract standalone selling price of all child items, except for the child item that uses this SSP origin. <br />![Note icon](../../../Resources/images/icons/iAXnote.gif)**Note:** This option can be selected by only one child item in the revenue split. <br />* **None**:   The origin of the standalone selling price is based on the child items. This option applies to items that are defined as a parent item in a revenue split template. When **Revenue split** is selected, this option is automatically selected and cannot be changed.  <br />* **Percent of parent invoice price**:  The origin of the standalone selling price is a percent of the invoice price of the parent item. You can change the default value.  Available only for child items in a revenue split template. <br />* **Percent of parent standard price**: The origin of the standalone selling price is a percent of the standard price of the parent item. You can change the default value. Available only for child items in a revenue split template. Default option for child items. When the option for a child item is changed from percent of parent standard price to invoice price (or vice versa), the calculated values are also updated.  
 |

