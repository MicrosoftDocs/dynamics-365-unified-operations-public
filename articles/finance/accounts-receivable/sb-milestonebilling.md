---
# required metadata

title: Milestone templates
description: This topic explains tting up your system to use the milestone billing funcationality in Subscription billing. 
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

# Milestone templates

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic explains how to define templates for the milestone billing functionality in Subscription billing. You can define the allocation percentages or amounts for each line within the milestone template. You can then assign the milestone template to billing schedule items that use the milestone billing functionality. 

## Add Template

To add a milestone template:

1. Go to **Subscription billing > Recurring contract billing > Setup > Milestone templates**.
2. Click **New**. 
3. Enter a unique **Milestone template** identifier and a **Description**. 
4. Select an **Allocation method**. 
5. Optionally, specify the **Total amount** for the template. 
6. To add a line, select **Add**, and select the **Item number**. 
   - If **Allocation method** is **Percentage**, specify the allocation **Percentage**. When you specify percentages, the sum **Total percentage** must be equal to 100. 
   - If **Allocation method** is **Variable Amount**, specify the **Amount** for each line. 
   - If **Allocation method** is **Equal Amount**, you do not need to specify an amount. The lines are automatically updated with the correct percentage and amount based on the  number of items added to the template. 
6. Select **Save**.

## Delete Template

To delete a milestone template: 
1. Select one or more lines that you want to delete, and select **Delete**. 
2. When you are asked to confirm the action, select **Yes**.

## Milestone template fields

The **Milestone templates** page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
| **Milestone template**|A unique identifier for the milestone template. | 
| **Description**| A description for the milestone template. |  
| **Allocation method**|Select the allocation method: <br />- **Percentage of completion**: A cumulative completion value for each line. <br />- **Percentage**: A percentage amount can be specified for the allocation. The sum of all percentages must equal 100. <br />- **Variable amount**: An amount can be specified for the allocation. The allocation amount is specified at the transaction level. <br />- **Equal amount**: The allocation percentages are automatically calculated and equally split among the items within the template. |    
| **Total amount**| Specify the milestone amount for the template. | 
| **Lines**| |  
| **Item number**| Select the item number for the milestone template. |    
| **Product name**|Displays the name of the item. | 
| **Percentage**|Enter the allocation percentage for the line: <br />- When **Allocation method** is **Percentage**, specify the percentage.<br />- When **Allocation method** is **Equal amount**, the percentage is automatically divided into equal percentages based on the number of items in the template. <br />The sum of all the percentages must equal 100%.<br />If the **Total amount** in the header is specified, changing the percentage updates the **Amount** for the line. The reverse is also true, changing the **Amount** updates the percentage.  |  
| **Amount**| Displays the allocation amount for the line: <br />- When **Allocation method** is **Variable amount**, specify the amount for the line. <br />- When **Allocation method** is **Equal amount**, the amount is automatically divided into equal amounts based on the number of items in the template and the **Total amount** specified in the header.<br />The sum of all the amounts must equal the **Total amount** specified in the header. <br />If the **Total amount** in the header is specified, changing the amount updates the **Percentage** for the line. The reverse is also true, changing the **Percentage** updates the amount. |    
| **Totals**| | 
| **Total percentage**|Displays the sum total of the percentage. The sum of all percentages must equal 100.  | 
| **Total amount**|Displays the sum total of the **Amount** for all lines. This sum must  equal to the **Total amount** specified in the header. |  
| **Remaining amount**| Displays the  remaining amount, which is calculated as the **Total amount** from the header minus the sum total of the **Amount** for all lines.|  

---
## Milestone allocation

Before you can begin using milestone functionality, you will want to:

1. Add one or more milestone templates.
2. Create a billing schedule group, and specify the item type as milestone and select a template. This is optional. 
3. In **Item setup**, **Subscription billing > Recurring contract billing > Setup > Items**, select an **Item relation** and a milestone template for the item setup. This is optional.

After milestone templates, billing schedule groups, and items have been created, you can create a billing schedule that usees the milestone functionality. 

To set up billing schedules that use milestones: 

1. From the **All/Active billing schedules** list, select <span class="gui">New</span>. 
2. On the **All billing schedules** page, create a new billing schedule with a customer account and a start date.  
3. In the **Billing schedule lines**, select **Add line** and add Item number. Set the **Item type** to **Milestone**.  
If a default milestone template is set up for the item, the milestone events are automatically added to the billing schedule lines. End dates are blank for milestone lines.
   - If the milestone template is not setup for an item, select **Milestone allocation**. 
   - On the **Milestone allocation**, select a **Milestone template**, make any adjustments as needed, and select **Close** to return to the billing schedule. 
   - Finish creating the billing schedule. 
4. To create invoices for the billing schedule, the end date for each milestone even must be updated. <br />For a single billing schedule, you can update the end date for the milestone event on the **Billing schedule lines**. To update multiple billing schedules, use the **Update completion date process**. 
5. After the end date is updated, you can create the invoice. For a single billing schedule, use the **Generate invoice** button from the **All billing schedules** page. To create invoices for multiple billing schedules, use the **Generate invoice** or **Generate invoice batch processing** under **Periodic tasks**.


## Edit milestone allocation on billing schedule line

To edit milestone allocation for a billing schedule line: 
1. In the list of all billing schedules, click the **Schedule number** of the billing schedule.  
2. In the **Billing schedule lines** section, enter an item and set **Item type** to **Milestone**, and select **Milestone allocation**. 
3. Select a **Milestone template**. 
4. Select **Process**. 
5. The milestone template lines are automatically added to the billing schedule lines.

## Milestone allocation fields 

The **Milestone allocation** page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
|**Parent item**|Displays the item number for the parent.|
|**Extended price**|Displays the extended price of the item. This value corresponds to the **Net amount** for the billing schedule line. <br />For a milestone parent item, the default value is the **Total amount** specified for the milestone template. When the total amount is zero (0), the default value is the **Net amount** for the billing schedule line.|
|**Milestone template**|Displays the milestone template ID for the line item. |
|**Template description**|Displays the description for the milestone template. |
|**Allocation method**|Displays the allocation method used for the milestone template. |
|**Lines**|The default values for all lines are based on the selected milestone template and can be changed as needed. |
|**Item number**|Displays the item number for the item number for the milestone allocation template. |
|**Product name**|Displays the product name. |
|**Percentage**|Displays the allocation percentage for the line. The sum of all the percentages must equal 100%. <br />Changing the percentage, updates the **Net amount** for the line. The reverse is also true, changing the **Net amount** updates the percentage. |
|**Net amount**|Displays the allocation amount for the line. The sum total of the net amount for all lines must equal the **Extended price** specified in the header. <br />Changing the net amount, updates the **Percentage** for the line. The reverse is also true, changing the **Percentage** updates the net amount. |
|**Totals**| &nbsp; |
|**Total percent**|Equals the sum of the **Percentage** for all lines. This sum must equal 100. |
|**Total amount**|Displays the sum total of the **Net amount** for all lines. This sum must equal to the **Extended price** specified in the header. |
|**Remaining amount**|Displays the remaining amount, which is calculated as the **Extended price** from the header minus the sum total of the **Net amount** for all lines. The final amount must be zero (0). |

