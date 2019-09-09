---
 # required metadata

title: Templates and layouts
description: This topic describes how and when to use templates and layouts within the e-commerce authoring toolset.
author: Nick Holman
manager: Brendan Sullivan
ms.date: 07/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: 
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: retail
ms.author: phinneyridge
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Working with preset layouts:

Please be sure to read the **[Preset vs. custom layouts](#preset-and-custom-layouts)** section before continuing with the steps below.

## Create a new preset layout

There are two methods to create a preset layout.  The first is to save an existing custom layout as a preset, and the second is to create a new preset layout from scratch.

To create a preset layout from an existing custom layout, follow these steps.

1. Open an existing page that does not currently use a preset layout and has a module structure you would like to re-use for other pages within your site.

   > [!TIP]
   >
   > To quickly see if a specific page is currently bound to a preset layout, select the page in the pages list view and read the layout metadata in the property panel on the right.  
   
2. Check out the page by clicking the "**Check out**" button in the page editor's action bar.

3. Once the page is checked out to you, there will be a new action bar button to "**Save as new layout**".  Click this button to launch the save as layout modal.

4. Enter a name and description for your layout.  The name and description are shown to other authors when they create a new page from, or switch to, your layout.  Enter something helpful to a page author.

5. Click "**OK**" after you have filled out the layout metadata fields.

6. Your preset layout is now available when you create new pages, or choose another layout for a page within the same template hierarchy.

To create a preset layout from scratch, follow these steps.

1. From the left navigation bar select "**Layouts**" 

   > [!NOTE] 
   > Subsequent tool versions will group layouts under the templates list view.
   
2. From the action bar at the top of the list view, click the "**New Layout**" button.  This will launch the new layout modal window.

3. Choose the **template** that you would like to use for your preset layout.

4. Enter a name and description for your preset layout.  The name and description are shown to other authors when they create a new page from or switch to your new layout.  Enter something helpful to a page author.

5. Click "**OK**" to create the new layout and enter the layout editor.

6. In the layout editor, add and configure modules using the outline and property panel just as you would in the template editor.  Your module arrangement and locked defaults will be the centralized module configuration for any pages that use this layout.

## Modify a preset layout

To modify a preset layout, follow these steps.

1. Navigate to the layout editor for the preset layout you wish to modify.  This can be done through any of these navigation paths:
   * If you are editing a page that uses a preset layout, you can navigate to the layout editor by selecting the top node in the outline view and clicking the **Layout** link in the property panel.
   
   * If you are in the pages list view, select a page that uses a preset layout and click the **Layout** link in the property panel.
   
   * From the left navigation bar select "**Layouts**".  Click on the name of the layout you wish to modify from the list view.
   
     > [!NOTE] 
     > Subsequent tool versions will group layouts under the templates list view.
   
2. In the layout editor's outline view, select a module that you wish to modify and do any of the following:

   * To move a module up or down within its parent, choose the "**Move up**" or "**Move down**" options in the module's action menu ("**...**").
   * To change default module settings, use the property panel to enter default values and optionally lock them for all downstream pages.
   * For container modules, add new modules or fragments by selecting the "**Add module**" or "**Add fragment**" options in the module's action menu ("**...**").
   * To remove a module from the layout, select the "**Delete**" option in the module's action menu ("**...**").

## Change preset layout theme

A common practice is to set a default theme for all pages that use a preset layout.  To set or change a theme for all of your layout's child pages, follow these steps.

1. In the layout editor's outline view, select the page container module node (typically the second node titled "Default page").

2. Find the "**Theme**" picker control in the property panel on the right.

3. Select your desired theme from the dropdown selector.  

   > [!NOTE]
   >
   > To add new theme options to your site, read the help documentation for creating, editing, and adding new themes.

## Save, preview, and publish a preset layout

To save your layout, click the "**Save**" button in the action bar at the top of the layout editor.  Saved changes will not affect downstream pages until they are "**Checked In**".  To check in your changes and make them discoverable for downstream workflows, click the "**Check In**" button in the action bar.

To preview your changes, either open an existing page that uses this layout or create a new page from the layout.  

Once you have previewed your layout changes within a page preview context, there are multiple ways to publish the layout to your live site.

- Publishing a page that references an unpublished layout will automatically publish the layout.

- Select the layout in the layouts list view (**Left navigation control > Layouts > Selected layout**) and click the "**Publish**" button in the top action bar.

- Go back to the layout editor view and select "**Publish**" from the top action bar.

  > [!WARNING]
  >
  > Preset layouts can be referenced by multiple pages.  When you publish a preset layout, be aware that you may be affecting the layout for multiple pages with this action.  
