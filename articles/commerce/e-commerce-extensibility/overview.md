---
# required metadata

title: Online platform extensibility
description: This topic covers online platform extensibility in Microsoft Dynamics 365 Commerce.
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

This topic covers online platform extensibility in Microsoft Dynamics 365 Commerce.

## Overview

The Dynamics 365 Commerce platform provides a rich online software development kit (SDK) for developer extensibility and a store starter kit (SSK). The online SDK and SSK provide a set of ready-built modules and data actions that you can use for your site.

Online pages, such as the home page, product details page, and the category page, are made up of component modules, such as header, hero, and feature modules. The modules use data actions to fetch data (for example, retail product data, and ratings and reviews) and render HTML to show a customer-facing page. Each module contains configuration fields that a page author or site administrator can set. These fields include fields for layout options such as image placement in the module, fields for links to products or pages, and fields for images or strings that should be shown in the module.

## Online SDK

The online SDK lets developers create and customize e-Commerce modules, data actions, and themes.

## Store starter kit

The SSK contains production-ready components, modules, data actions, and themes that work with preconfigured authoring templates and pages. A developer can use the online SDK to customize each module and theme as required.

## Command-line interface tools

Command-line interface (CLI) tools are provided as part of the online SDK. These tools help you create new modules, data actions, and themes. There is also a CLI tool that you can use to package all the configurations for your site into a single configuration file. You can then upload this file to your production or test site by using Microsoft Dynamics Lifecycle Services (LCS).
