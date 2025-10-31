---
title: What's new or changed in Dynamics 365 for Operations platform update 3 (November 2016)
description: Learn about the new or changed features in Dynamics 365 for Operations platform update 3. This version was released in November 2016.
author: johnmichalak
ms.author: johnmichalak
ms.topic: whats-new
ms.date: 10/31/2025
ms.update-cycle: 1095-days
ms.custom: 
  - bap-template
  - evergreen
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3
ms.assetid: 8beb4e7f-4a71-4c50-adf7-7733e6a150d9
ROBOTS: NOINDEX, NOFOLLOW
---

# What's new or changed in Dynamics 365 for Operations platform update 3 (November 2016)

[!include [banner](../../../finance/includes/banner.md)]

This article describes features that are new or changed in Dynamics 365 for Operations platform update 3. This version was released in November 2016 and has a build number of 7.0.4307.16141.

## General

| What you can do | Why is this important |
|-----------------|-----------------------|
| Dynamics AX is rebranded to Dynamics 365 for Operations. | Microsoft Dynamics AX is now part of the new Microsoft Dynamics 365 umbrella. This change requires rebranding in terms of both the product name and the product icon. The new name for Dynamics AX is Dynamics 365 for Operations. |
| Use a Dynamics 365 for Operations trial | You can get a 30-day trial of Dynamics 365 for Operations through a simple email signup. The trial version of Dynamics 365 for Operations includes a Getting started guide that provides a step-by-step task guide, which allows you to view specific scenarios in action. You can explore the product and exercise scenarios. Demo data is included to ease the use of the product and to make the experience more meaningful. A reminder email is sent three days before the trial expiration. You can initiate a buy experience at that time to complete the purchase. |

## Development and customization

| What you can do | Why is this important |
|-----------------|----------------------|
| Extend label files to customize and localize labels. | You can modify the string values of existing labels and add new languages to existing label files without the need to edit or overlay existing models. Refer to the "Label extensions" section in [Customization: Overlayering and extensions](../../dev-itpro/extensibility/customization-overlayering-extensions.md). |
| Take advantage of seamless servicing and continuous updates. | The Dynamics 365 for Operations platform includes the following models:<br>• Application Platform<br>• Application Foundation<br>• Test Essentials<br>• Corresponding form adaptor models<br><br>Locking the platform paves the way for seamless servicing and continuous update of the Dynamics 365 for Operations platform. If you overlay any of the platform models, you won't be able to upgrade to this release. You need to refactor your code to use metadata and code extensions. For a tutorial about how to use extensions for customization, see [Customize model elements using extensions](../../dev-itpro/extensibility/customize-model-elements-extensions.md). You can also refer to [Customization: Overlayering and extensions](../../dev-itpro/extensibility/customization-overlayering-extensions.md), which is a general article on customizations.<br>**NOTE:** Regarding the Directory model, if your code overlayers elements in the Directory model, you need to deploy new environments running the latest Dynamics 365 for Operations application. Overlayering the directory model isn't supported on environments running the February 2016 or May 2016 releases of the application on top of Platform Update 3. |
| Add a form part to a form extension and use Go to/F9 functionality. | Using a form extension, you can now add a Form Part reference to any form without overlayering the form. In addition, you can use Go to (F9) to go to the referenced form when browsing a form part in the form designer. |
| Add a new mapping to a data entity extension. | You can now add a new mapping to a data entity extension, which means you can associate the data entity with a new map without overlayering. |
| Change a form caption using a form extension. | You can now change the caption of a form without overlayering the form. Using a form extension you can change the caption property. |
| Change an EDT FormHelp property using an EDT extension. | Using an extended data type (EDT) extension, you can change the FormHelp property. This lets you change or add a custom lookup form anywhere an EDT is used without overlayering the EDT. |
| Change the label of a table field using a table extension. Change the Created By, Created Date Time, Modified By, Modified Date Time properties of a table using a table extension. | You can change the label of an existing field of a table without overlayering the table. This can be done using a table extension. You can also modify the values of the properties Created By, Created Date Time, Modified By, Modified Date Time of a table without overlayering. |
| Refer to an extensible enum when defining fixed field relations for a data entity. | You can refer to an extensible enumeration when defining a fixed field relation on a data entity. |
| View extension fields in the Visual Studio debugger. | When debugging tables and other similar extensible elements, you can view extension fields in the debugger. |
| Customize application reports using extensions. | Avoid the expense and complexity associated with overlayering standard application solutions for common customizations. Dynamics 365 for Operations now includes support for customizing application reports using element extensions. This enhancement means that you can redirect existing menu items to custom reports designs without changing application references. You can also extend the datasets returned by Report Data Providers classes without duplicating or overlayering application code. For detailed information about using extensions for application customizations, see [Customize model elements using extensions](../../dev-itpro/extensibility/customize-model-elements-extensions.md). |
| Use built-in document brand management tools to customize modern report designs for core business documents, including Sales Invoices, Purchase Packing Slips, and Vendor Invoice Documents. Add the Application Suite Modern Designs model file available on Lifecycle Services to your solution. | This feature provides the following:<br>• A configuration-based solution for managing multiple commercial brands operated by a single legal entity.<br>• Modern report designs for various core business documents.<br>• A way for customers to manage document header information using administration forms without disrupting active services. |
| Customize Help using extensions | You can add a tab to the Dynamics 365 for Operations Help form to display third-party Help content, alongside the Task guides and article sources that ship out of the box. In previous versions, the only way to access to a user's search terms, so that they can be used in the additional source of Help, was to overlayer the form. A delegate has now been added to the Help form (SysHelpPane), so you can intercept a user's search terms and use them to search for Help content in third-party systems. |
| Prevent unsupported changes of configuration key properties. | You can no longer change a Configuration key property (for example, on a form control) if the referenced configuration key is defined in a binary model. A binary model is a model installed without its source code. ISVs define licenses and configuration keys and distribute them as binary models. This feature indicates to developers that changing configuration key assignments isn't officially supported by the development tools. This feature doesn't prevent a developer from making the change in a text editor outside of the Visual Studio development tools, which would be considered unauthorized use. |

## Servicing environments

| What you can do | Why is this important |
|-----------------|-----------------------|
| Merge up to three deployable packages. | This feature significantly reduces the downtime resulting from the application of these packages, and optimizes applying these packages and the overall wait time. |
| Apply deployable packages with reduced downtime. | Currently, the average downtime needed to apply a single package in an environment deployed through Lifecycle Services can be up to 5 hours. With this feature, the package application is optimized so that the downtime is greatly reduced. |
| Troubleshoot deadlocks using monitoring and diagnostics tool in Lifecycle Services. | With this feature you can troubleshoot deadlocks using the monitoring and diagnostics tools in Lifecycle Services to review the query that has deadlocks and perform advanced troubleshooting by reviewing the deadlock graphs. |

## Lifecycle Services

Lifecycle Services releases new features every month. For information about what's new, visit the [Lifecycle Services blog](https://blogs.msdn.microsoft.com/lcs/). Use the search term, "release plans" to search for and view the monthly release and new feature information.

## Client

| What you can do | Why is this important |
|-----------------|-----------------------|
| Use the down arrow in a grid to add a new row. | When adding rows to a grid, the use of down arrow to create a new row would be ignored if the current row contained incomplete information. This behavior was inconsistent with the use of the **Add New** button and its shortcut **Alt+N**. Using the down arrow to create a new row is now consistent. |
| Some APIs are now deprecated | With the introduction of a new web-based platform, the Dynamics 365 for Operations platform offers a complete set of new interactive controls. In some cases, seldom used properties or methods were deprecated on controls that existed in Dynamics AX 2012. In the case of the FormListControl, some seldom used methods weren't implemented but their API weren't marked as deprecated. With this release, those methods are now marked as deprecated. |

## Mobile app

| What you can do | Why is this important |
|-----------------|-----------------------|
| Design mobile workspaces to enable your users to stay productive while on the move. | Dynamics 365 for Operations brings support for a mobile phone app (available on the iTunes App Store for iPhones, Google Play Store for Android phones, and Windows Store for Window phones). The mobile approach allows you to reuse business logic and modeling from the product while enabling rich offline and mobile interactions, and an easy-to-use designer experience. Developers can create simplified forms in Microsoft Visual Studio and then design mobile pages that expose this functionality. This mobile solution makes it easy to change the forms and mobile app definitions in order to include customizations made to the product. For more information, see [Mobile platform resources](../mobile-apps/platform/mobile-platform-home-page.md). |

## Analytics

| What you can do | Why is this important |
|-----------------|----------------------|
| Create Power BI reports with enumerated fields. | When creating Microsoft Power BI reports with enumerated fields, you had to write formulas in Power BI desktop and expand the enumerated values into their string values. Now enumerated fields are expanded in Entity store and you can use the corresponding label field directly in your reports. |
| Access five new Power BI content packs for Human resources | The new content packs enable human resource organizations and human resources managers to analyze the following:<br><br>Workforce metrics<br>• Demographic breakdowns by age, gender, and marital status<br>• Compare attrition rates year over year and see a list of reasons employees gave for leaving the organization<br>• View a list of open positions, and a comparison of open to closed positions<br><br>Compensation and benefits<br>• Compare hourly and salaried employees<br>• View the number of employees enrolled in available benefits<br>• View employees by employment type<br><br>Recruiting<br>• Analyze applicants based on the number of applicants, where they're coming from, and what positions they're applying for<br><br>Organizational training<br>• Course registration by location<br>• Couse attendance by status<br>• List of employees registered for courses<br><br>Employee competencies and development<br>• List of skills held by employees<br>• Breakdown of skill types by team member |

## Additional resources

[What's new or changed in Finance and Operations home page](../../fin-ops/get-started/whats-new-changed.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
