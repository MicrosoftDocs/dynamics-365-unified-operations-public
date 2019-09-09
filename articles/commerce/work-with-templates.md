---
 # required metadata

title: Work with templates
description: This topic describes how to work with templates in Dynamics 365 Commerce.
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

# Work with templates

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes how to work with templates in Dynamics 365 Commerce

## Overview

As discussed in the [Templates and layouts overview](templates-layouts-overview.md), templates define the set of options available to downstream authors.  There are multiple reasons why this is helpful to an enterprise web authoring team, and well-structured templates can help with all of the following goals.

- Simplify the authoring experience for day-to-day content editor roles.  
    - Filter module options to only show relevant choices for a specific page section (for example, a marketing section of a template can be configured to filter out irrelevant module choices that should never be used within that context and would only add noise to content authoring tasks).
    - Configure module setting defaults to improve authoring efficiency.
    - Define page fragments defaults to improve authoring efficiency (for example, header and footer fragments in a template will automatically appear in every downstream page).
- Ensure that enterprise sites stay on-brand by defining an approved set of module arrangement and configuration options.  

   > [!TIP] 
   > E-Commerce sites thrive on providing customers with familiar, repeatable, and on-brand UX design patterns. Templates can control these measures of consistency across your site.  

- Improve SEO scores by ensuring repeatable and programmatically defined page definitions and metadata.

> [!NOTE]
> While templates are designed to control consistency across a site, they can theoretically be configured to not enforce any consistency. Brand and site administrators are empowered to set any level of variability for pages in their site. For example, a template could be left entirely open, which would allow content authors to create any page design they choose. In this example, all of the benefits listed above are not applicable.

## Modify a template
Templates are modified using the template editor UI.  There are multiple navigation paths into the template editor:
- Navigate to the template inspector list view (**[Your Site] > Templates**) and click on a template's name to enter into the template editor UI.

  or,

- If you are in the page editor for an existing page, you can navigate to the page's template directly from the property panel.  In the outline, make sure the top node is selected and then click on the **Edit Template** link from the property panel.

To edit a template, follow these steps.

1. Open a template in the editor UI using either of the above navigation paths.

2. Notice the outline tree view on the left.  This outline shows the module options and structures that are available to child layouts and pages.  

3. Notice the property panel on the right.  Select a module in the outline to view the template properties for the selected module.  You will notice some unique properties that are specific to template editing, such as:

  | Property Name | Description |
  | ---- | --- |
  | Min Occurs | Sets the minimum number of occurrence of the the selected module.  For example, setting "Min Occurs" = 1 makes the module required, whereas setting it = 0 makes the module optional for downstream authors. |
  | Max Occurs | Sets the maximum number of occurrence for the selected module.  For example, setting "Max Occurs" = 1 means that module can only be added once. |
  | Min Modules (Containers) | Modules that contain other modules (containers), can set the minimum number of total modules that should be added as children.  For example, a carousel module might define that the minimum number of child modules is greater than 1. |
  | Max Modules (Containers) | Modules that contain other modules (containers), can set the maximum number of total modules that should be added as children.  For example, a carousel module might define that the maximum number of child modules is less than 10. |
  | Locked | You will notice a boolean control titled "locked" next to all core module properties.  This allows the template author to lock a module setting in the template that can't be overridden by any child layouts or pages.  A locked module setting becomes a centrally editable property value for all layouts and pages that use the template. |
   
   

## Create a new template
To create a new template, follow these steps.

1. Navigate to the **Templates** tab in the left navigation bar of your site within the Dynamics e-Commerce authoring interface.  This will bring you to the template inspector view.
2. Click the "**New Template**" button in the action bar at the top of the inspector view.  This will launch the template creation modal window.
3. Enter a name and description for your template.  This will be shown to authors during new page creation workflows, so enter metadata that would be useful to page authors (example: "Use this template to create general marketing pages").  This can always be edited later.
4. Click "**OK**" to create the new template and navigate into the template editor.
5. The template editor will show an outline on the left, and a property panel on the right.  Expand the nodes in the outline and select the "**HTML Head**" slot.  If there are no modules yet in this slot, click the ellipse menu ("**...**") and select "**Add Module**".
6. In the module picker modal that appears, choose "**Default page summary**" from the options and then "**OK**".
7. With the newly added module selected in the outline, enter any default settings in the property panel that you want to automatically populate for all child pages of the template.  If you don't want any defaults then just leave the values blank.
8. Now select the "**Body**" slot and, if it is empty, click the ellipse menu ("**...**") and select "**Add Module**".
9. Select a page container module (depending on your site, there may only be one option) and click "**OK**".
10. Under this new page container module you will see a new set of slots (Header, Main, etc.).  This is where you can add and configure module options that are available to authors when creating pages from this template.  If you add no modules to a slot, then the default behavior is to allow all available modules types for that slot.
11. The template is now technically valid, and can be saved, checked-in, and used for creating new pages.  But as you will see below, there are some other defaults you will likely want to configure first.

## Add headers and footers

If your site already has a header fragment and you've completed the "Create a new template" steps above, follow these steps to add a header and footer to your new template.

1. Expand the "**Body**" slot and its child page module in the outline.
2. Select the "**Header Slot**" in the outline.
3. In the Header Slot's action menu ("**...**"), select "**Add Fragment**".
4. Search for and select your site's header fragment, and press "**OK**".
5. All pages that use this template will now automatically inherit this header fragment.

If your site does not yet have a header fragment, please do the following.

1. Read and follow the steps in the **Fragments > Create a fragment** section of this documentation and choose "**Header**" as the module type for the fragment.
2. Continue with the steps in the section above.

## Change template theme
To set the default theme for all pages that use this template, follow these steps.

1. Expand the "**Body**" slot in the outline.
2. Select the page container module within it (example: "Default Page").
3. In the property panel on the right, locate the property settings dropdown selector titled, "**Theme**".
4. From the selector control choose a theme (example: "default").
5. All new pages will now default to this theme.  If you would like to restrict pages from overriding this setting at a layout or page level, set the "**Locked**" Boolean control to true.


## Add script to a template
HTML script tags containing JavaScript can be added to your template to provide default script behaviors to the HTML head, body begin, and body end of your pages.  To add a script to your template, follow these steps.

1. In the outline, select the slot where you would like your script tag to be added (HTML head, body begin, body end).
2. In the slot's action menu ("**...**"), choose "**Add Module**".
3. From the module picker modal, choose your desired script module (examples: External Script, Inline Script).
4. In the property panel on the right, enter your script into the script property control (examples: "Inline Script" or "Script tags").
5. Enter any other optional settings in the property panel that you wish to configure.

> [!TIP]
> Script modules that you want to re-use for other templates can be converted intto fragments for more efficient authoring and central updates.  To convert your script module into a fragment, follow the steps in the **Fragments > Save an existing module configuration as a fragment** article within this documentation.

## Save, check in, preview, and publish a template
To save your template, click the "**Save**" button in the action bar at the top of the template editor.  Saved changes will not affect downstream pages until they are "**Checked In**".  To check in your changes and make them discoverable for downstream workflows, click the "**Check In**" button in the action bar.

To preview your changes, either open an existing page that uses this template or create a new page from the template.  

Once you have previewed your template changes within a page preview context, there are multiple ways to publish the template to your live site.

* Publishing a page that references an unpublished template will automatically publish the template.
* Select the template in the templates list view (**Left navigation control > Templates > Selected template**) and click the "**Publish**" button in the top action bar.
* Go back to the template editor view and select "**Publish**" from the top action bar.

> [!WARNING]
>
> By definition, **publishing** a template (or any other CMS item) means that it is discoverable on the internet.  No not publish documents or assets until you wish to make them public.  Saved, and Checked In document versions are only discoverable to authenticated system users.
