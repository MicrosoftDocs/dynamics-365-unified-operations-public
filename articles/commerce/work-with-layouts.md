---
 # required metadata

title: Work with preset layouts
description: This topic describes how to work with preset layouts in Microsoft Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Work with preset layouts


[!include [banner](includes/banner.md)]

This topic describes how to work with preset layouts in Microsoft Dynamics 365 Commerce.

## Overview

Before you complete the procedures in this topic, be sure to read [Preset and custom layouts](templates-layouts-overview.md#preset-and-custom-layouts). For a general overview, see [Templates and layouts overview](templates-layouts-overview.md).

## Create a new preset layout

There are two methods for creating a preset layout. You can save an existing custom layout as a new preset layout, or you can create a preset layout from scratch.

### Create a preset layout from an existing custom layout

To create a preset layout from an existing custom layout, follow these steps.

1. Open an existing page that doesn't currently use a preset layout, and that has a module structure that you want to reuse for other pages on your site.
1. Select **Check out**.
1. Select **Save as new layout**. The **Save as new layout** dialog box appears.
1. Enter a name and description for your preset layout. The values that you enter will be shown to other authors when they create new pages from your layout or switch to it. Therefore, enter values that will be useful to page authors.
1. Select **OK**.

The preset layout will now be available when you create new pages or select a different layout for a page in the same template hierarchy.

> [!TIP]
> To quickly see whether a specific page is currently bound to a preset layout, select the page in the pages list view, and inspect the layout metadata in the property pane on the right.

### Create a new preset layout

To create a preset layout from scratch, follow these steps.

1. In the navigation pane on the left, select **Layouts**.
1. Select **New Layout**. The **New layout** dialog box appears.
1. Select the template to use for your preset layout.
1. Enter a name and description for your preset layout. The values that you enter will be shown to other authors when they create new pages from your layout or switch to it. Therefore, enter values that will be useful to page authors.
1. Select **OK** to create the new preset layout and open the layout editor.
1. In the layout editor, add and configure modules by using the outline tree on the left and the property pane on the right. (The process resembles the process for adding and configuring modules for a template in the template editor.) The arrangement of modules and any locked default settings become the centralized module configuration for any pages that use this preset layout.

## Modify a preset layout

To modify a preset layout, follow these steps.

1. In the navigation pane on the left, select **Layouts**.
1. In the layout editor, in the outline tree on the left, select the module to modify. Then follow any of these steps:

    - To move a module up or down inside its parent, select the ellipsis button (**...**) for the module, and then select **Move up** or **Move down**.
    - To change a module's default settings, use the property pane to enter default values and optionally lock them for all downstream pages.
    - To add new modules or fragments to container modules, select the ellipsis button, and then select **Add module** or **Add fragment**.
    - To remove a module from the layout, select the ellipsis button, and then select **Delete**.

## Change a preset layout theme

A typical practice is to set a default theme for all pages that use a preset layout.

To set or change the theme for all child pages that use your preset layout, follow these steps.

1. In the layout editor, in the outline tree on the left, select the page container module. (Typically, this module is the second node and is named **Default page**.)
1. In the property pane on the right, in the **Theme** field, select a theme.

## Save, check in, preview, and publish a preset layout

To save and check in your preset layout, follow these steps.

1. Select **Save** at the top of the layout editor. Saved changes don't affect downstream pages until they are checked in.
1. Select **Check In**. Your changes are now discoverable for downstream workflows.

To preview your changes, either open an existing page that uses the preset layout or create a new page from the layout.

After you've previewed the changes to your preset layout, follow one of these steps to publish the layout to your live site:

* Go to **Layouts**, select the layout, and then select **Publish**.
* In the layout editor, select **Publish**.
* Publish a page that references the unpublished layout. The layout will automatically be published.

> [!WARNING]
> Preset layouts can be referenced by multiple pages. When you publish a preset layout, be aware that you might affect the layout of multiple pages.

## Additional resources

[Templates and layouts overview](templates-layouts-overview.md)

[Work with templates](work-with-templates.md)
