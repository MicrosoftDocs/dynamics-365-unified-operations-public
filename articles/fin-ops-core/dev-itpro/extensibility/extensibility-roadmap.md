---
title: Application extensibility roadmap
description: Learn about the requirements and schedule for converting code from overlayering-based to extension-based, including additional information about customizations.
author: FrankDahl
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-10
ms.dyn365.ops.version: Platform update 1
ms.assetid: 
---

# Application extensibility roadmap

[!include [banner](../includes/banner.md)]

Reducing implementation and upgrade effort is a major initiative for the development team. The benefits of this initiative are to enable you to quickly take advantage of new innovations from Microsoft and your partners, reduce the total cost of ownership, and improve quality. A major part of this initiative is to change the customization approach for the product. In Dynamics AX 2012, several extension capabilities were added to the product. For example, the ability to do event-based customization by using methods that pre-and post-events was introduced. Extension capabilities have continued to grow in the evolution to the new application.  

Extension-based customizations have several advantages over the legacy approach of overlayering-based customizations, especially when it comes to reducing implementation and upgrade effort.  

+ Overlayering-based customizations require code upgrade, recompile time, and extensive testing. This requirement limits the ability to seamlessly apply hot fixes. These costs can be an inhibitor for customers to upgrade to newer versions containing innovations from Microsoft and partners.  
+ Extension-based customizations also improve the development experience. Models containing overlayered customizations must be in the same package as the base objects. This requirement results in longer compile cycles and larger package distributions. Extensions are also much easier to unit test in isolation from the base object.  
+ Reducing upgrade costs through extension-based customizations reduces the support matrix for partners as fewer release combinations need to be supported.

For these reasons, we gradually sealed the product models so they only support extension-based customizations. **AppPlatform** and **AppFoundation** were the first models. We sealed these models for overlayering in Platform update 3 (November 2016). We now provide binary updates to these models on a monthly basis, achieving our goals of reducing upgrade cost and delivering innovation to our customers at a faster cadence.

With Microsoft Dynamics 365 for Finance and Operations release 8.0, all product models are sealed. Now, only extension-based customizations are supported.

The following illustration shows the roadmap that we followed as we moved to extensions, away from overlayering.

![Extensibility roadmap.](media/extensibility-roadmap.jpg)

> [!NOTE]
> A soft seal results in a compiler warning upon overlayering. A hard seal results in a compiler error upon overlayering.

The modern support policy provides three years of support for a release. Given this policy, overlayered code is supported for three years starting November 2017 on the Microsoft Dynamics 365 for Finance and Operations, Enterprise edition 7.3 release. However, the product doesn't move this code forward to subsequent product releases until the overlayered code is moved to extensions.  

There's a substantial amount of work for Microsoft, partners, and customers to accomplish this goal. Workshops, office hours, Help topics, and additional resources are available for training and collaboration in this ecosystem. Internally, we're ready to build more extensibility features in both the core platform and the application. We're working closely with partners with applications on Marketplace to define patterns as they migrate to extensions.

The benefits of reducing upgrade friction and enabling innovation uptake are worth the effort to remove overlayering.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
