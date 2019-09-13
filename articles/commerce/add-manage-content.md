---
# required metadata

title: Add and manage content
description: This topic covers how to add and manage content on your Dynamics 365 Commerce site.
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
## Add and manage content

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

This topic covers how to add and manage content on your Dynamics 365 Commerce site.

## Overview

There are many different actions you can take to alter the look, feel, and content of your site.  Depending on the required level of customization, many of these tasks can be performed by non-developers. Building templates, picking themes, and selecting and configuring modules can all be achieved without writing any code. In contrast, a new theme or module does require development skills to leverage the e-Commerce software development kit (SDK) and Lifecycle Services (LCS) deployment workflow. Within this section, we will focus primarily on areas of your site that do not require a developer, and where necessary point you towards tasks that will require SDK work.

Read through the following documentation if you would like to...

* To change the text, image, or video on an existing site page, see [Work with modules](work-with-modules.md)
* To ensure a foolproof and on-brand authoring experience for web content authors, see [Work with templates](work-with-templates.md)
* To re-arrange how sections are organized on a site page, see [Work with layouts](work-with-layouts.md)
* To change the fonts, colors, and general look of site pages, see [Select a site theme](select-site-theme.md)

## Additional resources

[Page elements](page-elements.md)
[Document states](document-states.md)

## Page elements

Below is a quick look at some terms you should be familiar with in order to modify the look, feel, and content within your site.  Follow any links for a more complete explanation and walkthrough.

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

## Document states and lifecycle
### CMS Items

The CMS document types listed in the section above have several different possible states within the authoring tool that affect who and when they can be edited.  These different document states help enforce data conflicts, versioning, and who and when changes are viewable by others.

Term | Short description
---|---
Check out | When a CMS item is checked out to you, it can't be edited by any other authenticated system users.  Any changes you make to the item are only visible to you. 
Check in | When a CMS item is checked in, all changes are visible to other authenticated system users and the document is available to check out and edit.  Each check in creates a document version record in the item's history. 
Publish | When a CMS item is published, it is pushed to your live site and becomes discoverable on the internet by non-authenticated external users.  Publish can only be performed on checked in documents. 
Save | Save is an action that can be made on a checked out document to persist changes to the CMS before they are checked in or published.  These saved changes are not visible to other authenticated system users until the document is checked in, and not visible to external users until published. 
Discard check out | When a checked out CMS item is discarded, all saved changes are deleted and the item is reverted to the most recently checked in version of the item. 
