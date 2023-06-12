---
# required metadata

title: Plan case category security, case processes, and case categories
description: This article describes the considerations and decisions that you must make during the planning process, before you begin to configure cases.
author: kfend
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: CaseCategorySetup, CaseCategoryTypeSecurity
# ROBOTS: 
audience: IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: 0a1ffae4-5750-46a2-becb-604f7a989d32
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Plan case category security, case processes, and case categories

[!include [banner](../includes/banner.md)]

This article describes the considerations and decisions that you must make during the planning process, before you begin to configure cases.

You can use the case functionality to resolve both issues that are external to your organization and internal issues.

## Case category security by role

Only appropriate employees in an organization should have access to cases and related information. To control which employees have access to view, create, and update different types of cases, you can assign security roles to case category types. You must determine which security roles should have access to the various case category types.

**Decision:** Determine which security roles should have access to the following case category types. Your organization might not use all these category types, so make decisions only for those categories that are appropriate.

- General
- Sales
- Purchase
- Service
- Project
- Production
- Collections
- Audit
- Web
- Human Resources
- Product change
- FMLA

## Case processes

You should set up processes that employees must follow for the cases that are opened in your organization. Processes help guarantee consistency for the people who are involved in cases, and also help employees resolve cases faster and more efficiently. You can set up a process for each case category that cases are assigned to. Although planning a separate process for each case type takes time, case resolution will go much more smoothly if the processes are planned out.

**Decisions:** For each case process, you must make the following decisions:

- What are the name and description of the process?
- Is the process active, and should employees use it when they handle a case that the process is assigned to?
- Who in the organization will be responsible for applying the process to a case? For example, Cost accounting or Human resources might be responsible for some case processes. Note that multiple areas can be responsible for completing one process.

## Case categories

The Case category hierarchy provides a list of categories that you can assign cases to (see the "Case category security by role" section). Each top-level category includes subcategories, so that you can create more specific categories for the cases that your organization works with. Review the list of existing categories and subcategories to determine whether you must create more. If you must create more categories and subcategories, you must make the following decisions for each addition.

**Decisions:**

- Are you creating a new top-level category?

    - What is the name of the category

- Are you creating a new subcategory?

    - What is the parent category of the subcategory?
    - What is the name of the subcategory?
    - Which worker will own the subcategory?
    - What department is the subcategory assigned to?
    - What case process will be assigned to this subcategory?
    - What is the default service level agreement (SLA) that is assigned to this subcategory?
    - Should an activity be created when a case that this subcategory is assigned to is opened?
    - If so, what are the activity category, type, purpose, and phase?
    - Should a follow-up activity for the case be created?
    - If so, what are the follow-up activity category, type, purpose, and phase?


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]