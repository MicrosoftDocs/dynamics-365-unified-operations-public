---
# required metadata

title: Positions
description: This article describes the conceptual elements that a position can include. It also provides examples that show how you can use those elements in your organization.
author: twheeloc
ms.date: 06/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.author: twheeloc
ms.reviewer: twheeloc

# ms.tgt_pltfrm: 
ms.custom: 269054
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Positions


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the conceptual elements that a position can include. It also provides examples that show how you can use those elements in your organization.

Before you can create a position, a job must be set up. Some position details, such as the compensation region, worker assignment, position duration, and reporting relationship, are date effective.

## General information

When you create a position, you must select a job. The following information will automatically be filled in from the job that you select:

- Description
- Title
- Full-time equivalent
- Job family

The position title is used to reference an employee's title. (The title that is listed on the employee isn't used.) Therefore, position titles should be standardized as much as possible.

> [!NOTE]
> A worker can't be assigned to a position on a date that is before the available-for-assignment date.
>
> A parameter on the **Positions** tab of the **Human resources shared parameters** page controls the worker assignment behavior. Select one of the following values:
>
> - **Always** – You can assign workers to new positions when positions are created. When positions are created, the **Available for assignment** date and time on the **General** tab of the **Position** page are automatically set to the creation date and time.
> - **Never** – You can't assign workers to new positions when positions are created. If you select this option, you must open the **Position** page for each new position as it becomes available. Then, on the **General** tab, enter the **Available for assignment** date to enable worker assignment. If you select this option, the worker assignment date will be set to **Never** by default when you try to assign the worker.

## Position duration

Every position is effective for a specific amount of time that is referred to as the duration. For example, summer positions might have a duration of May 1, 2021, until August 31, 2021. The activation date is the date when the position is active in the system. The retirement date is when the position is no longer active in the system.

Note that neither the available-for-assignment date nor the worker assignment date can be before the activation date. A position isn't considered active until the activation date has been reached. Additionally, a worker assignment can't extend past the position's retirement date.

## Reports-to position

Positions are important elements in the lower level of an organization hierarchy. On the **Position** page, you can specify the position that a position reports to. When you assign a worker to a position that reports to another position, you create a reporting relationship between the workers who are assigned to those two positions. For example, position 000220 reports to position 000300. Kim Akers is assigned to position 000220, and Sanjay Patel is assigned to position 000300. Therefore, Kim Akers reports to Sanjay Patel.

> [!TIP]
> The reports-to position is used throughout the system to determine who an employee's manager is. In the preceding example, if the manager role is assigned to Sanjay Patel in the system, Sanjay will see Kim Akers as a direct report in Manager Self-Service. The reporting relationship can also be used when you create workflow routing rules and checklist tasks.

## Relationships

If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types. You can then add reporting relationships to positions for each hierarchy type that you set up. For example, Lori Penor is a general manager at Adventure Works and is assigned to the **General Manager** position. Lori manages the development of a product that is used to clean widgets and requires an accountant to help with the finances. Therefore, Lori has recruited Kim Akers to be the accountant. Kim reports directly to Sanjay Patel, but also works with Lori Penor on work that is related to the finances for development of the widget cleaner.

For the preceding example, you must complete the following tasks to set up the working relationship between Kim Akers and Lori Penor:

1. Create a custom position hierarchy type that is named **Widget** to create a hierarchy that includes positions that are responsible for working on the widget cleaner product.
2. Specify the **General Manager** position as the position that Kim's position reports to in the **Widget** hierarchy.
3. Use the position hierarchy to view the reporting structure of positions. If you have multiple position hierarchies, you can view the hierarchy for each hierarchy type in the position hierarchy. You can also search for a position by position ID or by the name of the worker who is assigned to the position. The position hierarchy is an organizational hierarchy.

## Labor union

You can record whether a union agreement is required for the position, and which labor union is used. You can also associate the agreement with a legal entity.

## Financial dimensions

When you create the financial dimension for a position, you must specify a legal entity. You can select the default dimensions for each dimension individually. Alternatively, you can select a distribution template to automatically fill in default dimensions. A distribution template also provides the option to allocate amounts across multiple dimension values.
