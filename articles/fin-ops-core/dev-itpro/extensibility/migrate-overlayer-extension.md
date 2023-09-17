---
title: Migrate from overlayering to extensions
description: This article provides information about migration from customizations that are based on overlayered code to customizations that are based on extensions.
author: FrankDahl
ms.date: 04/10/2018
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer
ms.reviewer: josaw
ms.search.region: Global
ms.author: fdahl
ms.search.validFrom: 2017-07-01
ms.dyn365.ops.version: Platform update 9
ms.assetid: 
---

# Migrate from overlayering to extensions

[!include [banner](../includes/banner.md)]

## Introduction

When the application was first released, we strongly recommended that extensions be used instead of overlayering for customization. Overlayering-based customizations have been migrated from release to release through code migrations, and many customizations of application code are still based on the overlayering of code. For most partners, at least some of their solution is still based on overlaying, and some partners will have lots of overlayering across their solutions.

The amount of work that is required to change an implementation from overlayered code to extensions depends on the code itself. Some overlayered code can be changed relatively seamlessly. However, for some changes, you must rethink the customization to find an appropriate way to accomplish it through extension. Therefore, it can be a major undertaking to change complete solutions where multiple places have overlayered code. Such an undertaking requires an investment in the solution. The upside of this investment is a more seamless upgrade process, because customization is now based on application programming interfaces (APIs) through extensions. Additionally, a lengthy code upgrade process is no longer required as it was for overlayered code. More importantly, daily servicing of a running environment offers many benefits. The core application and extensions no longer have to be compiled together, and patching can be done by deploying precompiled assemblies. Therefore, customers can apply patches to their system in a relatively seamless manner, and the amount of downtime is minimized. However, there is work that must be done before this result can be achieved.

Although there are multiple ways to approach this task, we have gained experience through our close work with independent software vendors (ISVs) and value-added resellers (VARs) that have already started to migrate from overlayering to extensions. In this article, we share some of this experience.

### First things first

The task ahead is substantial, and we want to make sure that our shared investment pays dividends. Keep the goal in mind as you work through your customizations. When customization is done correctly, your solution has these qualities:

+ It has no intrusive customizations.
+ It supports side-by-side deployment with other ISV solutions.
+ It's resilient to changes in Microsoft code.
+ It's resilient to changes in other ISV solutions.
+ It can be upgraded automatically to future versions.

This type of customization represents a fundamental shift of approach. Previously, the primary objective was to implement the functional requirements on the current version. This objective was acceptable, because we knew that manual work was required in order to upgrade the solution. Previously, great engineers minimized the manual upgrade cost. Now, *every* engineer must implement solutions that require *zero effort* to upgrade.

### Staying on the right path

Cars are designed to be safe. However, they can't yet prevent accidents. Accident prevention remains the driver's responsibility. Similarly, the development toolset is designed for extensibility. However, the toolset can't yet prevent every type of intrusive customization. As an engineer, it's your responsibility to avoid intrusive customizations. 

Sometimes, you might find that you can reach your functional goal only by implementing intrusive customizations. In this case, you should reach out to Microsoft to find a correct solution. You should not force your way forward. Otherwise, customers who, for example, experience an outage of their service after an automated upgrade might realize that your solution isn't future-proof after all.

Because a future-proof solution represents a competitive advantage, it's worth the extra effort to do it correctly.

## Obtain an overview of your code

When you create an overview of your code, first consider analyzing each of your solutions independently instead of analyzing them all together. This approach might be practical even if different teams work on the individual solutions. By choosing one team that you will engage before the other teams, you can gain some experience. Experience is valuable, because it not only helps you analyze and plan the work, but also helps the team ramp up and become familiar with the extensibility model. Therefore, the experience that you and your team gain can become valuable "lessons learned" that you can apply to later solutions.

We have gained practical experience both with ISVs that take each ISV solution in turn, and with ISVs that work as VARs and take customer solutions later.

No matter how the work is pieced together in solutions, you can use the [Customization Analysis Report (CAR)](../dev-tools/customization-analysis-report.md) to get information about what has been overlayered. This report is generated when you submit your solutions to the Code Migration tool on Microsoft Dynamics Lifecycle Services (LCS). The report is in Microsoft Excel format and includes a list of all the places that have overlayered code. You can use the report to both analyze and categorize all overlayered instances in your solution.

To obtain an overview, you might find it helpful to categorize each overlayered instance. The category that you apply to an overlayered instance should represent the approximate effort that is required in order to change the customization to extensions. Some customizations will be easily changed to extensions. However, for other customizations, the change will be more difficult.

From our experience working with numerous ISVs, we have found that the following categories are a good starting point.

| Category | Description |
|----------|-------------|
| Extensible enums | You can add new enum values by using extensions. For more information, see [Add values to enums through extension](add-enum-value.md). |
| Construct with throw | Most construct methods are simple and can be extended by using post-event handlers. However, some construct methods are more complex and throw an exception when no class is created. |
| Exposing members | Member variables that have the **private** access modifier in their definition can't be accessed through extensions unless they become exposed through public methods. You can request that we add access to members through extensions that currently have not been exposed for this. Note that access to protected members is generally enabled through extension classes. |
| Data manipulation methods that don't raise DataEvents | In some places in the application, data methods such as **insert()** and **update()** don't call **super()**. Therefore, the methods don't raise DataEvents to add extensions to. Microsoft plans to refactor the standard application so that it includes additional methods that enable extensions in these places. If you submit a request for Microsoft to add this, add any of the affected methods that you must currently overlayer, if those methods haven't already been accounted for. |
| Extract method | This category is for code changes in the middle of methods, which can't be made through chain of command. When you request a method extraction, be sure to specify which lines of a method to extract, and what the signature of the new method must be. |
| SQL statement operations | SQL statements that are written directly in the application code don't enable extensions. When you make a request to extend these SQL statements, be sure to explicitly specify what you must extend, such as a field list, **where** clauses, or ordering. |
| Metadata overlayering | Provide the Application Object Tree (AOT) path of the element where you believe the metadata (property value) must be changed. Metadata changes can't be made through the current extension capabilities. |
| Method overlayering | This category is for customizations where a method is overlayered. You should consider converting the overlayed method to an extension, so that changes are clean by extension not substitution. |
| Method signature changes | The capability to change method signatures through overlayering will be discontinued. Other patterns for achieving similar results are required. You can request changes to the standard signature to support extensibility. Be sure to include information about additional parameters that are required. |
| Inventory dimensions | You can no longer add dimensions by editing the macro and recompiling the standard application. Another approach will be offered that involves predefined dimensions that are deployed at runtime. This approach drives changes to existing customizations where new dimensions are added. |
| Extensibility platform  | Some customizations might not be possible through extensions unless new platform features are added. If you determine that customizations can't currently be done through extensions, open an extensibility request that explains the scenario and what is required. |
| Reports  | Customizations of report designs have limited support for extensibility. In general, a new report must be created. Data provider classes can also be customized so that they include additional information. In some places, the standard application must be changed to enable this type of customization. |
| Other  | This category is for overlayering instances that don't fit into any other category. |

By categorizing all overlaying code, you gain an overview of what must be changed.

## Analyzing for impact and estimating work

In a typical approach to assessing work impact, you break down tasks into something tangible. This approach also applies to this work. The categories that were discussed in the previous section help frame similar customizations, and a first pass on estimates can be built by coming up with an overall estimate for each of these categories and similar categories that make up your solution. The group of customizations in a given category often has a few extremes that stand out, and it might be appropriate to establish estimates for these customizations individually.

Consider that some customizations will require either a request to Microsoft to enable extensibility or significant refactoring of the customization so that it can be done through extensibility. Both of these scenarios will increase the estimates for migrating the solution.

Customization that drives what are referred to as intrusive changes is often more complex to convert to extensions. For these changes, you must consider what is the correct way to approach the customization. Here are some examples of these changes:

+ Customizations that request inline delegates. 
+ Customizations of complex classes or methods such as **SalesLinetype**.
+ Changes to method signatures.
+ Additions of inventory dimensions.
+ Changes to report definitions and report data provider classes.
+ Intrusive changes to forms.

For changes that require different approaches to make the customizations extension-based, you might have to log requests to Microsoft to enable extensibility. When creating your migration schedule, you'll need to take into account the delay of waiting for updates from Microsoft.

## What is supported, and what requires an extensibility request?

When you review a customization, be sure to consider different options for converting it to an extension. Be sure to consider whether a method is hookable, or whether it can be a class extension or form event. Review most of the currently available application code that is available to you. 

You might conclude that a change to the standard application is required in order to enable the required extension. In this case, you must [log an extensibility request](extensibility-requests.md). The request is then put into the backlog at Microsoft so that it can be addressed. Don't log extensibility requests by opening a request for a hotfix, because Microsoft doesn't release extensibility requests as hotfixes.

Be sure to supply enough contextual information in your extensibility requests. For example, a request for an inline delegate might come from the current customization approach. However, to better accommodate extension, the requirement that led to this customization might be better served by a structural change to the standard application. We appreciate suggestions of this type, because they help move the application toward a better platform for building different customizations.

## Planning the migration

Be sure to start planning the migration of your solutions early. This planning is important because it helps you make sure that you have room in your schedules to identify and log extensibility requests, and that you have room for the time delay before these requests become available in product releases. Additionally, acknowledge that your developers might have to build new skills, and make sure that you cater to any required learning as part of the migration plan.

Your solution might contain intrusive customizations that aren't easily accommodated through extensions. You should consider whether the business value of these customizations outweighs the effort of building them through extensions. In some cases, partners have decided to discontinue parts of their solutions, because they found that it was impractical to rebuild those parts through extensions, and those parts weren't critical to the solutions.

Some smaller fixes that you're customizing across the application might not be core for your solution, but they are important for the customers that you engage with. In these cases, you must decide whether you prefer to ask Microsoft to implement similar capabilities in the standard application. You can enter an extensibility request for this purpose. For example, if customers want to simplify standard business processes in the system, you might suggest that we add options for disabling steps of the process in the standard application.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
