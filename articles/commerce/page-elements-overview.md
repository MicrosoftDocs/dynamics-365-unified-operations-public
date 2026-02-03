---
title: Page model glossary
description: Learn about the various elements used on Microsoft Dynamics 365 Commerce site pages.
author: phinneyridge
ms.date: 01/27/2026
ms.topic: how-to
ms.reviewer: v-griffinc
ms.search.region: Global
ms.author: asharchw
ms.search.validFrom: 2019-10-31
ms.custom: 
  - bap-template
---
# Page model glossary

[!include [banner](includes/banner.md)]

This article describes the various elements that are used on Microsoft Dynamics 365 Commerce site pages.

## Page element definitions

The following table provides a summary of terms that you should be familiar with when you change the look, feel, and content of your site. For more thorough explanations and procedures, follow the links.

| Term | Description and notes |
|------|-----------------------|
| [Module](work-with-modules.md) | <p>**Definition:** Modules are building blocks that you author to make up the skeleton of a webpage. Examples include header, hero, and carousel modules.</p><p>**Where it's selected:** You can select and configure deployed modules in various stages of the site authoring workflow, such as the template, layout, page, and fragment authoring stages.</p><p>**Where it's edited:** You create custom modules in code by using the software development kit (SDK). Then, you upload them to your site, where they become available for selection.</p> |
| Module property | <p>**Definition:** Module properties are specific settings that the module defines. You can edit them in the e-commerce authoring tools. For example, use module properties to set the heading and background image of a banner module.</p><p>**Where it's configured:** You select and configure module properties in the property pane that appears in the authoring environments (editors) for templates, layouts, pages, fragments, and app settings.</p> |
| [Template](templates-layouts-overview.md) | <p>**Definition:** Templates define the module combinations and options that you should use for a category of pages (for example, marketing pages, category pages, and product pages).</p><p>**Where it's selected:** You can select templates during page or layout creation workflows.</p><p>**Where it's edited:** You author templates in the template editor. No code is required to create or modify them.</p> |
| [Layout](templates-layouts-overview.md) | <p>**Definition:** Layouts define the final selection and arrangement of modules from the parent template's set of options. You can configure a layout for a single page (*custom layout*), or share it by multiple pages (*preset layout*).</p><p>**Where it's selected:** You can select layouts during new page creation or when a different layout is required for an existing page.</p><p>**Where it's edited:** You author layouts in the layout editor. No code is required to create or modify them.</p> |
| [Page instance](modify-existing-page.md) | <p>**Definition:** Page instances define the final, page-specific localized content for a single page. This content comes from the values of module properties.</p><p>**Where it's selected:** You select pages when you assign URLs.</p><p>**Where it's edited:** You edit pages in the page editor. No code is required to create or modify them.</p> |
| [Theme](select-site-theme.md) | <p>**Definition:** Themes define the Cascading Style Sheet (CSS), and determine the look and feel of the modules that are rendered on a page.</p><p>**Where it's selected:** After you upload a theme to your site by using Microsoft Dynamics Lifecycle Services (LCS), select it as a property of the page container module.</p><p>**Where it's edited:** You currently create and edit themes by using the SDK. Then, you upload them to your site by using LCS.</p> |
| [Fragment](work-with-fragments.md) | <p>**Definition:** Fragments are fully configured modules with localized content that you can reuse and centrally update across multiple pages. For example, a fragment that you create from a header module can be used in all templates and on all pages across your site, and you can centrally update it in one place.</p><p>**Where it's selected:** You can select fragments wherever modules can be selected. Substitute a fragment for a module to help increase efficiency through reusable and centralized authoring.</p><p>**Where it's edited:** You edit fragments in the fragment editor. No code is required to create or modify them.</p> |
| [URL](create-page-URL.md) | <p>**Definition:** Uniform resource locators (URLs) are addresses that point to webpages or other URLs.</p><p>**Where it's selected:** You select URLs if you need links between pages.</p><p>**Where it's edited:** You edit URLs in the URL editor. No code is required to create or modify them.</p> |
| Asset | <p>**Definition:** Assets are file binaries that have an extension such as .jpg, .docx, .pdf, or .mpg.</p><p>**Where it's selected:** You select assets as module properties for modules that require them.</p><p>**Where it's edited:** You upload assets and edit associated metadata in the asset manager.</p> |

## Additional resources

[Ways to add content](add-manage-content.md)

[Document states and lifecycle](document-states-overview.md)

[Work with publish groups](publish-groups.md)

[Enable and use cross-channel sharing](cross-channel-sharing.md)

[Work with modules](work-with-modules.md)

[Work with fragments](work-with-fragments.md)

[Templates and layouts overview](templates-layouts-overview.md)

[Customize site navigation](customize-site-navigation.md)


[!INCLUDE[footer-include](../includes/footer-banner.md)]
