---
title: Security governance FAQ
description: Get answers to frequently asked questions about security governance.
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

This article provides answers to the most frequently asked questions about the security governance feature, how it's set up, and how it's used.

## Can the feature be used to hide specific fields on a page or control the ability of some roles to edit specific fields on a page?

For most fields, you must do a custom implementation of the business logic to control the permissions. However, if there is an entry point behind the selected field, it can be controlled through the user security governance feature.

## Is the feature integrated with any version control system to maintain the various XML or AXTR files that are generated during use?

No, security governance isn't integrated directly with any version control. We recommend that you control all files through version control, so that system administrators can maintain copies of files or task recording files. This approach is helpful for compliance audits, because users just have to compare the security versions with the approved security architecture.

## Does the process hierarchy work with customized menu items that are mapped to privileges?

Yes, the process hierarchy works with custom menu items.

## Is temporary role management captured in the security audit trail?

Yes. Any role changes that are made for an active user account are captured on the **Security audit trail** report.

## Does the feature work with user groups or user access that is assigned through Microsoft Azure Active Directory (Azure AD)?

No. Security governance uses the user that is created directly in the **Security administration** module in Dynamics 365 finance and operations apps.

## If a user is disabled in the Microsoft Entra app, is that user also disabled in finance and operations apps?

No. The two user management systems aren't currently integrated.

## Is the task recording functionality in security governance session recording similar to the Dynamics AX 2012 Security development tool?

Yes, the task recording functionality is similar to the Security development tool. However, it includes some new technical changes.

## Is there any feature that includes usage information by user, and that shows not only users who have the correct licenses, but also how often those users sign in and use the system?

Yes. The **User aging** report provides this information.

## Where can I view information about user license utilization?

The **License summary** report shows license use by factors such as role, user, duty, or privilege.
