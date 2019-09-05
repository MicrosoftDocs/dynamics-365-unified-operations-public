---
# required metadata

title: Online platform extensibility
description: This topics covers online platform extensibility in Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: samjar
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Online platform extensibility

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topics covers online platform extensibility in Dynamics 365 Commerce.

## Overview

The Commerce platform provides a rich online developer extensibility software development kit (SDK) and store starter kit (SSK) that provide a set of ready-built modules and data actions for your site.

Online pages such as the home page, product details page, and category page are made up of componentized modules such as header, hero, and feature. The modules leverage data actions to fetch data (for example, retail product data, ratings and reviews, etc.) and render HTML to display a customer-facing page. Each module contains configuration fields that a page author or site administrator can fill out. Fields include layout options such as image placement within the module, links to products or pages, and images or strings to be displayed in the module.

## Online SDK
The online SDK enables developers to create and customize e-Commerce modules, data actions, and themes.

## Store starter kit
The store starter kit contains production-ready components, modules, data actions, and themes that work with preconfigured authoring templates and pages. If needed, each of the modules and themes can be customized by a developer using the online SDK.

## Command-line interface tools
Command-line interface (CLI) tools are provided as part of the online SDK to help in the creation of new modules, data actions, and themes. There is also a CLI tool to package up all of the configurations for your site into a single configurations file which will be uploaded to your production or test site using Microsoft Lifecycle Services (LCS).
