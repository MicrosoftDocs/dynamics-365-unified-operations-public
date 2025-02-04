---
title: What's new or changed in Dynamics 365 for Finance and Operations platform update 26 (May 2019)
description: Learn about features that are in preview in Dynamics 365 for Finance and Operations platform update 26 (May 2019).
author: sericks007
ms.author: sericks
ms.topic: whats-new
ms.custom: 
  - bap-template
  - evergreen
ms.date: 04/12/2024
ms.reviewer: johnmichalak
ms.search.region: Global
ms.search.validFrom: 2019-XX-XX
ms.dyn365.ops.version: Platform 26
---

# What's new or changed in Dynamics 365 for Finance and Operations platform update 26 (May 2019)

[!include [banner](../includes/banner.md)]

This article describes features that are new or changed in Dynamics 365 for Finance and Operations platform update 26. This version has a build number of 7.0.5257. For more information about Platform update 26, see [Additional resources](whats-new-platform-update-26.md#additional-resources).

## Business events generally available
[Business events](../../dev-itpro/business-events/home-page.md) are now generally available. This means that business events are out of preview and are available by default, without having to enable the flight. 

## 1:N support for Microsoft Power Automate to subscribe to business events
Multiple Power Automate apps can subscribe to the same business event in the same legal entity. The [Business events in Microsoft Power Automate](../../dev-itpro/business-events/business-events-flow.md) can be leveraged for tasks such as sending notifications and triggering approval flows. 

## Workflow business events
The [Workflow business events](../../dev-itpro/business-events/business-events-workflow.md) are a particularly good target for triggering approval flows. The **Workflow workitem** event can be used in conjunction with the validate and complete OData actions to facilitate completion of a work item in Power Automate. Power Automate templates for facilitating completion of a work item are in progress and more information about them will be available on the [Workflow business events](../../dev-itpro/business-events/business-events-workflow.md) page in the near future.

## Business events are idempotent
Business events are idempotent. This means that the payload of a business event has a unique and ever increasing number called the ControlNumber. This control number can be used by consumers to apply duplicate detection logic and out of order delivery detection logic to ensure robust processing of events.

## Azure Data Lake integration - CDM folder and model improvements 
Entity store in Azure Data Lake is available as public preview with Platform update 25. In Platform update 26, we have made improvements to the folder structure to enable multiple environments to use the same storage account. We have also included additional properties in the model, including relationships between entities. This will enable relationships in the model to appear in the Power BI dataset with the features introduced by PowerBI.com.

## Feature callouts
New features are regularly being developed for Finance and Operations. While documentation is helpful for explaining new features, raising awareness of these new capabilities to users directly in the product when they are encountered is powerful. To this end, [Feature callouts](../../dev-itpro/user-interface/feature-callouts.md) are available in Platform update 26 to point out a new capability to a user and optionally provide a hyperlink for the user to learn more about the feature.  

## Extensibility enhancements
The [third wave of platform extensibility enhancements](/business-applications-release-notes/April19/dynamics365-finance-operations/platform-extensibility3) included in Platform update 26 is documented in the April 2019 Release notes. There are seven enhancements detailed, with one of the highlights being that Chain of Command can now target and extend other method extensions.

## Additional resources

### Platform update 26 bug fixes
For information about the bug fixes included in each of the updates that are part of Platform update 26, sign in to Lifecycle Services (LCS) and view this [KB article](https://fix.lcs.dynamics.com/Issue/Details?bugId=313846&dbType=3&qc=a4ba239cdec6f528657f529750b68845b75580e5fdb0ad6060c4bc33f8da67f8).

### Dynamics 365 April '19 release notes
Wondering about upcoming and recently released capabilities in any of our business apps or platform?

[Check out the April '19 release notes](/business-applications-release-notes/April19/index). We've captured all the details, end to end, top to bottom, in a single document that you can use for planning.

### Removed and deprecated features
The [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article describes features that have been removed or deprecated for Dynamics 365 for Finance and Operations.

- A *removed* feature is no longer available in the product.
- A *deprecated* feature is not in active development and may be removed in a future update.

Before any feature is removed from the product, the deprecation notice will be announced in the [Removed or deprecated features for Finance and Operations](../../dev-itpro/migration-upgrade/deprecated-features.md) article 12 months prior to the removal.

For breaking changes that only affect compilation time, but are binary compatible with sandbox and production environments, the deprecation time will be less than 12 months. Typically these are functional updates that need to be made to the compiler.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
