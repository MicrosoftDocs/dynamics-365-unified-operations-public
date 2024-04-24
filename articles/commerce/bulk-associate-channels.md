---
title: Bulk associate channels with e-commerce sites
description: This article describes feature functionality that lets site authors bulk associate multiple channels with Microsoft Dynamics 365 Commerce e-commerce sites.
author: ashishmsft
ms.date: 01/23/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
---

# Bulk associate channels with e-commerce sites

[!include [banner](../includes/banner.md)]

This article describes feature functionality that lets site authors use a wizard experience to bulk associate multiple channels with Microsoft Dynamics 365 Commerce e-commerce sites.

The bulk association feature simplifies the process of creating and managing multiple channels for a site. It provides options for customizing the domain, path, authentication profile, and geo redirection settings for each channel.

The feature also lets site authors enable cross-channel sharing, so that retailers can reuse and share content among multiple channels of a site. This functionality helps reduce content duplication and improve the consistency and quality of the site.

The main benefit of this feature is that it helps save time and effort when site authors create and manage multiple channels for a site. Site authors who use the wizard experience can easily select and associate multiple channels with a site. In addition, they can easily configure the default and optional settings for each channel.

## Common uses of the bulk association feature

Here are some common uses of the bulk association feature:

- A site author wants to bulk associate multiple channels with a site. In this way, they can more efficiently create and manage multiple site channels for that site.
- A site author wants to use an option to automatically enter default values for the domain, path, and authentication profile configurations for each channel. In this way, they don't have to manually provide those values for each combination of a channel and a locale.
- A site author wants to enable geo redirection for each channel. In this way, users are directed to the appropriate channel, based on their location.
- A site author wants to override the default settings for each channel. In this way, they can customize the channel properties according to requirements.

## Best practices for the bulk association feature

We recommend that you follow these best practices when you use the bulk association feature:

- Enable cross-channel sharing. This capability lets you reuse and share content among multiple channels of a site. It's useful when the site channels have a compatible base language, or when they have numerous content items in common. [Learn more.](./cross-channel-sharing.md)
- Carefully review the default and optional settings for each channel, to ensure that they match your expectations and requirements. You can override the settings for individual channels as needed.
- Test the channel associations and settings before you launch the site, and verify that the site works as expected for different channels and locales. You can use the preview mode in site builder to test the site for different channels.

## Bulk associate multiple channels in site builder

> [!NOTE]
> The bulk association feature is available on a preview basis. To access the feature, append the query string parameter `&set=enableBulkChannels` to your site builder URL.

To bulk associate multiple channels in site builder, follow these steps.

1. In the left navigation pane for your site, select **Channels**.
1. Select **Add channel**.
1. In the **Add channel** dialog box, in the **Channel selection** field, select **Add multiple channels**. Then select **Next**.
1. In the **Channel details** step, select the domain and authentication profile to associate with each channel.
1. Optionally set the **Enable all channels for auto redirection** option to **On** to enable geo redirection by default. You can override this setting at the channel level later, as needed.
1. Select **Next**.
1. In the **Add channels** step, search for and select the channels to associate with the site. The list of channels shows **Channel name** and **Operating Unit Number (OUN)** values for each channel. Select channels one by one, or select all channels from the header.
1. Select **Next**.
1. In the **Locales** step, a list shows all the locales that are associated with each channel by default. If you previously enabled geo redirection, a list of countries or regions is assigned to each locale. Optionally select **Edit** to add or remove locales, countries, or regions from each channel as needed. Then select **Add locales**.
1. Select **Next**.
1. In the **URL paths** step, you can view the default URLs for each channel. You can override the URL paths, domain, or authentication profile for each channel as needed. In addition, in the **Set default application channel** field, you can select which channel is the default application channel when site pages are authored in site builder.
1. Select **Next**.
1. In the **Locale defaults** step, select the default locale for each channel, and then select **Next**.
1. In the **Review and finish** step, review the configuration, and make any changes that are required.
1. Select **Save and publish**.

> [!NOTE]
> To associate a single channel with your site, select **Add a single channel** instead of **Add multiple channels** in step 3 of this procedure.
