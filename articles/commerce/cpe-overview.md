---
# required metadata

title: Dynamics 365 Commerce evaluation environment overview
description: This topic gives an overview of the Microsoft Dynamics 365 Commerce evaluation environment.
author: v-chgri
ms.date: 07/16/2020
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 

ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: josaw
ms.search.validFrom: 2019-12-10
ms.dyn365.ops.version: Release 10.0.5
---

# Dynamics 365 Commerce evaluation environment overview

[!include [banner](includes/banner.md)]

This topic gives an overview of the Microsoft Dynamics 365 Commerce evaluation environment.

> [!NOTE]
> Commerce evaluation environments aren't generally available, and are granted to partners and customers on a per-request basis. For more information, reach out to your Microsoft partner contact.

The Commerce evaluation environment is an optional end-to-end environment of Dynamics 365 Commerce that lets partners and potential customers try out the Commerce product.

Evaluation environments are partially preconfigured to reduce the required post-provisioning steps.

Aside from some minor limitations that don't affect features or functionality, the Commerce evaluation environment provides the complete Commerce experience, and can be used by customers and implementation partners to evaluate the product, provide feedback, and do fit/gap analysis.

## Limitations of the Commerce evaluation environment

Although the Commerce evaluation environment provides the full set of Commerce features and functionality, there are some minor limitations:

- Although the Commerce evaluation environment itself has no geographical limitations, components of the environment, such as the Retail Cloud Scale Unit (RCSU) and e-Commerce applications, should be provisioned only in the United States.
- Use of the Commerce evaluation environment is limited to 30 days from the date when e-Commerce is provisioned.
- The Commerce evaluation environment can be successfully deployed and initialized only in an environment that uses the demo topology, where all components of an environment are deployed on a single cloud-hosted virtual machine (VM). The main limitation of this topology is the number of concurrent users that the environment can support.

## Get started

To provision the Commerce evaluation environment, see [Provision a Commerce evaluation environment](provisioning-guide.md).

## Additional resources

[Provision a Dynamics 365 Commerce evaluation environment](provisioning-guide.md)

[Configure a Dynamics 365 Commerce evaluation environment](cpe-post-provisioning.md)

[Configure BOPIS in a Dynamics 365 Commerce evaluation environment](cpe-bopis.md)

[Configure optional features for a Dynamics 365 Commerce evaluation environment](cpe-optional-features.md)

[Dynamics 365 Commerce evaluation environment FAQ](cpe-faq.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
