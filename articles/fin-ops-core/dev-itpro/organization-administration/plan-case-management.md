---
title: Plan case category security, case processes, and case categories
description: Learn about the considerations and decisions that you must make during the planning process, before you begin to configure cases.
author: kfend
ms.author: johnmichalak
ms.topic: article
ms.date: 12/02/2025
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: CaseCategorySetup, CaseCategoryTypeSecurity
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 0a1ffae4-5750-46a2-becb-604f7a989d32
---

# Plan case category security, case processes, and case categories

[!include [banner](../../../finance/includes/banner.md)]

This article describes the considerations and decisions that you must make during the planning process, before you begin to configure cases.

You can use the case functionality to resolve both issues that are external to your organization and internal issues.

## Case category security by role

Only appropriate employees in an organization should have access to cases and related information. To control which employees have access to view, create, and update different types of cases, assign security roles to case category types. Determine which security roles should have access to the various case category types.

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

Set up processes that employees must follow for the cases they open in your organization. Processes help guarantee consistency for the people involved in cases, and they help employees resolve cases faster and more efficiently. Set up a process for each case category that you assign cases to. Although planning a separate process for each case type takes time, case resolution goes much more smoothly if you plan out the processes.

**Decisions:** For each case process, make the following decisions:

- What are the name and description of the process?
- Is the process active, and should employees use it when they handle a case that the process is assigned to?
- Who in the organization is responsible for applying the process to a case? For example, cost accounting or human resources might be responsible for some case processes. Multiple areas can be responsible for completing one process.

## Case categories

The case category hierarchy provides a list of categories that you can assign cases to (see the "Case category security by role" section). Each top-level category includes subcategories, so that you can create more specific categories for the cases that your organization works with. Review the list of existing categories and subcategories to determine whether you need to create more. If you need to create more categories and subcategories, make the following decisions for each addition.

**Decisions:**

- Are you creating a new top-level category?

    - What is the name of the category?

- Are you creating a new subcategory?

    - What is the parent category of the subcategory?
    - What is the name of the subcategory?
    - Which worker owns the subcategory?
    - What department is the subcategory assigned to?
    - What case process is assigned to this subcategory?
    - What is the default service level agreement (SLA) that is assigned to this subcategory?
    - Should an activity be created when a case that this subcategory is assigned to is opened?
    - If so, what is the activity category, type, purpose, and phase?
    - Should a follow-up activity for the case be created?
    - If so, what is the follow-up activity category, type, purpose, and phase?


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]