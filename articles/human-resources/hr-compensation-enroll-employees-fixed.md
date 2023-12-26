--- 
# required metadata 
 
title: Enroll an employee in a fixed compensation plan
description: The compensation and benefits manager can assign employees to fixed compensation plans to manage their base pay. 
author: twheeloc
ms.date: 08/25/2021
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: HRMCompFixedEmpl, HRMCompFixedEmplActionDialog, HcmPositionLookup, HRMCompRefPointLookup, HcmCompensationWorkspace   
audience: Application User 
# ms.devlang:  

# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2016-06-30 
ms.dyn365.ops.version: Version 7.0.0 

---

# Enroll an employee in a fixed compensation plan


[!INCLUDE [PEAP](../includes/peap-1.md)]

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]

The compensation and benefits manager can assign employees to fixed compensation plans to manage their base pay. This procedure assumes that a fixed plan has been created and is active, and that eligibility rules have been set for the plan. The demo data company used to create this procedure is USMF. To begin the procedure, go to **Human resources** > **Workers** > **Employees** > **Compensation** > **Fixed plan**.

1. Click **New**.
2. In the **Action** field, select a Fixed compensation action of **Hire/Rehire** to describe the change in the employee's compensation.
3. In the list, click the link in the selected row.
4. In the **Position** field, click the drop-down button to open the lookup.
5. In the list, click the link in the selected row.
    * The level that's displayed is from the **Compensation** FastTab > **Level** field from the **Job** that is assigned to the **Position**. The level must be set on the Job before compensation can be assigned to the employee.  
6. In the **Plan** field, select the fixed compensation plan for the employee. The **Plan** lookup is filtered to show only the plans that the employee is eligible for based on the **Eligibility rules**.
7. In the list, find and select the desired record.
    * The **Effective** and **Expiration** dates for the compensation default from the start and end dates for the worker's position assignment. You can adjust these dates as needed.  
    * If the Fixed compensation plan is a step plan, select the step containing the correct pay rate for the employee. If the fixed compensation plan is a grade or a band plan, enter the pay rate for the employee. The pay rate will be validated against the tolerance settings for the plan, and the minimum and maximum reference points for the job's compensation level.  
8. Click **OK**.



[!INCLUDE[footer-include](../includes/footer-banner.md)]
