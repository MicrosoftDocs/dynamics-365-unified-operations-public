---
title: Manage access to sensitive data
description: Learn about the user log functionality, including overviews on sensitive data, language-specific information, and log retention.
author: ToddLefor
ms.author: tlefor
ms.topic: article
ms.date: 03/13/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-12-31
ms.dyn365.ops.version: AX 7.0.0
---

# Manage access to sensitive data

[!include [banner](../includes/banner.md)]

System administrators can use the **User log** page to keep an audit log of users who sign in to the system. Knowing who signs in can help protect your organization's data. The enhanced user logging capability helps administrators identify roles that provide access to sensitive data.

## What is sensitive data?

An organization can define what constitutes *sensitive data* in whatever way serves its needs. For some organizations, sensitive data might be any data that is related to financial or human resource data, or just data that is personal data. Some industries or some countries or regions might have a more specific definition of sensitive data that an organization can adopt for itself. It's up to each organization to decide whether and how to use the sensitive data identifier.

The sensitive data identifier enhances the user logging experience by helping your organization produce audit logs that show who in your system has access to sensitive data. This capability is helpful for organizations that might have multiple roles that have varying degrees of access to certain data. It can also be helpful for organizations that want a detailed level of auditing to track users who have had access to data that's been identified as sensitive data.

## Language-specific information

The role information in the user log is language-specific and matches the current user language.

## Log retention

You can retain separately the log entries of users who have access to data that's been declared to be sensitive data from all other data in the log. The administrator can enable this functionality by setting an option on the **User log cleanup** page.

:::image type="content" source="../media/privacy-sensitive-data-4.jpg" alt-text="Screenshot of the User log cleanup page.":::

> [!NOTE]
> This feature is available in version 8.0. This feature is available for Dynamics AX 2012 R3 (via KB 4074643).

## Additional resources

[!INCLUDE [gdpr-intro](~/../shared-content/shared/privacy-includes/gdpr-intro.md)]

### Disclaimer

(c) 2018 Microsoft Corporation. All rights reserved. This document is provided "as-is." Microsoft grants you no legal rights to any intellectual property in any Microsoft product. You bear the risk of using the information and views expressed in this document, including URL and other Internet website references, which might change without notice. You may copy and use this document for your internal reference purposes.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
