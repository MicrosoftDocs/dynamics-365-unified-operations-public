---
# required metadata


title: Channel mapping to e-commerce sites
description: This article will provide guidance for setting up common channel mapping scenarios.
author: samjarawan
ms.date: 09/21/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Channel mapping to e-commerce sites

Dynamics 365 Commerce provides support for many difference business scenarios of mapping [online channels](channels-overview.md#online-channels) to [e-commerce sites](online-store-overview.md).  They range from a single language channel mapped to a single e-commerce site (a single brand in a single region with a single language), multi-language channel mapped to a single or multi-language e-commerce sites (a single brand site in a single region serving multiple languages an example is Canada with French and English could have the same or different e-commerce site experiences) or multiple online channels mapped to a single e-commerce site (multiple online channels set up to support different geographical regions with a single set of e-commerce pages, an example is single web site serving Australia and New Zealand markets, users from both regions get the same experience but can have different products, prices, discount, shipping options, etc... This article will provide guidance for setting common channel mapping scenarios.

## Online channel

An online channels represent an online e-commerce storefront which is used to map products, pricing, discounts, languages, payment methods, delivery modes, fulfillment centers and other aspects of the online experience that will be available to your customers. Online channels are created and managed within the headquarters (HQ) tool. 

For an overview on channels see the [Channel overview](channels-overview.md) topic and to learn about creating an online channel see the [Set up an online channel](channel-setup-online.md) topic.

The below image shows the default online channels that are deployed with Dynamics 365 Commerce if the demo data option was selected.

![Default demo data channels](media/channel-mapping-1.png)

## E-commerce site

An e-commerce site represents the set of pages that make up the website that customers use to shop.  E-commerce sites are managed from within the site builder tool as shown in the below image.  To learn more about how to create and manage sites from within the site builder see the [E-commerce site overview](online-store-overview.md) topic.

![Site builder e-commerce site list](media/channel-mapping-2.png)

## Channel mapping scenarios

Dynamics 365 Commerce supports a great range of channel mapping scenarios. Understanding the below set of common scenarios should help in planning out any unique business scenarios you may have.  You will find examples below using the Dynamics 365 Commerce ficticious storefronts included with demo data including the Fabrikam fashion store and Adventure Works sporting goods.

### Single market site with a single online site experience
An example for this scenario is the Adventure Works online store setup for a single market (US) with a single language (en-us) and a single online experience.  The below image shows an example of the channel setup within HQ.  Notice how an online channel only maps to a single legal entity, which is usually based in a single country that requires the tax reporting for the channel, a single currency, but can be localized into multiple languages (only en-us in this example).

![Adventure Works online store in HQ](media/channel-mapping-3.png)

The above single online channel can then be mapped to a single e-commerce site within the site builder tool. The below shows how a new site is created in site builder where the online store channel and default language are chosen.

![Creating a new site in site builder](media/channel-mapping-4.png)

**Note:** In general you won't create new sites as shown above since it will start out as an empty site without any site pages (ie: homepage, category page, product page, ...). A better practice is to start out with a copy of one of the provided starter sites such as Fabrikam or Adventure Works.  In this case you will select **Copy site** where you can pick the source site and the destination site name.  

![Site copy in site builder](media/channel-mapping-5.png)

Notice in the screen capture above the online channel is not an option to pick yet, this can be picked once the site copy has completed.  When the site is first selected in site builder, it will bring up a setup dialog where the default channel and language can be selected as shown in the below image.  Note a single domain name can host multiple sites, the path is used to separate the sites.  For example the domain could be "www.MyCompany.com" that supports two different e-commerce sites, one for Fabrikam and one for Adventure Works.  So a path could be left blank for one site such as the Fabrikam site and a path could be added for the second site such as "adventureworks" so that the site is accesses with www.MyCompany.com/adventureworks or a path can be added for both sites.

![Initialize site in site builder](media/channel-mapping-6.png)

### Single market site with multiple languages but same site experience
Single online channel with multiple languages mapped to a single e-commerce site
Adventure Works online channel configured with en-ca and fr-ca - users in both French Canada and English Canada get the exact same experience, same currency but site is localized

### Single market site with multiple languages but different site experiences
online channel with multiple languages mapped to different e-commerce sites

### Brand with multiple markets and single site
AW en-us channel with US currency single site
AW de-de channel with EU currency single site

### Brand with multiple markets and site but different page experiences
AW en-us channel with US currency single site
AW de-de channel with EU currency single site

### Brand with multiple markets and site but different site experiences
AW en-us channel with US currency site 1
AW de-de channel with EU currency site 2

