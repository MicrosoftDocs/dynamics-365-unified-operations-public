---
# required metadata

title: Extensibility home page
description: This topic provides links to topics about extensibility.
author: FrankDahl
manager: AnnBe
ms.date: 05/14/2019
ms.topic: index-page
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 268724
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: fdahl
ms.search.validFrom: 2019-05-14
ms.dyn365.ops.version: Platform update 4

---
# Extensibility home page

[!include [banner](../includes/banner.md)]

Microsoft Dynamics 365 Finance is extensively customized by partners, value added resellers (VARs), and even some customers. The ability to customize the product is a strength that has historically been supported through overlayering of the application code. The move to the cloud, together with more agile servicing and frequent updates, requires a less intrusive customization model, so that updates are less likely to affect custom solutions. This new model is called *extensibility* and has replaced customization through overlayering.

Extensibility is the only customization framework in the application and Microsoft Dynamics 365 for Retail. Overlayering isn't supported.

## Introduction

These introductory topics contain general information about customization. This information includes information about when the transition occurs from customization through overlayering to a purely extension-based model. These topics also explain how to log extensibility requests to Microsoft, and provide answers to frequently asked questions (FAQ).

+ [Application extensibility plans](extensibility-roadmap.md)
+ [Extensibility requests](extensibility-requests.md) 
+ [Extensibility FAQ](app-sealing-faq.md) 

## What's new

Read [What's new for extensibility](extensibility-new.md) for extensibility-related updates that have been made since July 2017.

## Getting started

The topics in this section will help you start to build extensions. They will also help you migrate solutions that are currently based on overlayered code to extension-based solutions. This section includes hands-on labs that walk you through simple customizations.

+ [Migrate from overlayering to extensions](migrate-overlayer-extension.md)
+ [Customize model elements using extensions (tutorial)](customize-model-elements-extensions.md)
+ [Customization: overlayering and extensions](customization-overlayering-extensions.md)
<!--+ [Customize by overlayering metadata source code (Office Mix)](https://mix.office.com/watch/1ol6ov90jrd4w)-->

## Fundamentals on extensions

This section includes fundamentals, principles, and practices for making extensions. The guiding principles in these topics discuss how customization must be approached through extensions. These principles include naming guidelines. Additionally, these topics discuss the foundation framework, such as extensions and chain of command.

+ [Intrusive customizations](intrusive-customizations.md)
+ [Class extensions](class-extensions.md)
+ [Class extension: Method wrapping and Chain of Command](method-wrapping-coc.md)
+ [Naming guidelines](naming-guidelines-extensions.md)
+ [Relax model restrictions to enable the refactoring of over-layering into extensions](refactoring-over-layering.md)

## How do I create extensions?

This section includes "How do I?" topics that explain how to customize specific object types or code. Most of these topics are brief and to the point. Because there are many topics here, it might be practical to search for a specific topic.

### Data types
+ [Add an enum value](add-enum-value.md)
+ [Modify an extended data type](modify-edt.md) 

### Classes
+ [Register a subclass for factory methods](register-subclass-factory-methods.md)
+ [Respond with EventHandlerResult](respond-event-handler-result.md)
+ [Extend the RunBase class](extend-runbase-class.md)
+ [Use delegates to customize Application startup](startup-customizations.md)

### Tables
+ [Modify an existing field in a table](modify-existing-field.md)
+ [Add a new field to an existing table](add-field-extension.md)
+ [Add an index to an existing table](add-index.md)
+ [Add a relation to an existing table](add-relation.md)
+ [Modify properties on an existing table](modify-properties.md)
+ [Add a method to a table](add-method-table.md)
+ [Perform business actions throughout the lifecycle of a table record](subscribe-table-events.md)

### Forms
+ [Add a new data source to a form](add-datasource.md)
+ [Change the caption on a form](change-caption-form.md)
+ [Modify form control properties](modify-control-properties.md)

### Others
+ [Extending decimal point precision](decimal-point-precision.md)

### Reports
+ [Extend the list of Electronic reporting functions](../analytics/general-electronic-reporting-formulas-list-extension.md)
+ [Customize App Suite reports](../analytics/customize-app-suite-reports-with-extensions.md)

### Blog posts

Information about customization is also shared through blogs where various topics are discussed. This section includes reference to some of these blogs.

+ [Extending Dynamics 365 for Finance and Operations](https://blogs.msdn.microsoft.com/mfp/2017/01/31/extending-dynamics-365-for-operations/)
+ [Extending class state](https://blogs.msdn.microsoft.com/mfp/2017/01/31/extending-class-state/)
+ [Extension methods](https://blogs.msdn.microsoft.com/mfp/2015/12/15/x-in-ax7-extension-methods/)
+ [Extensible base enumerations](https://kashperuk.blogspot.dk/2016/09/development-tutorial-extensible-base.html)
+ [Static event subscription](https://blogs.msdn.microsoft.com/mfp/2015/12/10/x-in-ax7-static-event-subscription/)
+ [Responding through delegates](https://blogs.msdn.microsoft.com/mfp/2017/01/31/responding-through-delegates/)
+ [Subscribing to onValidatingWrite](https://blogs.msdn.microsoft.com/mfp/2017/01/31/subscribing-to-onvalidatingwrite/)
+ [Extending inventory dimensions](https://blogs.msdn.microsoft.com/mfp/2017/08/10/extensible-inventory-dimensions/)
+ [Embrace the extensions mindset with Dynamics 365 for Finance and Operations](https://blogs.msdn.microsoft.com/axinthefield/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations/)
+ [Extensible X++ - Method Signatures](https://blogs.msdn.microsoft.com/mfp/2017/08/31/extensible-x-method-signatures/)

## How do I create an extensible solution?

This section includes some best practices on how to create/make your solution extensible, so that consumers of your code can extend your solution.

+ [Writing extensible code](writing-extensible-code.md)
+ [Classes](extensible-classes.md)
+ [Methods](extensible-methods.md)
+ [Forms](extensible-forms.md)
+ [Extended data types](extensible-edts.md)
+ [Extensible enums](extensible-enums.md)
+ [Delegates](extensible-code-delegates.md)
+ [Tables](extensible-tables.md)
+ [Extensibility attributes for methods](extensibility-attributes.md)

## Breaking changes
When you make your solution extensible, you also help guarantee that you won't break those extension points later. For pointers that can help you avoid breaking your consumers, see [Breaking changes](breaking-changes.md).
