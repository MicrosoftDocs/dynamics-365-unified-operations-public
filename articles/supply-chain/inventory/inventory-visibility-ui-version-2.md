---
title: Inventory Visibility app user interface versions
description: Learn about the differences between version 1 and version 2 of the Inventory Visibility app user interface with an outline on supported features and configurations.
author: yufei-huang
ms.author: yufeihuang
ms.topic: how-to
ms.date: 11/27/2023
ms.custom: bap-template
ms.reviewer: kamaybac
ms.search.form:
---

# Inventory Visibility app user interface version

[!include [banner](../includes/banner.md)]

The Inventory Visibility app runs in Microsoft Power Apps. The current version of the app supports two versions of the user interface. You can choose which version you prefer to use. The following versions are available:

- User interface version 2, which is referred to as *UI version 2* in this article
- User interface version 1, which is referred to as *UI version 1* in this article

This article describes the differences between the two versions, the new operations that are supported in UI version 2, and how to migrate from UI version 1 to UI version 2.

> [!NOTE]
> User interface version 1 will be deprecated in a future release. Users are suggested to switch to UI version 2 when possible. 

## Features and configurations supported by each version

The following settings and features are accessible only from the configuration page for UI version 1:

- Cleanup of preloaded on-hand results
- Operations that are related to inventory allocation

> [!NOTE]
> Most of the features for setting up and viewing preloaded on-hand results are supported by both versions of the user interface. Only the cleanup of existing preloaded on-hand results requires UI version 1.

The following settings and features are accessible only from the pages for UI version 2:

- Support for 180-day available-to-promise (ATP) calculations
- Inventory adjustments via the user interface

The following settings are accessible on the pages for both UI version 1 and UI version 2. Changes are synced between versions:

- Index hierarchy setup

All other features and settings can be accessed in both versions of the user interface. However, changes aren't synced between versions.

## Switch between UI versions 1 and UI version 2

New installations of Inventory Visibility use UI version 2 by default. If you first installed an older version, the app continues to use UI version 1 by default, even after updates. However, you can switch to UI version 2 when you're ready.

Follow these steps to switch between UI versions.

1. In Power Apps, open the **Inventory Visibility** app.
1. On the navigation pane, select **UI Version Control**.
1. Select **Configuration entity version**.
1. Set the **Entity version** field to *2* or *1*, depending on the version of the UI (and Dataverse configuration entities) that you want to use.

If you're switching to UI version 2, you'll probably want to migrate your UI version 1 settings as described in the next section.

## Migrate configuration settings from UI version 1 to UI version 2

When you switch from UI version 1 to UI version 2, Inventory Visibility is updated and uses only configuration values from the Dataverse entities that correspond to UI version 2. You can still read and update the old (legacy) Dataverse entities by using the pages from UI version 1. However, changes to the settings have no effect unless you switch the whole app back to UI version 1. While UI version 2 is active, only the settings that you configure on the UI version 2 pages are used. To view and edit the legacy settings from UI version 1, open the Inventory Visibility menu at the bottom of the navigation pane, and then select **Legacy UI**.

After you switch to UI version 2, you can migrate your previous UI version 1 settings to the new Dataverse entities that are used by UI version 2. Although you can switch back to UI version 1 at any time, you can't migrate settings from UI version 2 to UI version 1. If you switch back to UI version 2 after you've been working in UI version 1 for a while, you can remigrate your UI version 1 settings. However, only newly created records are migrated. Updated and deleted records aren't replicated. Therefore, all your previous UI version 2 settings are kept.

To migrate your settings from UI version 1 to UI version 2, follow these steps.

1. In Power Apps, open the **Inventory Visibility** app.
1. On the navigation pane, select **Admin settings**.
1. On the **Migrate entities to V2** tile, select **Manage**.
1. In the dialog box that appears, enter the credentials that you used when you installed the Inventory Visibility service, and then select **Login**.
1. The system copies your existing settings from UI version 1 to UI version 2.

For a more detailed migration guide with screenshots and troubleshooting tips, see [Migrate Configuration Settings from UI Version 1 to UI Version 2](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples/blob/main/Troubleshooting%20Guide/Migrate%20Configuration%20Settings%20from%20UI%20Version%201%20to%20UI%20Version%202.md) in the [Inventory Visibility Add-in Examples](https://github.com/microsoft/Inventory-Visibility-Add-in-Examples) repo on GitHub.
