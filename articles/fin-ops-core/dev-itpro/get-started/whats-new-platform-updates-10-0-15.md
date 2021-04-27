---
# required metadata

title: Platform updates for version 10.0.15 of Finance and Operations apps (January 2021)
description: This topic lists the features that are included in the platform updates for version 10.0.15 of Finance and Operations apps.
author: sericks007
ms.date: 12/08/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2020-10-31
ms.dyn365.ops.version: 10.0.15

---
# Platform updates for version 10.0.15 of Finance and Operations apps (January 2021)

[!include [banner](../includes/banner.md)]

This topic lists the features that are included in the platform updates for version 10.0.15 of Finance and Operations apps. This version has a build number of 7.0.5816 and is available on the following schedule:

- **Preview release:** October 2020
- **General availability (self-update):** November 2020
- **Auto-update:** January 2021

## Features included in this release

-  Azure Pipelines task for asset deployment now supports self-service environments<br>- For more information to enable this support, see
[Deploy assets by using Azure Pipelines](../dev-tools/pipeline-deploy-asset.md).
- Specific full user license information is now available when configuring security and assigning roles to users.<br>- For more information, see
[Stay compliant with user licensing requirements](../sysadmin/stay-compliant-user-license-requirement.md).
- Regression suite automation tool (RSAT) 2.0<br>- For RSAT users, version 10.0.15 requires the latest version of RSAT to address a known issue. RSAT 2.0.7031.98 or newer will be available for download at https://www.microsoft.com/en-us/download/details.aspx?id=57357 on Monday, October 12, 2020.

## Additional resources

### Bug fixes

For information about the bug fixes that are included in this update, sign in to Microsoft Dynamics Lifecycle Services (LCS), and view the [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=514518&dbType=3&qc=8fbe12733a7e1aa197e91fb11530f69fa89b9b39c08d89a19873f755c9430988).

### Dynamics 365: 2020 release wave 2 plan

Wondering about upcoming and recently released capabilities in any of our business apps or platform?

Check out the [Dynamics 365: 2020 release wave 2 plan](/dynamics365-release-plan/2020wave2/). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated platform features

The [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic describes features that have been removed, or that are planned for removal in platform updates of Finance and Operations apps.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature isn't in active development and might be removed in a future update.

A deprecation notice will be added in the [Removed or deprecated platform features](removed-deprecated-features-platform-updates.md) topic 12 months before the removal of any feature from the product.

For breaking changes that affect only compilation time, but that are binary-compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these changes are functional updates that must be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]