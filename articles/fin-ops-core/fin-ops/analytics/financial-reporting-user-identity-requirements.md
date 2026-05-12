---
title: User identity requirements for Financial Reporting
description: Learn about user identity requirements and supported access patterns for Financial Reporting in Dynamics 365 Finance and Operations.
author: JinnieWong  
ms.author: jiwo
ms.topic: article
ms.date: 05/12/2026
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

Financial Reporting in Dynamics 365 Finance and Operations does **not support external authentication**.

Users provisioned as any of the following in Microsoft Entra ID are not supported for accessing Financial Reporting:

- External users  
- Guest users  
- B2B users  
- External members  

This applies to all Financial Reporting capabilities, including:

- Report Designer  
- Viewing financial reports  
- Editing financial reports  

While some external or guest users may have previously been able to launch Report Designer or generate reports, this behavior was inconsistent and dependent on authentication token handling between Finance and Operations and the Financial Reporting service. These scenarios were never supported and may fail intermittently or be blocked entirely.

## Supported access

To access Financial Reporting, users must be provisioned as:

- Internal users within the organization’s Microsoft Entra ID tenant  
- Assigned appropriate roles and permissions within Finance and Operations  

Guest user identities added through B2B collaboration are not supported for Financial Reporting access.

## Impact

Organizations that currently rely on external or guest user access may experience:

- Inability to open Report Designer  
- Errors when viewing reports  
- Errors when editing reports  

Provisioning users as internal Microsoft Entra ID users is required to restore supported access.

## Additional resources

[Create new users in Finance and Operations](https://learn.microsoft.com/dynamics365/fin-ops-core/dev-itpro/sysadmin/tasks/create-new-users)

[Create or delete users in Microsoft Entra ID](https://learn.microsoft.com/entra/fundamentals/how-to-create-delete-users)

[B2B guest user properties](https://learn.microsoft.com/entra/external-id/user-properties)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
