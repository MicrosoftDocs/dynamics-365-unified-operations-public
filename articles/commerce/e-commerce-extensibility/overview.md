---
title: Online channel extensibility
description: This article provides an overview of online platform extensibility in Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 05/28/2024
ms.topic: overview
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---

# Online channel extensibility

[!include [banner](../includes/banner.md)]

This article provides an overview of online platform extensibility in Microsoft Dynamics 365 Commerce.

The Dynamics 365 Commerce platform provides a rich online software development kit (SDK) for developer extensibility. It also provides a module library. The module library provides a set of ready-built modules, data actions, and themes that you can use for your site.

Online pages (for example, the home page, product details pages, and category pages) are made up of component modules (for example, header, carousel, and content block modules). The modules use data actions to fetch data (for example, product data, and ratings and reviews) and to render HTML to show a customer-facing page. Each module contains configuration fields that a page author or site administrator can set in the site builder tool. These fields include fields for layout options such as image placement in the module, fields for links to products or pages, and fields for images or strings that will be shown in the module. Themes contain Cascading Style Sheets (CSS) code that is used for styling. They also contain layout overrides for modules.

## Online SDK

The online SDK lets developers create and customize e-Commerce modules, data actions, and themes.

## Module library

The module library contains production-ready components that work with preconfigured authoring templates and pages. These components include modules, data actions, and themes. A developer can use the online SDK to customize each module and theme as required.

## Command-line interface tools

Command-line interface (CLI) tools are provided as part of the online SDK. These tools help you create new modules, data actions, and themes. There is also a CLI tool that you can use to package all the configurations for your site into a single configuration file. You can then upload this file to your production or test site by using Microsoft Dynamics Lifecycle Services (LCS).

## Additional resources

[Architectural overview](architectural-overview.md)

[System requirements](system-requirements.md)

[Set up a development environment](setup-dev-environment.md)

[Module library overview](../starter-kit-overview.md)

[e-Commerce components](ecommerce-components.md)

[CLI command reference](cli-command-reference.md)

[Package configurations and deploy them to an online environment](package-deploy.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
