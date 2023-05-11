---
title: Available geographies for Dynamics 365 finance and operations apps
description: This article provides information about the supported geographies and endpoints for Microsoft Dynamics 365 finance and operations apps.
author: ShaileshNikam-MSFT
ms.date: 05/10/2023
ms.topic: article
audience: IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: shailesn
ms.search.validFrom: 2022-04-28
---

# Available geographies for Dynamics 365 finance and operations apps

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 finance and operations apps are generally available to support data residency in specific geographies. These deployment options serve customers in regulated industries and commercial organizations that do business with entities in specific geographies that might require local data residency.

## Data residency

Data residency for finance and operations apps environments and Microsoft Dynamics Lifecycle Services isn't necessarily the same. You can view the supported regions when you deploy environments. Only regions that are marked **Data resident region** store the data in the same geography as Lifecycle Services. Regions that aren't marked in this way are *not data resident* (that is, the data isn't located in the same geography as Lifecycle Services). Customers who require that neither Lifecycle Services data nor environment data should leave the geographic boundary must ensure that they use the correct Lifecycle Services endpoint and the correct region for environment deployment when they create the Lifecycle Services Implementation project. For more information about which geographies store Lifecycle Services data, see the [Supported geographies and endpoints](#supported-geographies-and-endpoints) section of this article.

### Supported geographies and endpoints

Dynamics 365 finance and operations apps environments can be deployed across many geographies. For a complete list of available regions, see the [Feature availability across geographies](#feature-availability-across-geographies) section of this article. Lifecycle Services is used to deploy the environments, and several instances are available globally to provide data residency for the data that's stored in Lifecycle Services.

The following table lists the Lifecycle Services geographies and endpoints.

> [!NOTE]
> In the URLs in the "Environment URL" column, **NAME** represents the unique customer-defined environment name.

| Geography | Lifecycle Services portal | Lifecycle Services API endpoint | Environment URL |
|-----------|--------------|------------------|----------------------|
| United States | [https://lcs.dynamics.com/](https://lcs.dynamics.com/) | `https://lcsapi.lcs.dynamics.com` | `https://NAME.operations.dynamics.com/` |
| Europe | [https://eu.lcs.dynamics.com/](https://eu.lcs.dynamics.com/) | `https://lcsapi.eu.lcs.dynamics.com` | `https://NAME.operations.eu.dynamics.com/` |
| France | [https://fr.lcs.dynamics.com/](https://fr.lcs.dynamics.com/) | `https://lcsapi.fr.lcs.dynamics.com` | `https://NAME.operations.fr.dynamics.com/` |
| Norway | [https://no.lcs.dynamics.com/](https://no.lcs.dynamics.com/) | `https://lcsapi.no.lcs.dynamics.com` | `https://NAME.operations.no.dynamics.com/` |
| South Africa | [https://sa.lcs.dynamics.com/](https://sa.lcs.dynamics.com/) | `https://lcsapi.sa.lcs.dynamics.com` | `https://NAME.operations.sa.dynamics.com/` |
| Switzerland | [https://ch.lcs.dynamics.com/](https://ch.lcs.dynamics.com/) | `https://lcsapi.ch.lcs.dynamics.com` | `https://NAME.operations.ch.dynamics.com/` |
| United Arab Emirates | [https://uae.lcs.dynamics.com/](https://uae.lcs.dynamics.com/) | `https://lcsapi.uae.lcs.dynamics.com` | `https://NAME.operations.uae.dynamics.com/` |

## Feature availability across geographies

Microsoft strives to maintain functional parity between our commercially available services across geographies. We continue to evaluate these services and capabilities for inclusion and updates in future releases. Use the following documents to get an overview of services and their availability in the geographies that you're planning to use:

* [Microsoft Business Application Feature Availability - Americas](https://aka.ms/bapfunctionalparityamericas)
* [Microsoft Business Application Feature Availability - EMEA](https://aka.ms/bapfunctionalparityemea)
* [Microsoft Business Application Feature Availability - APAC](https://aka.ms/bapfunctionalparityapac)

For more information about these exceptions, or for questions about regional services, contact [Microsoft Dynamics 365 Support](https://dynamics.microsoft.com/support/).

For information about product availability per country and workload, see [Dynamics 365 and Power Platform availability](https://dynamics.microsoft.com/availability-reports/).
