---
title: Copy content to another locale
description: This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.
author: josaw1
ms.date: 01/12/2023
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: josaw
ms.search.validFrom: 2017-06-20
---

# Copy content to another locale

[!include[banner](../includes/banner.md)]

This article describes how to copy existing content to another locale within a site in Microsoft Dynamics 365 Commerce site builder.

When you create content in Commerce site builder, it's always associated with a locale identifier, such as "en-us." You can copy individual pages and assets to a different locale within the same e-commerce site by switching the locale when you edit a content item and then creating a new variant of the item. In some cases, such as when you're launching an entirely new locale on your storefront, it makes sense to duplicate all the content items in an existing locale to the new locale. If the new locale has the same base language as one of the existing locales, you can use the existing locale as the source locale for the locale copy operation. (For example, the "en-us" and "en-au" locales both use the English language.) In this way, you help reduce the effort that is required to localize the content in the new locale.

The following procedures explain how to add a new locale to an existing channel, copy all the content items from an existing locale to a new locale, and monitor the status of a locale copy operation.

## Add a new locale

To add a new locale in Commerce site builder, follow these steps.

1. In site builder, go to your site.
1. In the left navigation pane, select **Site settings**, and then select **Channels**.
1. Under **Channel**, select the channel to add the new locale to.
1. In the channel dialog box that appears on the right, select **Add a locale**.
1. In the **Add a locale** dialog box, in the **Locale to support** field, select a locale.
1. Confirm that the **Domain** value is correct.
1. Under **Path**, enter a unique URL path (for example, **en-us** or **english-us**).
1. Select **OK**.
1. Close the channel dialog box.
1. Under **Channel**, confirm that the new locale is listed next to the correct channel.
1. Select **Save and publish**.

> [!NOTE]
> Before the new locale can be configured in site builder, it must be added to the associated online store channel in Commerce headquarters.

## Copy all content items to a new locale

To copy all content items to a new locale in Commerce site builder, follow these steps.

1. In site builder, go to your site.
1. In the left navigation pane, select **Site settings**, and then select **Channels**.
1. On the command bar, select **Create locale copy from**.
1. In the **Create locale copy** dialog box that appears on the right, under **Source site**, confirm that the correct site is selected.
1. In the **Source channel** field, select the source channel.
1. In the **Destination channel** field, select the same source channel.
1. In the **Source locale** field, select the source locale.
1. In the **Destination locale** field, select the new locale.
1. Select **Copy locale**. A notification confirms that the locale copy operation has started.

> [!NOTE]
> You can also copy content between different channels.

## Monitor the status of the locale copy

To monitor the status of a locale copy operation, follow these steps.

1. In site builder, go to your site.
1. In the left navigation pane, select **Site settings**, and then select **Jobs**.
1. Under **Current jobs**, select the job to monitor. Job details are shown in the dialog box that appears on the right.

## Delete a locale

To delete a locale and all the contents in that locale, follow these steps.

1. In site builder, go to your site.
1. In the left navigation pane, select **Site settings**, and then select **Channels**.
1. Under **Channel**, select the name of the channel from which you want to delete a locale.
1. On the channel properties pane on the right, under **Locale-domain mappings**, select the vertical ellipsis next to the locale you want to delete, and then select **Delete**.
1. In the confirmation dialog box, ensure that the information is correct, and then select **Delete locale**.
