---
title: Security governance FAQ
description: This frequently asked questions article answers to some frequently asked questions about Security governance. 
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

This article provides answers to the most frequently asked questions about security governance feature, set up, and usage. 

## Can this feature be used for hiding some fields on a page or control the editability of certain fields on a page for certain roles?
For most fields, you need to do custom implementation of business logic to control the permissions. If there's an entrypoint behind the selected field, then it can be controlled through user security governance feature. 

## Does this tool integrates with any version control system to maintain various XMLs or AXTR files generated during the usage of it?
No, it's not integrated directly with any version control. It's recommended to control all files through a version control so that system administrators can maintain copies of files or task recordings files. It's helpful for compliance audits, users just need to compare the security versions with approved security architecture. 

## Will the process hierarchy work with customized menu items if they're mapped to privileges?
Yes, it works with custom menu items. 

## Is temporary role management captured in the security audit trail?
Yes, any role changes happening for an active user account, are captured in the **Security audit trail** report. 

## Does it work with user groups or user access assigned through Azure AD?
No. Security governance uses the user created directly within Dynamics 365 finance and operations security administration module.

## By disabling any user in Entra app, will it also disable the same user in Dynamics 365 finance and operations?
No. At this time, these user management systems aren't integrated. 

## Is the task recording within security governance session recording is similar to the AX 2012 Security development tool?
Yes, it's similar as security development tool with some new technical changes.  

## Is there a feature that includes usage information by user, not just users having the right licenses but also how often are they logging in and using the system?
Yes. The **User aging report** provides this information.  

## Where can we see the user license utilization?
The **License summary** report displays licenses usage by various factors like by role, user, duty, or privilege. 










