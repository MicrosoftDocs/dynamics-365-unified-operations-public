---
# required metadata

title: Dynamics 365 Commerce component versioning requirements
description: This topic provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.
author: rezaassadi
manager: AnnBe
ms.date: 10/16/2020
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

<a href="https://docs.microsoft.com/en-us/dynamics365/commerce/media/commerce-component-versioning.jpg" target="_blank">![Dynamics 365 Commerce Component versioning requirements and dependencies](./media/commerce-component-versioning.jpg)</a>

## Component dependencies

### Service updates

To ensure compatibility between all Commerce components that are serviced and deployed by customers and partners, you must follow several versioning dependencies during servicing updates. The following list describes all these dependencies.

- **Commerce headquarters and Finance and Operations apps must be on the same version as, or a newer version than, Commerce Scale Unit (both cloud and self-hosted).**

    For example, if Commerce headquarters and Finance and Operations apps are on version 10.0.15, Commerce Scale Unit must be on version 10.0.15 or earlier (for example, 10.0.14 or 10.0.13).

- **Commerce Scale Unit must be on the same version as, or a newer version than, Modern Point of Sale (POS), Hardware Station, and the Commerce software development kit (SDK) and associated local site configurations (such as modules, data actions, and themes).**

    For example, if Commerce Scale Unit is on version 10.0.15, Modern POS, Hardware Station, and the Commerce storefront must be on version 10.0.15 or earlier (for example, 10.0.14 or 10.0.13).

- **Extension packages must be compiled against the same version as, or a newer version than, the target component that the extension applies to.**

    For example, if the deployed Commerce Scale Unit is on version 10.0.15, the corresponding extension packages must be compiled against version 10.0.15 or earlier (for example, 10.0.15 or 10.0.14).

### Quality updates

During quality updates, no specific versioning requirements must be followed for each Commerce component, besides what is required for service updates.

## Current supported versions

The following table describes the current supported versions of various Commerce components as of **December 4, 2020**.

| Component | Latest available release (first release available in Sandbox) | Latest available component version number (first release available in Sandbox) | Earliest supported release | Earliest supported component version number |
|---|---|---|---|---|
| Finance and Operations apps | 10.0.15 | 10.0.15 | 10.0.11 | 10.0.11 |
| Commerce Scale Unit (cloud-hosted) | 10.0.15 | 9.25 | 10.0.11 | 9.21 |
| Commerce module library | 10.0.15 | 9.25 | 10.0.11 | 9.21 |
| Commerce Scale Unit (self-hosted) | 10.0.15 | 9.25 | 10.0.7 | 9.17 |
| Modern POS | 10.0.15 | 9.25 | 10.0.7 | 9.17 |
| Hardware Station | 10.0.15 | 9.25 | 10.0.7 | 9.17 |

## One Version requirements

Commerce components follow the same [One Version service updates](https://cloudblogs.microsoft.com/dynamics365/bdm/2018/07/06/modernizing-the-way-we-update-dynamics-365/) that were announced in July 2018, and also the subsequently published [flexible service updates for Finance and Operations apps](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/06/03/new-flexible-service-updates-for-dynamics-365-for-finance-and-operations/) that were announced in June 2019. For more information, see [One Version service updates FAQ](../fin-ops-core/fin-ops/get-started/one-version.md).

### Cloud components

Customers can pause up to three consecutive updates across the following components. (Three updates correspond to approximately six calendar months.)

- Commerce headquarters and Finance and Operations apps
- Commerce Scale Unit (cloud-hosted)
- Commerce SDK and associated local site configurations (such as modules, data actions, and themes)

For example, customers who are currently on version 10.0.2 can pause updates to versions 10.0.3, 10.0.4, and 10.0.5. However, they must then update to version 10.0.6. In this scenario, after version 10.0.7 becomes available, version 10.0.2 is no longer supported.

### In-store components

Customers can pause up to seven consecutive updates across the following components. (Seven updates correspond to approximately twelve calendar months.)

- Commerce Scale Unit (in-store hosted)
- Modern POS
- Hardware Station

For example, customers who are currently on version 10.0.2 can pause updates to versions 10.0.3 through 10.0.9. However, they must then update to version 10.0.10. In this scenario, after version 10.0.11 becomes available, version 10.0.2 is no longer supported.

## Additional resources

### One Version service updates

For more information about One Version service updates, see the following resources:

- [One Version service updates FAQ](../fin-ops-core/fin-ops/get-started/one-version.md)
- [Modernizing the way we update Dynamics 365](https://cloudblogs.microsoft.com/dynamics365/bdm/2018/07/06/modernizing-the-way-we-update-dynamics-365/)
- [New flexible service updates for Finance and Operations apps](https://cloudblogs.microsoft.com/dynamics365/bdm/2019/06/03/new-flexible-service-updates-for-dynamics-365-for-finance-and-operations/)

### Component selection

For more information about how to select the correct components to meet your needs, see the following topics:

- [Select an in-store topology](./dev-itpro/retail-in-store-topology.md)
- [Choose between Modern POS (MPOS) and Cloud POS (CPOS)](mpos-or-cpos.md)

### Servicing instructions

For more information about how to service individual components that are described in this topic, see the following topics:

- [Configure and install Commerce Scale Unit](./dev-itpro/retail-store-scale-unit-configuration-installation.md)
- [Apply updates and extensions to Retail Cloud Scale Unit](../fin-ops-core/dev-itpro/deployment/update-retail-channel.md)
- [Configure, install, and active Modern POS (MPOS)](retail-modern-pos-device-activation.md)
- [Configure and install Retail hardware station](retail-hardware-station-configuration-installation.md)
- [Package configurations and deploy them to an online channel](./e-commerce-extensibility/package-deploy.md)

### Extensibility and packing

For more information about serviceability for extensions, see [Create deployable packages](./dev-itpro/retail-sdk/retail-sdk-packaging.md).
