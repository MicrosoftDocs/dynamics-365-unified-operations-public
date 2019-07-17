---
# required metadata

title: e-Commerce components
description: This topic contains a high level summary of the common e-Commerce configuration components that you'll have access to with the e-Commerce SDK in Dynamics 365 for Commerce. 
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
# e-Commerce components
This topic contains a high level summary of the common e-Commerce configuration components that you'll have access to with the Dynamics 365 for Commerce e-Commerce SDK. 

## Modules
Modules represent the core building blocks that make up an e-Commerce page. Some examples of modules include: a feature module that is being featured on a page and displays a product image and description with a call to action button to purchase or get more info; a hero module which highlights a campaign or provides marketing information; a header module made up of smaller module components such as a search module, a sign-in module, and a navigation module.

## Module configuration fields
Each module can expose configuration fields that are surfaced on the authoring page. The configuration fields are generally used for module settings or layout options. For example, you can use an image alignment field that allows the page author to set the the alignment to left, center, and right inside the module, or a title string to display a heading in a module. The module code would read this value and create the appropriate html in the view. Multiple values are supported, including boolean, numbers, strings, rich text, enumerators, images, and video.

## Data ations
Data actions are used to acquire data and apply business logic to a module. 

### Core data actions
A set of data actions is included in the e-Commerce platform to perform common actions such as getting product data from the Dynamics 365 for Commerce database or get ratings and review information for a product. Core data actions cannot be modified.

### Custom data actions
Custom data actions can be created to be used within your modules. Custom data actions can be globally scoped to use across multiple modules or within a single module. Core data actions can call Dynamics 365 for Commerce proxy APIs (or any other service provider) to get retail data. Custom business logic can be applied as required or call any web service.

## Themes
Themes contain site CSS and allow you to add custom module CSS. A site theme can be set in the authoring tools so that all pages will use the theme by default. Additional themes can be added and set on a master or shared template or a specific page. This is useful if you want to change the theme for a campaign or for a temporary seasonal change, and can be set on the whole site or a subset of pages.

## Script injectors
The e-Commerce platform provides a built in script injector module that allows easy script injection into the head, bodybegin, etc. from within the admin tool. Script injectors make it very simple to add script, for example, 3rd party analytics. You may have advanced requirements to inject custom html within your e-Commerce site with custom script injector modules.
