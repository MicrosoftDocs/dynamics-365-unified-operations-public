---
 # required metadata

title: Templates and layouts overview
description: This topic covers templates and layouts in Dynamics 365 Commerce.
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

# Templates and layouts overview

[!include [banner](../includes/preview-banner.md)]
[!include [banner](../includes/banner.md)]

Templates are a foundational element of the Dynamics 365 Commerce page model. Learning to leverage templates within your website is a critical initial step to maximize efficiency and consistency for site authoring workflows. Early decisions around template structure are important and can significantly affect cost and agility for daily, seasonal, and sitewide brand updates. Well-structured templates have other benefits such as improving sitewide SEO scores and minimizing bug counts. A good place to start with templates is to understand the functional benefits, differences, and hierarchy between templates and layouts, described in more detail below.

The following diagram shows the page model hierarchy behind a rendered webpage.

![Page Model Diagram](../commerce/media/page-model-diagram.png)



| Entity        | Basic function                                               |
| ------------- | ------------------------------------------------------------ |
| Template      | Defines the module options and basic scaffolding for a set of layouts and page instances |
| Layout        | Defines the final module selection and arrangement for a page or set of pages |
| Page instance | Defines the data and content for a specific page        |

## Templates

Templates sit at the top of the Commerce page model and represent a key early step for site configuration. Conceptually, templates control consistency across a family of child *layouts* and *pages* by defining the base structure and authoring options for downstream layout and page creation workflows. Templates can simplify the content authoring process with predetermined centrally managed elements (headers, footers, etc.), and guided authoring flows that ensure on-brand module configuration choices.  

### Controlling Consistency
The biggest business decision to make when designing a template is how much control to exert over the page creation process. A template that leaves everything open for a downstream author is the simplest template to create, but may have long-term maintenance consequences for pages created from it. A well-written template will provide guidance and a streamlined authoring experience for an author, while allowing them enough flexibility to complete their task. All of that is based on the level of control enforced by the template.

Templates can help content authors be more efficient and stay on-brand in the following ways.

- Narrow down which modules should be used in a page
- Suggest default module choices and configuration
- Explicitly make some module and configuration choices that are controlled at the template level, also known as *locking* a setting.

A basic template example could be configured and described as follows.

- All child layouts of template "X" must have a header, body, and a footer container.
- The header configuration is locked within template "X" and can't be changed anywhere except within the template itself. All child layouts and pages will always get this header.
- The body container requires at least one, and up to a maximum of ten, modules that are defined by a downstream layout and by page authors.
- The available module choices for the body container are hero, feature, carousel, and banner.
- The footer container is configured within template "X," but can be overridden by downstream pages and layouts.

The example above describes a simple structure and set of options for downstream content authors. Notice that certain page parts (the header) are fully defined and locked within the template and can't be changed by downstream authors. Other parts (the body) are left for downstream authors to define within chosen guidelines (between the minimum of one configured module to the maximum of ten configured modules from the set of allowed modules). And other parts (the footer) are defaulted in the template but allowed to be overridden by downstream authors. The level of constraint vs. flexibility for child page and layout authors is 100% configurable using templates. Determining this balance is an important upfront step for site and brand administrators and will affect how page elements are centrally updated (locked within the template) or left to individual child levels down the page hierarchy.

To get started using templates, [Work with templates](work-with-templates.md).

## Layouts

Where a template defines all of the possible combinations of modules allowed for a page, a layout is an explicit selection of one of those combinations. Pages then sit below a layout in the hierarchy and define the localized content for the modules selected within the layout. 

Building on the template example above, an example of a basic layout could be configured and described as follows.

- A layout whose parent template requires that the body contain between one and ten modules from the options of hero, feature, carousel, and banner:
  - can define a banner to reside as the first module in the body container, followed by a hero, and two feature modules.
  - can define that the first feature module is left aligned and the second feature module is right aligned.
- Even though a default footer is inherited from the template, the layout can override this with a different footer fragment since the template author chose to leave this unlocked.

The layout example above describes the final module arrangement for any of its child pages. A layout, like a template, can also define default or locked module properties that will be inherited by child pages (for example, left vs. right alignment of the feature module). The actual content (or data) for each module within the layout is then defined further down the hierarchy within each child page instance. An important distinction here is that layouts do not directly contain localizable content, whereas their child pages do. The layout's primary function is to define the final module arrangement and default configuration of modules for its child pages.

This architecture is powerful for a couple of reasons. First, layouts that share the same parent template are treated as compatible for
layout switching scenarios. This means any page can switch to a different layout from within the same template hierarchy without reauthoring page-level content. This can be used for seasonal design updates, experimentation, or permanent site redesign scenarios.
Secondly, layouts provide another way to centrally modify common elements for a group of pages without the need to update individual pages. For example, if there are 1,000 pages in a product category that all share the same layout, reordering the modules in the layout
will immediately be reflected in all 1,000 child pages. Understanding this hierarchy can go a long way towards delivering an agile and
efficient site structure that saves cost, scales, and produces better results as your site evolves over time.

### Preset and custom layouts

The following diagram shows preset and custom layout scenarios.

![Template Figure 1](../commerce/media/template-figure1.png)

Layouts can have one of two forms within your site: *preset* or *custom*.  

- **Preset layouts** enable a page creation workflow where all modules are already chosen and arranged, and only data entry is required. This can be a big time saver when authoring many pages with the same layout requirements. Another important distinction for preset layouts is that they have a one-to-many relationship with their child pages, meaning that you can have a single preset layout to centrally control the module arrangement for hundreds or thousands of child pages.
- **Custom layouts** are essentially one-offs that are embedded within a single page and are not exposed as an option when creating other new pages or layout swapping scenarios. The benefit of this approach is that authors can experiment by authoring a page using a custom layout, and if they decide they want to reuse the layout for other pages, they can easily convert it to a preset layout. Once the new preset layout is saved, it becomes an available option for both new page creation workflows, and layout swapping for pages that share a common template hierarchy. Conversely, preset layouts can be branched into a custom layout, which allows a page to break away from a preset layout and create a custom one-off layout (which would still be bound by any constraints in the parent template).

Editing preset vs. custom layouts occur in different surface areas within the authoring toolset. Custom layouts are edited directly within the page editor since they have no dependencies on other pages. In this scenario, the existence of a layout is mostly
transparent to the user and is only exposed in page-level properties and through layout option actions. Preset layouts, because changes to them may affect many pages, must be edited in the layout editor where publish actions consider the full downstream impact to (what could be many) child pages.

To get started using preset layouts, see [Work with preset layouts](work-with-layouts.md).

