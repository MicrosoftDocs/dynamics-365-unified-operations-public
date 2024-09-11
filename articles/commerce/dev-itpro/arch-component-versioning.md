---
title: Dynamics 365 Commerce component versioning requirements
description: This article provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.
author: Reza-Assadi
ms.date: 03/28/2024
ms.topic: article 
audience: Developer
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: rassadi
ms.search.validFrom: 2020-07-01

---

# Dynamics 365 Commerce component versioning requirements

[!include [banner](../includes/banner.md)]

This article provides an overview of the component versioning requirements and dependencies for all components in the Microsoft Dynamics 365 Commerce ecosystem.

The following illustration shows an overview of Dynamics 365 Commerce components and corresponding versioning requirements and dependencies.

<a href="/dynamics365/commerce/media/commerce-component-versioning.jpg" target="_blank">![Dynamics 365 Commerce Component versioning requirements and dependencies.](../media/commerce-component-versioning.jpg)</a>

## Component dependencies

### Service updates

To ensure compatibility between all Commerce components that are serviced and deployed by customers and partners, you must follow several versioning dependencies during servicing updates. The following list describes all these dependencies.

- ** Commerce Scale Unit (both cloud and self-hosted) must be on one of the serviceable releases and it has to be same as F&O app release or lower but must always be serviceable. **

- 
    EXPAND here with examples of serviceable and non-serviceable 

   For example, if Commerce headquarters and finance and operations apps are on version 10.0.30, Commerce Scale Unit must be on version 10.0.30 or earlier (for example, 10.0.29 or 10.0.28).

- ** Store Commerce app, Hardware Station, and the Commerce software development kit (SDK) and associated local site configurations (such as modules, data actions, and themes) must be on one of the serviceable releases and it has to be same as Commerce Scale Unit release or lower but must always be serviceable. **

    For example, if Commerce Scale Unit is on version 10.0.30, Store Commerce app, Hardware Station, and the Commerce storefront must be on version 10.0.30 or earlier (for example, 10.0.29 or 10.0.28).

- **Extension packages must be compiled against the same version as, or an earlier version than, the target component that the extension applies to.**

    For example, if the deployed Commerce Scale Unit is on version 10.0.30, the corresponding extension packages must be compiled against version 10.0.30 or earlier (for example, 10.0.29 or 10.0.28).

### Quality updates

During quality updates, no specific versioning requirements must be followed for each Commerce component, besides what is required for service updates.

## Current supported versions

The following table describes the current supported versions refer link here - https://learn.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/get-started/public-preview-releases.


## One Version requirements

Commerce components follow the One Version service updates. For more information, see [One Version service updates FAQ](../../fin-ops-core/dev-itpro/get-started/one-version.md).

### Cloud components

For more information about how to pause service updates for Cloud components listed below, see [Pause service updates through Lifecycle Services)](../../dev-itpro/lifecycle-services/pause-service-updates.md).

- Commerce headquarters and finance and operations apps
- Commerce Scale Unit (cloud-hosted)
- Commerce SDK and associated local site configurations (such as modules, data actions, and themes)

### In-store components

Following In-store components need to be within serviceable releases, as shared above, for it to be supported 

- Store Commerce app for Windows, Android, and iOS
- Sealed Commerce Scale Unit (self-hosted)
- Sealed Hardware station

[!note] Legacy in-store components are NOT supported

- Commerce Scale Unit (self-hosted)
- Modern point of sale (MPOS) and hybrid apps
- Hardware station (Legacy)
- Retail SDK

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

