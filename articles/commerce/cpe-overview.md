---
# required metadata

title: Dynamics 365 Commerce preview environment overview
description: This topic gives an overview of the Microsoft Dynamics 365 Commerce preview environment.
author: v-chgri
manager: annbe
ms.date: 12/10/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Operations, Retail, Core
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: v-chgri
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Dynamics 365 Commerce preview environment overview


[!include [banner](includes/banner.md)]

This topic gives an overview of the Microsoft Dynamics 365 Commerce preview environment.

## Overview

The Commerce preview environment is an optional end-to-end preview environment of Dynamics 365 Commerce that lets potential customers try out the Commerce product before its general release to the public.

Aside from some minor limitations that don't affect features or functionality, the Commerce preview environment provides the complete Commerce experience, and can be used by customers and implementation partners to evaluate the product, provide feedback, and do fit/gap analysis.

## Limitations of the Commerce preview environment

Although the Commerce preview environment provides the full set of Commerce features and functionality, there are some minor limitations:

- Although the Commerce preview environment itself has no geographical limitations, components of the environment, such as the Retail Cloud Scale Unit (RCSU) and e-Commerce applications, can be provisioned only in the United States.
- Use of the Commerce preview environment is limited to 30 days from the date when e-Commerce is provisioned.
- The Commerce preview environment can be successfully deployed and initialized only in an environment that uses the demo topology, where all components of an environment are deployed in a single virtual machine (VM). The main limitation of this OneBox VM topology is the number of concurrent users that the preview environment can support.
- The Commerce preview environment can be evaluated only until the general availability (GA) of the Commerce product. New demo environments will be available after GA.

## Get started

To provision the Commerce preview environment, see [Provision a Commerce preview environment](provisioning-guide.md).

## Additional resources

[Provision a Dynamics 365 Commerce preview environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce preview environment](cpe-post-provisioning.md)

[Configure optional features for a Dynamics 365 Commerce preview environment](cpe-optional-features.md)

[Dynamics 365 Commerce preview environment FAQ](cpe-faq.md)
