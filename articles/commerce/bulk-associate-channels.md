---
title: Bulk associate channels to e-commerce sites
description: This article describes feature functionality that allows site authors to bulk associate more than one channel to Microsoft Dynamics 365 Commerce e-commerce sites.
author: ashishmsft
ms.date: 01/19/2024
ms.topic: article
audience: Application user
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
---

# Bulk associate channels to e-commerce sites

[!include [banner](../includes/banner.md)]

This article describes feature functionality that allows site authors to bulk associate more than one channel to Microsoft Dynamics 365 Commerce e-commerce sites using a wizard experience.

The bulk association feature simplifies the process of creating and managing multiple channels for a site, and provides options to customize the domain, path, authentication profile, and geo redirection settings for each channel. The feature also allows site authors to enable cross-channel sharing, which lets retailers reuse and share content among multiple channels of a site, reducing content duplication and improving the consistency and quality of the site.

The main benefit of this feature is to save site authors time and effort when creating and managing multiple channels for a site. Site authors using the wizard experience can easily select and associate multiple channels with a site, and configure the default and optional settings for each channel.

## Common uses of the bulk association feature

Some common uses of the bulk association feature are:

- A site author wants to bulk associate multiple channels with a site to more efficiently create and manage multiple site channels for that site.
- A site author wants to use an option to automatically default the domain, path, and authentication profile configurations for each channel to avoid manually providing those values for each channel-locale combination individually.
- A site author wants to enable geo redirection for each channel to direct users to the appropriate channel based on their location.
- A site author wants to override the default settings for each channel to customize the channel properties according to requirements.

## Best practices for the bulk association feature

The following best practices are recommended when using the bulk association feature.

- Enable cross-channel sharing when using the bulk association feature, as it lets you reuse and share content among multiple channels of a site. This capability is useful when the site channels have a compatible base language, or when they have numerous content items in common. [Learn more](./cross-channel-sharing.md)
- Review the default and optional settings for each channel carefully to ensure that they match your expectations and requirements. You can override the settings for individual channels as needed.
- Test the channel associations and settings before launching the site, and verify that the site works as expected for different channels and locales. You can use the preview mode in site builder to test the site for different channels.

## Bulk associate multiple channels in site builder

> [!NOTE] 
> The bulk association feature is available on a preview basis. To access the feature, append the query string parameter `&set=enableBulkChannels` to your site builder URL.

To bulk associate multiple channels in site builder, follow these steps.

1. In the left navigation pane for your site, select **Channels**.
1. Select **+Add channel**.
1. In the **Add channel** flyout menu, for **Channel selection**, select **Add multiple channels**, and then select **Next**.   
1. On the **Channel details** step, select the **Domain** and **Authentication profile** to be associated with each channel.
1. Optionally, set the **Enable all channels for auto redirection** to **On** to enable geo redirection by default. You can override this setting at the channel level later if needed.
1. Select **Next**.
1. On the **Add channels** step, search for and select the channels that you want to associate with the site. In the list of channels, you can see the **Channel name** and the **Operating Unit Number (OUN)** for each channel. Select the channels you want individually, or select all channels from the header, and then select **Next**.
1. On the **Locales** step, a list displays all the locales that are associated with each channel by default. If you previously enabled geo redirection, you can also see a list of countries or regions assigned to each locale. Optionally, select **Edit** to add or remove locales, countries, or regions from each channel as needed, and then select **Add locales**.
1. Select **Next**.
1. On the **URL paths** step, you can view the default URLs for each channel. You can override the URL paths, domain, or authentication profile for each channel as needed, and also select the **Set default application channel** drop-down list to choose which channel is the default application channel when authoring site pages in site builder.
1. Select **Next**.
1. On the **Locale defaults** step, select the default locale for each of the channels, and then select **Next**.
1. On the **Review and finish** step, review the configuration and make changes as needed.
1. Select **Save and publish**.

> [!NOTE]
> To associate a single channel with your site, for step three of the procedure, select **Add a single channel** instead.




  
   
