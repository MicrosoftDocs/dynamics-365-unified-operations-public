---
# required metadata

title: Regulatory Configuration Service (RCS) - Lifecycle services (LCS) storage deprecation
description: This topic provides an overview and guidance related to the LCS storage deprecation plan as part of RCS GLobal repository rollout.
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
# Regulatory Configuration Service (RCS) - Lifecycle services (LCS) storage deprecation

[!include [banner](../includes/banner.md)]

LCS as a storage repository for Electronic reporting configurations is being deprecated. This deprecation includes: 

- No longer publishing Microsoft-produced configurations to use in Dynamics 365 applications to the Lifecycle services (LCS) Shared Asset library. Instead, the configurations will be published only through the RCS Global repository. Configurations for Dynamics AX2012 still will be published to LCS Shared Asset library until that product support lifecycle ends.
- Deactivate the functionality that allows you to upload configurations to the LCS Project Asset library from Finance and Operations apps and from RCS. You can still upload configurations to the LCS Project Asset library by using the browser which will support adding configurations to LCS for inclusion in solution packages.
- Importing configurations from LCS will still be available and supported in Finance and Operations apps and in RCS for some time. However, the functionality will be deprecated at a future date (to be announced later).

## Deprecation notice
Depreciation of LCS as storage was communicated in the topic, [Removed or deprecated features in Dynamics 365 Finance - LCS Deprecation notice](../get-started/removed-deprecated-features-finance.md#features-removed-or-deprecated-in-the-finance-10017-release) with a planned deprecation date of April 01, 2022.
 
## Key features

- RCS can be used to create and edit configurations which can be pushed to a connected application directly from designer. This allows you to can quickly change and test your configurations. 
- The global repository is the centralized storage for all ER configurations.

## Guidance for moving forward
The following sections include a set of steps that must be completed one time, and a set that must be completed going forard. 

### One time action

Import all necessary configurations from LCS to RCS and publish them from RCS to the Global repository. If you are storing derived configurations in LCS by using project specific asset libraries, the following steps must be completed while LCS is still accessible.

1. Provision an RCS instance if you don't already have one available. For more information, see [RCS overview](rcs-overview.md).
2. In the provisioned RCS instance, register the appropriate LCS repository for every LCS project in the asset library that includes derived ER configurations.
3. Import the ER configurations from the LCS repositories to RCS. For more information, see [Import configurations from LCS](../../dev-itpro/analytics/tasks/er-import-configuration-lifecycle-services.md) 
4. Register the Global repository in RCS if it's not automatically provided.
5. Upload all derived configurations from the current RCS instance to the Global repository. To help with upload, use the feature, **Configuration packages that allows the user to upload all configurations to GR in one operation**. For more information, see [RCS global repo upload](rcs-global-repo-upload.md). 

### Going forward
For new configurations, use the visual designers in RCS to create your configuration, and then upload it to the Global repository for storage. For more information, see [Create ER configuration in RCS and upload to Global repo](rcs-global-repo-upload.md)

## Frequently asked questions

### Does this mean LCS can’t be used as central storage for configurations?
Yes. The functionality that allows you to upload configurations to the LCS Project Asset library from Finance and Operations apps will be deprecated. However, you can still upload configurations to the Project Asset library using browser in LCS if needed.

### I thought that RCS was a replacement repository for importing global template files, not for storing configurations. Which is it?
RCS is a design service for creating and editing ER configurations. RCS has its own repository called the Global repository. This repository is used to store configurations that are created in RCS and is the single source for Microsoft configuration after the LCS deprecation. There is a one-time action required to move your configurations to RCS by importing all configurations you need from LCS to RCS and publishing them from RCS to the Global repository.

### Without LCS, what is the suggested way to store configurations that enables easy management and transfer of “test” and “production” configurations?
RCS uses the concept of *Connected application* which forms a connection between RCS and any instance of Finance and Operations apps. Because RCS can be used to edit configurations, the configurations can be pushed using the connected app directly from designer to the Finance and Operations apps environments, so that you can quickly "change and test" rather then having to go through LCS project-level storage.

### Do you have any examples of how this is setup and managed?
No examples, but you can complete the steps earlier in the topic to migrate your configurations to the RCS Global repository.

