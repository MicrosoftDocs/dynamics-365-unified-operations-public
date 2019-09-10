---
 # required metadata

title: Work with preset layouts
description: This topic describes how to work with preset layouts in Dynamics 365 Commerce.
author: phinneyridge
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
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

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to work with preset layouts in Dynamics 365 Commerce. For more information, see [Work with templates](work-with-templates.md) and [Work with preset layouts](work-with-layouts.md).

## Overview

Please read [Preset and custom layouts](templates-layouts-overview.md#preset-and-custom-layouts) before continuing with the steps below. For a general overview, see [Templates and layouts overview](templates-layouts-overview.md).

## Create a new preset layout

There are two methods to create a preset layout. The first is to save an existing custom layout as a new prest layout, and the second is to create a new preset layout.

### Create a preset layout from an existing custom layout

To create a preset layout from an existing custom layout, do the following.

1. Open an existing page that does not currently use a preset layout and has a module structure you would like to reuse for other pages within your site.

1. Click **Check out**.

1. Click **Save as new layout**. The Save as new layout dialog box appears.

1. Enter a name and description for your layout. The name and description are shown to other authors when they create a new page from, or switch to, your layout. Enter something helpful to a page author.

1. Click **OK**.

The preset layout is now available when you create new pages or choose another layout for a page within the same template hierarchy.

> [!TIP]
   >
   > To quickly see if a specific page is currently bound to a preset layout, select the page in the pages list view and inspect the layout metadata in the property panel on the right.  

### Create a preset layout

To create a preset layout from scratch, follow these steps.

1. From the left navigation bar, click **Layouts**. 
   
2. Click the **New Layout**. The New layout dialog box appears.

3. Select the template that you would like to use for your preset layout.

4. Enter a name and description for your preset layout. The name and description are shown to other authors when they create a new page from, or switch to, your new layout. Enter something helpful to a page author.

5. Click **OK** to create the new layout and enter the layout editor.

6. In the layout editor, add and configure modules using the outline and property panel just as you would in the template editor. The module arrangement and locked defaults will be the centralized module configuration for any pages that use this layout.

## Modify a preset layout

To modify a preset layout, do the following.

1. From the left navigation bar, click **Layouts**. 
   
1. In the layout editor outline view, select a module that you wish to modify and do any of the following:

    - To move a module up or down within its parent, choose the "**Move up**" or "**Move down**" options in the module's action menu ("**...**").
    - To change default module settings, use the property pane to enter default values and optionally lock them for all downstream pages.
    - To add new modules or fragments to container modules,  click the ellipsis button (**...**), then select "**Add module**" or "**Add fragment**.
    - To remove a module from the layout, click the ellipsis button (**...**), then select **Delete**.

## Change a preset layout theme

A common practice is to set a default theme for all pages that use a preset layout. 

To set or change a theme for all of your layout's child pages, do the following.

1. In the layout editor outline view, select the page container module (typically the second node titled "Default page").

1. In the property pane on the right, click the **Theme** dropdown menu, then select a theme.  

## Save, check in, preview, and publish a preset layout

To save and check in your preset layout, do the following.

1. Click **Save** at the top of the layout editor. Saved changes will not affect downstream pages until they are checked in.  
1. Click **Check In**. Changes are now discoverable for downstream workflows.

To preview your changes, either open an existing page that uses the template or create a new page from the template.  

Once you have previewed your template changes within a page preview context, there are multiple ways to publish the template to your live site.


* Go to **Layouts**, select the layout, then click **Publish**.

-or-

* From the layout editor, click **Publish**.

-or-

* Publish a page that references the unpublished layout. This will automatically publish the layout.

  > [!WARNING]
  >
  > Preset layouts can be referenced by multiple pages.  When you publish a preset layout, be aware that you may be affecting the layout for multiple pages with this action.  
