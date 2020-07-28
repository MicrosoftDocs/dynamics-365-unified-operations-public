---
# required metadata

title: Cross-channel sharing
description: This topic describes the cross-channel sharing feature of Dynamics 365 Commerce site builder that allows content to be shared between multiple channels of an e-Commerce site.
author: psimolin
manager: annbe
ms.date: 07/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: psimolin
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Cross-channel sharing

[!include [banner](includes/banner.md)]
[!include [banner](includes/preview-banner.md)]

This topic describes the cross-channel sharing feature of Dynamics 365 Commerce site builder that allows content to be shared between multiple channels of an e-Commerce site.

## Overview

Cross-channel sharing allows the retailer to reuse and share content between multiple channels of a site. This is particularly useful when the channels of a site have a compatible base language or they have a lot of common content items that can be shared as such between the channels.

Cross-channel sharing works by enabling a default channel which will be searched for available content in case channel specific version of the requested content is not found. Content meant to be shared between channels is created in this channel and can be localized to any of the locales used on any channels of the site.

### When to use the cross-channel sharing feature

Cross channel sharing is useful when there are multiple channels on a single site that can share some of the content between them.

One example would be a retailer with multiple brands and storefronts that are grouped under a single site. In this case some of the content can be shared with all or some of the storefronts, for example terms and conditions, payment terms, shipment methods and FAQ. Cross channel sharing supports fragments as well, which means that terms and conditions page can be created as cross channel content, with channel specific fragments used in it. This means that while most of the content is shared between the channels, with cross channel sharing it is possible to have storefront (channel) specific fragments on a cross channel page, which are rendered only when requested from that specific storefront.

Sites with a single channel only or multiple channels which cannot share content do not benefit from cross channel sharing.

### Enable cross-channel sharing

Cross-channel sharing is enabled at the site level and is a one-way operation. Once enabled, it cannot be disabled.

To enable cross-channel sharing in site builder, follow these steps.

1. Go to **Site settings \> Features**.
1. Under **Cross Channel**, set the feature to **On**. 

The following image show the **Cross Channel** setting in site builder under **Site settings \> Features**.

![Enabling cross channel sharing](./media/enabling-cross-channel-sharing.png)

After enabling cross-channel sharing, cross-channel information will be visible in the **Channels** section under **Site settings \> Features**, as shown in the following example image.

![Channels view after enabling cross channel sharing](./media/channels-cross-channel.png)

After enabling cross-channel sharing, the **Channel** drop down menu options in site builder will also include a **Cross Channel Online Store** entry to manage cross-channel content, as show in the following image.

![Channels view after enabling cross channel sharing](./media/cross-channel-dropdown.png)

### Create cross channel content

Log in to the Site builder and navigate to the site you wish to create cross channel content to. Select the Cross channel entry from the drop down list and ensure that the source locale is selected.

In this example we do the following
* Create a cross channel fragment
* Create a cross channel page where we use the cross channel and channel specific fragments
* Override cross channel fragment with a channel specific version

#### Create cross channel fragment

Click **Fragments** from the left side navigation. Click **New** and choose the **Promo banner** module. Enter any name, e.g. **Cross channel banner** and click OK.

Select **Promo banner** and Add Message with text "Cross channel". Finish editing and publish.

The fragment you just created is a **Cross channel fragment**. It can be used on a cross channel page or page created on any of the channels of this particular site.

#### Creating cross channel page and use cross channel content on it

Click **Pages** from the left side navigation. Click **New** and choose open template such as **Marketing**. Enter any name for the page e.g. "Cross channel page". Enter Page URL e.g. "examplepage". Click **OK**.

Select Main Slot and Add a Page Fragment. Select the cross channel fragment with a banner you just created. Click OK. Save and preview, make sure you see a banner with "Cross channel". Finish editing and publish.

Cross channel pages are available on any channels of your site. Think of this example, the URL of the page is **toc** and has common "Terms and Conditions" for all the channels of the site. If the base URLs for the channels of the site are www.fabrikam.com/brand1 and www.fabrikam.com/brand2, the cross channel shared Terms and Conditions would be available from both urls, www.fabrikam.com/brand1 and www.fabrikam.com/brand2.

This allows you to create the shared content once and any update required later needs to be done in single place only.

#### Create channel specific page and use cross channel content on it

For this step, select a specific channel from the channel selected, e.g. "Fabrikam extended online store". Create new page with open template, name it "Channel specific page".

Select main Slot and Add a Page Fragment. From the channel drop down list in the fragment picker, select the Cross channel entry. You should see the cross channel fragment in the list. Select it.

Notice how you can use Cross channel content on channel specific pages. This allows you to create your shared content fragment once and use it on channel specific pages. This is very useful for shared content e.g. terms and conditions, payment terms or contact information.

#### Create channel specific version of a cross channel page

Cross channel sharing supports overriding a cross channel content. Think of a scenario, where all but one of your channels can the exact same piece of content, but for one channel you need to have different content. In this example we show how would you override the cross channel content with a channel specific content for that one channel only.

Make sure that the Cross channel entry is selected from the channels drop down list. Open the cross channel page you created earlier in the page editor. From the channels drop down list, select the channel that you want to have specific content. You will see empty page editor with an option to create new page variant - Click **Create page variant**.

Select Main slot and Add a module - choose a **Promo banner** module. Add a message with a text "Channel specific". Then Finish editing and Publish.

Now if you use the base URL of the channel and navigate to the URL of the cross channel page on that site, you will see that you get the "Channel specific" content instead of the cross channel content.

#### Recap

* Enabling Cross Channel sharing is a one-way operation - make sure your site structure benefits from Cross channel sharing before enabling it
* Cross channel sharing allows creating content (pages and fragments) which will be available on all the channels of the site using the same URL
* Cross channel pages can use also channel specific fragments, which will be rendered only when the page is requested from that specific storefront (channel)
* Channel specific pages can use cross channel fragments
 
## Additional resources

[Authoring page overview](authoring-home-overview.md)

[Document states and lifecycle](document-states-overview.md)
