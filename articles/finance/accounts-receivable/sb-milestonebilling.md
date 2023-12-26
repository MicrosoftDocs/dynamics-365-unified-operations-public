---
# required metadata

title: Milestone templates
description: This article explains how to set up the milestone billing functionality in Subscription billing. 
author: JodiChristiansen
ms.date: 01/28/2023
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

# Milestone billing

[!include [banner](../includes/banner.md)]

This article explains how to define templates for the milestone billing functionality in Subscription billing. For each line in the milestone template, you can define the allocation percentage or amount. You can then assign the milestone template to billing schedule items that use the milestone billing functionality.

## Add a template

To add a milestone template, follow these steps.

1. Go to **Subscription billing \> Recurring contract billing \> Setup \> Milestone templates**.
2. Select **New**.
3. In the **Milestone template** field, enter a unique identifier for the new template.
4. In the **Description** field, enter a description.
5. In the **Allocation method** field, select an allocation method.
6. Optional: In the **Total amount** field, specify the total amount for the template.
7. To add a line, select **Add**. Then, in the **Item number** field, select the item number for the new line.
8. Follow one of these steps, depending on the value that you selected in the **Allocation method** field:

    - If you selected **Percentage** as the allocation method, in the **Percentage** field, specify the allocation percentage for each line. If you specify percentages, the sum of percentages that is shown in the **Total percentage** field must equal **100**.
    - If you selected **Variable amount** as the allocation method, in the **Amount** field, specify the amount for each line.
    - If you selected **Equal amount** as the allocation method, you don't have to specify an amount. Each line will be updated with the correct percentage and amount, based on the number of items that are added to the template.

9. Select **Save**.

## Delete a template

To delete a milestone template, follow these steps.

1. Select one or more lines to delete, and then select **Delete**.
2. When you're prompted to confirm the action, select **Yes**.

## Milestone template fields

The **Milestone template** page contains the following fields.

| Field | Description |
|-------|-------------| 
| Milestone template | The unique identifier of the milestone template. |
| Description | The description of the milestone template. |
| Allocation method | <p>Select the allocation method:</p><ul><li>**Percentage of completion** – A cumulative completion value is used for each line.</li><li>**Percentage** – A percentage amount can be specified for the allocation. The sum of all percentages must equal 100.</li><li>**Variable amount** – An amount can be specified for the allocation. The allocation amount is specified at the transaction level.</li><li>**Equal amount** – The allocation percentages are automatically calculated and equally split among the items in the template.</li></ul> |
| Total amount | Specify the milestone amount for the template. |
| **Lines** | |
| Item number | Select the item number for the milestone template. |
| Product name | The name of the item. |
| Percentage | <p>Enter the allocation percentage for the line:</p><ul><li>If the **Allocation method** field is set to **Percentage**, specify the percentage for the line.</li><li>If the **Allocation method** field is set to **Equal amount**, the percentage is automatically divided into equal percentages, based on the number of items in the template.</li></ul><p>The sum of all the percentages must equal 100.</p><p>If a **Total amount** value is specified on the header, and you change the **Percentage** value for the line, the **Amount** value is updated. Conversely, if you change the **Amount** value, the **Percentage** value is updated.</p> |
| Amount | <p>The allocation amount for the line:</p><ul><li>If the **Allocation method** field is set to **Variable amount**, specify the amount for the line.</li><li>If the **Allocation method** field is set to **Equal amount**, the amount is automatically divided into equal amounts, based on the number of items in the template and the **Total amount** value that is specified on the header.</li></ul><p>The sum of all the amounts must equal the **Total amount** value that is specified on the header.</p><p>If a **Total amount** value is specified on the header, and you change the **Amount** value for the line, the **Percentage** value is updated. Conversely, if you change the **Percentage** value, the **Amount** value is updated.</p> |
| **Totals** | |
| Total percentage | The sum of percentages. The sum of all percentages must equal 100. |
| Total amount | The sum of **Amount** values for all lines. This sum must equal the **Total amount** value that is specified on the header. |
| Remaining amount | The remaining amount. The value is calculated as the **Total amount** value from the header minus the sum of **Amount** values for all lines.|

## Milestone allocation

Before you start to use milestone functionality, you should complete these tasks.

1. Add one or more milestone templates.
2. Create a billing schedule group. Specify **Milestone** as the item type, and select a template.
3. On the **Item setup** page (**Subscription billing \> Recurring contract billing \> Setup \> Items**), select an item relation and a milestone template for the item setup.

After you've created the milestone templates, billing schedule groups, and items, you can create a billing schedule that uses the milestone functionality.

To set up a billing schedule that uses milestones, follow these steps.

1. From the **All/Active billing schedules** list on the **Billing schedules** page, select **New**.
2. On the **All billing schedules** page, create a new billing schedule, and specify a customer account and a start date.
3. In the **Billing schedule lines** section, select **Add line**. Then add an item number, and set the **Item type** field to **Milestone**.

    If a default milestone template is set up for the item, the milestone events are automatically added to the billing schedule lines. End dates are blank for milestone lines.

    If no milestone template is set up for the item, select **Milestone allocation**. Then, on the **Milestone allocation** page, select a milestone template, and make any required updates. Then select **Close** to return to the billing schedule, and finish creating the billing schedule.

4. To create invoices for the billing schedule, you must update the end date for each milestone event. For a single billing schedule, you can update the end date for the milestone event on the billing schedule lines. To update multiple billing schedules, select **Update completion date process**.
5. After the end date is updated, you can create the invoice. For a single billing schedule, select **Generate invoice** on the **All billing schedules** page. To create invoices for multiple billing schedules, select **Generate invoice** or **Generate invoice batch processing** under **Periodic tasks**.

## Edit milestone allocation on a billing schedule line

To edit milestone allocation on a billing schedule line, follow these steps.

1. On the **Billing schedules** page > **All or active billing schedules**, in the **Schedule number** field, select the schedule number of the billing schedule.
2. In the **Billing schedule lines** section, enter an item, specify **Milestone** as the item, and select **Milestone allocation**.
3. In the **Milestone template** field, select a milestone template.
4. Select **Process**. The milestone template lines are automatically added to the billing schedule lines.

> [!Note]
> A feature was added in Dynamics 365 Finance version 10.0.31 that allows a **Billing schedule** line with **Item type** of **Milestone** to set **Renew automatically** to **Yes**. 

## Milestone allocation fields

The **Milestone allocation** page contains the following fields.

| Field | Description |
|-------|-------------|
| Parent item | The item number of the parent. |
| Extended price | <p>The extended price of the item. The value corresponds to the **Net amount** value of the billing schedule line.</p></p>For a milestone parent item, the default value is the **Total amount** value that is specified for the milestone template. If the total amount is 0 (zero), the default value is the **Net amount** value of the billing schedule line.</p> |
| Milestone template | The milestone template ID of the line item. |
| Template description | The description of the milestone template. |
| Allocation method | The allocation method that is used for the milestone template. |
| **Lines** | The default values for all lines are based on the selected milestone template. You can change them as required. |
| Item number | The item number for the milestone allocation template. |
| Product name | The product name. |
| Percentage | <p>The allocation percentage for the line. The sum of all the percentages must equal 100.</p><p>If you change the **Percentage** value for the line, the **Net amount** value is updated. Conversely, if you change the **Net amount** value, the **Percentage** is updated.</p> |
| Net amount | <p>The allocation amount for the line. The sum of net amounts for all lines must equal the **Extended price** value that is specified on the header.</p><p>If you change the **Net amount** value for the line, the **Percentage** value is updated. Conversely, if you change the **Percentage** value, the **Net amount** value is updated.</p> |
| **Totals** | |
| Total percent | The sum of **Percentage** values for all lines. This sum must equal 100. |
| Total amount | The sum of **Net amount** values for all lines. This sum must equal the **Extended price** value that is specified on the header. |
| Remaining amount | The remaining amount. The value is calculated as the **Extended price** value from the header minus the sum of **Net amount** values for all lines. The final amount must be 0 (zero). |
