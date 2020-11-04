---
# required metadata

title: E-Commerce site overview
description: This topic provides an overview of the Dynamics 365 Commerce e-Commerce site support.
author: bicyclingfool
manager: AnnBe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations, Retail
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: stuharg
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.5

---

# E-Commerce site overview

[!include [banner](includes/banner.md)]

This topic provides an overview of the Dynamics 365 Commerce e-Commerce site support.

This topic explains how e-Commerce online stores are used in Microsoft Dynamics 365 Commerce. It also provides a link to more information about online stores and information about how to set up and configure an e-Commerce site.

## Online store channel
Before you can build your site in Dynamics 365 Commerce, at least one online store channel must be set up, details can be found on the [set up an online channel](channel-setup-online) topic. In Dynamics 365 Commerce, you use an online store channel to establish the products, pricing, languages, payment methods, delivery modes, fulfillment centers, and other aspects of the online experience that should be available to your customers.

Only one online store channel has to be set up before you can get started with Dynamics 365 Commerce. However, a single e-Commerce site can provide the online experience for multiple online stores. For example, if multiple online stores are set up to support different geographical regions, a single set of e-Commerce pages can be used to provide the unique experiences that are defined by each store. For more information about how to configure a site to support multiple online stores, see [Associate an online site with a channel](associate-site-online-store.md).

After an online store is set up, it can be associated with the Dynamics 365 Commerce site that will serve as your online storefront. For more information about online stores and how to set them up, see [Set up online stores](https://docs.microsoft.com/dynamics365/unified-operations/retail/online-stores).

## Deploy a new e-Commerce tenant
During initialization of an e-Commerce site, you will be prompted for a domain name, follow the [configure your domain name](configure-your-domain-name.md) topic for more information.  Follow the steps on the [deploy a new e-Commerce tenant](deploy-ecommerce-site) topic to deploying a new e-Commerce tenant using [Microsoft Dynamics Lifecycle Services (LCS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).  Once the e-Commerce tenant is setup in LCS, it will provide a link to the site builder tool to initialize and configure your e-Commerce site(s).

## Initialize your e-Commerce site
The first launch of the site builder tool will take you to the "Sites" page with two pre-configured sites named "default" and "fabrikam" as shown in the below image.

![e-Commerce site list](media/e-commerce-site-01.png)

## Additional resources

[Create an e-Commerce site](create-ecommerce-site.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Configure your domain name](configure-your-domain-name.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)
