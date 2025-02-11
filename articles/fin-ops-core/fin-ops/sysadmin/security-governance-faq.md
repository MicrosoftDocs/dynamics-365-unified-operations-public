---
title: Security governance FAQ
description: Learn how to set up security categories that are used to create the process hierarchy and security configuration.
author: saurabhgupta
ms.author: saurabhgupta
ms.topic: article
ms.date: 01/25/2025
ms.custom: 
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2025-01-20
ms.search.form: SysSecRolesEditUsers, SysSecAssignmentQueryLookup, SysQueryForm, SysSecRoleExcludeUsers
ms.dyn365.ops.version: Version 7.0.0
---

# Security governance FAQ

[!include [banner](../../../finance/includes/banner.md)]
[!INCLUDE [preview-banner](~/../shared-content/shared/preview-includes/preview-banner.md)]

This article provides answers to many of the most frequently asked questions about security governance feature, setup and usage in business sceanrios. 

## Can this feature be also used for hiding some fields on a form or control the editability of certain fields on a form for certain roles?
For most fields, you'll need to do custom implementation of business logic to control the permissions but if there is an entrypoint behind the selected field, then it can be controlled through user security governance feature. 

## Does this tool integrates with any version control system to maintain various XMLs or AXTR files generated during the usage of it?
No, it is not integrated directly with any version control but we would definitely recommend everyone to control all files through a version control so that **system administrators** be able to maintain copies of files, task recordings files etc. It can be helpful in future if for any compliance audits, one need to compare the security versions with approved security architecture. 

## Will the process hierarchy work with customised menu items, as long as they are mapped to privileges?
Yes, it will work with custom menu items. 

## Will temporary role management also get captured in security audit trail?
Yes, any role changes happening for an active user account, will be captured in the **security audit trail** report. 

## Does it work with user groups or user access assigned through azure AD?
No. Security governance uses the user created directly within Dynamics 365 Finance & Operations security administration module.

## By disabling any user in Entra app, will it also disable the same user in Dynamics 365 Finance & operations?
No. At this time, both these user management systems are not integrated. 

## Is the "task recording" referred here within security governance session recording is similar to the AX 2012 Security Development Tool?
Yes, it is similar as security development tool with some new technical changes. You can read more about the **Task Recording** utility. 

## Is there a feature which can include usage information by user - not just users having the right licenses but also how often are they logging in/using the system?
Yes. Newly introduced **User aging report** serves this business purpose. 

## Where can we see the user licence utilization?
Newly introduced **License Summary** report will allow system administrators to be able to see licenses usage by various factors like by role, user, duty, privilege etc. 










