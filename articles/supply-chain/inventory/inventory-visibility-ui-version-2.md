---
title: Inventory Visibility app user interface versions (preview)
description: This article describes the difference between version 1 and version 2 of the Inventory Visibility app user interface. It describes the new operations supported in version 2 and how to migrate to it from version 1.
author: yufeihuang
ms.author: yufeihuang
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 11/27/2023
audience: Application User
ms.search.region: Global
ms.custom: bap-template
---

# Inventory Visibility app user interface versions (preview)

[!INCLUDE [preview-banner](../includes/preview-banner.md)]

The Inventory Visibility app runs in Microsoft Power Apps. The current version of the app supports two user interface versions. You can choose which version you prefer to use. The following versions are available:

- User interface version 2, which is referred to as *UI version 2* in this article
- User interface version 1, which is referred to as *UI version 1* in this article

This article describes the differences between the two versions, the new operations supported in UI version 2, and how to migrate from UI version 1 to UI version 2.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Features and configurations supported by each version

The following settings and features are only accessible from the UI version 1 configuration page:

- Clean up of preloaded on-hand results
- Operations related to inventory allocation

> [!NOTE]
> The majority of the features for setting up and viewing preloaded on-hand results are supported by both UI versions. Only the clean up of existing preloaded on-hand result requires UI version 1.

The following settings and features are only accessible from UI version 2 pages:

- Support for 180 days available-to-promise (ATP) calculations
- Inventory adjustments via the user interface

The following settings are accessible both in UI version 1 and UI version 2 pages. Changes are synchronized between versions:

- Index hierarchy setup

All other features and settings can be accessed in the both UI versions, but changes aren't synchronized between versions.

## Switch between UI versions 1 and UI version 2

New installations of Inventory Visibility use UI version 2 by default. If you first installed an older version, then the app continues to use UI version 1 by default, even after updates (though you can change to UI version 2 when you're ready).

Follow these steps to switch between UI versions:

1. Open the **Inventory Visibility** app in Power Apps.
1. On the navigation pane, select **UI Version Control**.
1. Select **Configuration entity version**.
1. Set **Entity version** to *2* or *1*, depending on which version of the UI (and Dataverse configuration entities) you want to use.
1. If you're moving to UI version 2, you'll probably want to migrate your UI version 1 settings, as described in the next section.

## Migrate configuration settings from UI version 1 to UI version 2

When you change from UI version 1 to UI version 2, Inventory Visibility updates to only use configuration values from the Dataverse entities that correspond to UI version 2. You'll still be able to read and update the legacy Dataverse entities using the pages from UI version 1, but changes to these settings won't have any effect unless you switch the entire app back to UI version 1. While UI version 2 is active, only the settings made on the UI version 2 pages are used. To view and edit the legacy settings from UI version 1, open the Inventory Visibility menu at the bottom of the navigation pane and then select **Legacy UI**. <!-- KFM: Please confirm this edit. -->

After you change to UI version 2, you can migrate your previous UI version 1 settings to the new Dataverse entities used by UI version 2. You can switch back to UI version 1 at any time, but you can't migrate settings from UI version 2 to UI version 1. If you later return to UI version 2 after working in UI version 1 for a while, you can remigrate your UI version 1 settings, but only newly created records will be migrated; updated and deleted records aren't replicated, so all of your previous UI version 2 settings will be kept.

To migrate your settings from UI version 1 to UI version 2, follow these steps:

1. Open the **Inventory Visibility** app in Power Apps.
1. On the navigation pane, select **Admin settings**.
1. On the **Migrate entities to V2** tile, select **Manage**.
1. A dialog opens where you must enter the credentials you used when installing the Inventory Visibility service. Enter the credentials and then select **Login**.
1. The system copies your existing settings from UI version 1 to UI version 2.
