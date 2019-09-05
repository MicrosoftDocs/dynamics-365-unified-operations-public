---
# required metadata

title: Maintenance checklists
description: This topic describes maintenance checklists in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 08/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-15
ms.dyn365.ops.version: 10.0.5

---


# Maintenance checklists


[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

Maintenance checklists are set up on maintenance job types and used when you work on a work order. Filling out maintenance checklists is part of completing a work order. See the [Maintenance job type categories and maintenance job types, maintenance job type variants, maintenance job trades, and maintenance checklists](../setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md) section for more information on how to set up maintenance checklists on maintenance job types in the **Maintenance job type defaults** form.

When you work with maintenance checklists on a work order, you can fill out the predefined maintenance checklists that are related to maintenance job types. It is also possible to add additional maintenance checklists.

## Fill out a maintenance checklist

1. Click **Asset management** > **Common** > **Work orders** > **All work orders** or **Active work orders**.

2. Select the work order and click **Maintenance checklist**.

3. In **Work order maintenance job checklist**, you see maintenance checklists for all work order jobs. If the work order jobs have different maintenance job types, the maintenance checklists may be different on each work order job. Select a work order job to work with the related maintenance checklist. Details of a selected maintenance checklist line are shown on the **Line details** FastTab.

4. Complete all the maintenance checklist lines, one at a time, in the sequential order they are shown. A maintenance checklist line of type "Header" is used as a heading to group the maintenance checklist lines below. You are not required to fill out a header, but as for all maintenance checklist line types, it is possible to add a **Note** to the header.

5. If instructions are related to a maintenance checklist line, the **Instructions** check box is selected. Read instructions for the selected maintenance checklist line on the **Line details** FastTab > **Instructions** section.

6. The information required to complete a maintenance checklist line may vary, depending on the related maintenance checklist type. You complete a maintenance checklist line by filling out the fields on the **Line details** FastTab. For example, on a line of type "Text", you add a **Note** explaining what was the result of that checklist line. On a line of type "Measurement", you add the **Counter value** you read on the equipment, and you can also add a **Note**, if required.

- When you have completed a maintenance checklist line, select the **Checked** check box on the line to mark it as completed. If you want to discard a maintenance checklist line because it's not relevant for the work order job, select the **N/A** check box on the line. If a maintenance checklist line is marked **Mandatory**, you must mark it as either "Checked" or "N/A".  
- You can only update maintenance checklist registrations if the work order is in an [Active](../setup-for-work-orders/work-order-lifecycle-states.md) lifecycle state.  


## Add a maintenance checklist line

Maintenance checklists are created from the definition on the maintenance job type default and transferred to a work order job. If required, you can add maintenance checklist lines to a work order job. Manually added maintenance checklist lines get the reference "Manual".

1. In **Work order maintenance job checklist**, select the work order job for which you want to add a maintenance checklist.

2. On the **Maintenance checklist lines** FastTab, select a maintenance checklist line and press the arrow-down button on your keyboard if you want to insert a new line after the selected maintenance checklist line. The next number in the sequence is automatically inserted in the **Line number** field. You can also select a maintenance checklist line and click the **Add line** button if you want to insert a new line above the selected maintenance checklist line.

3. Insert a name for the maintenance checklist line in the **Name** field.

4. In the **Type** field, select a type for the maintenance checklist line. For each maintenance checklist type, the related fields are shown on the **Line details** FastTab.  
  a. "Text" is used to add a maintenance checklist line with a text description of what to do. This maintenance checklist type can be used if you want a worker to check or inspect something, without expecting a specific (measurable) result. Insert a description of what to do in the **Instructions** section on the **Line details** FastTab. 
  b. "Header" is used as a heading to group the maintenance checklist lines shown below the header. This is useful if you have several maintenance checklist lines that can be divided into specific areas. Insert a descriptive name in the **Name** field.  
  c. "Template" is not applicable when you add a maintenance checklist line manually on a work order job.  
  d. "Variable" is used to define a possible result in a range on a maintenance checklist line. The setup of maintenance checklist variables is described in [Maintenance job type categories and maintenance job types, maintenance job type variants, maintenance job trades, and maintenance checklists](../setup-for-work-orders/job-groups-and-job-types-variants-trades-and-checklists.md). Insert a name to describe the variable in the **Name** field. Select the variable in the **Variable** field. Insert a description of what to do in the **Instructions** section on the **Line details** FastTab.  
  e. "Measurement" is used to record a specific measurement. Insert a name for the measurement in the **Name** field. On the **Line details** FastTab, select **Counter** and **Unit**. Insert a description of what to do in the **Instructions** section.  

5. When you are done adding maintenance checklist lines manually, fill out the lines as described in the section above.

>[!NOTE]
>In **Work order maintenance job checklist**, you can't delete maintenance checklist lines with the reference "Job type". You can only delete maintenance checklist lines with the reference "Manual", which you or other maintenance workers have created manually.


![Figure 1](media/14-work-orders.png)

