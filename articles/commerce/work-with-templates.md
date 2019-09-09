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
Templates are modified using the template editor. 

To enter the template editor, do one the following.

- In the navigation pane of your site, click **Templates**, then select the template you want to modify.

  -or-

- In the page editor for an existing page, select the top node in the outline tree on the left. Then in the right-side property pane, click **Edit Template**.

The outline tree view on the left shows the module options and structures that are available to child layouts and pages. When you select a module in the outline tree, you can view the template properties for the selected module in the property pane on the right. You will notice some unique properties that are specific to template editing, such as those listed in the following table.

  | Property name | Description |
  | ---- | --- |
  | Min Occurs | Sets the minimum number of occurrence of the the selected module. For example, setting "Min Occurs" = 1 makes the module required, whereas setting it = 0 makes the module optional for downstream authors. |
  | Max Occurs | Sets the maximum number of occurrences for the selected module. For example, setting "Max Occurs" = 1 means that the module can only be added once. |
  | Min Modules (Containers) | Modules that contain other modules (containers modules) can set the minimum number of total modules that should be added as children. For example, a carousel module might define that the minimum number of child modules is greater than 1. |
  | Max Modules (Containers) | Modules that contain other modules (container modules) can set the maximum number of total modules that should be added as children. For example, a carousel module might define that the maximum number of child modules is less than 10. |
  | Locked | You will notice a boolean control titled "locked" next to all core module properties. This allows the template author to lock a module setting in the template that can't be overridden by any child layouts or pages. A locked module setting becomes a centrally editable property value for all layouts and pages that use the template. |
   
## Create a new template

To create a new template, do the following.

1. In the navigation pane of your site, click **Templates**. This will bring you to the template inspector view.
1. Click **New Template**. This will launch the template creation dialog box.
1. Enter a name and description for the template. This will be shown to authors during new page creation workflows, so enter metadata that would be useful to page authors (for example, "Use this template to create general marketing pages"). This metadata can always be edited later.
1. Click "**OK**" to create the new template and navigate into the template editor. The template editor will show an outline tree on the left, and a property pane on the right.
1. Expand the nodes in the outline and select the **HTML Head** slot. If there are no modules yet in this slot, click the ellipsis menu (**...**) and select **Add Module**.
6. In the **Add Module** dialog box, select **Default page summary**, then click **OK**.
7. With the new module selected in the outline, enter any default settings in the property pane that you want to automatically populate for all child pages of the template. If you don't want any defaults, leave the values blank.
8. In the outline tree, select the **Body** slot, click the ellipsis button (**...**), then select **Add Module**.
9. Select a page container module (there may only be one option) and click **OK**.

Under this new page container module you will see a new set of slots (Header, Main, etc.). This is where you can add and configure module options that are available to authors when creating pages from this template. If you add no modules to a slot, then the default behavior is to allow all available modules types for that slot.

The template is now technically valid, and can be saved, checked in, and used for creating new pages. But as you will see below, there are some other defaults you will likely want to configure first.

## Add headers and footers

If your site already has a header fragment, to add a header and footer to a template, do the following.

1. In the outline tree, expand the **Body** slot and its child page module.
2. Select **Header** slot.
3. In the header slot, click the ellipsis button (**...**), then select **Add Fragment**.
4. Search for and select your site's header fragment, then click **OK**.

All pages that use this template will now automatically inherit this header fragment.

If your site does not yet have a header fragment, see [Create a fragment](fragments.md#create-a-fragment), then continue with the steps above.

## Change template theme

To set the default theme for all pages that use a template, do the following.

1. Expand the "**Body**" slot in the outline tree.
1. Select the page container module within it (for example, "Default Page").
1. In the property pane on the right, click the **Theme** dropdown menu, then select a theme.

All new pages will now default to this theme.  If you would like to restrict pages from overriding this setting at a layout or page level, set the "**Locked**" Boolean control to true.

## Add script to a template

HTML script tags containing JavaScript can be added to your template to provide default script behaviors to the HTML head, body begin, and body end sections of your pages. 

To add a script to your template, do the following.

1. In the outline, select the slot where you want to add the script tag (for example, HTML head, body begin, or body end).
1. Click the slot's ellipsis button (**...**), then select **Add Module**.
1. From the Add Module dialog box, select the desired script module (for example, "External Script" or "Inline Script").
1. In the property pane on the right, enter your script into the script property control (for example, "Inline Script" or "Script tags").
1. Enter any other optional settings in the property pane that you wish to configure.

> [!TIP]
> Script modules that you want to reuse for other templates can be converted into fragments for more efficient authoring and centralized updating. To convert your script module into a fragment, see [Save an existing module configuration as a fragment](fragments.md#save-an-existing-module-configuration-as-a-fragment).

## Save, check in, preview, and publish a template

To save and check in your template, do the following.

1. Click **Save** at the top of the template editor. Saved changes will not affect downstream pages until they are checked in.  
1. Click **Check In**. Changes are now discoverable for downstream workflows.

To preview your changes, either open an existing page that uses the template or create a new page from the template.  

Once you have previewed your template changes within a page preview context, there are multiple ways to publish the template to your live site.


* Go to **Templates**, select the template, then click **Publish**.

-or-

* From the template editor, click **Publish**.

-or-

* Publish a page that references the unpublished template. This will automatically publish the template.

> [!WARNING]
>
> By definition, **publishing** a template (or any other CMS item) means that it is discoverable on the internet. Do not publish documents or assets until you wish to make them public. Saved and checked-in document versions are only discoverable to authenticated system users.
