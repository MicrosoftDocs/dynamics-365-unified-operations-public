---
title: Regulatory Configuration Service (RCS) - Lifecycle Services (LCS) storage deprecation
description: This article provides information about the deprecation of Microsoft Dynamics Lifecycle Services (LCS) storage that is planned as part of the rollout of the Regulatory Configuration Service (RCS) Global repository.
author: kfend
ms.date: 10/27/2021
ms.topic: article
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2020-05-01
ms.dyn365.ops.version: AX 10.0.19
ms.assetid: 
ms.search.form: RCS, Regulatory Configuration Services, Localization, LCS storage, LCS storage deprecation
---
# Regulatory Configuration Service (RCS) – Lifecycle Services (LCS) storage deprecation

[!include [banner](../includes/banner.md)]

The use of Microsoft Dynamics Lifecycle Services (LCS) as a storage repository for Electronic reporting (ER) configurations is being deprecated. This deprecation will involve the following changes:

- Microsoft-produced configurations that are used in Microsoft Dynamics 365 applications will no longer be published to the Shared asset library in LCS. Instead, they will be published only through the RCS Global repository. However, configurations for Dynamics AX 2012 will continue to be published to the Shared asset library in LCS until the support lifecycle for AX 2012 ends.
- The functionality that lets you upload configurations to the Project asset library in LCS from finance and operations apps, and from RCS, will be inactivated. However, you will still be able to use the browser in LCS to upload configurations to the Project asset library. Therefore, you will still be able to add configurations to LCS so that they can be included in solution packages.
- Import of configurations from LCS will continue to be available and supported in finance and operations apps, and in RCS, for some time. However, the functionality will eventually be deprecated. (The exact deprecation date will be announced later.)

## Deprecation notice

Deprecation of the use of LCS as storage was communicated in [Removed or deprecated features in Dynamics 365 Finance - LCS Deprecation notice](../get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release). The planned deprecation date is April 1, 2022.

## Key features

- Use RCS to create and edit ER configurations and Globalization features.
- Push configurations directly from the RCS designer to a connected application, such as a Dynamics 365 Finance environment, so that you can quickly make and test changes in your configurations.
- Centrally store, share, and manage the lifecycle for both ER configurations and Globalization features through the Global repository's centralized storage.

## Guidance for one-time and ongoing actions

This section describes a set of steps that must be completed one time. It also describes steps that must be completed on an ongoing basis afterward.

### One-time action

Import all required configurations from LCS to RCS, and then publish them from RCS to the Global repository. If you're using project-specific asset libraries to store derived configurations in LCS, the following steps must be completed while LCS is still accessible.

1. If an RCS instance isn't already available, provision one. For more information, see [RCS overview](rcs-overview.md).
2. In the provisioned RCS instance, for every LCS project in the Asset library that includes derived ER configurations, register the appropriate LCS repository.
3. Import the ER configurations from the LCS repositories to RCS. For more information, see [Import configurations from LCS](/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-import-configuration-lifecycle-services).
4. If the Global repository isn't automatically provided, register it in RCS.
5. Upload all derived configurations from the current RCS instance to the Global repository. Use the **Configuration packages** feature to help with the upload. For more information, see [RCS global repo upload](rcs-global-repo-upload.md).

### Going forward

Use the visual designers in RCS for the following purposes:

- Extend the Microsoft-provided templates.
- Create new configurations that your organization requires.
- Customize Globalization features for Electronic invoicing and the Tax Calculation service.

Use the Globalization repository for the following purposes:

- Access Microsoft-produced configurations and Globalization features.
- Upload configurations that you created or extended to the Global repository for storage, and share them across your organization's Dynamics 365 application environments or with external organizations. For more information, see [Create ER configuration in RCS and upload to Global repo](rcs-global-repo-upload.md).

## Frequently asked questions

### Does this change mean that LCS can't be used as central storage for configurations?

Yes. The functionality that lets you upload configurations to the Project asset library in LCS from finance and operations apps will be deprecated. However, you can still use the browser in LCS to upload configurations to the Project asset library as you require.

### I thought that RCS was a replacement repository for importing global template files. I didn't think that it's used to store configurations. Which is correct?

RCS is a design service for creating and editing ER configurations. RCS has its own repository that is known as the Global repository. This repository is used to store configurations that are created in RCS. After the use of LCS as storage is deprecated, the Global repository will be the single source for Microsoft configurations. You must complete a one-time action to import all the configurations that you require from LCS to RCS and then publish them from RCS to the Global repository.

### Without LCS, what is the suggested way to store configurations so that "test" and "production" configurations can easily be managed and transferred?

RCS uses the concept of a *connected application*. A connected application forms a connection between RCS and any instance of finance and operations apps. Because RCS can be used to edit configurations, the connected application can be used to push the configurations directly from the designer to finance and operations apps environments. Therefore, you can quickly change and test your configurations instead of having to go through LCS project-level storage.

### Are there any examples that show the setup and management?

There are no examples, but you can complete the steps earlier in this article to migrate your configurations to the RCS Global repository.

### Is RCS a prerequisite to configure Electronic reporting?

Yes. RCS includes capabilities that support the setup of Globalization features that are used by Globalization services such as Electronic invoicing and the Tax Calculation service. However, the service has the same visual designer functionality that lets you extend or create new ER configurations. RCS also provides lifecycle management for both ER configurations and Globalization features.

### Which regions can RCS be deployed in?

RCS is available in the following Azure regions:

- United States
- India
- France
- Europe

For more information about product support, see [Dynamics Globalization services overview](globalization-services-overview.md). For information about geographic support, see [Dynamics 365 and Power Platform: Availability, data location, language, and localization](https://aka.ms/rcs/D365Productavailabilityguide).

### What's the cost of using RCS?

RCS and the Globalization repository are provided free of charge as part of existing finance and operations app licenses. No separate costs are associated with using the RCS design service or storing configurations in the Global repository. There is currently no limit on the number of configurations or connected applications.
