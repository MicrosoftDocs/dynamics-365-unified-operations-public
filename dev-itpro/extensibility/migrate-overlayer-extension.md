---
# required metadata

title: Migrate from overlayering to extensions
description: 
author: FrankDahl
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinarh
ms.search.scope: Operations, Platform, AX Platform
# ms.tgt_pltfrm: 
ms.custom: 89563
ms.assetid: 8DA4DA85-0C2D-4CAF-B350-DAC9C1BE4DF9
ms.search.region: Global
# ms.search.industry: 
ms.author: pvillads
ms.search.validFrom: 2017-07/01
ms.dyn365.ops.version: Platform update 9
---

# Migrate from overlayering to extensions

# Introduction

When Dynamics 365 for Finance and Operations, Enterprise Edition was first released we strongly encouraged strongly extensions over overlayering for customization. Overlayering-based customizations have been migrated from release to release through code migrations, and still today there is a lot of customization of application code that is based on overlaying of code. Most partners will have at least some of their solution that is still based on overlaying, and some will have a lot of overlaying across their solutions.

The work involved in changing an implementation from overlayered code to extensions depends on the specific code. Some overlayered code can be changed quite seamlessly while some changes require rethinking the customization to find a suitable way of accomplishing this through extension. This can amount to quite an undertaking to change complete solutions that consist of multiple places of overlayered code. This means an investment in the solution. The upside of making this investment is a more seamless upgrade process as customization now has become API based through extensions - and there is no longer a need for going through long and tiresome code upgrade as it used to with overlayered code. More importantly though are daily servicing of running environment that offer immense benefits. The core application and extensions no longer require to be compiled together, and patching can be done through deploying precompiled assemblies. This help customers quite seamlessly in applying patches to their system, and minimize the downtime otherwise experienced. Still there is work that initially must be done before this can be achieved.

While there are multiple ways to approach this effort, we from Microsoft have been collecting some experience through working closely with some ISVs and VARs that have started on this journey. This topic seeks to share some of the experience collected across these partners.

## First things first! 

The task ahead is substantial and we want to be sure our shared investment pays dividends. Keep the goal in mind as you work through your customizations. When done correctly, your solution has these qualities:
+ Has no intrusive customizations
+ Supports side-by-side deployment with other ISV solutions.
+ Is resilient to changes in Microsoft code.
+ Is resilient to changes in other ISV solutions.
+ Can be upgraded automatically to future versions.

This is a fundamental shift of approach! Previously the primary objective was to get the functional requirements implemented on the current version. This was ok, as we knew manual work was required to upgrade the solution. Previously; great engineers *minimized*  the manual upgrade cost. **Now; every engineer must implement solutions requiring zero effort to upgrade.**

## Staying on the right path

Cars are designed to be safe; however they cannot (yet) prevent accidents - that remains the driver's responsibility. Similarly; the development tool set is designed for extensibility. However; the tool set cannot (yet) prevent every type of intrusive customizations.  As an engineer it is your responsibility to avoid intrusive customizations. 

There will be cases where you can only reach your functional goal by implementing intrusive customizations. If you find yourself in that unfortunate situation, the right action would be to reach out to Microsoft to find a proper solution. You should not force your way ahead. The consequences could be customers realizing your solution is not future proof after all - for example due to an outage of their service after an automated upgrade. 

"Being future-proof" as a competitive advantage, it is worth the extra effort to get right.

# Obtaining an overview

When you try to obtain an overview, they first consider analyzing each of your solutions independently rather than altogether. This may be practical even if you have different teams each working on the separate solutions, as you may consider one team to engage earlier than others to obtain some experience there first. Experience is valuable both in the sense of how to analyze, and plan the work, while also for the team to ramp up and become familiar with the extensibility model. Jointly this may prove to become valuable lessons learned from this can be applied on later solutions.

Practically we have experience from ISVs that take each of their ISV solutions in turn, and some ISVs that also operate as VARs take customer solutions later.

Irrespective on how the work is pieced up in solutions, one convenient means of getting information on what has been overlayered is with the CAR report. The CAR report is the report that is generated when you submit your solutions to the Code Migration tool on LCS. The CAR report in Excel format includes a list of all placed with overlayered code. This file can be used to both analyze and categorize all overlayered instances in your solution.

Then to obtain an overview it is commonly helpful to categorize each overlayered instance. It is suitable to apply categories to the overlayered instances that roughly represent the effort associated with changing to extensions. There are overlayer code that will seamless render itself to transform into extensions, but then there are also those that require more.

From working with a number of ISVs we have found the following categories a good basis for the initial categorization.

| Category       | Description          |
|---------------- |:-------------|
| Extensible enums     | When you add values to an enumerable, where this is only possible by overlayering, and also with overlayer of methods throughout the application to account for the new value - Microsoft plan to make requested enums extensible and refactor (adding extension points) to the impacted methods.|
| Construct with throw| Most construct methods are simple, and can be extended using post event handlers. However, some construct methods are more complicated and throws an exception when no class is created. |
| Exposing members | Member variables defined with access modifiers private are not accessible through extensions, unless they become exposed through public methods. Requests access to members through extensions that current have not been exposed for this. Notice access to protected members will generally be enabled through extension classes |
| Data manipulation methods that does not raise DataEvents| Some places in the application where data methods like insert() / update() does not call super() and as such does not raise DataEvent to add extensions to. Microsoft to refactor the standard application to include additional methods that enable extensions in these places. When creating requests for this, please add any of these impacted methods that you need to overlayer today, if not already accounted for. |
| Hookable methods | Methods defined with access modifiers private are not possible to extend. This epic is to track requests request for adding such hooks where these currently are not exposed.|
| Inline delegates | Code changes done in the middle of methods which are not possible through either pre- / post event and also not through extension classes. When requesting an inline delegate make sure to specify what variables are critical for your extension.|
| SQL statement operations | SQL statements written directly in the application code does not enable extensions. When making request for extending these, make sure to explicitly specify what you need to extend like field list, where clauses, ordering|
| Metadata overlayering | Provide the AOT path of the element where you believe the metadata (property value) needs to be changed, which currently cannot be done through existing extension capabilities|
| Method overlayering | Customization where a method is overlayered. Consider here the feasibility for transforming into an extension class or similar such that changes are clean as by extension not substitution|
| Method signature changes | Changing method signatures by overlaying will be discontinued, and other patterns for achieving similar is required. Places where the standard signature should be changes for extensibility may be requested as far requirements are of general interest. Please share information on what additional parameters are needed. |
| Inventory dimensions | There is no longer support for adding dimensions by editing the macro and recompiling the standard application. Another approach will be offered with predefined dimensions that are then deployed at runtime. This drives changes to existing customization where new dimensions are added.|
| Extensibility platform  | Some customizations may not be possible by extensions without adding new planform features. If this is concluded then open an extensibility request that explain the scenario and what is needed.|
| Reports  | Customizations of reports designs have limited extensibility support and generally require that a new report is created. Data Provider classes may also be customized with additional information which in some places require changed to the standard application to enable.|
| Other  | There is always the odd one out - that does not fit in with other categories and for this categorizing this separately|

Having all overlaying code categorized helps obtain an overview of what needs to be changed.

# Analyzing for impact and estimate work

The common approach of breaking down tasks into something tangible to help assessing the work impact also applies with this work. The categories discussed in the prior paragraph helps frame similar customizations, and a first pass on estimates may be built from coming up with an overall estimate for each of these and similar categories that make up your solution. The group of customizations in a given category often has a few extremes that stand out, and it may suitable to establish estimates for these individually.

Do consider that some customization will either require a request to Microsoft for enabling extensibility, or alternative refactoring of the customization in ways it can be done through extensibility. This will add to estimates for migrating the solution.

Customization that drives what we refer to as intrusive changes are often more complex to migrate into becoming extension based. These changes require consideration on what is the right way to approach the customization. This list contains examples to where this may be the case.

| Customization       |
|:----------------|
|Customization that request inline delegates |
|Customization of complex classes / methods like SalesLinetype |
| Changes to method signature |
| Adding inventory dimensions |
| Report changes to report definition and data provider classes |
| Intrusive change to forms |

Changes that require different approaches for customization to become extension based, may result in logging requests for enabling extensibility to Microsoft. Make sure to account for both the time that go into this as schedule impact into your plans.

# What is supported, and what require logging an extensibility request?

When you review a customization make so to consider different options for building this through extensions. Make sure to review options like if a method is hookable, or possible as class extension, form event or what else is offered that can be used. Review most current available application code you have available, which includes planned monthly CTP drops as downloadable VHD's. A source of information that offer guidance is the what's new for customizations changelog that are planned to be published regularly.

Some customizations end up with the conclusion that a change to the standard application is required to enable the customization by extensions. This is where an extensibility request must be logged through the connect feedback program, to put this into the backlog at Microsoft for to address. Do **not** log extensibility request by opening requests for hotfix, as Microsoft will not release extensibility requests as hotfixes.

Make sure to supply sufficient context information with extensibility requests. For instance, a request for an inline delegate may come from the current customization approach, while the requirement that led to this customizaition might be better served with a structure change to the standard application to better accommodate extension. We from Microsoft appreciate suggestions like this as it helps bring the application toward a better platform for building different customizations.

# Planning the migration

Make sure to start early with planning migration of your solutions. This is particularly advisable to ensure room in your schedules for identifying extensibility requests, logging these, and time inferred before these can become available for you to deploy. Also acknowledge your developers may require building new skills and make sure to cater for any required learning is part of the migration plan.

Microsoft plan to release CTP drops regularly as VHD downloads, that will include up to date application code. The general idea is to offer that partners can work concurrently with Microsoft toward the next release. This is to minimize the time lag after the new release is made public available to when your solution is ready to be deployed.

You solution may contain intrusive customizations that are not easy to accommodate through extensions. Here optionally consider if the business value of these customization outweighs the effort of building these through extensions. Some partners have decided to discontinue some part of their solution that they found impractical to rebuild by extensions, while at the same time they were not critical to their solution.

You may be customizing smaller fixes across the application that you do not see core for your solution, yet find important for customers you engage with. In such cases consider if you would rather prefer to ask Microsoft for implementing similar capabilities in the standard application. In such cases we welcome that you share this by filing an extensibility requests for this, that we then may address not through your customization but directly in the standard application. For instance, customers may want to simplify standard business processes in the system, that may suggest we add options for disabling steps in the process in the standard application.

The documentation around extensibility includes many small how to type of pages, that will further help assist your migration. Please use these resources and provide feedback if information is missing.
