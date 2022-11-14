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

This article explains how to set up worker access by legal entity.

[!include [Applies to Human Resources](../includes/applies-to-hr.md)]


Employees are employed in legal entities. For example:
- Aaron Con is employed in USSI 
- Ahmed Barnett is employed in USMF 
- Alicia Thornber is employed in GLSI and USMF 

To control which employees the user can see, select the **Restrict access to worker information** parameter on the **Human Resources shared parameters** page.
Depending on a user’s role in the company, they may need access to view all employees across all legal entities. Or they may need to be restricted to viewing only employees in the legal entity that they have access to. 

For example, a user who has access to the **Worker** page and has access only to USMF:
 - If the feature isn't enabled, the user will be able to see information for Aaron, Ahmed, and Alicia.
 - When this feature is enabled, the user will see information for only Alicia and Ahmed.

Depending on the application that you're using, different information will be displayed.

### Dynamics 365 Human Resources stand-alone 

When the feature is enabled to restrict access to worker information, the restricted user will see a blank value in some lists that contain the worker name. 

For example: 
 - The user only has access to USMF. 
 - On the **Active positions** list, the **Worker** column will be blank for Aaron’s position because the user doesn't have access to employees in USSI. 
 - If the user drills down on the worker name, a blank **Worker** page will be displayed.

### Dynamics 365 Human Resources on Finance infrastructure 

When the feature is enabled to restrict access to worker information, the restricted user will see the worker name in some lists. 
For example: 
 - The user only has access to USMF. 
 - On the **Active positions** list, the **Worker** column will display Aaron’s name. When hovering on the name, only the name and title will display. 
 - If the user drills down on the worker name, a blank **Worker** page will be displayed.

>[!Note] 
>If you are using Dynamics 365 Human resources on Finance infrastructure and would like restricted users to see blank values for worker names. You can add 
security privilege **Restrict access to workers** to the user roles in **Security configuration** page.


After turning on the feature, there are extra steps to set permissions for each user whose view must be restricted.
1.	On the **Users** page, select a user.
2.	Select a role for the user. The **Assign organizations** option becomes available.
3.	Select **Assign organizations**.
4.	On the new page, select **Grant access to specific organizations individually**, and then select the organizations that the user should have access to.
5.	Repeat steps 2 through 4 for every additional role that the user has, including the system user role.

>[!Note] 
>The companies that a user has access to must match across all the user's roles.
