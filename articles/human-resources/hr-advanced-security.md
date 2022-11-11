---
# required metadata

title: Configure worker access
description: This article explains how to set up worker access by legal entity.
author: twheeloc
ms.date: 11/28/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: HcmSharedParameters, HcmPersonnelManagementWorkspace
# ROBOTS: 
audience: Application User
# ms.devlang: 

# ms.tgt_pltfrm: 
ms.custom: 51891
ms.assetid: c7d8f58c-d78a-4035-abbf-2b0ce16109fe
ms.search.region: Global
# ms.search.industry: 
ms.author: twheeloc
ms.search.validFrom: 2020-02-03
ms.dyn365.ops.version: Human Resources

---

# Restrict access to workers by legal entity

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]


Employees are employed in legal entities. For example, using demo data- Aaron Con is employed in USSI, Ahmed Barnett is employed in USMF, and Alicia Thornber is
employed in GLSI and USMF. Depending on a user’s role in the company, they may need access to view all employees across all legal entities or they may need to be
restricted to viewing only employees in the legal entity that they have access to. Use the **Restrict access to worker information** setting, in **Human Resources Shared 
Parameters** page to control which employees the user can see.

When this feature is not enabled, a user (that has access to the **Worker** page) will be able to view Aaron, Ahmed, and Alicia- even though they may only
have access to USMF. When this feature is enabled, the user will only see information for Alicia and Ahmed if they only have access to USMF.
Depending on the application that you are using, the visual experience will vary slightly.

Dynamics 365 Human Resources stand-alone – When the feature is enabled to restrict access to worker information, the restricted user will see a blank value in some 
lists that contain the worker name. Example using the demo data above: The user only has access to USMF. When navigating to the **Active positions** list, the **Worker** 
column will be blank for Aaron’s position because the user does not have access to employee’s in USSI. If the user attempts to drill down on the worker name, they 
will be brought to the worker form but no data will be displayed.


Dynamics 365 Human Resources on Finance infrastructure– When the feature is enabled to restrict access to worker information, the restricted user will see the worker 
name in some lists. Example using the demo data above: The user only has access to USMF. When navigating to the **Active positions** list, the **Worker** column will 
display Aaron’s name, but when hovering on his name, only his name and title will display. If the user attempts to drill down on the worker name, they will be 
brought to the worker page but no data will be displayed.

>[!Note] 
>If you are using Dynamics 365 Human resources on Finance infrastructure, and would like restricted users to see blank values for worker names, you can add 
security privilege Restrict access to workers to their user roles in **Security configuration** page.


In conjunction with turning the feature on, there are additional steps to set the appropriate permissions for each user whose view must be restricted.
1.	On the **Users** page, select a user.
2.	Select a role for the user. The **Assign organizations** option becomes available.
3.	Select **Assign organizations**.
4.	On the new page, select **Grant access to specific organizations individually**, and then select the organizations that the user should have access to.
5.	Repeat steps 2 through 4 for every additional role that the user has, including the system user role.

>[!Note] 
>The companies that a user has access to must match across all the user's roles.
