---
# required metadata

title: Online channel extensibility
description: This topic covers online platform extensibility in Microsoft Dynamics 365 Commerce.
author: samjarawan
manager: annbe
ms.date: 01/31/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-365-commerce
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer
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
# Online channel extensibility

[!include [banner](../includes/banner.md)]

This topic covers online platform extensibility in Microsoft Dynamics 365 Commerce.

## Overview

The Dynamics 365 Commerce platform provides a rich online software development kit (SDK) for developer extensibility. It also provides a store starter kit (SSK). The SSK provides a set of ready-built modules, data actions, and themes that you can use for your site.


Online pages (for example, the home page, product details pages, and category pages) are made up of component modules (for example, header, hero, and feature modules). The modules use data actions to fetch data (for example, product data, and ratings and reviews) and to render HTML to show a customer-facing page. Each module contains configuration fields that a page author or site administrator can set. These fields include fields for layout options such as image placement in the module, fields for links to products or pages, and fields for images or strings that should be shown in the module. Themes contain Cascading Style Sheets (CSS) code that is used for styling. They also contain layout overrides for modules.

## Online SDK

The online SDK lets developers create and customize e-Commerce modules, data actions, and themes.

## Store starter kit

The SSK contains production-ready components that work with preconfigured authoring templates and pages. These components include modules, data actions, and themes. A developer can use the online SDK to customize each module and theme as required.

## Command-line interface tools

Command-line interface (CLI) tools are provided as part of the online SDK. These tools help you create new modules, data actions, and themes. There is also a CLI tool that you can use to package all the configurations for your site into a single configuration file. You can then upload this file to your production or test site by using Microsoft Dynamics Lifecycle Services (LCS).

## Additional resources

[Architectural overview](architectural-overview.md)

[System requirements](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Starter kit overview](../starter-kit-overview.md)

[e-Commerce components](ecommerce-components.md)

[CLI command reference](cli-command-reference.md)
