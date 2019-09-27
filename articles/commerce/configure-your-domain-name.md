---
# required metadata

title: Configure a domain name
description: This topic explains how to configure a domain name for a Microsoft Dynamics 365 e-Commerce site.
author: psimolin
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Configure a domain name

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic explains how to configure a domain name for a Microsoft Dynamics 365 e-Commerce site. 

## Add domains during e-Commerce initialization

To associate domains with your e-Commerce environment, initialize e-Commerce as described in [Deploy an e-Commerce site](deploy-ecommerce-site.md). During initialization, you're asked to provide information that will be used to provision your e-Commerce environment. In the **Supported host names** field, add all the domains that you plan to use with this environment. Multiple domains should be separated with semi-colon. In this way, the domains are configured in all the required e-Commerce components, and they are ready to be used when you switch traffic from your content delivery network (CDN) or web server and point it to the e-Commerce front ends.

## Add domains after e-Commerce initialization

To associate new domains with your e-Commerce environment after e-Commerce initialization, you must submit a service request.
