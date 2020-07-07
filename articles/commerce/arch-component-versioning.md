---
# required metadata

title: Dynamics 365 Commerce component versioning requirements
description: This topic provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.
author: rezaassadi
manager: AnnBe
ms.date: 07/07/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: RetailITWorkspace
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2020-07-01
ms.dyn365.ops.version: Release 10.0.11

---

# Dynamics 365 Commerce component versioning requirements

[!include [banner](includes/banner.md)]

This topic provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.

## Overview

The following illustration shows an overview of Dynamics 365 Commerce components and corresponding versioning requirements and dependencies.

<a href="https://docs.microsoft.com/en-us/dynamics365/commerce/media/commerce-component-versioning.jpg" target="_blank">![Dynamics 365 Commerce Component Versioning Requirements](./media/commerce-component-versioning.jpg)</a>

## Component Dependencies
### Service Updates
To ensure compatibility between all Dynamics 365 Commerce components that are serviced and deployed by customers and partners there are several versioning dependencies that need to be followed during servicing updates. The list below describes the full list of dependencies:

- **Finance and Operations apps/Commerce headquarters must be on the same or newer version as the Commerce Scale Unit (both cloud and self-hosted)**.
  For example, if the Finance and Operations apps/Commerce headquarters is on version 10.0.10, then the Commerce Scale Unit must be on version 10.0.10 or earlier (for example, 10.0.9, 10.0.8, etc.).
 
- **Commerce Scale Unit must be on the same or newer version than the Modern Point of Sale (POS), Hardware Station, and Commerce software development kit (SDK) and associated local site configurations (such as modules, data actions, and themes)**.
  For example, if the Commerce Scale Unit is on version 10.0.10, then the Modern POS, Hardware Station, and Commerce storefront must be on version 10.0.10 or earlier (for example, 10.0.9, 10.0.8, etc.).
 
- **Extension packages must be compiled against the same or newer version as the target component to which the extension applies.**
  - For example, if the deployed Commerce Scale Unit is on version 10.0.10 then the corresponding extension packages must be compiled against version 10.0.10 or earlier (for example, 10.0.10, 10.0.9, etc).

### Quality Updates
During quality updates there are no specific versioning requirements that need to be followed for each of the Dynamics 365 Commerce components aside from what is required for service updates.

## Current Supported Versions
The following describes the current supported versions of various Dynamics 365 Commerce components as of **July 1st, 2020**.
| | Latest available release | Latest available component version number | Earliest supported release | Earliest supported component version number |
| --- | :-: | :-: | :-: | :-: |
| Finance and Operations app | 10.0.12 | 10.0.12 | 10.0.9 | 10.0.9 |
| Commerce Scale Unit (cloud-hosted) | 10.0.12 | 9.22 | 10.0.9 | 9.19 |
| Commerce Store Starter Kit (SSK) | 10.0.12 | 9.22 | 10.0.9 | 9.22 |
| Commerce Scale Unit (self-hosted) | 10.0.12 | 9.22 | 10.0.5 | 9.15 |
| Modern POS | 10.0.12 | 9.22 | 10.0.5 | 9.15 |
| Hardware Station | 10.0.12 | 9.22 | 10.0.5 | 9.15 |

## One Version requirements
Dynamics 365 Commerce components follow the same [One Version service updates](https://cloudblogs.microsoft.com/dynamics365/bdm/2018/07/06/modernizing-the-way-we-update-dynamics-365/) that were announced in July 2018 as well as the subsequently published [flexible service updates for Finance and Operations apps](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/06/03/new-flexible-service-updates-for-dynamics-365-for-finance-and-operations/) announced in June 2019. For additional details, see the [One Version service updates FAQ](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/one-version).

### Cloud components
Customers can choose to pause up to three consecutive updates (which correspond to roughly six calendar months) across the following components:
- Dynamics 365 Finance and Operations/Commerce headquarters
- Commerce Scale Unit (cloud-hosted)
- Commerce SDK and associated local site configurations (such as modules, data actions, and themes).

For example, customers who are currently on version 10.0.2 can choose to pause updates to versions 10.0.3, 10.0.4, and 10.0.5 but must then update to version 10.0.6. In this scenario, once 10.0.7 becomes available, version 10.0.2 is no longer supported.

### In-store components
Customers can choose to pause up to seven consecutive updates (which correspond to roughly twelve calendar months) across the following components:
- Commerce Scale Unit (in-store hosted)
- Modern POS
- Hardware Station 

For example, customers who are currently on version 10.0.2 can choose to pause updates to versions 10.0.3 through 10.0.9 but must then update to version 10.0.10. In this scenario, once 10.0.11 becomes available, version 10.0.2 is no longer supported.

## Additional resources

### One Version
For additional details on One Version service updates, see the following articles.
- [One Version service updates FAQ](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/get-started/one-version)
- [Modernizing the way we update Dynamics 365](https://cloudblogs.microsoft.com/dynamics365/bdm/2018/07/06/modernizing-the-way-we-update-dynamics-365/)
- [New flexible service updates for Finance and Operations apps](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/06/03/new-flexible-service-updates-for-dynamics-365-for-finance-and-operations/)

### Component selection
For additional details on selecting the right components to meet your needs, see the following articles.
- [Select an in-store topology](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-in-store-topology)
- [Choose between Modern POS (MPOS) and Cloud POS (CPOS)](https://docs.microsoft.com/en-us/dynamics365/commerce/mpos-or-cpos)

### Servicing instructions
For additional details on how to service individual components described in this topic, see the following articles.
- [Configure and install Commerce Scale Unit](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-store-scale-unit-configuration-installation)
- [Apply updates and extensions to Retail Cloud Scale Unit](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/deployment/update-retail-channel)
- [Configure, install, and active Modern POS (MPOS)](https://docs.microsoft.com/en-us/dynamics365/commerce/retail-modern-pos-device-activation)
- [Configure and install Retail hardware station](https://docs.microsoft.com/en-us/dynamics365/commerce/retail-hardware-station-configuration-installation)
- [Package configurations and deploy them to an online channel](https://docs.microsoft.com/en-us/dynamics365/commerce/e-commerce-extensibility/package-deploy)

### Extensibility and packing
For additional details on serviceability for extensions, see the following article.
- [Create deployable packages](https://docs.microsoft.com/en-us/dynamics365/commerce/dev-itpro/retail-sdk/retail-sdk-packaging)
