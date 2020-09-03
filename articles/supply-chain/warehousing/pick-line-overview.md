---
# required metadata

title: Set up a mobile device menu item to provide a pick line overview
description: This topic explains how to define when warehouse workers will be shown a list of all work lines when they are processing warehouse work on a mobile device. This can be useful for warehouse workers who often need to get an overview of the pick lines in a work order so they can better optimize their picking sequence.
author: MarkusFogelberg
manager: tfehr
ms.date: 09/03/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form:  [Operations AOT form name to tie this topic to]
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope:  Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: [leave blank for most, retail, public sector]
ms.author: mafoge
ms.search.validFrom: 2020-09-03
ms.dyn365.ops.version: Release 10.0.13
---

# Set up a mobile device menu item to provide a pick line overview

[!include [banner](../includes/banner.md)]
[!include [preview banner](../includes/preview-banner.md)]

This topic explains how to add a **Show work line list** option for mobile device menu items used to manage picking work. It enables warehouse workers to view and select from a list of all the work lines related to the current task, which can help workers better optimize their picking sequence. This feature provides options that can replace the standard **Skip** button, which requires workers to cycle through each line, one at a time, in a fixed order (though that option is still available).

Administrators can configure each menu item individually to control how the **Show work line list** option will work for that item and which options it will provide.

## Turn on the work pick line overview feature

Before you can use this feature, it must be turned on in your system. Admins can use the [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) settings to check the status of the feature and turn it on if it's required. In the **Feature management** workspace, the feature is listed in the following way:

- **Module:** _Warehouse management_
- **Feature name:** _Work pick line overview_

## Configure menu items to show list of all work lines

To set up a mobile device menu item to provide a pick line overview:

1. Go to **Warehouse management > Setup > Mobile device > Mobile device menu items**.

1. Select or create a menu item related to picking work that uses the following settings:

    - **Mode** - *Work*
    - **Use existing work** - *Yes*
    - **Directed by** - *User directed* or *System directed*.

    For more information about how to create menu items and use the various settings available on the **Mobile device menu items** page, see [Set up mobile devices for warehouse work](configure-mobile-devices-warehouse.md).

1. On the **General** FastTab, configure this feature by setting **Show work line list** to one of the following values:

    - **Show only upon request** - Workers will be able to choose to see the pick line list by selecting the **Skip to** button.
    - **Show at the start of every pick** - Workers will see the list every time they start or complete a pick line, and can see it again by selecting the **Skip to** button.
    - **Show at the start of the first pick only** - Workers will see the list each time they start a new picking work, but not after each line. If needed, they can see the list again by selecting the **Skip to** button.
    - **Never show** - Provides the standard **Skip** button, thereby disabling the work lines list display. The **Skip** button lets workers cycle through each line, one at a time, in a fixed order.

1. On the Action Pane, select **Save**. Provided you set **Show work line list** to anything other than *Never show*, the **Field list** button on the Action Pane becomes active.

1. On the Action Pane, select **Field list**.

1. The **Field list** page opens. Use the settings here to configure the information that will be displayed by the warehouse app for each line in the list. The following settings are provided:

    - **Primary control** is always set to *LineNum*, which means that each row in the list will begin with a line number.
    - Add up to seven additional display fields using the remaining seven **Display field** drop-down lists. Select a work-line field name from each drop-down list, as required, to display a value for that field for each line. The values will be shown in the same order that you choose here. If you don't require all seven values, just leave the unneeded drop-down lists set to blank.

1. On the Action Pane, select **Save** and then close the **Field list** page.
