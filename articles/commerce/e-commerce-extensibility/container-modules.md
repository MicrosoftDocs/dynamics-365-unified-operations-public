---
# required metadata

title: Container modules
description: Container modules can help control the layout for building complex modules or pages out of small component modules.  Example container modules may be a header, footer or a buy box module, which have nested modules inside. 
author: SamJarawan
manager: JeffBl
ms.date: 08/30/2019
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: SamJar
ms.search.validFrom: 2019-08-30
ms.dyn365.ops.version: 

---
# Container modules
Container modules can help control the layout for building complex modules or pages out of small component modules.  Example container modules may be a header, footer or a buy box module, which have nested modules inside.  There are two types of container modules, layout and page covered below.

Container modules can define 'slots' which are surfaced to template authors, you can think of these slots as regions inside the module.  Page authors can configure which modules go into each slot and the container module code is responsible for the html layout of those slots.  Configuration settings can also be exposed to page authors to further configure the layout of a container modules.  The container module is also responsible for building a responsive design to ensure the module looks great at any size be it a mobile screen or a full web browser.

Container Modules are created just like regular modules but will require a change to the `$type` inside the MODULE_NAME.definition.json file:`"$type": "containerModule"`

## Layout container modules
Layout container modules are useful when you need to make a complex module out of simple modules and control their layout.  An example may be a header layout container module that is made up of required an optional sub modules such as search, sign-in and navigation modules. The containers role is to provide an adaptive layout. 

## Page container modules
A page container contains the core structure for page authoring.  An example could be a page container with a slot defined for the header, main content area and footer area.  A page container is simply a module that controls the layout of a set of named slots.  A page container can only be imbedded at the root of a page.  Each page must have one and only one page container which is defined the master template.

Similarly to layout container modules, page container modules can define names slots which are surfaced to template authors.  Page authors can configure which modules go into each slot and the container render code controls the layout of those slots.  Configuration settings can also be exposed to page authors to further configure the layout.
