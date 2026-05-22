---
title: Work with fragments
description: Learn how to use fragments in Microsoft Dynamics 365 Commerce.
author: phinneyridge
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Work with fragments 

[!include [banner](includes/banner.md)]

This article describes how to use fragments in Microsoft Dynamics 365 Commerce.

Fragments provide a centralized authoring experience for module configurations that you need to reuse throughout your site. For example, you often configure headers, footers, and banners as fragments, because they're shared across many pages. You can think of fragments as miniature webpages that you can insert into other pages on your site. Fragments have their own lifecycle. In other words, you create, reference, update, and delete them as independent entities in the authoring tools.

After you configure fragments, use them wherever you can use modules in your site structure. You can reference fragments on pages, in layouts, in templates, and in other fragments.

> [!NOTE]
> You can nest fragments up to seven levels deep inside other fragments.

For example, if you want to promote a seasonal event across many pages on your site, use a fragment. The first step in the process of creating a new fragment is to select the type of module that you want to start from. For this example, you can build the fragment from a hero module.

> [!NOTE]
> You can build fragments from any module type.

Next, configure the hero fragment with your specific promotional content. You can also localize it as you require. The new stand-alone hero fragment can then be consumed as a preconfigured module throughout your site. You can easily add it to templates, to specific pages, or to other fragments that can contain hero modules.

All the places where you add the fragment are references to the central hero fragment that you created. If you publish changes to the fragment, those changes immediately appear in all the places where the fragment is referenced across the site. Therefore, fragments provide a powerful and efficient way to reuse and centrally manage module configurations on a site. By effectively using them, you can significantly increase agility and help reduce the cost that is associated with managing site content.

The following illustration shows how fragments can be used to centralize authoring of shared module configurations across an e-Commerce site.

:::image type="content" source="./media/fragment-figure1.png" alt-text="Screenshot of how fragments can be used to centralize authoring of shared module configurations across an e-commerce site.":::

## Create a fragment

You can either create a new fragment or save an existing module configuration as a fragment.

### Save an existing module configuration as a fragment

To convert a previously configured module to a reusable fragment in Commerce site builder, follow these steps:

1. Open a page or template that contains the module that you want to convert to a fragment.
1. In the outline pane on the left or directly in visual page builder, select the previously configured module.
1. Select the ellipsis (**...**) next to the name of the module in either the outline pane or the selected module's toolbar in visual page builder. 
1. Select **Share as fragment**. 
1. In the **Save as fragment** dialog box, enter a name for the fragment.
1. Select **OK** to save the module configuration as a fragment that you can add to other pages.

### Create a new fragment

To create a new fragment in Commerce site builder, follow these steps:

1. In the navigation pane on the left, select **Fragments**.
1. Select **New**. A **New fragment** dialog box appears that shows all the available module types. As mentioned earlier, you can create fragments from any module type.
1. Select a module type for your fragment.

## Add, remove, or edit fragments on a page

The following procedures describe how to add, remove, and edit fragments.

### Add a fragment

To add a fragment to a page in Commerce site builder, follow these steps:

1. In the outline pane on the left or directly in visual page builder, select a container or slot to which you can add child modules.
1. Select the ellipsis (**...**) next to the name of the container or slot. Alternatively, if you're using visual page builder, select the plus symbol (**+**).  
1. Select **Add fragment**.
 
    > [!NOTE]
    > If the container or slot doesn't support new child modules, the **Add fragment** option is unavailable.
  
1. In the **Select fragment** dialog box, search for and select a fragment to add. If no available fragments are listed, you might first have to create a fragment from a module type that the selected container or slot supports.
1. Select your desired fragment to add it to the container or slot on your page.

> [!NOTE]
> The page's template or the modules' own definitions define which modules are allowed in a container or slot.

### Remove a fragment

To remove a fragment from a slot or container on a page in Commerce site builder, follow these steps:

1. In the outline pane on the left, select the ellipsis (**...**) next to the name of the fragment to remove, and then select the trash can symbol. Alternatively, you can select the fragment in visual page builder and select the trash can symbol in the fragment's toolbar.
1. When you're prompted to confirm that you want to remove the fragment, select **OK**.

> [!NOTE]
> When you remove a fragment from a page, you just remove the reference to it from that page. You don't delete the fragment from your site. To delete fragments from your site, use the fragment inspector user interface (UI). You can delete fragments from a site only if no pages, templates, or other fragments reference them.

### Edit a fragment

To edit a fragment in Commerce site builder, follow these steps:

1. In the navigation pane on the left, select **Fragments**.
1. Under **Fragments**, select the fragment to edit.
1. Edit the fragment's module properties and structure as needed. The process resembles the process for editing modules in the page editor view.

You can also edit a fragment by selecting it on a page, in a template, or in a parent fragment. Then, select **Edit Fragment** in the properties pane on the right.

### Rename a fragment

To rename an existing fragment in site builder, follow these steps:

1. In the left navigation pane, select **Fragments**.
1. Select the fragment name that you want to rename.
1. Select **Edit** to start editing the fragment. You can't edit a fragment if someone else is already editing the fragment.
1. In the fragment properties pane, select the pen symbol next to the fragment name.
1. Edit the fragment name as needed.
1. Select the check mark to confirm the name change.
1. Select **Finish editing**.

You can rename a fragment after you create it by editing the fragment and then selecting the pen symbol next to the fragment name in the property pane.

## Additional resources

[Templates and layouts overview](templates-layouts-overview.md)

[Work with templates](work-with-templates.md)

[Work with preset layouts](work-with-layouts.md)

[Work with publish groups](publish-groups.md)

[View version history to revert pages and fragments](version-history-revert.md)

[!INCLUDE[footer-include](../includes/footer-banner.md)]
