---
# required metadata

title: Copy content to another locale
description: This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.
author: psimolin
ms.date: 07/05/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: tfehr
ms.search.validFrom: 2017-06-20
---

# Copy content to another locale

[!include[banner](../includes/banner.md)]

This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.

When you create content in Commerce site builder, it is always associated with a locale identifier, for example "en-us". Individual pages and assets can be copied to a different locale within the same e-commerce site by switching the locale when editing a content item and then creating a new variant of the content item. In some cases it makes sense to duplicate all of the content items in a locale to a new locale, for example when you are launching an entirely new locale on your storefront. If the new locale shares the same base language as one of the existing locales, using the existing locale as the source locale for the locale copy operation reduces the effort required to localize the content in the new locale. For example, the "en-us" and "en-au" locales both use the English language. 

The following procedures step through how to add a new locale to existing channel, how to copy all the content items from existing locale to a new locale, and how to monitor the status of a locale copy operation.

## Add a new locale

To add a new locale in Commerce site builder, follow these steps.

1. In site builder, navigate to your site.
1. In the left navigation pane, select **Site settings**, and then select **Channels**.
1. Under **Channel**, select the channel to which you want to add the new locale.
1. In the channel flyout menu on the right, select **+ Add a locale**.
1. In the **Add a locale** dialog box, select a locale from the **Locale to support** drop-down list.
1. Confirm that the **Domain** value is correct.
1. Under **Path**, enter a unique URL path (for example, "en-us" or "english-us").
1. Select **OK**.
1. Close the channel flyout menu.
1. Under **Channel**, confirm that the new locale is listed next to the correct channel.
1. Select **Save and publish**.

> [!NOTE]
> Before the new locale can be configured in the site builder, it must be added to the associated online store channel in Commerce headquarters.

## Copy all content items to a new locale

To copy all content items to a new locale in Commerce site builder, follow these steps.

1. In site builder, navigate to your site.
1. In the left navigation pane, select **Site settings**, and then select **Channels**.
1. On the command bar, select **Create locale copy** from  – locale copy side pane will open.
1. In the **Create locale copy** on the right, confirm that the correct site has been selected under **Source site**.
1. On the **Source channel** drop-down menu, select the source channel.
1. On the **Destination channel** drop-down menu, select the same source channel.
1. On the **Source localel** drop-down menu, select the source locale. in “” and the new locale in ****.
1. On the **Destination locale** drop-down menu, select the new locale.
1. Select **Copy locale**. A notification will appear confirming that the locale copy operation has started.

> [!NOTE]
> You can also copy content between different channels.

## Monitor the status of the locale copy

To monitor the status of the locale copy, follow these steps.

1. In site builder, navigate to your site.
1. In the left navigation pane, select **Site settings**, and then select **Jobs**.
1. Under **Current jobs**, select the job you want to monitor. Job details will appear on the flyout menu on the right.




