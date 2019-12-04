---
# required metadata

title: Commerce preview environment overview
description: This topic gives an overview of the Microsoft Dynamics 365 Commerce preview environment.
author: v-chgri
manager: annbe
ms.date: 12/02/2019
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
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
---

# Commerce preview environment overview

[!include [banner](includes/preview-banner.md)]
[!include [banner](includes/banner.md)]

This topic gives an overview of the Microsoft Dynamics 36 Commerce preview environment.

## Overview

The Microsoft Dynamics 365 Commerce preview environment is an optional end-to-end preview environment of Dynamics 365 Commerce that allows potential customers to try out the Commerce product before its general release to the public. 

The Commerce preview environment provides the complete Commerce experience with some minor limitations that don't impact features or functionality, and can be used by customers and implementation partners to evaluate the product, provide feedback, and do fit/gap analysis.

## Commerce preview environment limitations

Although the Commerce preview environment provides the full features and functionality of Dynamics 365 Commerce, there are some minor limitations as follows:

- Although the Commerce preview environment itself has no geographical limitation, components of the environment such as the Retail Cloud Scale Unit (RCSU) and e-Commerce applications can only be provisioned in the United States.
- Use of the Commerce preview environment is time-limited to 30 days from the provisioning of e-Commerce.
- The Commerce preview environment can only be successfully deployed and initialized on an environment that uses the demo topology, where all components of an environment are deployed in a single virtual machine (VM). The main limitation of this OneBox VM topology is the number of concurrent users that the preview environment can support.
- The Commerce preview environment can only be evaluated until the general availability (GA) of the Dynamics 365 Commerce product. New demo environments will be available after GA.

## Get started

To get started provisioning the Commerce preview environment, see [Provision a Commerce preview environment](provisioning-guide.md).

## Additional resources

[Provision a Commerce preview environment](provisioning-guide.md)

[Configure a Commerce preview environment](cpe-post-provisioning.md)

[Configure Commerce preview environment optional features](cpe-optional-features.md)

[Commerce preview environment FAQ](cpe-faq.md)

