--- 
# required metadata 
 
title: Enroll an employee in a variable compensation plan
description: The Compensation and Benefits manager can enrol employees in variable compensation plans to calculate cash and non-cash awards for employees. 
author: kherr75
manager: AnnBe 
ms.date: 11/14/2016
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
# ms.search.form:   
audience: Application User 
# ms.devlang:  
ms.reviewer: rschloma
ms.search.scope: Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: kherr
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: AX 7.0.0 
---
# Enroll an employee in a variable compensation plan

[!include[task guide banner](../../includes/task-guide-banner.md)]

The Compensation and Benefits manager can enrol employees in variable compensation plans to calculate cash and non-cash awards for employees. This procedure assumes that a variable compensation plan has been created with the Enable enrolment field set to Yes, and that eligibility rules have been created for that variable compensation plan. The demo data company used to create this procedure is USMF. To begin this procedure, go to Human resources > Workers > Employees > Compensation > Variable plan enrolment

1. Click New.
2. In the Plan field, click the drop-down button to open the lookup.
    * The plan lookup will be filtered to only show the variable compensation plans that the employee is eligible for based on the eligibility rules.  
3. In the list, click the link in the selected row.
4. Toggle the expansion of the General section.
5. In the Effective date field, enter a date.
6. Click Save.
7. Toggle the expansion of the Overrides section.
    * Optionally, a hire rule date can be set to override the hire date for an employee when the hire rule specified for the selected variable plan is Percent.  
    * If the variable plan is a percent of basis plan, the award percentage can be overridden for the employee. If the variable compensation plan is a number of units plan, the number of units can be overridden for the employee.  
    * If the employee should be given a flat amount for their award, the amount can be set here.  
8. Toggle the expansion of the Organizational overrides section.
    * If the employee's performance should take into consideration, the performance of different departments, or a department other than the one assigned on the employee's position, the department can be overridden. The Percent column should total 100.  

