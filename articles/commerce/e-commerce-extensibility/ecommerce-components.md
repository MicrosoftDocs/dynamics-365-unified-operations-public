---
# required metadata

title: e-Commerce components
description: This topic contains a high level summary of the common e-Commerce configuration components that you'll have access to with the e-Commerce SDK. 
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
# E-Commerce components
This topic contains a high level summary of the common e-Commerce configuration components that you'll have access to with the e-Commerce SDK. 

## Modules
Modules represent the core building blocks that make up an e-Commerce page.  Examples include a feature module which displays a product image and description that is being featured on a page with a call to action button to purchase or get more info, a hero module which  campaign or marketing information and a header module which is made up of smaller module components such as a search module, a sign-in module and a navigation module.

## Module Configuration Fields
Each module can expose configuration fields that are surfaced on the authoring page.  These configuration fields are generally used for module settings or layout options.  An example would be an image alignment field that allows the page author to set the the alignment to left, center and right inside the module or a title string to display a heading in a module.  The module code would read this value and create the appropriate html in the view.  Multiple types are supported including boolean, numbers, strings, rich text, enumerators, images or video.

## Data Actions
Data Actions are used to acquire data and apply business logic that a module needs. 

### Core Data Actions
A set of data actions is included in the e-Commerce platform to perform common actions such as getting product data from Dynamics 365 Commerce Retail database or get ratings and review information for a product.  Core data actions cannot be modified.

### Custom Data Actions
Custom data actions can be created to be used within your modules.  They can be globally scoped to use across multiple modules or within a single module.  Core data actions can call Dynamics 365 Commerce proxy APIs (or any other service provider) to get retail data and custom business logic can be applied as require or call any web service.

## Themes
Themes contain site CSS and allows you to add custom module CSS.  A site theme can be set in the authoring tools that all pages will use by default, but additional themes can be added and set on a master or shared template or a specific page.  This is useful if you want theme changes for a campaign or for a temporary seasonal change and can be set on the whole site or a subset of pages.

## Script Injectors
The e-Commerce platform provides a built in script injector module that allows easy script injection into the head, bodybegin, ... from within the admin tool.  This makes it very simple to add script such as 3rd party analytics.  You may have advanced requirements to inject custom html within your e-Commerce site with custom script injector modules.
