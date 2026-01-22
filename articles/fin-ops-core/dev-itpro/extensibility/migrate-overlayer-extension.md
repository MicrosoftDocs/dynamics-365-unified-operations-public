---
title: Migrate from overlayering to extensions
description: Learn about migration from customizations that are based on overlayered code to customizations that are based on extensions.
author: FrankDahl
ms.author: johnmichalak
ms.topic: upgrade-and-migration-article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer
ms.search.region: Global
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
---

# Migrate from overlayering to extensions

[!include [banner](../includes/banner.md)]

## Introduction

When the application was first released, Microsoft strongly recommended using extensions instead of overlayering for customization. Developers migrated overlayering-based customizations from release to release through code migrations, and many customizations of application code are still based on the overlayering of code. For most partners, at least some of their solution is still based on overlaying, and some partners have lots of overlayering across their solutions.

The amount of work that is required to change an implementation from overlayered code to extensions depends on the code itself. You can change some overlayered code relatively seamlessly. However, for some changes, you must rethink the customization to find an appropriate way to accomplish it through extension. Therefore, it can be a major undertaking to change complete solutions where multiple places have overlayered code. Such an undertaking requires an investment in the solution. The upside of this investment is a more seamless upgrade process, because customization is now based on application programming interfaces (APIs) through extensions. Additionally, a lengthy code upgrade process is no longer required as it was for overlayered code. More importantly, daily servicing of a running environment offers many benefits. The core application and extensions no longer have to be compiled together, and patching can be done by deploying precompiled assemblies. Therefore, customers can apply patches to their system in a relatively seamless manner, and the amount of downtime is minimized. However, there's work that must be done before this result can be achieved.

Although there are multiple ways to approach this task, Microsoft gained experience through close work with independent software vendors (ISVs) and value-added resellers (VARs) that already started to migrate from overlayering to extensions. In this article, Microsoft shares some of this experience.

### First things first

The task ahead is substantial, and you want to make sure that your shared investment pays dividends. Keep the goal in mind as you work through your customizations. When customization is done correctly, your solution has these qualities:

+ It has no intrusive customizations.
+ It supports side-by-side deployment with other ISV solutions.
+ It's resilient to changes in Microsoft code.
+ It's resilient to changes in other ISV solutions.
+ It can be upgraded automatically to future versions.

This type of customization represents a fundamental shift of approach. Previously, the primary objective was to implement the functional requirements on the current version. This objective was acceptable, because manual work was required in order to upgrade the solution. Previously, great engineers minimized the manual upgrade cost. Now, *every* engineer must implement solutions that require *zero effort* to upgrade.

### Staying on the right path

Cars are designed to be safe. However, they can't yet prevent accidents. Accident prevention remains the driver's responsibility. Similarly, the development toolset is designed for extensibility. However, the toolset can't yet prevent every type of intrusive customization. As an engineer, it's your responsibility to avoid intrusive customizations. 

Sometimes, you might find that you can reach your functional goal only by implementing intrusive customizations. In this case, reach out to Microsoft to find a correct solution. Don't force your way forward. Otherwise, customers who, for example, experience an outage of their service after an automated upgrade might realize that your solution isn't future-proof.

Because a future-proof solution represents a competitive advantage, it's worth the extra effort to do it correctly.

## Obtain an overview of your code

When you create an overview of your code, first consider analyzing each of your solutions independently instead of analyzing them all together. This approach might be practical even if different teams work on the individual solutions. By choosing one team that you engage before the other teams, you can gain some experience. Experience is valuable, because it not only helps you analyze and plan the work, but also helps the team ramp up and become familiar with the extensibility model. Therefore, the experience that you and your team gain can become valuable "lessons learned" that you can apply to later solutions.

You can gain practical experience both with ISVs that take each ISV solution in turn and with ISVs that work as VARs and take customer solutions later.

No matter how you piece together the work in solutions, you can use the [Customization Analysis Report (CAR)](../dev-tools/customization-analysis-report.md) to get information about what code is overlayered. You generate this report when you submit your solutions to the Code Migration tool on Microsoft Dynamics Lifecycle Services (LCS). The report is in Microsoft Excel format and includes a list of all the places that have overlayered code. You can use the report to both analyze and categorize all overlayered instances in your solution.

To obtain an overview, you might find it helpful to categorize each overlayered instance. The category that you apply to an overlayered instance should represent the approximate effort that's required to change the customization to extensions. Some customizations are easily changed to extensions. However, for other customizations, the change is more difficult.

From our experience working with numerous ISVs, the following categories are a good starting point.

| Category | Description |
|----------|-------------|
| Extensible enums | You can add new enum values by using extensions. For more information, see [Add values to enums through extension](add-enum-value.md). |
| Construct with throw | Most construct methods are simple and can be extended by using post-event handlers. However, some construct methods are more complex and throw an exception when no class is created. |
| Exposing members | You can't access member variables that use the **private** access modifier in their definition through extensions unless they're exposed through public methods. You can request that Microsoft add access to members through extensions that aren't currently exposed. Access to protected members is generally enabled through extension classes. |
| Data manipulation methods that don't raise DataEvents | In some places in the application, data methods such as **insert()** and **update()** don't call **super()**. Therefore, these methods don't raise DataEvents to add extensions to. Microsoft plans to refactor the standard application so that it includes additional methods that enable extensions in these places. If you submit a request for Microsoft to add this functionality, add any of the affected methods that you must currently overlayer, if those methods aren't already accounted for. |
| Extract method | This category is for code changes in the middle of methods, which can't be made through chain of command. When you request a method extraction, be sure to specify which lines of a method to extract and what the signature of the new method must be. |
| SQL statement operations | SQL statements that are written directly in the application code don't enable extensions. When you make a request to extend these SQL statements, be sure to explicitly specify what you must extend, such as a field list, **where** clauses, or ordering. |
| Metadata overlayering | Provide the Application Object Tree (AOT) path of the element where you believe the metadata (property value) must be changed. You can't make metadata changes through the current extension capabilities. |
| Method overlayering | This category is for customizations where a method is overlayered. Consider converting the overlayered method to an extension, so that changes are clean by extension and not substitution. |
| Method signature changes | The capability to change method signatures through overlayering is deprecated. Other patterns for achieving similar results are required. You can request changes to the standard signature to support extensibility. Be sure to include information about additional parameters that are required. |
| Inventory dimensions | You can no longer add dimensions by editing the macro and recompiling the standard application. Another approach is offered that involves predefined dimensions that are deployed at runtime. This approach drives changes to existing customizations where new dimensions are added. |
| Extensibility platform  | Some customizations might not be possible through extensions unless new platform features are added. If you determine that customizations can't currently be done through extensions, open an extensibility request that explains the scenario and what is required. |
| Reports  | Customizations of report designs have limited support for extensibility. In general, a new report must be created. Data provider classes can also be customized so that they include additional information. In some places, the standard application must be changed to enable this type of customization. |
| Other  | This category is for overlayering instances that don't fit into any other category. |

By categorizing all overlaying code, you gain an overview of what must be changed.

## Analyzing impact and estimating work

Typically, you assess work impact by breaking down tasks into tangible components. This approach also applies to this work. The categories discussed in the previous section help frame similar customizations. You can build a first pass on estimates by coming up with an overall estimate for each of these categories and similar categories that make up your solution. A group of customizations in a given category often has a few extremes that stand out. It might be appropriate to establish estimates for these customizations individually.

Some customizations require either a request to Microsoft to enable extensibility or significant refactoring of the customization so that it can be done through extensibility. Both of these scenarios increase the estimates for migrating the solution.

Customization that drives what are referred to as intrusive changes is often more complex to convert to extensions. For these changes, you must consider what is the correct way to approach the customization. Here are some examples of these changes:

+ Customizations that request inline delegates. 
+ Customizations of complex classes or methods such as **SalesLinetype**.
+ Changes to method signatures.
+ Additions of inventory dimensions.
+ Changes to report definitions and report data provider classes.
+ Intrusive changes to forms.

For changes that require different approaches to make the customizations extension-based, you might have to log requests to Microsoft to enable extensibility. When creating your migration schedule, take into account the delay of waiting for updates from Microsoft.

## What is supported, and what requires an extensibility request?

When you review a customization, consider different options for converting it to an extension. Consider whether a method is hookable, or whether it can be a class extension or form event. Review most of the currently available application code that is available to you. 

You might conclude that a change to the standard application is required to enable the required extension. In this case, [log an extensibility request](extensibility-requests.md). Microsoft adds the request to the backlog. Don't log extensibility requests by opening a request for a hotfix, because Microsoft doesn't release extensibility requests as hotfixes.

Supply enough contextual information in your extensibility requests. For example, the current customization approach might lead to a request for an inline delegate. However, to better accommodate extension, the requirement that led to this customization might be better served by a structural change to the standard application. Microsoft appreciates suggestions of this type, because they help move the application toward a better platform for building different customizations.

## Planning the migration

Start planning the migration of your solutions early. This planning helps you make sure that you have room in your schedule to identify and log extensibility requests, and that you have room for the time delay before these requests become available in product releases. Your developers might need to build new skills, so make sure that your migration plan includes any required learning.

Your solution might contain intrusive customizations that aren't easily accommodated through extensions. Consider whether the business value of these customizations outweighs the effort of building them through extensions. In some cases, partners decide to discontinue parts of their solutions because they find that it's impractical to rebuild those parts through extensions, and those parts aren't critical to the solutions.

Some smaller fixes that you're customizing across the application might not be core for your solution, but they're important for the customers that you engage with. In these cases, decide whether you prefer to ask Microsoft to implement similar capabilities in the standard application. You can enter an extensibility request for this purpose. For example, if customers want to simplify standard business processes in the system, you might suggest that Microsoft add options for disabling steps of the process in the standard application.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
