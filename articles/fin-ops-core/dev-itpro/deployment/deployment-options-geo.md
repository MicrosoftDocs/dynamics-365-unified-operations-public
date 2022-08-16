---
title: Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies
description: This article provides information about the supported geographies and endpoints for Microsoft Dynamics 365 Commerce, Dynamics 365 Finance, and Dynamics 365 Supply Chain Management.
author: Shailesh4all
ms.date: 04/28/2022
ms.topic: article
audience: IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: shailesn
ms.search.validFrom: 2022-04-28
---

# Dynamics 365 Finance, Supply Chain Management, and Commerce in local geographies

[!include[banner](../includes/banner.md)]

## Data residency

Microsoft Dynamics 365 Commerce, Dynamics 365 Finance, and Dynamics 365 Supply Chain Management are generally available to support data residency in specific geographies. These deployment options serve customers in regulated industries and commercial organizations that do business with entities in specific geographies that require local data residency.

All required services and related data are deployed in the corresponding data centers of the geography. These services and data include Microsoft Dynamics Lifecycle Services (LCS), telemetry, databases, and environments. Customer data doesn't leave the geographic boundary.

### Supported local geographies and endpoints

The following table lists the local geographies and endpoints that Commerce, Finance, and Supply Chain Management support.

| Geography | LCS endpoint |
|-----------|--------------|
| France | [https://fr.lcs.dynamics.com/](https://fr.lcs.dynamics.com/) |
| United Arab Emeritus | [https://uae.lcs.dynamics.com/](https://uae.lcs.dynamics.com/) |
| South Africa | [https://sa.lcs.dynamics.com/](https://sa.lcs.dynamics.com/) |
| Switzerland | [https://ch.lcs.dynamics.com/](https://ch.lcs.dynamics.com/) |
| Europe | [https://eu.lcs.dynamics.com/](https://eu.lcs.dynamics.com/) |
| Norway | [https://no.lcs.dynamics.com/](https://no.lcs.dynamics.com/) |

## Feature availability in local geographies

Microsoft strives to maintain functional parity between our commercially available services across geographies. The exceptions are noted in the following list. This list is intended to help you understand and plan for a successful implementation of your business application solution.

We continue to evaluate these services and capabilities for inclusion and updates in future releases.

- The Dynamics Regulatory Alert Submission service isn't available in local geographies because it operates as a single global service. However, you can access the service from Global LCS.
- No corporate libraries are available in the American Productivity & Quality Center (APQC) Business process modeler (BPM) library. For each local geography, LCS publishes only the Getting started library and the last published APQC library. You can copy libraries to your project library to edit and publish them as the corporate library.
- The Dynamics 365 Translation Service is available only in the United States and the European Union (EU).
- Electronic reporting (ER) assets aren't visible in the Shared asset library. However, you can manually upload them from the LCS Global asset library. To work around this issue, you can run a script that is provided by Microsoft Engineering. Alternatively, you can access Microsoft Support ER assets by connecting to the Global repository. For more information, see [Regulatory Configuration Service (RCS) - Lifecycle Services (LCS) storage deprecation](../../../finance/localizations/rcs-lcs-repo-dep-faq.md).
- The embedded Power BI dashboard isn't available.
- Environment monitoring of LCS doesn't expose the same dashboard interface as Global LCS. However, the core key performance indicators (KPIs) are available.
- For an Azure build pipeline that uses hosted agents, the nuggets package from the LCS library isn't available in the Shared asset library.
- Cloud scale unit for commerce and e-commerce is available only in the United States and the EU.
- The Planning optimization service isn't available.
- Local business data deployment is available only in the EU.
- Code upgrade functionality, to upgrade from Dynamics AX 2012 to finance and operations apps, isn't available in any geography except LCS US (lcs.dynamics.com).

For more information about these exceptions, or for questions about regional services, contact [Microsoft Dynamics 365 Support](https://dynamics.microsoft.com/support/).

For information about product availability per country and workload, see [Dynamics 365 and Power Platform availability](https://dynamics.microsoft.com/availability-reports/).

