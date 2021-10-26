---
# required metadata

title: Regulatory Configuration Service (RCS) - Lifecycle Services (LCS) storage deprecation
description: This topic provides information about the deprecation of Microsoft Dynamics Lifecycle Services (LCS) storage that is planned as part of the rollout of the Regulatory Configuration Service (RCS) Global repository.
author: JaneA07
ms.date: 05/25/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: RCS, Regulatory Configuration Services, Localization, LCS storage, LCS storage deprecation
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
ms.custom: 97423
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: janeaug
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: AX 10.0.19

---
# Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation

[!include [banner](../includes/banner.md)]

The use of Microsoft Dynamics Lifecycle Services (LCS) as a storage repository for Electronic reporting (ER) configurations is being deprecated. This deprecation will involve the following changes:

- Microsoft-produced configurations that are used in Microsoft Dynamics 365 applications will no longer be published to the Shared asset library in LCS. Instead, they will be published only through the RCS Global repository. However, configurations for Dynamics AX 2012 will continue to be published to the Shared asset library in LCS until the support lifecycle for AX 2012 ends.
- The functionality that lets you upload configurations to the Project asset library in LCS from Finance and Operations apps, and from RCS, will be inactivated. However, you will still be able to use the browser in LCS to upload configurations to the Project asset library. Therefore, you will still be able to add configurations to LCS so that they can be included in solution packages.
- Import of configurations from LCS will continue to be available and supported in Finance and Operations apps, and in RCS, for some time. However, the functionality will eventually be deprecated. (The exact deprecation date will be announced later.)

## Deprecation notice

Deprecation of the use of LCS as storage was communicated in [Removed or deprecated features in Dynamics 365 Finance - LCS Deprecation notice](../get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). The planned deprecation date is April 1, 2022.

## Key features

- You can use RCS to create and edit Electronic Reporting (ER) configurations and Globalization features. 
- You can push configurations directly from RCS's designer to a connected application (for e.g. Dynamics 365 Finance environment) to allow you to quickly make and test changes in your configurations.
- Through the Global repository's centralized storage you can centrally store, share and manage the lifecycle for both ER configuration and globalization features.

## Guidance for one-time and ongoing actions

This section describes a set of steps that must be completed one time. It also describes steps that must be completed on an ongoing basis afterward.

### One-time action

Import all required configurations from LCS to RCS, and then publish them from RCS to the Global repository. If you're using project-specific asset libraries to store derived configurations in LCS, the following steps must be completed while LCS is still accessible.

1. If an RCS instance isn't already available, provision one. For more information, see [RCS overview](rcs-overview.md).
2. In the provisioned RCS instance, for every LCS project in the Asset library that includes derived ER configurations, register the appropriate LCS repository.
3. Import the ER configurations from the LCS repositories to RCS. For more information, see [Import configurations from LCS](../../dev-itpro/analytics/tasks/er-import-configuration-lifecycle-services.md).
4. If the Global repository isn't automatically provided, register it in RCS.
5. Upload all derived configurations from the current RCS instance to the Global repository. Use the **Configuration packages** to upload all configurations to GR in one operation** feature to help with the upload. For more information, see [RCS global repo upload](rcs-global-repo-upload.md).

### Going forward

Use the visual designers in RCS to:
- Extend the Microsoft provided templates
- Create brand new configurations that your organization requires
- Customise Globalization features for Electronic invoising and Tax Calculation services. 

Use Globalization repository (GR) to:
- Access Microsoft produced configurations and globalization features.
- Upload configurations to that you have created/extended to the Global repository for storage, sharing across your organization Dynamics applications environments or external organization. For more information, see [Create ER configuration in RCS and upload to Global repo](rcs-global-repo-upload.md).

## Frequently asked questions:

### Does this change mean that LCS can't be used as central storage for configurations?

Yes. The functionality that lets you upload configurations to the Project asset library in LCS from Finance and Operations apps will be deprecated. However, you can still use the browser in LCS to upload configurations to the Project asset library as you require.

### I thought that RCS was a replacement repository for importing global template files. I didn't think that it's used to store configurations. Which is correct?

RCS is a design service for creating and editing ER configurations. RCS has its own repository that is known as the Global repository. This repository is used to store configurations that are created in RCS. After the use of LCS as storage is deprecated, the Global repository will be the single source for Microsoft configurations. You must complete a one-time action to import all the configurations that you require from LCS to RCS and then publish them from RCS to the Global repository.

### Without LCS, what is the suggested way to store configurations so that "test" and "production" configurations can easily be managed and transferred?

RCS uses the concept of a *connected application*. A connected application forms a connection between RCS and any instance of Finance and Operations apps. Because RCS can be used to edit configurations, the connected application can be used to push the configurations directly from the designer to Finance and Operations apps environments. Therefore, you can quickly change and test your configurations instead of having to go through LCS project-level storage.

### Are there any examples that show the setup and management?

There are no examples, but you can complete the steps earlier in this topic to migrate your configurations to the RCS Global repository.

### It is mentioned that RCS is prerequisite to configure new globalization microservices like Electronic Invoicing and Tax Service, but is it for Electronic Reporting too?

Yes. RCS includes capabilities that support the set-up of Globalization features which are used by globalization services, like Electronic Invoicing and Tax Calculation Service, but the service has the same visual designer functionality that allows a user to extend or create new Electronic Reporting configuration. RCS also provides lifecycle management for both ER configurations and Globalization features.  

### What regions is RCS avaliable to be deployed in?

RCS is avaliable in the following Azure geo's: United States, India, France and Europe. To find out more information about product support, see [Dynamics Globalization services overview](/finance/localizations/globalization-services-overview.md). For information on geo support, see [Dynamics 365 and Power Platform: Availability, data location, language, and localization](https://aka.ms/rcs/D365Productavailabilityguide).  

### What's the cost of using RCS?

RCS and Globalization repository are provided free of charge as part of existing Dynamics 365 Finance and Operations licenses. There are no separate costs associated with using RCS design service or storing configurations in Global repository and there is no limit to the number of configurations or connected applications at this time.


