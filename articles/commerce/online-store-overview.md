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

This topic explains how e-Commerce online stores are used in Microsoft Dynamics 365 Commerce. It also provides a link to more information about online stores and information about how to set up and configure an e-Commerce site.  This topic does not cover everything needed to setup a production e-Commerce site, but covers many of the basics, more advanced topics can be found within the e-Commerce documention table of contents.

## Online store channel
Before you can build your site in Dynamics 365 Commerce, at least one online store channel must be set up, details can be found on the [set up an online channel](channel-setup-online) topic. 

In Dynamics 365 Commerce, you use an online store channel to establish the products, pricing, languages, payment methods, delivery modes, fulfillment centers, and other aspects of the online experience that should be available to your customers.

Only one online store channel has to be set up before you can get started with Dynamics 365 Commerce. However, a single e-Commerce site can provide the online experience for multiple online stores. For example, if multiple online stores are set up to support different geographical regions, a single set of e-Commerce pages can be used to provide the unique experiences that are defined by each store. For more information about how to configure a site to support multiple online stores, see [Associate an online site with a channel](associate-site-online-store.md).

After an online store is set up, it can be associated with the Dynamics 365 Commerce site that will serve as your online storefront. For more information about online stores and how to set them up, see [Set up online stores](https://docs.microsoft.com/dynamics365/unified-operations/retail/online-stores).

## Deploy a new e-Commerce tenant
During initialization of an e-Commerce site, you will be prompted for a domain name, follow the [configure your domain name](configure-your-domain-name.md), and [domains in Dynamics 365 Commerce](domains-commerce.md) topic for more information.  Follow the steps on the [deploy a new e-Commerce tenant](deploy-ecommerce-site) topic to deploy a new e-Commerce tenant using [Microsoft Dynamics Lifecycle Services (LCS)](https://docs.microsoft.com/en-us/dynamics365/unified-operations/dev-itpro/lifecycle-services/lcs-user-guide).  Once the e-Commerce tenant is setup in LCS, it will provide a link to the site builder tool to initialize and configure your e-Commerce site(s).

## Initialize your e-Commerce site
Launching the site builder tool from LCS will take you to the "Sites" page with two pre-configured sites named "default" and "fabrikam" as shown in the below image.

![e-Commerce site list](media/e-commerce-site-01.png)

Selecting one of the sites will prompt you to select a domain name, a default online store channel, a supported language for the selected channel and a path.  If only one channel is used, the path can be left empty.  More online store channels or languages can be configured later within the site builder, each additional one will require a unique path.  For example if you have two online channels associated with a single site and the site domain name is www.fabrikam.com, the path for one channel can be the default with no path, ie: "https://www.fabrikam.com" and the second channel could be set to a new path such as "site2" which would have a URL: "https://www.fabrikam.com/site2".  The below images shows an example site initiatlization dialog box.

![e-Commerce site initialization](media/e-commerce-site-02.png)

The "Sites" page also has a "New site" button that will bring up a similar dialog box to create a new site, however new sites will be blank and not include the same default templates, fragments, pages and images that the "default" and "fabrikam" sites come with.  A support ticket can be opened to have a copy of default content added to a new blank site if required.  For more information see the [create an e-Commerce site](create-ecommerce-site.md) topic.

Once the site is initialized, it will load the site page with the site builder tool as shown below.

![e-Commerce site initialization](media/e-commerce-site-03.png)

## Modifying or adding additional online store channels to an e-Commerce site
Once an e-Commerce site is created, the channel it is associated with can be changed by following the information on the [asssociate an e-Commerce site with an online channel](associate-site-online-store.md) topic.  The below screen shot shows how a new channel operating unit number (OUN) can be changed from the "Channels" section within the "Site Settings".  Once a change is made, be sure to select the "Save and publish" link for the changes to go live.  

![e-Commerce site initialization](media/e-commerce-site-04.png)

New channels can be added with the "Add a channel" button and new languages by selecting the channel which will bring up a dialog box with an "Add a locale" button.  Locales must be pre-configured on the online store channel within the Headquarters app before they will appear in this dialog.

![e-Commerce site initialization](media/e-commerce-site-05.png)

## Setup Azure B2C tenant
Dynamics 365 Commerce uses Azure AD B2C to support user credential and authentication flows.  Follow the instructions on the [setup a B2C tenant in Commerce](set-up-b2c-tenant.md), [set up custom pages for user sign-ins](custom-pages-user-logins.md), and [configure multiple B2C tenants in a Commerce environment](configure-multi-b2c-tenants.md) topics to set this up.

## Overview of default site pages
The E-Commerce "default" and "fabrikam" site come with pre-configured templates, fragments and pages to get you started.  See the following for topics for overviews:
* [Home page overview](quick-tour-home-page.md)
* [Product details page overview](quick-tour-pdp.md)
* [Cart and checkout pages overview](quick-tour-cart-checkout.md)
* [Account management pages overview](quick-tour-account-management.md)

## Manage site settings
There are several topics available to help you manage your site settings including:
* [Manage e-Commerce users and roles](manage-ecommerce-users-roles.md)
* [Search engine optimization (SEO) considerations for your site](/search-engine-optimization-considerations.md)
* [Manage Content Security Policy (CSP)](manage-csp.md)
* [Select a site theme](select-site-theme.md)

## Manage site content
Before managing site content, you should understand the terms with the [page model glossary](page-elements-overview.md) topic as well as the [document states and lifecycle](document-states-overview.md) topic.

You will also want to have an overview of the following topics:
* [Templates and layout](templates-layouts-overview.md)
* [Work with fragments](work-with-fragments.md)
* [Work with modules](work-with-modules.md)
* [Digital asset management overview](dam-overview.md)
* [Module library overview](starter-kit-overview.md)


## Additional resources

[Create an e-Commerce site](create-ecommerce-site.md)

[Deploy a new e-Commerce site](deploy-ecommerce-site.md)

[Associate an online site with a channel](associate-site-online-store.md)

[Configure your domain name](configure-your-domain-name.md)

[Add support for a content delivery network (CDN)](add-cdn-support.md)

[Enable location-based store detection](enable-store-detection.md)

[Set up custom pages for user logins](custom-pages-user-logins.md)
