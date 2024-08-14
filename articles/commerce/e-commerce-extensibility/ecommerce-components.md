---
title: E-commerce components
description: This article contains a high-level summary of some frequently used e-commerce configuration components that the Microsoft Dynamics 365 Commerce online software development kit (SDK) provides access to.
author: samjarawan
ms.date: 08/02/2024
ms.topic: how-to
audience: Developer
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# E-commerce components

[!include [banner](../includes/banner.md)]

This article contains a high-level summary of some frequently used e-commerce configuration components that the Microsoft Dynamics 365 Commerce online software development kit (SDK) provides access to.

## Modules

Modules represent the core building blocks that make up an online page. Here are some examples of modules:

- A feature module that is featured on a page, and that shows a product image and description, together with a "call-to-action" button that can be used to purchase the product or get more information about it
- A hero module that highlights a campaign or provides marketing information
- A header module that is made up of smaller module components, such as a search module, a sign-in module, and a navigation module

## Data actions

Data actions are used to get data, apply business logic to a module, and share data across modules.

### Core data actions

The e-Commerce platform module library includes a set of data actions for performing typical actions, such as getting product data from the Dynamics 365 Commerce database, or getting ratings and reviews information for a product. Core data actions can't be modified.

### Custom data actions

You can create custom data actions and use them in your modules. Custom data actions can be globally scoped so that they can be used across multiple modules. Alternatively, they can be used in a single module. Custom data actions can call Dynamics 365 Commerce proxy application programming interfaces (APIs), or any other service provider, to get data. Custom business logic can be applied as required.

## Themes

Themes contain site-wide Sassy Cascading Style Sheets (SCSS) style definitions. They also let you add custom, module-specific SCSS style definitions. You can set a site theme in the authoring tools. All pages then use that theme by default. You can add more themes, and set them on a template, a layout, or a specific page. This capability is useful if you want to change the theme for a campaign or a temporary seasonal change. You can set the theme on the whole site or a subset of pages.

Themes can also override module views (including module library modules), and can add module definition extensions to extend the configurations and resources on a module. Because themes can change the look and feel of all modules (custom and module library) without requiring that modules be cloned, they allow for better serviceability.

## Script injectors

The online platform provides a built-in script injector module that makes it easy to inject scripts into the head, bodybegin, and so on, from the admin tool. Script injectors make it easy to add scripts such as third-party analytics. You might have advanced requirements to use custom script injector modules to inject custom HTML into your online site.

## Additional resources

[E-commerce architectural overview](architectural-overview.md)

[CLI command reference](cli-command-reference.md)


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
