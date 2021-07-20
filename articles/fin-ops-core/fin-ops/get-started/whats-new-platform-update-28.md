---
# required metadata

title: What's new or changed in Dynamics 365 for Finance and Operations platform update 28 (July 2019)
description: This topic describes features that are in preview in Dynamics 365 for Finance and Operations platform update 28 (July 2019). 
author: tonyafehr
ms.date: 07/08/2019
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2019-07-31
ms.dyn365.ops.version: Platform 28

---
# What's new or changed in Dynamics 365 for Finance and Operations platform update 28 (July 2019)

[!include [banner](../includes/banner.md)]

This topic describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 28. This version has a build number of 7.0.5314. For more information about Platform update 28, see [Additional resources](whats-new-platform-update-28.md#additional-resources).

## Data management enhanced view as the default view
For several years the standard view in data management has been deprecated. Users going to the data management workspace were informed about the deprecation during this period. The enhanced view is now being set as the default view. The standard view is still available and can be brought back using the existing setting in framework parameters, although it is not recommended to use standard view as it will be deleted sometime in future. If users explicitly choose to use standard view by clicking the **Standard view** button on any of the data management forms, these users will continue to see standard view as their personalized settings will be honored. However, such users are also advised to switch to using enhanced view.

## Preview documents using embedded PDF viewer control
You can streamline the document viewing experience in Dynamics 365 for Finance and Operations by taking advantage of the new 'Preview' option for application reports. The embedded PDF document viewer gives you direct access to locally connected printers and offers fidelity between the screen presentation and the output printed on paper. The 'Preview' option is available on all supported devices and does not depend on any third-party software. The embedded PDF viewer includes a built-in toolbar with intuitive controls that make it easy to download and navigate documents.

## Create custom commands for embedded PowerBI.com reports
Turn insights into action using custom menu commands for chart visualizations displayed in PowerBI.com reports hosted in Application workspaces for Dynamics 365 Finance and Operations. Empower users with intuitive gestures to perform business operations on filtered views of their report data. With the latest Platform update, developers can add custom extensions that give users an actionable experience interacting with analytical solutions within Finance and Operations applications.

## Extended availability of the legacy navigation bar
In Platform update 24, a restyled navigation bar was introduced for Finance and Operations as part of an effort across the Dynamics 365 products to align to the Office header visuals, which notably did not include a breadcrumb. At that time, the legacy navigation bar was put on an expedited deprecation schedule (to not be available after Platform update 28) because of the branding impact. Due to customer concern around the missing breadcrumb in the new navigation bar, we have decided to extend access to the legacy navigation bar until April 2020. See [Updated navigation bar that aligns with the Office header](/business-applications-release-notes/April19/dynamics365-finance-operations/updatednavbar) for more detail on the navigation bar and for instructions on how to temporarily revert to the legacy navigation bar. 

## Alert users before sessions end due to inactivity
The default idle timeout for Finance and Operations is currently 60 minutes. After that inactivity limit has been surpassed by a user, the user is alerted that their session has ended. To provide users with additional awareness of an impending session suspension due to inactivity and to avoid losing any unsaved changes, users will now be notified 3 minutes before their sessions are set to end due to inactivity. Users are also provided an opportunity to reconnect before the session ends.  

## Export all BYOD job name changes
The syntax of the execution job name for the BYOD export all companies job will now have a GUID appended to the naming convention. This will ensure that the names are always unique.

## Extensibility enhancements
The following enhanced extensibility capabilities have been added in Platform update 28:

- Enable extension of WorkflowType so elements (Task, Approval, AutomatedTask) and event handlers can be added (Ref# 198838).
- Enable extension to change TableRelation.RelatedTableCardinality and TableRelation.Role (Ref# 280969).
- Enable extension of country region codes on data entities (Ref# 282123).
- Enable extension of the Label, Help Text, and Group Prompt properties of entity fields (Ref# 265666).

## Additional resources

### Platform update 28 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 28, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=328737&dbType=3&qc=c3c678b3cdf18a7df3f284866ca4c5705b9e1e8df684b6db0222788c15fe1d2b).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) topic 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically, these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]