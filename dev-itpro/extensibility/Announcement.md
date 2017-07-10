---

# required metadata

title: Introduction
description: 
author: Frank Dahl, Dave Froslie
manager: AnnBe
ms.date: 07/10/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

---

# Announcing application extensibility plans

[!include[banner](../includes/banner.md)]

Reducing implementation and upgrade effort is a major initiative for the Microsoft Dynamics 365 for Operations development team. The benefits of this initiative are to enable customers to quickly take advantage of new innovations from Microsoft and their partners, reduce the total cost of ownership, and improve quality.

One of the major costs of upgrades is moving customizations forward to the next release. Customizations that were done using the overlayering capabilities in Dynamics 365 for Operations require code upgrade, re-compile time, and extensive testing. Oftentimes customers end up stranded on old release because of the high cost of moving their overlayered code forward.

There are also costs required for manually applying hot fixes. The ability to seamlessly apply hot fixes in a binary format is something we’re striving for in the future.

There’s also the ‘version hell’ that partners constantly battle.  Reducing the size of the support matrix driven by combinations of Microsoft product versions and partner solution versions would be a significant benefit.  Supporting many code branches is a large tax on any engineering team.

One solution that addresses many of these challenges is to move away from the intrusive customization approach of overlayering, and use the extension capabilities in Dynamics 365 for Operations. The product platform models, AppPlatform and AppFoundation, already require the use of extensions for customizations as they were sealed for overlayering in Fall 2016 in platform update 3. 

At the Dynamics 365 Technical Conference held on March 13-15, 2017, we announced the next steps in this journey, which is to move from overlayering to extensions. The current roadmap for the journey is shown below.

![alt text](https://community.dynamics.com/cfs-file/__key/communityserver-blogs-components-weblogfiles/00-00-00-12-72/AppExtensibilityRoadmap.jpg)

Note, a soft seal results in a compiler warning upon overlayering. A hard seal results in a compiler error upon overlayering. 

The Modern support policy provides three years of support for a release.  Given this, overlayered code will continue to be supported on the Fall 2017 release  for three years. However, this code will not be moved forward to subsequent product releases until the overlayered code is moved to extensions.  

We recognize there is a substantial amount of work for Microsoft, partners, and customers to accomplish this goal. Workshops, office hours, wiki articles, and more are planned for training and collaboration in this ecosystem. Internally, we’ve already ramped up investment to build more extensibility features in both the core platform and the application. We’re working closely with partners with applications on AppSource to define patterns and unblock them as they migrate to extensions.

The benefits of reducing upgrade friction and enabling innovation uptake will be worth the effort to remove overlayering.
