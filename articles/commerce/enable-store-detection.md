---
# required metadata

title: Enable location-based store detection
description: This topic describes how to turn on location-based store detection for your Dynamics 365 Commerce site.
author: brianshook
manager: annbe
ms.date: 07/02/2020
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
ms.author: brshoo
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Enable location-based store detection


[!include [banner](includes/banner.md)]

This topic describes how to turn on location-based store detection for your Dynamics 365 Commerce site.

## Overview

Location-based store detection in Commerce lets you provide relevant site content to customers, based on their location. When location-based store detection is turned on, the Commerce rendering service uses the country/region information from the IP address of the customer's web browser to direct the customer to the best geographical site configuration that is available.

## Privacy notice

If you turn on the location-based store detection feature, information from the customer's browser is sent to a Microsoft location service. This information is then used to provide the customer content that is relevant to his or her location. Both the information that is sent from the customer's browser and the location-based information that is returned to the customer are subject to privacy and cookie compliance policies.

## Turn on location-based store detection

To turn on location-based store detection in Commerce, follow these steps.

1. In the authoring tool, go to your site.
1. In the navigation pane on the left, select **Site Management**.
1. Select **Site Settings**.
1. Set the **Enable location based store detection** option to **On**.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Create an e-Commerce site](create-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Upload URL redirects in bulk](upload-bulk-redirects.md)

[Set up a B2C tenant in Commerce](set-up-B2C-tenant.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Configure multiple B2C tenants in a Commerce environment](configure-multi-B2C-tenants.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)
