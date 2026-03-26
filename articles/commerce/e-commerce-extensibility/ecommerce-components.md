---
title: E-commerce components
description: This article provides a high-level summary of some frequently used e-commerce configuration components in the Microsoft Dynamics 365 Commerce online software development kit (SDK).
author: samjarawan
ms.date: 02/03/2026
ms.topic: overview
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# E-commerce components

[!include [banner](../includes/banner.md)]

This article provides a high-level summary of some frequently used e-commerce configuration components in the Microsoft Dynamics 365 Commerce online software development kit (SDK).

## Modules

Modules represent the core building blocks that make up an online page. Here are some examples of modules:

- A feature module that a page features. It shows a product image and description, together with a "call-to-action" button that you can use to purchase the product or get more information about it.
- A hero module that highlights a campaign or provides marketing information.
- A header module made up of smaller module components, such as a search module, a sign-in module, and a navigation module.

## Data actions

Use data actions to get data, apply business logic to a module, and share data across modules.

### Core data actions

The Commerce e-commerce platform module library includes a set of data actions for performing typical actions, such as getting product data from the Dynamics 365 Commerce database, or getting ratings and reviews information for a product. You can't modify core data actions.

### Custom data actions

Create custom data actions and use them in your modules. You can make custom data actions globally scoped so that you can use them across multiple modules, or use them in a single module. Custom data actions can call Dynamics 365 Commerce proxy application programming interfaces (APIs), or any other service provider, to get data. Apply custom business logic as required.

## Themes

Themes contain site-wide Sassy Cascading Style Sheets (SCSS) style definitions. They also let you add custom, module-specific SCSS style definitions. You can set a site theme in the authoring tools. All pages then use that theme by default. You can add more themes, and set them on a template, a layout, or a specific page. This capability is useful if you want to change the theme for a campaign or a temporary seasonal change. You can set the theme on the whole site or a subset of pages.

Themes can also override module views (including module library modules), and can add module definition extensions to extend the configurations and resources on a module. Because themes can change the look and feel of all modules (custom and module library) without requiring that modules be cloned, they allow for better serviceability.

## Script injectors

The online platform provides a built-in script injector module that makes it easy to inject scripts into the head, `bodybegin`, and so on, from the admin tool. Script injectors make it easy to add scripts such as partner analytics. You might have advanced requirements to use custom script injector modules to inject custom HTML into your online site.

## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[CLI command reference](cli-command-reference.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
