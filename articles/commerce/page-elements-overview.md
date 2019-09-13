---
# required metadata

title: Page elements overview
description: This topic describes the various page elements used on a Dynamics 365 Commerce site page.
author: phinneyridge
manager: annbe
ms.date: 10/01/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-retail
ms.technology: 

# optional metadata

ms.search.form:  
audience: Application User
# ms.devlang: 
ms.reviewer: v-chgri
ms.search.scope: Retail, Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: 
ms.author: niholman
ms.search.validFrom: 2019-10-31
ms.dyn365.ops.version: Release 10.0.5

---
# Page elements overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic describes the various page elements used on a Dynamics 365 Commerce site page.

## Page element definitions

The following table provides a summary of terms you should be familiar with in order to modify the look, feel, and content within your site. Follow any links for a more complete explanation and walkthrough.

Term | Notes and description 
---|---
[Module](modules.md) | **Definition:** Authorable building blocks that make up the skeleton of a webpage (examples: header, hero, carousel, etc.)<br />**Where to select:** Already deployed modules are selectable and configurable at various stages within the site authoring workflow.  This includes the template, layout, page, and fragment authoring UX.<br />**Where to edit**: Custom modules are created in code using the SDK and then uploaded to your site where they become selectable options, as described above. 
Module Property | **Definition:** A specific setting defined by the module that can be edited within the e-Commerce authoring toolset (example: heading and background image would be module properties for a banner module).<br />**Where to configure:** Module properties are selected and configured in the property panel UX within the template, layout, page, fragment, and app settings authoring UX. 
[Template](templates-layouts-overview.md) | **Definition:** Defines which module combinations and options should be used for a category of pages [examples: marketing page template, category page template, product page template, etc.].<br />**Where to select:** Templates can be selected during page or layout creation workflows.<br />**Where to edit**: Templates are authored in the template editor UX, and do not require any code to create or modify. 
[Layout](templates-layouts-overview.md) | **Definition:** Defines the final selection and arrangement of modules from the parent template's set of options.  Layout can be for a single page (custom) or shared by multiple pages (preset).<br />**Where to select:** Templates can be selected during new page creation or when choosing  an alternate layout for an existing page.<br />**Where to edit**: Layouts are authored in the layout editor UX, and do not require any code to create or modify. 
Page Instance | **Definition:** Defines the final page specific localized content (module property values) for a single page.<br />**Where to select:** Pages are selected when assigning URLs.<br />**Where to edit**: Pages are edited in the page editor UX, and do not require any code to create or modify. 
Theme | **Definition:** Defines the CSS and determines the look and feel of how modules within a page should render.<br />**Where to select:** Once a theme is uploaded to your site through LCS, they are selectable as a property on the page container module.<br />**Where to edit**: Themes are currently created and edited using the SDK, and uploaded to your site through LCS. 
[Fragment](work-with-fragments.md) | **Definition:** A fully configured module with localized content that can be re-used and centrally updated across multiple pages (example: a fragment created from a header module can be used in all templates and pages across your site, and centrally updated in one place).<br />**Where to select:** Fragments are selectable anywhere modules are, and can be substituted for a module to increase efficiency through re-usable and centralized authoring. <br />**Where to edit**: Fragments are edited in the fragment editor UX, and do not require any code to create or modify. 
URL | **Definition:** "Uniform Resource Locator", a URL is a World Wide Web address that points to a webpage or other URL.<br />**Where to select:** URLs are selected wherever links are needed between pages. <br />**Where to edit**: URLs are edited in the URL editor UX, and do not require any code to create or modify. 
Asset | **Definition:** A file binary (with an extension like .jpg, .docx, .pdf, .mpg, etc.).<br />**Where to select:** Assets are selected as module properties for modules that require them. <br />**Where to edit**: Assets are uploaded and associated metadata is edited within the asset manager UX. 

## Additional resources

- [Add and manage content](add-manage-content.md)
- [Document states overview](document-states-overview.md)
