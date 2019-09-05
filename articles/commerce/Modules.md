---
# required metadata

title: Work with modules
description: This topic describes how and when to use modules in Dynamics 365 Commerce.
author: Nick Holman
manager: Brendan Sullivan
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
ms.author: phinneyridge
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---

# Work with modules

This topic describes how and when to use modules in Dynamics 365 Commerce.

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

## Overview

Modules are logical building blocks that make up your page structure, and they come in a variety of purposes and scopes. Some modules are high-level containers whose sole purpose is to organize other child modules. Other modules can have a very granular purpose, like a simple image placement module. And others, like a carousel module, fall somewhere in between. By default, your Commerce site comes with a starter kit module library that will enable you to achieve most basic e-Commerce scenarios. You should be able to construct an end-to-end e-Commerce site just using these modules, but you may want to customize or build brand-new modules for specific needs. To build custom modules, there is a module design software development kit (SDK) available to create a custom module library. 

## Container modules and "slots"

As mentioned above, some modules are designed to contain other child modules. This family of modules are named *containers* and they allow hierarchies of nested modules to be contained within one another. Container modules use *slots*, which handle the layout and purpose of child modules within the container. A good example of this is a basic page container module (a top-level module for any given page) that defines several important slots: 1) a header slot, 2) a body slot, and 3) a footer slot. The module's developer defines these slots and determines which and how many child modules can be directly contained within it. For example, the header slot might allow only one module of type Header Module, and the body slot might allow unlimited modules of any type (with the exception of another page container module). Within the authoring toolset, page authors don't need explicit knowledge of which modules are allowed or not allowed in each slot. When an author initially selects a slot and goes to pick a module to add, they will see a filtered view of module types that are supported for that slot. 

## Content modules

Content modules contain content and media elements such as text (headlines, paragraphs, links) or asset references (images, video, PDFs, etc.). Examples of common content module types are Hero, Feature, and Banner, each of which can contain text or media and don't require any further child modules to render something visible on a page. Content modules represent the majority of typical day-to-day page and content authoring activities, primarily because they define the actual content rendered within their parent container modules. There are many different content modules to choose from, and content modules are generally the final pieces added to your page's module nesting hierarchy.

The following diagram illustrates how modules nest into parent container module slots.
![Nesting Modules](../commerce/media/basic-module-nesting.png)

## Add or remove modules

The following procedures describe how to add and remove modules. 

### Add a module
To add a module to a slot or container within your page, do the following.

1. In the left-side outline pane, select a container or slot that allows a child module to be added to it.
> [!NOTE]
> The list of allowed modules types that can be added to a specific module slot is defined by the module developer. Template authors can then further refine the allowed module options to ensure SEO consistency and authoring efficiency for pages built from a specific template.
   
1. Click **Add Module** from the selected item's ellipsis button. The Add Module dialog box appears, and is automatically filtered to only show modules allowed for the chosen container or slot as determined by the page's template or the container module definition.
> [!NOTE]
> If the container or slot does not allow new child modules, the **Add Module** option will be disabled.

1. From the dialog box, search for and select a module to add to your page. Click **OK** to add the new module to your page within the originally selected container or slot.

> [!TIP]
> Feature or Hero modules are good '*Hello World*' module types for beginners.

### Remove a module

To remove a module from a slot or container within your page, do the following.

1. In the left-side outline pane, click the ellipsis button next to the name of the module you wish to remove.

1. In the drop-down menu, select the trashcan button. This should launch a confirmation dialog box asking if you are sure you want to remove the module.

1. Click **OK** to remove the module.

## Configure modules

The following procedures describe how to configure content and container modules. 

### Configure a content module

To configure a content module within your page, do the following.

1. In the left-side outline pane, select a content module (for example, Feature, Hero, or Banner).

1. In the right-side properties pane, expand nested controls by clicking on the headers and set any required control values.

1. If there is a **Data Configuration** section in the properties pane, click to expand it. If not, go to step 5.

1. If there is a **Add Data Source** dropdown button, click it and select any content items you want to add.

1. Enter settings for any required or desired module controls.

1. Click **Save**.

### Configure a container module

To configure a container module within your page, do the following.

1. Select a container module within your page (for example, Carousel or Fluid Container).

1. In the right-side properties pane, expand nested controls by clicking on the headers and set any required control values.

1. In the left-side outline pane, click the ellipsis button next to the container name or next to any slots within the container. The drop-down menu will appear and you can then follow the same steps enumerated in the "Add a Module" procedure above to populate your selected container with child modules.

1. If multiple modules reside as siblings within a container, reordering their display order within the parent container can be done by clicking the up and down arrow buttons within the module's ellipsis button drop-down menu.




