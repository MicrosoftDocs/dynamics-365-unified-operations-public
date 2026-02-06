---
title: Container modules
description: Learn how container modules help you control the layout when you build complex modules or pages out of small component modules with Microsoft Dynamics 365 Commerce.
author: samjarawan
ms.date: 01/30/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template 
---
# Container modules

[!include [banner](../includes/banner.md)]

This article explains how container modules help you control the layout when you build complex modules or pages out of small component modules with Microsoft Dynamics 365 Commerce.

For example, a container module might be a header, footer, or buy box module that has nested modules inside it.

Container modules can define "slots" that you expose to template authors. You can think of slots as regions inside the container module. Page authors can configure which modules go into each slot. The code of the container module is responsible for the HTML layout of the slots.

You can also expose configuration settings to page authors. In this way, page authors can do more configuration of the layout of container modules. The container module is responsible for building a responsive design, to help guarantee that the module looks good at any size, regardless of whether it's viewed on a mobile device screen or in a full web browser.

Create container modules just like regular modules. However, in the `MODULE_NAME.definition.json` file, you must change the **$type** value as shown in the following example.

```json
"$type": "containerModule"
```

Two types of container modules exist: layout container modules and page container modules.

## Layout container modules

Layout container modules are useful when you must make a complex module out of multiple simple modules, and you want to control the layout of those simple modules. For example, you can use a header layout container module that is made up of required or optional submodules, such as search, sign-in, and navigation modules. The purpose of the layout container is to provide an adaptive layout.

For more information, see [Create a layout container module](create-layout-container.md).

## Page container modules

Page container modules contain the core structure for page authoring. For example, you can create a page container where you define slots for the header area, main content area, and footer area. A page container is just a module that controls the layout of a set of named slots. You can embed it only at the root of a page. Each page must have only one page container. You add this page container to a template in the authoring tools.

Like layout container modules, page container modules can define named slots that template authors can use. Page authors can configure which modules go into each slot. The rendering code for the container controls the layout of those slots. You can also expose configuration settings to page authors, so they can do more configuration of the layout.

For more information, see [Create a page container module](create-page-containers.md).

## Additional resources

[Create a new module](create-new-module.md)

[Clone a module library module](clone-starter-module.md)

[Add module configuration fields](add-module-config-fields.md)

[Preview and debug a module](test-module.md)

[Test modules by using module mocks](test-module-mock.md)

[Test modules by using page mocks](test-page-mock.md)

[Localize a module](localize-module.md)

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
