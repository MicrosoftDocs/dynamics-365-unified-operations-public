---
title: Dynamics 365 finance and operations apps available geographies
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

# Dynamics 365 finance and operations apps available geographies

[!include[banner](../includes/banner.md)]

Microsoft Dynamics 365 finance and operations apps are generally available to support data residency in specific geographies. These deployment options serve customers in regulated industries and commercial organizations that do business with entities in specific geographies that may require local data residency.

## Data residency

Data residency for finance and operations apps environments and Microsoft Lifecycle Services aren't necessarily the same. You can see the supported regions when deploying environments. Only regions marked **Data resident region** store the data within the same geography as Lifecycle Services. Regions without this mark are **not data resident**, meaning the data isn't located in the same geography as Lifecycle Services. Customers requiring both Lifecycle Services and environments data don't leave the geographic boundary needed to ensure they create the Lifecycle Services Implementation project using the correct Lifecycle Services endpoint and correct region for environment deployment. For more information about which geographies store Lifecycle Services data, see the [Supported geographies and endpoints](#supported-geographies-and-endpoints).

### Supported geographies and endpoints

Dynamics 365 finance and operations apps environments can be deployed across many different geographies. For a complete list of available regions, see [Feature availability across geographies](#feature-availability-across-geographies). Lifecycle Services is used for deploying the environments, and there are several instances available globally to provide data residency for the data stored in Lifecycle Services.

The following table lists the Lifecycle Services geographies and endpoints.

| **Geography** | **Lifecycle Services portal** | **Lifecycle Services API endpoint** | **Environment URL*** |
|-----------|--------------|------------------|----------------------|
| United States | [https://lcs.dynamics.com/](https://lcs.dynamics.com/) | <https://lcsapi.lcs.dynamics.com> | <https://NAME.operations.dynamics.com/> |
| Europe | [https://eu.lcs.dynamics.com/](https://eu.lcs.dynamics.com/) | <https://lcsapi.eu.lcs.dynamics.com> | <https://NAME.operations.eu.dynamics.com/> |
| France | [https://fr.lcs.dynamics.com/](https://fr.lcs.dynamics.com/) | <https://lcsapi.fr.lcs.dynamics.com> | <https://NAME.operations.fr.dynamics.com/> |
| Norway | [https://no.lcs.dynamics.com/](https://no.lcs.dynamics.com/) | <https://lcsapi.no.lcs.dynamics.com> | <https://NAME.operations.no.dynamics.com/> |
| South Africa | [https://sa.lcs.dynamics.com/](https://sa.lcs.dynamics.com/) | <https://lcsapi.sa.lcs.dynamics.com> | <https://NAME.operations.sa.dynamics.com/> |
| Switzerland | [https://ch.lcs.dynamics.com/](https://ch.lcs.dynamics.com/) | <https://lcsapi.ch.lcs.dynamics.com> | <https://NAME.operations.ch.dynamics.com/> |
| United Arab Emirates | [https://uae.lcs.dynamics.com/](https://uae.lcs.dynamics.com/) | <https://lcsapi.uae.lcs.dynamics.com> | <https://NAME.operations.uae.dynamics.com/> |

**NAME represents the unique customer defined environment name.*

## Feature availability across geographies

Microsoft strives to maintain functional parity between our commercially available services across geographies. We continue to evaluate these services and capabilities for inclusion and updates in future releases. Use the following documents to get an overview of services and their availability in the geographies you're planning to use.

* [Microsoft Business Application Feature Availability - Americas](https://aka.ms/bapfunctionalparityamericas)
* [Microsoft Business Application Feature Availability - EMEA](https://aka.ms/bapfunctionalparityemea)
* [Microsoft Business Application Feature Availability - APAC](https://aka.ms/bapfunctionalparityapac)

For more information about these exceptions, or for questions about regional services, contact [Microsoft Dynamics 365 Support](https://dynamics.microsoft.com/support/).

For information about product availability per country and workload, see [Dynamics 365 and Power Platform availability](https://dynamics.microsoft.com/availability-reports/).
