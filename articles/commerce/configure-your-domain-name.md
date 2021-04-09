---
# required metadata

title: Configure your domain name
description: This topic explains how to configure a domain name for a Microsoft Dynamics 365 e-commerce site.
author: psimolin
ms.date: 07/02/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: Retail
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Configure your domain name


[!include [banner](includes/banner.md)]

This topic explains how to configure a domain name for a Microsoft Dynamics 365 e-commerce site. 

## Add domains during e-commerce initialization

To associate domains with your Dynamics 365 Commerce e-commerce environment, initialize e-commerce as described in [Deploy a new e-commerce tenant](deploy-ecommerce-site.md). During initialization, you're asked to provide information that will be used to provision your e-commerce environment. In the **Supported host names** field, add all the domains that you plan to use with this environment. Multiple domains should be separated with semi-colon. In this way, the domains are configured in all the required Commerce components, and they are ready to be used when you switch traffic from your content delivery network (CDN) or web server and point it to the e-commerce front ends.

## Add domains after e-commerce initialization

To associate new domains with your e-commerce environment after e-commerce initialization, you must submit a service request.

## Additional resources

[Deploy a new e-commerce tenant](deploy-ecommerce-site.md)

[Create an e-commerce site](create-ecommerce-site.md)

[Associate a Dynamics 365 Commerce site with an online channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]