---
title: Work with templates
description: This article describes how to work with templates in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 05/28/2024
ms.topic: how-to
audience: Application User
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Work with templates

[!include [banner](includes/banner.md)]

This article describes how to work with templates in Microsoft Dynamics 365 Commerce.

As was discussed in [Templates and layouts overview](templates-layouts-overview.md), templates define the set of options that is available to downstream authors. Templates are useful to an enterprise's web authoring team for several reasons, and well-structured templates can help with all the following goals:

- Simplify the authoring experience for day-to-day content editor roles.

    - Filter module options so that only relevant modules are shown for a specific page section. (For example, a marketing section of a template can be configured to filter out irrelevant modules that should never be used in that context, and that will just complicate content authoring tasks if they are shown.)
    - Configure default module setting to help improve authoring efficiency.
    - Define default page fragments to help improve authoring efficiency. (For example, header and footer fragments in a template will automatically appear on every downstream page.)

- Keep enterprise sites on-brand by defining an approved set of module arrangement and configuration options.

    > [!TIP] 
    > Successful e-commerce sites provide customers with familiar, repeatable, and on-brand user experience (UX) design patterns. By using templates, you help control consistency across your site.

- Improve search engine optimization (SEO) scores by ensuring repeatable and programmatically defined page definitions and metadata.

> [!NOTE]
> Although templates are designed to control consistency across a site, they can theoretically be configured so that they don't enforce any consistency. Brand and site administrators can define any level of variability for the pages on their site. For example, a template can be left entirely open, so that content authors can create any page design that they choose. In this case, none of the benefits in the preceding list are applicable.

## Modify a template

Templates are modified by using the template editor.

To open the template editor in Commerce site builder, follow one of these steps:

- In the navigation pane of your site, select **Templates**, and then select the template to modify.
- In the page editor for an existing page, select the top node in the outline tree on the left. Then, in the property pane on the right, select **Edit Template**.

The outline tree view on the left shows the module options and structures that are available to child layouts and pages. When you select a module in the outline tree, you can view the template properties for the selected module in the property pane on the right. Some of these properties are unique to template editing. The following table describes these properties.

| Property name | Description |
|---|---|
| Min Occurs | This property defines the minimum number of occurrences for the selected module. For example, if the value is set to **1**, the module is required for downstream authors, whereas if the value is set to **0** (zero), the module is optional. |
| Max Occurs | This property defines the maximum number of occurrences for the selected module. For example, if the value is set to **1**, the module can be added only one time. |
| Min Modules (Containers) | For modules that contain other modules (that is, for *containers modules*), this property defines the minimum number of total modules that should be added as children. For example, for a carousel module, the value might be set to a number that is more than 1. |
| Max Modules (Containers) | For container modules, this property defines the maximum number of total modules that should be added as children. For example, for a carousel module, the value might be set to a number that is less than 10. |
| Locked | A **Locked** Boolean control appears next to all core module properties. It lets the template author lock a module setting in the template. A module setting that is locked can't be overridden by any child layouts or pages. It becomes a centrally editable property value for all layouts and pages that use the template. |

## Create a new template

To create a new template in site builder, follow these steps.

1. In the navigation pane of your site, select **Templates** to open the template inspector view.
1. Select **New Template**.
1. In the template creation dialog box, enter a name and description for the template. The values that you enter will be shown to authors when they create new pages. Therefore, enter metadata that will be useful to page authors. For example, enter **Use this template to create general marketing pages** as the description. This metadata can be edited later.
1. Select **OK** to create the new template and open the template editor. The template editor shows an outline tree on the left and a property pane on the right.
1. In the outline tree, expand the nodes, and select the **HTML Head** slot.
1. If there aren't yet any modules in this slot, select the ellipsis button (**...**), and then select **Add Module**.
1. In the **Add Module** dialog box, select **Default page summary**, and then select **OK**.
1. In the outline tree, select the new module, and then, in the property pane, enter any default settings that should be automatically configured for all child pages of the template. If you don't want any default settings, leave the values blank.
1. In the outline tree, select the **Body** slot, select the ellipsis button, and then select **Add Module**.
1. Select a page container module (there might be only one option), and then select **OK**.

Under the new page container module, you will see a new set of slots (**Header**, **Main**, and so on). Here, you can add and configure the module options that will be available to authors when they create pages from this template. By default, if you don't add any modules to a slot, all available modules types are supported for that slot.

The template is now technically valid, and it can be saved, checked in, and used to create new pages. However, the next three sections describe some other default settings that you might want to configure first.

## Add a header and a footer

If your site already has a header fragment, follow these steps in site builder to add a header and a footer to a template.

1. In the outline tree, expand the **Body** slot and its child page module.
1. Select the **Header** slot.
1. Select the ellipsis button for the **Header** slot, and then select **Add Fragment**.
1. Search for and select your site's header fragment, and then select **OK**.

All pages that use the template will now automatically inherit this header fragment.

If your site doesn't yet have a header fragment, see [Create a fragment](work-with-fragments.md#create-a-fragment) for information about how to create it, and then complete the previous procedure.

## Change the template theme

To set the default theme for all pages that use a template, follow these steps in site builder.

1. In the outline tree on the left, expand the **Body** slot.
1. In the **Body** slot, select the page container module (for example, **Default Page**).
1. In the property pane on the right, in the **Theme** field, select a theme.

By default, all new pages will now use the selected theme. To prevent pages from overriding this setting at the layout or page level, set the **Locked** Boolean control to **True**.

## Add a script to a template

You can add HTML **&lt;script&gt;** elements that contain JavaScript to your template. In this way, you can provide default script behaviors to the HTML head, body begin, and body end sections of your pages.

To add a script to a template in site builder, follow these steps.

1. In the outline tree on the left, select the slot where you want to add the **&lt;script&gt;** element (for example, the HTML head, body begin, or body end).
1. Select the ellipsis button for the slot, and then select **Add Module**.
1. In the **Add Module** dialog box, select a script module (for example, **External Script** or **Inline Script**).
1. In the property pane on the right, in the appropriate script property control (for example, **Inline Script** or **Script tags**), enter your script.
1. In the property pane, enter any other optional settings that you want to configure.

> [!TIP]
> If you want to reuse any of your script modules for other templates, you can convert them to fragments. In this way, you help make the authoring process more efficient, and you centralize the update process. For information about how to convert a script module to a fragment, see [Save an existing module configuration as a fragment](work-with-fragments.md#save-an-existing-module-configuration-as-a-fragment).

## Save, check in, preview, and publish a template

To save and check in a template in site builder, follow these steps.

1. Select **Save** at the top of the template editor. Saved changes don't affect downstream pages until they are checked in.
1. Select **Finish editing**. Your changes are now discoverable for downstream workflows.

To preview your changes, either open an existing page that uses the template or create a new page from the template.

After you've previewed the changes to your template, follow one of these steps to publish the template to your live site:

* Go to **Templates**, select the template, and then select **Publish**.
* Select the layout name to open the layout editor, and then select **Publish**.
* Publish a page that references the unpublished template. The template is automatically published.

> [!WARNING]
> When a template, or any other content management system (CMS) item, is published, it's discoverable on the internet. Don't publish documents or assets until you're ready to make them public. Document versions that have been saved and checked in, but that haven't been published, are discoverable only to authenticated system users.

## Rename a template

To rename an existing template in site builder, follow these steps.

1. In the left navigation pane, select **Templates**.
1. Select the template name of the template that you want to rename.
1. Select **Edit** to start editing the template. Note that you cannot edit a template if someone else is already editing the template.
1. In the template properties pane, select the pen symbol next to the template name.
1. Edit the template name as needed.
1. Select the check mark to confirm the name change.
1. Select **Finish editing**.

## Additional resources

[Templates and layouts overview](templates-layouts-overview.md)

[Work with preset layouts](work-with-layouts.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
