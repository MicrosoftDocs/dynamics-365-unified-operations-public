---
# required metadata

title: Platform extensibility overview
description: The Dynamics 365 Commerce Platform provides a rich e-Commerce eeveloper extensibility SDK and starter kit with a set of ready built modules and data actions for your site.
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
# Platform Extensibility Overview

The Dynamics 365 Commerce Platform provides a rich e-Commerce eeveloper extensibility SDK and starter kit with a set of ready built modules and data actions for your site.

E-Commerce pages such as the home page, product details page or category page are made up of componentized 'modules' (ex: header, hero, feature,...) that leverage 'data actions' to fetch data (ex: Dynamics 365 Retail data, Ratings and Reviews, ...) and render html to make up a customer page.  Each module can surface configuration fields that a page author or site administrator can fill out, these could include layout options such as image placement within the module, links to products or pages, images or strings to be displayed in the module.

## E-Commerce SDK
The e-Commerce SDK enables a developer to customize e-Commerce modules, data actions and themes.

## Starter Kit
The starter kit contains production ready components, modules, data actions and themes that go along with pre-configured authoring templates and pages.  If needed each of the modules and themes can be modified by a developer using the e-Commerce SDK.

## CLI tools
CLI tools are provided as part of the e-Commerce SDK to help in creation of new modules, data actions and themes.  There is also a CLI tool to package up all of the configurations for your site into a single configurations file which will be uploaded to your production or test site via LCS.
