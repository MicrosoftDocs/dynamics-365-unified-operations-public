---
# required metadata

title: RCS - LCS storage deprecation
description: This topic provides an overview of the LCS storage deprecation plan as part of RCS GLobal repository rollout and provide customer guidenace & FAQ.
author: JaneA07
ms.date: 05/24/2021
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

 ## Our plans / Scope
We are deprecating LCS as a storage repository for Electronic reporting configurations. The scenarios impacted are as follows: 
- We will stop publishing Microsoft produced configurations for use in Dynamics 365 applications to Lifecycle services (LCS) Shared Asset library. They will be published through RCS Global repository only. Configurations for Dynamics AX2012 still will be published to LCS Shared Asset library until that product support lifecycle ends.
- We will disable the feature that allows users to upload configurations to LCS Project Asset library both from F&O and from RCS. Customers will still be able to upload configurations to LCS Project Asset library via the browser. This will support users that need to add configurations to LCS in order to include them in solution packages.
- Importing configurations from LCS will still be available/supported in both F&O and in RCS for some additional period of time, but is planned to be deprecated at a future date (To be announced later).

 ## Deprecation notice:
Depreciation of LCS as storage was notified through the docs.microsoft documentation "Removed or deprecated features in Dynamics 365 Finance" - [LCS Deprecation notice](https://docs.microsoft.com/en-us/dynamics365/finance/get-started/removed-deprecated-features-finance#features-removed-or-deprecated-in-the-finance-10017-release) 
Planned deprecation: By April 01, 2022
 
## Key features:
- RCS can be used to create and edit configurations which can be pushed to connected application directly from designer, so users can quickly "change and test" their configurations.
- Global repository centralise storage for all ER configurations.

## Customer guidance:
Customers should undertake the following steps:

- **As one time action** 
  - Import all configurations they need from LCS to RCS and publish them from RCS to Global repository as described in the steps below:

  - For users storing derived configurations in LCS by using project specific asset libraries, the following must be done while LCS is still accessible:
    - Provision an RCS instance (if it is not available yet). See [RCS overview](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-overview?toc=/dynamics365/finance/toc.json) 
    - Register in the provisioned RCS instance the appropriate LCS repository for every LCS project containing in the asset library derived ER configurations.
    - Import those ER configurations from such LCS repositories to RCS. See [Import configurations from LCS](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/dev-itpro/analytics/tasks/er-import-configuration-lifecycle-services) 
    - Register in RCS the Global repository (if it is not provided automatically);
    - Upload all derived configurations from the current RCS instance to the Global repo. To help with upload we have a preview feature called Configuration packages that allows the user to upload all configurations to GR in one operation. See [RCS global repo upload](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-global-repo-upload?toc=%2Fdynamics365%2Ffinance%2Ftoc.json) 

- **Going forward**
  - For new configurations user will create their configuration in RCS through the visual designers and will store them (via direct upload) to Global repository, instead of putting them into LCS. See [Create ER configuration in RCS and upload to Global repo](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/rcs-global-repo-upload?toc=%2Fdynamics365%2Ffinance%2Ftoc.json)

## FAQ (based on questions asked so far):
**Q. Does this mean LCS can’t be used as central storage for configurations?**
- A. Yes, we are going to disable feature that allows upload of configurations to LCS Project Asset library from F&O, but customers still can upload configurations to Project Asset library via browser in LCS if they need to.

**Q. I thought that the Regulatory Configuration Service (RCS) was used as a replacement repository used for importing global template files, not for storing configurations. Please correct me if I’m wrong?**
- A. RCS is a design service (creating/editing) for ER configuration and has its own repository (called ‘Global repository’) that is used to store RCS created configuration and will be the single source for Microsoft configuration post LCS deprecation. There is a one-time action required by the customer to move their configuration to RCS by importing all configurations they need from LCS to RCS and publish them from RCS to Global repository.

**Q. What is the suggested way of storing configurations if LCS can’t be used, that enables easy management and transfer of “test” and “production” configurations?**
- A. RCS uses concept of Connected application that forms a connection between RCS and any F&O instance. As RCS can be used to edit configuration these can then be pushed via connected app directly from designer to the F&O environment, so customer still can quickly "change and test" rather then having to go through LCS project level storage.

**Q. Do you have any examples of how this would be managed/set up?**
- A. The customer/user can take the steps outlined above in customer guidence to migrate their LCS configs to RCS Global repository.

