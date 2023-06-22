---
# required metadata

title: Set up a mobile device menu item to provide a pick line overview
description: This article explains how to define when a list of all work lines will be shown to warehouse workers who are processing warehouse work on a mobile device. This capability can be useful for warehouse workers who often require an overview of the pick lines in a work order so that they can optimize their picking sequence.
author: Mirzaab
ms.date: 09/03/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this article to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.collection: get-started
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mirzaab
ms.search.validFrom: 2020-09-03
ms.dyn365.ops.version: 10.0.13
---

# Set up a mobile device menu item to provide a pick line overview

[!include [banner](../includes/banner.md)]

This article explains how to configure options that are related to the pick line overview for mobile device menu items that are used to process picking work. The pick line overview lets warehouse workers view and select from a list of all the work lines that are related to their current task. This capability can help workers optimize their picking sequence. The feature provides options that replace the standard **Skip** button that lets workers cycle through the lines one at a time, in a fixed order. (However, the option to use that button is still available.)

Admins can configure each menu item individually to control how, when, and where the Warehouse Management mobile app presents the pick line overview.

## Turn on the Work pick line overview feature

Before you can use this feature, it must be turned on for your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** _Warehouse management_
- **Feature name:** _Work pick line overview_

## Configure menu items to show a list of all work lines

To set up a mobile device menu item to provide a pick line overview, follow these steps.

1. Go to **Warehouse management \> Setup \> Mobile device \> Mobile device menu items**.
1. Select or create a menu item that is related to picking work, and set the following values:

    - **Mode:** *Work*
    - **Use existing work:** *Yes*
    - **Directed by:** *User directed* or *System directed*

    For more information about how to create menu items and use the various settings that are available on the **Mobile device menu items** page, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

1. On the **General** FastTab, configure the feature by setting the **Show work line list** field to one of the following values:

    - **Show only upon request** – Workers can choose to view the pick line list by selecting the **Skip to** button in the Warehouse Management mobile app.
    - **Show at the start of every pick** – Workers see the list every time that they start or finish a pick line. They can also view the list again by selecting the **Skip to** button in the Warehouse Management mobile app.
    - **Show at the start of the first pick only** – Workers see the list every time that they start new picking work, but not after each line. They can also view the list again by selecting the **Skip to** button in the Warehouse Management mobile app.
    - **Never show** – The standard **Skip** button appears in the Warehouse Management mobile app, and display of the work line list is turned off. The **Skip** button lets workers cycle through the lines one at a time, in a fixed order. They can also cycle through the list as many times as they require, until all lines have been processed.

1. On the Action Pane, select **Save**.

    If you set the **Show work line list** field to any value except *Never show*, the **Field list** button on the Action Pane becomes available.

1. On the Action Pane, select **Field list**.
1. On the **Field list** page, configure the information that the Warehouse Management mobile app shows for each line in the list.

    - The **Primary control** field is always set to *LineNum*. Therefore, each row in the list begins with a line number.
    - Use the remaining **Display field** fields to add up to seven additional display fields, as you require. In each **Display field** field, select the name of a work line field. Each line will then show a value for that field. The values will be shown in the order that you select here. You can leave some of the **Display field** fields blank if you don't require all seven values.

1. On the Action Pane, select **Save**, and then close the **Field list** page.


[!INCLUDE[footer-include](../../includes/footer-banner.md)]