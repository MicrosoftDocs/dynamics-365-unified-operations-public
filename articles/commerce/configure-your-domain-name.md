---
# required metadata

title: Configure a domain name
description: This article describes how to configure a domain name for your Dynamics 365 e-Commerce site. 
author: psimolin
manager: AnnBe
ms.date: 09/06/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Enduser
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: psimolin
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5
[
---

# Configure a domain name

[!include [banner](includes/banner.md)]

[!include [banner](includes/preview-banner.md)]

This article describes how to configure a domain name for your Dynamics 365 for Commerce e-Commerce site. 

### Add domains when initializing e-Commerce

To associate domains with your e-Commerce environment, initialize e-Commerce as described in [Deploy an e-Commerce site](deploy-e-commerce-site.md). When you are in the process of initializing, you are asked to provide information that will be used for provisioning your e-Commerce environment. At that point, add all the domains you plan to use with this environment in the **Supported host names** field. That way, they are configured in all the required e-Commerce components and are ready to used when you switch traffic from your content delivery network (CDN) or web server to point to the e-Commerce front ends.

### Add domains after initialization

If you need to associate new domains with your e-Commerce environment after initialization, you will need to open a service request.
