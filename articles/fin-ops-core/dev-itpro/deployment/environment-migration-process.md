---
title: Environment migration process
description: This article describes hot to move your environment from one geography to another.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 10/19/2022
ms.custom:
---

# Finance and operations apps environment migration

## Introduction

Microsoft continues to open data centers for business service in both existing regions and new regions. The Geo migration feature lets you move your finance and operations apps environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move.

Microsoft 365 and Dynamics 365 are separate services. Moving your finance and operations apps environments will not move the Microsoft 365. Your finance and operations apps environment will still appear alongside the Microsoft 365 environment in your tenant.

When finance and operations apps environment is deployed in a geo, there are multiple Azure resources associated with it. As part of migration process these resources will also move from source geo to target geo.

## Considerations
Organizations looking to migrate environments from one geography to another need to consider various aspects mentioned below before actual migration.

**Supported scenarios**

- Sandbox and Production environments can be migrated between geographies. 
- Cloud Hosted Environment (CHE) migration is not supported.
- Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.

**Feature parity**

Make sure you review the [availability of features in the selected target geography](deployment-options-geo.md#feature-availability-across-geographies) before deciding on which geography to deploy into. If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly.

**Integration impact and updates with other services**

- Third party integrations: If the migration crosses data resident geographies, then finance and operations apps environment endpoint will change. Any 3rd party integrations that make use of the endpoint will require change. Learn more at [Supported geographies and endpoints](deployment-options-geo.md#supported-geographies-and-endpoints).
- Finance and operations apps add-ins and micro-services: add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes (e.g. dual-write needs to be reconfigured in target geo).

**Timeline of actions and downtime**

- We recommend that you migrate Sandbox environments first and validate them before you trigger a Production migration.
- Environment migrations are not self-serve and require customer initiated support ticket.
- Create your support request for migration at least 10 days before you want the environment to be migrated.
- Overall migration activity will require up to 48 hours of downtime. Overall time will vary depending on connectivity between two geos along with database and storage account size.
- If there is a linked Dataverse environment, it will need additional 24 hours of downtime.

**Geo migration between Lifecycle Services endpoints**

When deploying environments from LCS the available regions listed will display if the target region is "Data resident" or not. See finance and operations apps [data residency](deployment-options-geo.md#data-residency) for more information about how you can make finance and operations apps environments stay data resident with LCS. 

Some supported geographies will have different endpoint URLs. When moving between geographies, this can change the environment endpoint. Example, moving from United States to Europe will change the environment endpoint (from NAME.operations.dynamics.com to NAME.operations._eu_.dynamics.com). The change of the environment endpoint will impact any integrated service that takes a dependency on the correct endpoint URL. Consider the [list of avaialble geographies and endpoints](deployment-options-geo.md#supported-geographies-and-endpoints) to see what geograhpies change the URL. 

## Environment migration process

We recommend that you migrate Sandbox environments first and validate them before you trigger a Production migration.

After Sandbox migration validation is successfully completed, project team can plan the time for Production environment migration and follow same steps described above starting with raising the Support ticket. 

| **Step** | **Responsible** | **Description** | **Additional comments** |
|------|-------------|-------------|---------------------|
|1|Customer/Partner|Refresh Sandbox with Production data|Optional step if migrating Sandbox|
|2|Customer/Partner|Submit support request to migrate a specific environment|Create your support request for migration at least 10 days before you want the environment to be migrated. Information required in ticket is: Customer name, Azure Active Directory Tenant ID, Environment ID, LCS Project ID (associated with environment), source geography, target geography, and preferred date and time.|
|3|Microsoft|Review the geo-to-geo migration request and approve it||
|4|Customer/Partner|Before the start of downtime uninstall any microservices or add-ins||
|5|Microsoft|Execute migration|Associated Dataverse environment (if any) will also be migrated in same time frame. **Premigration** work begins 12 hours before the scheduled downtime. During premigration the environment remains available for use. The environment is put into an Infrastructure Maintenance state so that no lifecycle management operations can be performed. During the **migration** finance and operations apps and Dataverse environments are unlinked. Both environments are migrated and relinked after migration is complete.|
|6|Microsoft|Confirm completion of the migration to customer/partner||
|7|Customer/Partner|Validate functionality in the migrated environment in the target geo|Consider potential feature parity differences.|
|8|Customer/Partner|Reconfigure any add-ins, Commerce/POS, third-party integrations, etc|Consider change of endpoint URLs.|
