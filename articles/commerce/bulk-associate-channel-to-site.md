---
title: Bulk associate channels to e-commerce sites
description: This article describes functionality that allows site authors to bulk associate more than one channel to Microsoft Dynamics 365 Commerce e-commerce sites.
author: ashishmsft
ms.date: 01/18/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
---

# Bulk associate channels to e-commerce sites

[!include [banner](../includes/banner.md)]

This article describes functionality that allows site authors to bulk associate more than one channel to Microsoft Dynamics 365 Commerce e-commerce sites.

This document describes the new feature that allows site authors to associate more than one channel in a bulk manner using a wizard experience. 

This feature simplifies the process of creating and managing multiple channels for a site, and provides options to customize the domain, path, authentication profile, and geo-redirection settings for each channel. This feature also enables cross-channel sharing, which lets retailers reuse and share content among multiple channels of a site.

## Value proposition

The value proposition of this feature is to save time and effort for site authors who need to create and manage multiple channels for a site. By using the wizard experience, site authors can easily select and associate multiple channels with a site, and configure the default and optional settings for each channel. This feature also allows site authors to enable cross-channel sharing, which reduces the duplication of content and improves the consistency and quality of the site.

## Recommendations

Our recommendations for using this feature are:

- Enable cross-channel sharing when using the bulk association feature, as it lets you reuse and share content among multiple channels of a site. This capability is useful when the site channels have a compatible base language, or when they have numerous content items in common. [Learn more](./cross-channel-sharing.md)
- Review the default and optional settings for each channel carefully, and make sure they match your expectations and requirements. You can always override the settings for individual channels as needed.
- Test the channel associations and settings before launching the site, and verify that the site works as expected for different channels and locales. You can use the preview mode in site builder to test the site for different channels.

> [!NOTE] 
> This experience is available on a preview basis, to access it simply add the query string parameter `&set=enableBulkChannels` to your site builder URL.

## Applicable use cases

The applicable use cases for this feature are:

- A site author wants to associate multiple channels with a site in a bulk manner to create and manage multiple channels for a site more efficiently.
- A site author wants to use an option to autodefault the domain, path, and authentication profile configurations for each channel to avoid manually providing those values for each channel-locale combination individually.
- A site author wants to enable geo-redirection for each channel to direct users to the appropriate channel based on their location.
- A site author wants to override the default settings for each channel to customize the channel properties according to requirements.

## How to use

The steps for using this feature are:

1. Choose 'Add Multiple Channels' when prompted whether you're associating 'Single channel' or 'Multiple channels'.
2. Choose the default domain and authentication profile that would be associated with each channel. There's also an option to enable geo-redirection by default, which can be overridden at a channel level later.
3. Search and select the channels that you want to associate with the site. You can see the channel name and operating unit number (OUN) for each channel. You can select multiple channels or select all from the header.
4. In the Locales section, you can see all the locales that are associated with each channel by default. If you enabled geo-redirection, you can also see the list of countries or regions assigned to each locale. You can remove individual locales or countries or regions from each channel as needed.
5. In the URL paths section, you can view the default URLs for each channel as explained in the example. You can override the URL paths, domain, or authentication profile for each channel as needed. You can also choose which channel would be the default application channel when authoring site pages in site builder.
6. Next, you can verify and confirm the channel associations and settings for the site. You can also enable cross-channel sharing, which lets you reuse and share content among multiple channels of a site.
7. Last step is to review and finish the setup, providing you with an option to review all the configurations made in a snapshot. 

You can also add an individual channel to the site by choosing the option to associate a single channel. You can follow the same wizard steps to configure the channel settings as described above.


