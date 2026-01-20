---
title: Configure your domain name
description: Learn how to configure a domain name for a Microsoft Dynamics 365 e-commerce site.
author: josaw1
ms.date: 01/20/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Configure your domain name


[!include [banner](includes/banner.md)]

This article explains how to configure a domain name for a Microsoft Dynamics 365 e-commerce site. 

## Add domains during e-commerce initialization

To associate domains with your Dynamics 365 Commerce e-commerce environment, initialize e-commerce as described in [Deploy a new e-commerce tenant](deploy-ecommerce-site.md). During initialization, provide information to provision your e-commerce environment. In the **Supported host names** field, add all the domains that you plan to use with this environment. Separate multiple domains with a semicolon. This step configures the domains in all the required Commerce components. The domains are ready to use when you switch traffic from your content delivery network (CDN) or web server and point it to the e-commerce front ends.

## Add domains after e-commerce initialization

To associate new domains with your e-commerce environment after e-commerce initialization, follow the instructions in [Add supported host names](domains-commerce.md#add-supported-host-names).

## Additional resources

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](dev-itpro/upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](dev-itpro/set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
