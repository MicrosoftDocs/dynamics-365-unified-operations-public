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

Modules are logical building blocks that make up your page structure, and they come in a variety of purposes and scopes. Some modules are high-level containers whose sole purpose is to organize other child modules. Other modules can have a very granular purpose, like a simple image placement module. And others, like a carousel module, fall somewhere in between. By default, your Commerce site comes with a starter kit module library that will enable you to achieve most basic e-Commerce scenarios. You should be able to construct an end-to-end e-Commerce site with just these modules, but a day will likely come when you want to customize or build brand-new modules for specific needs. For this, there is a module design software deveopment kit (SDK) available for your system integration or in-house front-end JavaScript/React developer to create a custom module library to suit those needs. A whole set of documentation is available to drill into the module SDK, but this article will stick to foundational module concepts focused around page authoring workflows.

## Container modules and “slots”

As mentioned above, some modules are designed to contain other child modules. This family of modules are aptly named "Containers" and they allow a hierarchy of nested modules within one another. Container modules utilize an authoring concept called "Slots," which communicate the layout and purpose for child modules within the container. A good example of this is a basic page container module (which is the top-level module for any given page) and defines several important slots: 1) a header slot, 2) a body slot, and 3) a footer slot. The module's developer defines these slots and determines which and how many child modules can be directly contained within it. The header slot might allow only one module of type Header Module, and the body slot might allow unlimited modules of any type (with the exception of another page container module). Within the authoring toolset, page authors don't need explicit knowledge of which modules are allowed or not allowed in each slot. When an author initially selects a slot and goes to pick a module to add, they will see a filtered view of module types that are supported for that slot. 

## Content modules

Content modules, as their name suggests, contain actual content and media primitives, such as text (headlines, paragraphs, links) or asset references (images, video, PDFs, etc.). Examples of common content module types are Hero, Feature, and Banner, each of which can contain text or media and don't require any further child modules to render something visible on a page. Content modules represent the majority of typical day-to-day page and content authoring activities, primarily because they define the actual content rendered within their parent container modules. There are many different content modules to choose from, and the main takeaway here is that content modules are generally the final pieces in your page's module nesting hierarchy.

The following diagram illustrates how modules nest into parent container module slots.
![Nesting Modules](../commerce/media/basic-module-nesting.png)

## Add or remove modules

### Add a module
To add a module to a slot or container within your page, do the following.

1. In the page editor, select a container or slot that allows a child module to be added to it.
> [!NOTE]
> The list of allowed modules types that can be added to a specific module slot is defined by the module developer. Template authors can then further refine the allowed module options to ensure SEO consistency and authoring efficiency for pages built from a specific template.
   
1. Click **Add Module** from the selected item's ellipsis button. The Add Module dialog box appears, and is automatically filtered to show only allowable modules for the chosen container or slot as determined by the page's template or the container module definition.
> [!NOTE]
> If the container or slot does not allow new child modules, the **Add Module** option will be disabled.

1. From the module options, search for and select one to add to your page. Click **OK** to add the new module to your page within the originally selected container or slot.

> [!TIP]
> Feature or Hero modules are good '*Hello World*' module types for beginners.

### Remove a module

To remove a module from a slot or container within your page, do the following.

1. In either the Outline View or the Canvas, click the ellipse button next to the name of the module you wish to remove.

2. In the actions drop-down menu, click the trashcan button. This should launch a confirmation dialog box asking if you are sure you want to remove the module.

3. Assuming you wish to remove it, click **OK** and the canvas will refresh without the deleted module.

## Configure modules

### Configure a content module

To configure a content module within your page, do the following.

1. Select a content module on your page by clicking on it in either the outline or canvas (examples: Feature, Hero, Banner, etc.).

1. Notice that the selected module's settings and content controls are displayed in the properties pane on the right. Expand any nested controls in the property panel by clicking on the headers. Set any required control values, which are indicated by “\*” and validation warnings.

1. If there is a **Data Configuration** section in the properties pane, click to expand it. If not, go to step 5.

1. If there is a **Add Data Source** dropdown button, click it and select any content items you want to add \[For ‘Feature’ or ‘Hero’ modules, add ‘Heading’ and ‘Image’ to begin with\].

1. Enter settings for any required or desired module controls.

1. In the Action Button bar above the canvas click the ‘Save’ button. This will refresh the canvas with your new module settings.

### Configure a container module

To configure a container module that is in your page:

1. Select a container module within your page (examples: Carousel, Fluid Container).

2. Notice that the selected module’s settings and content controls are displayed in the properties pane on the right. Expand some of the nested controls in the property panel by clicking on the headers. Set any required control values, which are indicated by “\*” or by validation warnings.

3. In either the Outline View or the Canvas, click the ellipse button (“…”) next to the container’s name or next to any slots within the container. The action menu will display and you can follow the same steps enumerated in the “Add a Module” section above to populate your selected container with child modules.

4. If multiple modules reside as siblings within container, re-ordering their display order within the parent container can be done by clicking the up and down arrow buttons within the module's action menu ("...")




