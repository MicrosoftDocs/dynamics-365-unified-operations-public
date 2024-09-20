---
title: Dynamics 365 Commerce component versioning requirements
description: This article provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.
author: Reza-Assadi
ms.date: 09/20/2024
ms.topic: overview 
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2020-07-01
ms.custom: 
  - bap-template
---

# Dynamics 365 Commerce component versioning requirements

[!include [banner](../includes/banner.md)]

This article provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.

The following illustration shows an overview of Dynamics 365 Commerce components and corresponding versioning requirements and dependencies.

![Dynamics 365 Commerce Component versioning requirements and dependencies.](./media/CommerceComponentVersioning_Sep_2024.png)

## Component dependencies

### Service updates

To ensure compatibility between all Commerce components that are serviced and deployed by customers and partners, you must follow several versioning dependencies during servicing updates. The following list describes all these dependencies.

- **Commerce Scale Unit (CSU), whether cloud or self-hosted, must always be on a serviceable release version number that is either the same as or lower than the finance and operations apps release. For information on the current supported versions, see [Service update availability](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)**.

  For example, if today's date is September 20, 2024 the following releases are serviceable:
    - *Release Winter (GA: January 15, 2024, End of service: August 15, 2024)*
    - *Release Spring (GA: March 15, 2024, End of service: November 15, 2024)*
    - *Release Summer (GA: June 15, 2024, End of service: February 15, 2025)*
    - *Release Autumn (GA: September 15, 2024, End of service: May 15, 2025)*

  Of the releases listed, as of September 20, 2024, the *Release Winter* version reached end-of-service, which means that the CSU version must be at least from the *Release Spring* version (the earliest serviceable release). In other words, if Commerce headquarters and finance and operations apps are on the *Release Autumn* version, then the CSU must run a release version that is still serviceable, which means either the *Release Autumn*, *Release Summer*, or *Release Spring* release versions but not the *Release Winter* version because it reached end-of-service. 

- **The Store Commerce app, Hardware Station, and the Commerce software development kit (SDK), along with associated local site configurations (including modules, data actions, and themes), must be on a serviceable release. This release version number should be the same as or lower than the Commerce Scale Unit release version, but it must always be serviceable. For information on the current supported versions, see [Service update availability](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)**.

  For example, if today's date is September 20, 2024 the following releases are serviceable:
    - *Release Winter (GA: January 15, 2024, End of service: August 15, 2024)*
    - *Release Spring (GA: March 15, 2024, End of service: November 15, 2024)*
    - *Release Summer (GA: June 15, 2024, End of service: February 15, 2025)*
    - *Release Autumn (GA: September 15, 2024, End of service: May 15, 2025)*

  Of the releases listed, as of September 20, 2024, the *Release Winter* version reached end-of-service, which means that the Store Commerce app, Hardware Station, and Commerce SDK versions must run a release version that is still serviceable, which means either the *Release Autumn*, *Release Summer*, or *Release Spring* release versions but not the *Release Winter* version because it reached end-of-service. In other words, if the CSU is on the *Release Autumn* version, then the Store Commerce app, Hardware Station, and Commerce SDK versions must be either the serviceable *Release Autumn*, *Release Summer*, or *Release Spring* versions, but not the *Release Winter* version because it reached end-of-service.

- **Extension packages must be compiled against the same version as, or an earlier serviceable version than, the target component to which the extension applies. For information on the current supported versions, see [Service update availability](/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases)**.

  For example, if today's date is September 20, 2024 the following releases are serviceable:
     - *Release Winter (GA: January 15, 2024, End of service: August 15, 2024)*
     - *Release Spring (GA: March 15, 2024, End of service: November 15, 2024)*
     - *Release Summer (GA: June 15, 2024, End of service: February 15, 2025)*
     - *Release Autumn (GA: September 15, 2024, End of service: May 15, 2025)*

  Of the releases listed, as of September 20, 2024, the *Release Winter* version reached end-of-service, which means that extension packages must be on the *Release Autumn*, *Release Summer*, or *Release Spring* versions,  but not the *Release Winter* version because it reached end-of-service. In other words, if the target component is on the *Release Autumn* version, the corresponding extension packages must be compiled against one of the serviceable versions (*Release Autumn*, *Release Summer*, or *Release Spring*) but not the *Release Winter* version because it reached end-of-service.

### Quality updates

During quality updates, no specific versioning requirements must be followed for each Commerce component besides what is required for service updates.

## One Version requirements

Commerce components follow the One Version service updates. For more information, see [One Version service updates FAQ](../../fin-ops-core/dev-itpro/get-started/one-version.md).

### Cloud components

For more information about how to pause service updates for the following cloud components, see [Pause service updates through Lifecycle Services)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

- Commerce headquarters and finance and operations apps.
- CSU (cloud-hosted).
- Commerce SDK and associated local site configurations (such as modules, data actions, and themes).

### In-store components

The following in-store components need to be running serviceable release versions to be supported.

- Store Commerce app for Windows, Android, and iOS.
- Sealed CSU (self-hosted).
- Sealed Hardware station.

> [!NOTE]
> The following legacy in-store components aren't supported:
> - Commerce Scale Unit (self-hosted)
> - Modern Point of Sale (MPOS) and hybrid apps
> - Hardware station (Legacy)
> - Retail SDK

## Additional resources

### Component selection

For more information about how to select the correct components to meet your needs, see the following articles:

- [Select an in-store topology](retail-in-store-topology.md)
- [Choose between Store Commerce app and Store Commerce for web](MPOS-or-CPOS.md)

### Servicing instructions

For more information about how to service individual components that are described in this article, see the following articles:

- [Configure and install Commerce Scale Unit](retail-store-scale-unit-configuration-installation.md)
- [Apply updates and extensions to Retail Cloud Scale Unit](../../fin-ops-core/dev-itpro/deployment/update-retail-channel.md)
- [Configure and install Retail hardware station](retail-hardware-station-configuration-installation.md)
- [Package configurations and deploy them to an online channel](../e-commerce-extensibility/package-deploy.md)
<!-- [Configure, install, and activate the Store Commerce app](retail-modern-pos-device-activation.md)-->

### Extensibility and packing

For more information about serviceability for extensions, see [Create deployable packages](retail-sdk/retail-sdk-packaging.md).


[!INCLUDE[footer-include](../../includes/footer-banner.md)]

