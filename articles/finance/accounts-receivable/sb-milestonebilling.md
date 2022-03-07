---
# required metadata

title: Milestone templates
description: This topic explains how to define templates for the milestone billing functionality in Subscription billing. You can define the allocation percentages or amounts for each line within the milestone template.
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
ms.reviewer: roschlom
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

Modules > Subscription billing > Recurring contract billing > Setup > Milestone templates

This topic explains how to define templates for the milestone billing functionality in Subscription billing. You can define the allocation percentages or amounts for each line within the milestone template. You can then assign the milestone template to billing schedule items that use the milestone billing functionality. 

## Add Template

To add a milestone template, complete the following steps.

1. Click **New**. 
2. Specify a unique **Milestone template** identifier and a **Description**. 
3. Select the **Allocation method**. 
4. Optionally, specify the **Total amount** for the template. 
5. To add a line, select **Add**, and select the  **Item number**. 
   - If **Allocation method** is **Percentage**,  specify the allocation **Percentage**.   
      When you specify percentages, the sum **Total percentage** must be equal to 100. 
   - If **Allocation method** is **Variable Amount**, specify the **Amount** for each line. 
   - If **Allocation method** is **Equal Amount**, you do not need to specify an amount. The lines are automatically updated with the correct percentage and amount based on the  number of items added to the template. 
6. Repeat the previous step for each line you add. 
7. Select **Save**.

## Delete Template

To delete a milestone template, follow these steps: 
1. Select one or more lines that you want to delete, and select **Delete**. 
2. When you are asked to confirm the action, select **Yes**.

## Edit Template

To edit a milestone template, follow these steps: 
1. On the left of the page, select the record that you want to edit. 
2. Make the necessary changes, and click **Save**. 



## Fields

This page contains the following fields: 

| Field| Description|
| :------------- |:-------------| 
| **Milestone template**|Type a unique identifier for the milestone template. | 
| **Description**| Type a description for the milestone template. |  
| **Allocation method**|Select the allocation method: <br />- **Percentage of completion**: A cumulative completion value for each line. <br />- **Percentage**: A percentage amount can be specified for the allocation. The sum of all percentages must equal 100. <br />- **Variable amount**: An amount can be specified for the allocation. The allocation amount is specified at the transaction level. <br />- **Equal amount**: The allocation percentages are automatically calculated and equally split among the items within the template. |    
| **Total amount**| Specify the milestone amount for the template. | 
| **Lines**| |  
| **Item number**| Select the item number for the milestone template. |    
| **Description**|Displays the description of the item. You can change the description if needed.  | 
| **Percentage**|Displays the allocation percentage for the line: <br />- When **Allocation method** is **Percentage**, specify the percentage.<br />- When **Allocation method** is **Equal amount**, the percentage is automatically divided into equal percentages based on the number of items in the template. <br />The sum of all the percentages must equal 100%.<br />If the **Total amount** in the header is specified, changing the percentage updates the **Amount** for the line. The reverse is also true, changing the **Amount** updates the percentage.  |  
| **Amount**| Displays the allocation amount for the line: <br />- When **Allocation method** is **Variable amount**, specify the amount for the line. <br />- When **Allocation method** is **Equal amount**, the amount is automatically divided into equal amounts based on the number of items in the template and the **Total amount** specified in the header.<br />The sum of all the amounts must equal the **Total amount** specified in the header. <br />If the **Total amount** in the header is specified, changing the amount updates the **Percentage** for the line. The reverse is also true, changing the **Percentage** updates the amount. |    
| **Totals**| | 
| **Total percentage**|Displays the sum total of the percentage. The sum of all percentages must equal 100.  | 
| **Total amount**|Displays the sum total of the **Amount** for all lines. This sum must  equal to the **Total amount** specified in the header. |  
| **Remaining amount**| Displays the  remaining amount, which is calculated as the **Total amount** from the header minus the sum total of the **Amount** for all lines.|  
