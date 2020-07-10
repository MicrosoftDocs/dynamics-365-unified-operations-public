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

- **A header slot**
- A sub-header slot
- **A main slot**
- A sub-footer slot
- **A footer slot**

The module's developer defines these slots, and determines which child modules and how many child modules can be put directly inside it. For example, the header slot might support only one module of the **Header Module** type, whereas the body slot might support an unlimited number of modules of any type (except other page container modules).

In the authoring tools, page authors don't have to know in advance which modules can and can't be put in each slot. When page authors select a slot and then try to select a module to add to it, they see a filtered view of module types that are supported for that slot.

## Content modules

Content modules contain content and media elements, such as text (for example, headlines, paragraphs, and links) or asset references (for example, images, video, and PDFs). Examples of typical content module types are **Content blocks, Rich text, or Banners***. Modules of these three types can contain text or media, and they don't require any child modules to make something visible on a page.

The majority of typical, day-to-day page and content authoring activities involve content modules, primarily because these modules define the actual content that is rendered in their parent container modules. Many content modules are available, and these modules are typically the last pieces that you will add to a page's hierarchy of nested modules.

The following illustration shows how modules are nested inside parent container module slots.

![Nesting modules](../commerce/media/basic-module-nesting.png)

## Add or remove modules

The following procedures describe how to add and remove modules.

### Add a module

To add a module to a slot or container on a page, follow these steps.

1. In the outline pane on the left, or directly in the main canvas, select a container or slot that a child module can be added to.

    > [!NOTE]
    > The module designer defines the list of modules types that can be added to a specific module slot. Template authors can then refine the allowed module options to help guarantee consistent search engine optimization (SEO) and authoring efficiency for all the pages pages that are built from a specific template.

1. If using the outline pane, select the ellipsis button (**...**) for the module, and then select **Add Module**. If using the controls directly within the canvas, click the **"+"** icon in an empty slot or adjacent to the currently selected module and select **Add module"** from the menu.  The **Add Module** dialog box appears. This dialog box is automatically filtered so that it shows only modules that are supported in the selected container or slot. The list of modules is determined by the page's template or the container's module definition.

    > [!NOTE]
    > If a container or slot doesn't support new child modules, the **Add Module** option is unavailable.

1. In the dialog box, search for and select a module to add to your page.

    > [!TIP]
    > **Content Block** is a good module type for beginners to work with.

1. Select **OK** to add the selected module to the selected container or slot on your page.

### Remove a module

To remove a module from a slot or container on a page, follow these steps.

1. In the outline pane on the left, select the ellipsis button next to the name of the module to remove, and then select the trash can button.  Alternately, you can click the trash can button on a selected module's toolbar directly in the main canvas.
2. When you're prompted to confirm that you want to remove the module, select **OK**.

## Move modules to a new position

To move a module to a new position within your page, use any of the following methods:

### Move a module using the outline pane

1. Left click and hold down the mouse button on the module you wish to move in the outline pane.
2. Drag the module to a new position in the outline. 
3. The blue line in the outline and on the canvas indicates where the module can be placed.
4. Let go of the mouse button to drop the module into the new position.

### Move a module directly within the canvas

1. Select the module you wish to move in the canvas. 
2. Left click on the **Move** icon in the module's toolbar and hold down the mouse button.
3. Drag the module to a new position on the page.
4. The blue line in the canvas and outline indicates where the module can be placed.
5. Let go of the mouse button to drop the module into the new position.

### Move a module using buttons in the **...** drop-down

1. Select a module in either the outline or the canvas.
2. Click the **...** button next to the module in the outline, or in the module's toolbar in the canvas.
3. If the module can be moved up or down within the container or slot, you will see options for **Move up** or **Move down**.  Select the desired move action to move the module up or down relative to its siblings.


## Configure modules

The following procedures describe how to configure content and container modules.

### Configure a content module

To configure a content module on a page, follow these steps.

1. In the outline pane on the left, expand the tree and select any content module (for example, **Content Block**).  Alternately, simply click on the module within the main canvas.
1. In the properties pane on the right, find the module's content and settings controls.
1. Enter properties for any desired module controls.
1. Select **Save** in the command bar. This will also refresh the preview canvas.

#### In-line text editing

Module text properties that are not read-only can be edited directly within the canvas.  To edit module text, follow these steps:

1. Click on the text control in the canvas to select it.
2. Click again to place your cursor where you wish to begin typing.
3. Enter your text content.
4. Click outside the text content to continue editing other content.

#### In-line image selection

Module images that are not read-only can be changed directly from the canvas.  To choose a new image for a content module, follow these steps:

1. Double click on the image in the canvas.
2. This will bring up the media picker modal window.
3. Find and select a new image you want to use and click **Ok**.
4. The new image is rendered in the canvas.

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

