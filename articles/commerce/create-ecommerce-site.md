---
# required metadata

title: Create an e-Commerce site
description: This topic describes the steps and information required to create a new e-Commerce site in Dynamics 365 Commerce site builder.
author: bicyclingfool
manager: AnnBe
ms.date: 01/23/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
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
ms.search.industry:
ms.author: stuharg
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: 10.0.5

---

# Create an e-Commerce site


[!include [banner](includes/banner.md)]

This topic describes the steps and information required to create a new e-Commerce site in Dynamics 365 Commerce site builder.

Before you can start developing your e-Commerce site, you must first establish a new site in site builder. 


To start to develop your e-Commerce site, you must first establish a new site in the site authoring environment. Before you can create a new site, at least one online store must be created in Commerce. 


## Set up your site

To set up your site, do the following.

1. Open the site builder environment. You can find a link to site builder in Microsoft Lifecycle Services (LCS) in the environment features page for Commerce.
1. On the home page for the site authoring environment, select **New site**.
1. In the **New site** dialog box, provide the following information.

| Field                               | Description |
|-------------------------------------|-------------|
| Site name                           | Enter the display name that should be used for your site in the site authoring environment. This name is visible only in the authoring environment and will not be shown to customers. |
| Site administrator's security group | Specify the Microsoft Azure Active Directory (Azure AD) security group that manages users who have the site administrator role in this site. |
| Default channel (operating unit number) | Select the online store that this site will serve as the web storefront for. If you want your e-Commerce site to support multiple online stores, you must associate the stores with your site in **Site settings** after the site is set up. |
| Default language                            | Specify the default language for this online store and market. An online store can support multiple languages. If you want to support multiple languages for this online store or another online store, you can configure that support in **Site settings** after the site is set up.  |
| Domain                              | Select a domain name that will serve as the domain for this online store. If you haven't configured any domains in LCS, you can leave this field blank. After your domain is configured in LCS, you must add it to your online store in **Site settings**.  |
| Path                              | When your site supports more than one language for a given domain name, use the path field to create a unique site URL for that domain and language combination. If the language you specified in the **Default language** field is the only language you will support for this domain, or will continue to be the default language after you have localized your site into additional languages, we recommend that you leave this field empty. |


After your site is created, you can verify that it is associated with your online store by selecting the **Products** tab. You should see the assortment of products that has been allocated to the online store. You can also use the drop-down menu in the upper left of the page to access the allocated products by category.

## Additional resources

[Configure your domain name](configure-your-domain-name.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Manage robots.txt files](manage-robots-txt-files.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)
