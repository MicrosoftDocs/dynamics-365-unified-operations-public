---
title: Extensibility home page
description: This article provides links to topics about extensibility.
author: FrankDahl
ms.date: 05/14/2019
ms.topic: index-page
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2019-05-14
ms.dyn365.ops.version: Platform update 4
ms.collection: get-started
ms.assetid: 
---
# Extensibility home page

[!include [banner](../includes/banner.md)]

Dynamics 365 Finance, Supply Chain, and Commerce are extensively customized by partners, value added resellers (VARs), and even some customers. The ability to customize the product is a strength that has historically been supported through overlayering of the application code. The move to the cloud, together with more agile servicing and frequent updates, requires a less intrusive customization model, so that updates are less likely to affect custom solutions. This new model is called *extensibility* and has replaced customization through overlayering.

Extensibility is the only customization framework in Finance, Supply Chain, and Commerce. Overlayering isn't supported.

## Introduction

These introductory topics contain general information about customization. This information includes information about when the transition occurs from customization through overlayering to a purely extension-based model. These topics also explain how to log extensibility requests to Microsoft, and provide answers to frequently asked questions (FAQ).

+ [Application extensibility plans](extensibility-roadmap.md)
+ [Extensibility requests](extensibility-requests.md) 
+ [Extensibility FAQ](app-sealing-faq.md) 

## What's new

Read [What's new or changed for extensibility](extensibility-new.md) for extensibility-related updates that have been made since July 2017.

## Getting started

The topics in this section will help you start to build extensions. They will also help you migrate solutions that are currently based on overlayered code to extension-based solutions. This section includes hands-on labs that walk you through simple customizations.

+ [Migrate from overlayering to extensions](migrate-overlayer-extension.md)
+ [Customize model elements through extension](customize-model-elements-extensions.md)
+ [Customize through extension and overlayering](customization-overlayering-extensions.md)

## Fundamentals on extensions

This section includes fundamentals, principles, and practices for making extensions. The guiding principles in these topics discuss how customization must be approached through extensions. These principles include naming guidelines. Additionally, these topics discuss the foundation framework, such as extensions and chain of command.

+ [Intrusive customizations](intrusive-customizations.md)
+ [Class extension model in X++](class-extensions.md)
+ [Class extension - Method wrapping and Chain of Command](method-wrapping-coc.md)
+ [Naming guidelines for extensions](naming-guidelines-extensions.md)
+ [Relax model restrictions to refactor overlayering into extensions](refactoring-over-layering.md)

## How do I create extensions?

This section includes "How do I?" topics that explain how to customize specific object types or code. Most of these topics are brief and to the point. Because there are many topics here, it might be practical to search for a specific article.

### Data types
+ [Add values to enums through extension](add-enum-value.md)
+ [Modify extended data types (EDTs) through extension](modify-edt.md) 

### Classes
+ [Register subclasses for factory methods](register-subclass-factory-methods.md)
+ [Respond by using EventHandlerResult](respond-event-handler-result.md)
+ [Extend the RunBase class](extend-runbase-class.md)
+ [Customize application startup by using delegates](startup-customizations.md)

### Tables
+ [Modify existing fields in a table through extension](modify-existing-field.md)
+ [Add fields to tables through extension](add-field-extension.md)
+ [Add indexes to tables through extension](add-index.md)
+ [Add relations to tables through extension](add-relation.md)
+ [Modify table properties through extension](modify-properties.md)
+ [Add methods to tables through extension](add-method-table.md)
+ [Perform business actions throughout the lifecycle of table records](subscribe-table-events.md)

### Forms
+ [Add a new data source to a form](add-datasource.md)
+ [Change the captions of forms through extension](change-caption-form.md)
+ [Modify the properties of form controls through extension](modify-control-properties.md)

### Others
+ [Extending decimal point precision for selected data types](decimal-point-precision.md)
+ [Add new inventory dimensions through extension](inventory-dimensions.md)

### Reports
+ [Extend the list of Electronic reporting (ER) functions](../analytics/general-electronic-reporting-formulas-list-extension.md)
+ [Customize App Suite reports by using extensions](../analytics/customize-app-suite-reports-with-extensions.md)

### Blog posts

Information about customization is also shared through blogs where various topics are discussed. This section includes reference to some of these blogs.

+ [Extending Dynamics 365 for Finance and Operations](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/extending-dynamics-365-for-operations)
+ [Extension methods](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/x-in-ax7-extension-methods/)
+ [Extensible base enumerations](https://kashperuk.blogspot.dk/2016/09/development-tutorial-extensible-base.html)
+ [Static event subscription](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/x-in-ax7-static-event-subscription/)
+ [Subscribing to onValidatingWrite](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/subscribing-to-onvalidatingwrite/)
+ [Embrace the extensions mindset with Dynamics 365 for Finance and Operations](https://community.dynamics.com/ax/b/axinthefield/posts/embrace-the-extensions-mindset-with-dynamics-365-for-finance-and-operations-2-sysextension-framework)
+ [Extensible X++ - Method Signatures](https://community.dynamics.com/365/financeandoperations/b/mfp/posts/extensible-x-method-signatures/)

## How do I create an extensible solution?

This section includes some best practices on how to create/make your solution extensible, so that consumers of your code can extend your solution.

+ [Write extensible code](writing-extensible-code.md)
+ [Classes](extensible-classes.md)
+ [Methods](extensible-methods.md)
+ [Forms](extensible-forms.md)
+ [Extended data types](extensible-edts.md)
+ [Extensible enums](extensible-enums.md)
+ [Delegates](extensible-code-delegates.md)
+ [Tables](extensible-tables.md)
+ [Attributes that make methods extensible](extensibility-attributes.md)

## Breaking changes

When you make your solution extensible, you also help guarantee that you won't break those extension points later. 

+ For pointers that can help you avoid breaking your consumers, see [Breaking changes](breaking-changes.md).
+ The [compatibility checker tool](compatibility-checker-tool.md) can detect metadata breaking changes against a given baseline release or update, helping to ensure backward compatibility.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
