---
title: User identity requirements for Financial Reporting
description: Learn about user identity requirements and supported access patterns for Financial Reporting in Dynamics 365 Finance and Operations.
author: JinnieWong  
ms.author: jiwo
ms.topic: article
ms.date: 05/13/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.search.form: FinancialReportingSetup
ms.dyn365.ops.version: Version 1611
---

# User identity requirements for Financial Reporting

[!include [banner](../../../finance/includes/banner.md)]

Financial Reporting in finance and operations apps **doesn't support external authentication**.

Users that were created as any of the following types in Microsoft Entra ID can't access Financial Reporting:

- External users  
- Guest users  
- B2B users  
- External members  

This restriction applies to all Financial Reporting capabilities, including:

- Report Designer  
- Viewing financial reports  
- Editing financial reports  

While in the past some external or guest users might have been able to launch Report Designer or generate reports, this behavior was inconsistent and dependent on authentication token handling between finance and operations apps and the Financial Reporting service. These scenarios aren't supported and might fail intermittently or be blocked entirely.

## Supported access

To access Financial Reporting, users must be provisioned as:

- Internal users within the organization’s Microsoft Entra ID tenant  
- Assigned appropriate roles and permissions within finance and operations apps 

Guest user identities added through B2B collaboration aren't supported for Financial Reporting access.

## Effect on organizations that currently rely on external or guest user access

Organizations that currently rely on external or guest user access might experience:

- Inability to open Report Designer  
- Errors when viewing reports  
- Errors when editing reports  

To restore supported access, you need to create users as internal Microsoft Entra ID users.

## Additional resources

[Create new users in Finance and Operations](/dynamics365/fin-ops-core/dev-itpro/sysadmin/tasks/create-new-users)

[Create or delete users in Microsoft Entra ID](/entra/fundamentals/how-to-create-delete-users)

[B2B guest user properties](/entra/external-id/user-properties)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
