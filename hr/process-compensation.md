---
# required metadata

title: Process compensation
description: Compensation processing allows you to calculate new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance.
author: kherr
manager: AnnBe
ms.date: 07/01/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: rschloma
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 7521
ms.assetid: 3b953d5f-6325-4c9e-8b9b-6ab0458a73f8
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: AX 7.0.0

---

# Process compensation
Compensation processing allows you to calculate new base compensation amounts for your employees based on equity adjustments, merit increase targets, and performance. This blog post will cover the basic flow of compensation processing for Fixed compensation plans without factoring in performance.

## Plan the new compensation amounts and budgets
To give your employees a Merit increase, you must set up a Fixed increase budget for each of your Departments:  Compensation Management > Links > Merit increase targets. (Alternatively, you can open this form through the Department: Organization > Departments.) Here you can further specify whether employees in a certain Labor union or Location should get a different Increase percent. The **Budget** and **Currency** fields are informational and can be used to note a currency amount for the budget.

## Set up the compensation process
A process event lets you specify the parameters for the compensation processing. This includes the date period to evaluate for determining the compensation amounts.  and the date that the new compensation amounts should go into effect.

Optionally you can include a Fixed pay pro rated hire date if any of you fixed compensation plans use a hire rule of Percent. For those plans, anyone who was hired after the Cycle start date and before the Fixed pay pro rated hire date will receive 100% of their calculated merit or general increase. Anyone who was hired after the Fixed pay pro rated hire date and before the Cycle end date will receive a portion of their calculated increase based on how many days out of the total cycle days they were employed. For example, if our cycle runs from January 1 through December 31 and we have a Fixed pay prorated hire date of April 1, an employee who is hired in March will receive the full calculated increase while an employee hired on July 1 will receive approximately half of the calculated increase.

The process event **Point-in-time** date is only used for processing certain variable compensation plans and will not be covered in this blog post. The **Review deadline** is the deadline to make all the recommendations so that the new compensation amounts can be loaded into the employee’s record. The Review date is informational only.

Once the parameters of the process event have been saved, you can click the **Setup** button to indicate the plans to include in this process run and which Fixed compensation actions to take for each plan.

Click the **Add** button in the top tab to add a compensation plan to the process event. The **Use other leverage**, **Leverage factor**, and **Leverage description** columns are only used for variable compensation plans and are not be covered in this topic.

Save the record, then click the **Add** button in the bottom tab to add Fixed compensation actions for the selected plan. Use the Enable recommendation option if you want to be able to enter a different amount other than the calculated guideline increase for the action. If you want an action to be calculated based on the result of the previous action to link multiple compensation actions, mark the Use previous result option Fixed compensation actions are types of compensation logic that you can give descriptive names to. For Grade and Band plans, you can only add Fixed compensation actions that are of the following Types:
