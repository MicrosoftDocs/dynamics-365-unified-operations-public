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

A major part of this initiative is to change the customization approach for the product.  In AX 2012, several extension capabilities were added to the product.  For example, the ability to do event based customization using method pre and post events was introduced.  Extension capabilities have continued to grow in the product in the evolution to Dynamics 365 for Operations.  

Extension based customizations have several advantages over the legacy approach of overlayer based customizations, especially when it comes to reducing implementation and upgrade effort.  Overlayer based customizations require code upgrade, re-compile time, and extensive testing.  This limits our ability to seamlessly apply hot fixes.  These costs can be an inhibitor for customers to upgrade to newer versions containing innovations from Microsoft and partners.  

Extension based customizations also improve the development experience.  Models containing overlayered customizations must be in the same package as the base objects.  This results in longer compile cycles and much larger package distributions.  Extensions are also much easier to unit test in isolation from the base object.  

Finally, reducing upgrade costs through extension based customizations reduces the support matrix for partners as fewer release combinations will need to be supported.

All of these reasons were behind our decision to require the product platform models, AppPlatform and AppFoundation, to use extension based customizations. These models were sealed for overlayering in platform update 3 delivered in Fall 2016.  This has enabled us to provide binary updates to these models on a monthly basis, achieving our goals of reducing upgrade cost and delivering innovation to our customers at a faster cadence. 

At the Dynamics 365 Technical Conference held on March 13-15, 2017, we announced the next steps in this journey, which is to move from overlayering to extensions. The current roadmap for the journey is shown below.

![alt text](https://community.dynamics.com/cfs-file/__key/communityserver-blogs-components-weblogfiles/00-00-00-12-72/AppExtensibilityRoadmap.jpg)

Note, a soft seal results in a compiler warning upon overlayering. A hard seal results in a compiler error upon overlayering. 

The Modern support policy provides three years of support for a release.  Given this, overlayered code will continue to be supported on the Fall 2017 release  for three years. However, this code will not be moved forward to subsequent product releases until the overlayered code is moved to extensions.  

We recognize there is a substantial amount of work for Microsoft, partners, and customers to accomplish this goal. Workshops, office hours, wiki articles, and more are planned for training and collaboration in this ecosystem. Internally, we’ve already ramped up investment to build more extensibility features in both the core platform and the application. We’re working closely with partners with applications on AppSource to define patterns and unblock them as they migrate to extensions.

The benefits of reducing upgrade friction and enabling innovation uptake will be worth the effort to remove overlayering.
