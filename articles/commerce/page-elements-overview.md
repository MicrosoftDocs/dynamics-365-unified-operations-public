---
title: Page model glossary
description: This article describes the various elements that are used on the pages of a Microsoft Dynamics 365 Commerce site.
author: phinneyridge
ms.date: 10/09/2020
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5
ms.collection: get-started
ms.search.industry: 
ms.search.form: 
---
# Page model glossary


[!include [banner](includes/banner.md)]

This article describes the various elements that are used on the pages of a Microsoft Dynamics 365 Commerce site.

## Page element definitions

The following table provides a summary of terms that you should be familiar with when you change the look, feel, and content of your site. For more thorough explanations and procedures, follow the links.

| Term | Description and notes |
|------|-----------------------|
| [Module](work-with-modules.md) | <p>**Definition:** Modules are building block that can be authored and make up the skeleton of a webpage. Examples include header, hero, and carousel modules.</p><p>**Where it's selected:** Deployed modules can be selected and configured in various stages of the site authoring workflow, such as the template, layout, page, and fragment authoring stages.</p><p>**Where it's edited:** Custom modules are created in code by using the software development kit (SDK). They are then uploaded to your site, where they become available for selection.</p> |
| Module property | <p>**Definition:** Module properties are specific settings that are defined by the module. They can be edited in the e-Commerce authoring tools. For example, module properties are used to set the heading and background image of a banner module.</p><p>**Where it's configured:** Module properties are selected and configured in the property pane that appears in the authoring environments (editors) for templates, layouts, pages, fragments, and app settings.</p> |
| [Template](templates-layouts-overview.md) | <p>**Definition:** Templates define the module combinations and options that should be used for a category of pages (for example, marketing pages, category pages, and product pages).</p><p>**Where it's selected:** Templates can be selected during page or layout creation workflows.</p><p>**Where it's edited:** Templates are authored in the template editor. No code is required to create or modify them.</p> |
| [Layout](templates-layouts-overview.md) | <p>**Definition:** Layouts define the final selection and arrangement of modules from the parent template's set of options. A layout can be configured for a single page (*custom layout*), or it can be shared by multiple pages (*preset layout*).</p><p>**Where it's selected:** Layouts can be selected during new page creation or when a different layout is required for an existing page.</p><p>**Where it's edited:** Layouts are authored in the layout editor. No code is required to create or modify them.</p> |
| [Page instance](modify-existing-page.md) | <p>**Definition:** Page instances define the final, page-specific localized content for a single page. This content is derived from the values of module properties.</p><p>**Where it's selected:** Pages are selected when URLs are assigned.</p><p>**Where it's edited:** Pages are edited in the page editor. No code is required to create or modify them.</p> |
| [Theme](select-site-theme.md) | <p>**Definition:** Themes define the Cascading Style Sheet (CSS), and determine the look and feel of the modules that are rendered on a page.</p><p>**Where it's selected:** After a theme is uploaded to your site by using Microsoft Dynamics Lifecycle Services (LCS), it can be selected as a property of the page container module.</p><p>**Where it's edited:** Themes are currently created and edited by using the SDK. They are then uploaded to your site by using LCS.</p> |
| [Fragment](work-with-fragments.md) | <p>**Definition:** Fragments are fully configured modules that have localized content that can be reused and centrally updated across multiple pages. For example, a fragment that is created from a header module can be used in all templates and on all pages across your site, and centrally updated in one place.</p><p>**Where it's selected:** Fragments can be selected wherever modules can be selected. They can be substituted for a module to help increase efficiency through reusable and centralized authoring.</p><p>**Where it's edited:** Fragments are edited in the fragment editor. No code is required to create or modify them.</p> |
| [URL](create-page-URL.md) | <p>**Definition:** Uniform resource locators (URLs) are addresses that point to webpages or other URLs.</p><p>**Where it's selected:** URLs are selected if links between pages are required.</p><p>**Where it's edited:** URLs are edited in the URL editor. No code is required to create or modify them.</p> |
| Asset | <p>**Definition:** Assets are file binaries that have an extension such as .jpg, .docx, .pdf, or .mpg.</p><p>**Where it's selected:** Assets are selected as module properties for modules that require them.</p><p>**Where it's edited:** Assets are uploaded, and associated metadata is edited in the asset manager.</p> |

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
