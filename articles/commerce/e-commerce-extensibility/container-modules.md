---
# required metadata

title: Container modules
description: In Dynamics 365 for Commerce, container modules can help control the layout for building complex modules or pages out of small component modules.  
author: SamJarawan
manager: annbe
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
Container modules can help control the layout for building complex modules or pages out of small component modules. For example, container modules may be a header, footer, or a buy box module, which have nested modules inside. 

Container modules can define "slots" which are surfaced to template authors, where slots can be thought of as regions inside the module. Page authors can configure which modules go into each slot. The container module code is responsible for the html layout of the slots. 

Configuration settings can also be exposed to page authors to further configure the layout of container modules. The container module is also responsible for building a responsive design to ensure the module looks great at any size, be it a mobile screen or a full web browser.

Container modules are created just like regular modules, but require a change to the `$type` inside the MODULE_NAME.definition.json file:`"$type": "containerModule"`.

There are two types of container modules: layout and page container modules.

## Layout container modules
Layout container modules are useful when you need to make a complex module out of a number of simple modules, and you want to control their layout. For example, you can use a header layout container module that is made up of required or optional sub-modules such as search, sign-in, and navigation modules. The role of the container is to provide an adaptive layout. 

## Page container modules
Page container modules contain the core structure for page authoring. For example, you can create a page container with a slot defined for the header, main content area, and footer area. A page container is simply a module that controls the layout of a set of named slots. A page container can only be embedded at the root of a page. Each page must have only one page container, which is defined the master template.

Similar to layout container modules, page container modules can define names slots which are surfaced to template authors. Page authors can configure which modules go into each slot and the container render code controls the layout of those slots. Configuration settings can also be exposed to page authors to further configure the layout.
