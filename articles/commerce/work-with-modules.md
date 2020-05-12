---
# required metadata

title: Work with modules
description: This topic describes how and when to use modules in Microsoft Dynamics 365 Commerce.
author: v-chgri
manager: annbe
ms.date: 01/31/2020
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
ms.author: phinneyridge
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Work with modules

This topic describes how and when to use modules in Microsoft Dynamics 365 Commerce.


[!include [banner](includes/banner.md)]

## Overview

Modules are logical building blocks that make up your page structure, and they have various purposes and scopes. Some modules are high-level containers, and their only purpose is to hold and organize other modules (child modules). Other modules, such as a simple image placement module, have a very specific purpose. Other modules, such as a carousel module, fall somewhere between those two categories.

By default, your Dynamics 365 Commerce site includes a starter kit module library that lets you achieve most basic e-Commerce scenarios. You should be able to construct an end-to-end e-Commerce site just by using these modules. However, you might also want to customize these modules or build new, custom modules for specific needs. If you want to build custom modules, a module design software development kit (SDK) is available to help you create a custom module library.

## Container modules and slots

As was mentioned earlier, some modules are designed to hold child modules. These modules are known as *containers*, and they allow for hierarchies of nested modules. Container modules include *slots*. Slots are used to handle the layout and purpose of child modules in the container. An example is a basic page container module (a top-level module for any page) that defines several important slots:

- A header slot
- A body slot
- A footer slot

The module's developer defines these slots, and determines which child modules and how many child modules can be put directly inside it. For example, the header slot might support only one module of the **Header Module** type, whereas the body slot might support an unlimited number of modules of any type (except other page container modules).

In the authoring tools, page authors don't have to know in advance which modules can and can't be put in each slot. When page authors select a slot and then try to select a module to add to it, they see a filtered view of module types that are supported for that slot.

## Content modules

Content modules contain content and media elements, such as text (for example, headlines, paragraphs, and links) or asset references (for example, images, video, and PDFs). Examples of typical content module types are **Hero**, **Feature**, and **Banner**. Modules of these three types can contain text or media, and they don't require any child modules to make something visible on a page.

The majority of typical, day-to-day page and content authoring activities involve content modules, primarily because these modules define the actual content that is rendered in their parent container modules. Many content modules are available, and these modules are typically the last pieces that you will add to a page's hierarchy of nested modules.

The following illustration shows how modules are nested inside parent container module slots.

![Nesting modules](../commerce/media/basic-module-nesting.png)

## Add or remove modules

The following procedures describe how to add and remove modules.

### Add a module

To add a module to a slot or container on a page, follow these steps.

1. In the outline pane on the left, select a container or slot that a child module can be added to.

    > [!NOTE]
    > The module designer defines the list of modules types that can be added to a specific module slot. Template authors can then refine the allowed module options to help guarantee consistent search engine optimization (SEO) and authoring efficiency for all the pages pages that are built from a specific template.

1. Select the ellipsis button (**...**) for the module, and then select **Add Module**. The **Add Module** dialog box appears. This dialog box is automatically filtered so that it shows only modules that are supported in the selected container or slot. The list of modules is determined by the page's template or the container module definition.

    > [!NOTE]
    > If a container or slot doesn't support new child modules, the **Add Module** option is unavailable.

1. In the dialog box, search for and select a module to add to your page.

    > [!TIP]
    > **Feature** and **Hero** are good module types for beginners to work with.

1. Select **OK** to add the selected module to the selected container or slot on your page.

### Remove a module

To remove a module from a slot or container on a page, follow these steps.

1. In the outline pane on the left, select the ellipsis button next to the name of the module to remove, and then select the trash can button.
1. When you're prompted to confirm that you want to remove the module, select **OK**.

## Configure modules

The following procedures describe how to configure content and container modules.

### Configure a content module

To configure a content module on a page, follow these steps.

1. In the outline pane on the left, expand the tree and select any content module (for example, **Feature**, **Hero**, or **Banner**).
1. In the properties pane on the right, find the module's content and settings controls.
1. Enter properties for any desired module controls.
1. Select **Save** in the command bar. This will also refresh the preview canvas.

### Configure a container module

To configure a container module on a page, follow these steps.

1. Select a container module on your page (for example, a carousel or fluid container module).
1. In the properties pane on the right, expand the nested controls by selecting the headers, and set any required control values.
1. In the outline pane on the left, select the ellipsis button next to the name of either the container or any slots inside the container, and then select **Add Module**. Then, add child modules to the selected container. For more information, see the [Work with modules](#add-a-module) section earlier in this topic.
1. If multiple child modules exist as siblings in a parent container, you can change their display order in the parent container. Select the ellipsis button for a module, and then use the up arrow and down arrow buttons.

## Additional resources

[Templates and layouts overview](templates-layouts-overview.md)

[Work with templates](work-with-templates.md)

[Work with preset layouts](work-with-layouts.md)

[Work with fragments](work-with-fragments.md)

[Add a container module to a page](add-container-module.md)

[Work with publish groups](publish-groups.md)

