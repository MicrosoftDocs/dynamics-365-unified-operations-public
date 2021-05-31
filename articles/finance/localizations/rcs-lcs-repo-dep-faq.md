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

- You can use RCS to create and edit configurations. You can then push those configurations directly from the designer to a connected application. Therefore, you can quickly change and test your configurations.
- The Global repository is the centralized storage for all ER configurations.

## Guidance for one-time and ongoing actions

This section describes a set of steps that must be completed one time. It also describes steps that must be completed on an ongoing basis afterward.

### One-time action

Import all required configurations from LCS to RCS, and then publish them from RCS to the Global repository. If you're using project-specific asset libraries to store derived configurations in LCS, the following steps must be completed while LCS is still accessible.

1. If an RCS instance isn't already available, provision one. For more information, see [RCS overview](rcs-overview.md).
2. In the provisioned RCS instance, for every LCS project in the Asset library that includes derived ER configurations, register the appropriate LCS repository.
3. Import the ER configurations from the LCS repositories to RCS. For more information, see [Import configurations from LCS](../../dev-itpro/analytics/tasks/er-import-configuration-lifecycle-services.md).
4. If the Global repository isn't automatically provided, register it in RCS.
5. Upload all derived configurations from the current RCS instance to the Global repository. Use the **Configuration packages that allows the user to upload all configurations to GR in one operation** feature to help with the upload. For more information, see [RCS global repo upload](rcs-global-repo-upload.md).

### Going forward

Use the visual designers in RCS to create all new configurations. Then upload the configurations to the Global repository for storage. For more information, see [Create ER configuration in RCS and upload to Global repo](rcs-global-repo-upload.md).

## Frequently asked questions

### Does this change mean that LCS can't be used as central storage for configurations?

Yes. The functionality that lets you upload configurations to the Project asset library in LCS from Finance and Operations apps will be deprecated. However, you can still use the browser in LCS to upload configurations to the Project asset library as you require.

### I thought that RCS was a replacement repository for importing global template files. I didn't think that it's used to store configurations. Which is correct?

RCS is a design service for creating and editing ER configurations. RCS has its own repository that is known as the Global repository. This repository is used to store configurations that are created in RCS. After the use of LCS as storage is deprecated, the Global repository will be the single source for Microsoft configurations. You must complete a one-time action to import all the configurations that you require from LCS to RCS and then publish them from RCS to the Global repository.

### Without LCS, what is the suggested way to store configurations so that "test" and "production" configurations can easily be managed and transferred?

RCS uses the concept of a *connected application*. A connected application forms a connection between RCS and any instance of Finance and Operations apps. Because RCS can be used to edit configurations, the connected application can be used to push the configurations directly from the designer to Finance and Operations apps environments. Therefore, you can quickly change and test your configurations instead of having to go through LCS project-level storage.

### Are there any examples that show the setup and management?

There are no examples, but you can complete the steps earlier in this topic to migrate your configurations to the RCS Global repository.
