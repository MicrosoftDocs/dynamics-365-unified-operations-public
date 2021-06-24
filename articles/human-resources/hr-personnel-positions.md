---
# required metadata

title: Setting up positions
description: This article describes the conceptual elements that a position can include and provides examples of how you can use those elements in your organization. 
author: andreabichsel
ms.date: 06/24/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmPosition, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.author: anbichse
ms.reviewer: anbichse
ms.search.scope: Human Resources
# ms.tgt_pltfrm: 
ms.custom: 269054
ms.search.region: Global
# ms.search.industry: 
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Version 1611

---

# Setting up positions

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

This article describes the conceptual elements that a position can include and provides examples of how you can use those elements in your organization. 

Before you can create a position, you must have a job set up.  Some position details, such as the compensation region, worker assignment, position duration, and reporting relationship, are date-effective. 


## General information
When creating a position, it is required to select a job.  The following information will default from the Job that is selected at the time of position creation:  Description, Title, Full-time equivalent and Job Family.  Important items to note in this section are the following: 
++The position title is used to reference an employee's title rather than the title that is listed on the employee.  Therefore, position titles should be standardized as much as possible.  
++A worker cannot be assigned to the position at a date that is before the available for assignment date.  
 Pro tip:  There is a parameter setting that controls how this field works.  In Human resources shared parameters you can choose the appropriate worker assignment behavior under the Positions Tab.  You can select Always (you can assign workers to new positions when positions are created; the Available for assignment date and time will be set to the creation date and time on the General tab of the Position page when positions are created) or Never (you cannot assign workers to new positions when positions are created; if you select this option, you will have to open the Position page for each new position when it becomes available and enter the Available for assignment date on the General tab to enable worker assignment).  If you select 'Never'in the parameters form, the worker assignment date will default to 'Never' when attempting to assign the worker.  

## Position duration
Every position has a length of time that the position is effective. This length of time is referred to as duration. For example, summer positions might have duration of May 1, 2021 until August 31, 2021.  The Activation date is the date the position is active in the system and the retirement date is when the position is no longer active in the system.

Pro tip:  Neither the Available for assignment date or Worker assignment date can be before the Activation date.  The position is not considered active until the activation date has been reached. Also, a worker assignment cannot extend past the retirement date of the position.

## Reports to position
Positions are important elements of the lower level of an organization hierarchy. In the Position form, you can specify the position that a position reports to. When you assign a worker to a position that reports to another position, you create a reporting relationship between the workers who are assigned to the two positions. For example, position “000220” reports to position “000300”. Kim Akers is assigned to position “000220” and Sanjay Patel is assigned to position “000300”. This means that Kim Akers reports to Sanjay Patel.

Pro tip:  The Reports to position is used throughout the system for determining who the employee's manager is.  In the example above, if Sanjay is given the role of manager in the system, he will see Kim Akers as a direct report in Manager Self-Service.  The reporting relationship can also be used when creating workflow routing rules, as well as for creating checklist tasks.  

## Relationships
If your organization uses a matrix hierarchy or another custom hierarchy, you can set up position hierarchy types and then add reporting relationships to positions for each hierarchy type that you set up. For example, Lori Penor is a general manager at Adventure Works and is assigned to the “General Manager” position. Lori manages the development of a product that is used to clean widgets. Lori requires an accountant to help her with the finances for developing the product. Therefore, she has recruited Kim Akers to be her accountant. Kim reports directly to Sanjay Patel, but also works with Lori Penor on her work related to the finances for developing the widget cleaner.

For the previous example, you would complete the following tasks to set up the working relationship between Kim Akers and Lori Penor:

Create a custom position hierarchy type called “Widget” to create a hierarchy that includes positions responsible for working on the widget cleaner product.
Assign the General Manager position to be the position that Kim's position reports to in the Widget hierarchy.
Use the position hierarchy to view the reporting structure of positions. If you have multiple position hierarchies, you can view the hierarchy for each hierarchy type in the position hierarchy. Also, you can search for a position by position ID or by the name of the worker who is assigned to the position. The position hierarchy is an organizational hierarchy.

## Labor Union
You can record whether a union agreement is needed forthe position, which labor union is used, and associate the agreement to a legal entity.

# Financial Dimensions
When creating the financial dimension for the position, you must specify a legal entity.  You can select the default dimensions for each dimension individually or select a distribution template.  The distribution template will default the dimensions in, and also provide the option to allocate amounts across multiple dimension values.  


