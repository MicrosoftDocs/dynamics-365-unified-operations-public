---
title: Simplify Your Site Creation Process with Bulk Channel Association in Dynamics 365 Commerce Sitebuilder using Channel Wizard
description: This document describes the new feature that allows site authors to associate more than one channel in a bulk manner using a wizard experience.
author: ashishmsft
ms.date: 01/12/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
---

# Simplify Your Site Creation Process with Bulk Channel Association in Dynamics 365 Commerce Sitebuilder using Channel Wizard

## Introduction

This document describes the new feature that allows site authors to associate more than one channel in a bulk manner using a wizard experience. This feature simplifies the process of creating and managing multiple channels for a site, and provides options to customize the domain, path, authentication profile, and geo-redirection settings for each channel. This feature also enables cross-channel sharing, which lets retailers reuse and share content among multiple channels of a site.

## Value Proposition

The value proposition of this feature is to save time and effort for site authors who need to create and manage multiple channels for a site. By using the wizard experience, site authors can easily select and associate multiple channels with a site, and configure the default and optional settings for each channel. This feature also allows site authors to enable cross-channel sharing, which reduces the duplication of content and improves the consistency and quality of the site.

## Applicable use cases

The applicable use cases for this feature are:

- As a site author, I want to associate multiple channels with a site in a bulk manner, so that I can create and manage multiple channels for a site more efficiently.
- As a site author, I want to use an option to auto-default the domain, path, and authentication profile configurations for each channel, so that I don't have to manually provide those values for each channel-locale combination individually.
- As a site author, I want to enable geo-redirection for each channel, so that I can direct users to the appropriate channel based on their location.
- As a site author, I want to override the default settings for each channel, so that I can customize the channel properties according to my needs.


## How to Use

The steps for using this feature are:

1. Choose 'Add Multiple Channels' when prompted whether you are associating 'Single channel' or 'Multiple channels'.
2. Choose the default domain and authentication profile that would be associated with each channel. There is also an option to enable geo-redirection by default, which can be overridden at a channel level later.
3. Search and select the channels that you want to associate with the site. You can see the channel name and operating unit number (OUN) for each channel. You can select multiple channels or select all from the header.
4. In the Locales section, you can see all the locales that are associated with each channel by default. If you enabled geo-redirection, you can also see the list of countries or regions assigned to each locale. You can remove individual locales or countries or regions from each channel as needed.
5. In the URL paths section, you can view the default URLs for each channel as explained in the example. You can override the URL paths, domain, or authentication profile for each channel as needed. You can also choose which channel would be the default application channel when authoring site pages in Sitebuilder.
6. Next, you can verify and confirm the channel associations and settings for the site. You can also enable cross-channel sharing, which lets you reuse and share content among multiple channels of a site.
7. Last step is to review and finish the setup, providing you an option to review all the configurations made in a snapshot. 

You can also add an individual channel to the site by choosing the option to associate a single channel. You can follow the same wizard steps to configure the channel settings as described above.

## Recommendations

Our recommendations for using this feature are:

- Enable cross-channel sharing when using the bulk association feature, as it lets you reuse and share content among multiple channels of a site. This capability is useful when the site channels have a compatible base language, or when they have numerous content items in common.
- Review the default and optional settings for each channel carefully, and make sure they match your expectations and requirements. You can always override the settings for individual channels as needed.
- Test the channel associations and settings before launching the site, and verify that the site works as expected for different channels and locales. You can use the preview mode in Sitebuilder to test the site for different channels.

![NOTE] 
> This experience is available on a preview basis, to access it simply add following query string parameter to your sitebuilder URL &set=enableBulkChannels.
