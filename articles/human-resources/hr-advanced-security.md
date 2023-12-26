---
# required metadata

title: Restrict access to workers by legal entity
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

Employees are employed in legal entities. Here are some examples:

- Aaron Con is employed in the USSI legal entity.
- Ahmed Barnett is employed in the USMF legal entity.
- Alicia Thornber is employed in the GLSI and USMF legal entities.

Depending on a user's role in the company, they might require access to view all employees across all legal entities. Alternatively, a user might have to be restricted, so that they can view only employees in the legal entity that they have access to. To control which employees a user can view, select the **Restrict access to worker information** parameter on the **Human Resources shared parameters** page.

For example, a user has access to the **Worker** page and has access only to the USMF legal entity. In this case, the user can view the following information for the employees in the preceding list:

- If the feature for restricting access to worker information isn't enabled, the user can view information for Aaron, Ahmed, and Alicia.
- If the feature is enabled, the user can view information only for Alicia and Ahmed, because they're also employed in the USMF legal entity.

The information that's shown varies, depending on the application that you're using.

## Dynamics 365 Human Resources stand-alone

If the feature for restricting access to worker information is enabled, the restricted user will see a blank value in some lists that contain the worker's name.

For example, a user who has access only to the USMF legal entity will experience the following behavior:

- In the **Active positions** list, the **Worker** column will be blank for Aaron's position, because the user doesn't have access to employees in the USSI legal entity.
- If the user drills down on the worker's name, a blank **Worker** page will appear.

## Dynamics 365 Human Resources on Finance infrastructure

If the feature for restricting access to worker information is enabled, the restricted user will see the worker's name in some lists.

For example, a user who has access only to the USMF legal entity will experience the following behavior:

- In the **Active positions** list, the **Worker** column will show Aaron's name. If the user hovers over the worker's name, only the name and title will be shown.
- If the user drills down on the worker's name, a blank **Worker** page will appear.

> [!TIP]
> If you're using Dynamics 365 Human resources on Finance infrastructure and want restricted users to see blank values for worker names, you can add the **Restrict access to workers** security privilege to the user roles on the **Security configuration** page.

After you enable the feature, you must complete some extra steps to set permissions for each user whose view must be restricted.

1. On the **Users** page, select a user.
2. Select a role for the user. The **Assign organizations** option becomes available.
3. Select **Assign organizations**.
4. On the new page, select **Grant access to specific organizations individually**, and then select the organizations that the user should have access to.
5. Repeat steps 2 through 4 for every other role that the user has, including the system user role.

> [!NOTE]
> The legal entities that a user has access to must match across all the user's roles.
