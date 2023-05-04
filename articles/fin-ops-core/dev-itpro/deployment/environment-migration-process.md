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

Microsoft continues to open data centers for business service in both existing regions and new regions. The Geo migration feature lets you move your finance and operations environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move.

If your tenant resides in a Microsoft 365 environment in a single tenant, when you move your environment, the Microsoft 365 environment isn't moved. Your environment and the Microsoft 365 environment are separate services. Your environment will still appear alongside the Microsoft 365 environment in your tenant.

When finance and operations apps environment is deployed in a geo, there are multiple Azure resources associated with it. As part of migration process these resources will also move from source geo to target geo.

## Considerations before starting the migration
Organizations looking to migrate environments and data from one geography to another need to consider various aspects mentioned below before actual migration.

**Supported environments**
- Only Sandbox and Production environments can be migrated from one geo to another. 
- Cloud Hosted Environment (CHE) migration is not supported.
- Migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud [GCC] and China) aren't supported.

**Feature parity**

Make sure you review the [availability of features in the selected target geography](deployment-options-geo.md#feature-availability-in-local-geographies) before deciding on which geography to deploy into. If certain features are not available in target geo, associated functionality will not work in target geo after migration so plan migration activity accordingly.

Commerce isn't available in all target geographies. If you have Commerce components enabled, your migration won't be scheduled if you're migrating to one of the target geographies where Commerce isn't available.

**Integration impact and updates with other services**
- 3rd party integrations - if the migration crosses data resident geo then finance and operations apps environment endpoint will change. Any 3rd party integrations that make use of the endpoint will require change.
- Finance and operations apps add-ins and micro-services: Add-ins configurations are not migrated as part of migration process. You will have to uninstall the add-ins before the migration and then reinstall them once migration completes. (e.g. dual-write needs to be reconfigured in target geo)

**Timeline of actions and downtime**

- We recommend that you migrate Sandbox environments first and validate them before you trigger a Production migration.
- Environment migrations are not self-serve and require customer initiated support ticket.
- Create your support request for migration at least 10 days before you want the environment to be migrated.
- Overall migration activity will require up to 48 hours of downtime. Overall time will vary depending on connectivity between two geos along with database and storage account size.
- If Dataverse environment is linked then it will need additional 24 hours of downtime.

**Geo to geo migration between various geographies**

When deploying environments from LCS the available regions listed will display if the target region is Data resident or not. 

**Data resident geographies** indicate both the LCS data and the environment data will be stored within the same discrete geography.
  - Migration between two data resident local geographies is supported (e.g. migration from US to UAE or from EU to Norway is supported)
  - Migrating from one data resident geo to another will change -environment URL/endpoint as mentioned here (e.g. migrating from US to UAE will change URL from <https://NAME.operations.dynamics.com/> to <https://NAME.operations.uae.dynamics.com/>) 

**Non-data resident geographies** indicate the LCS data and the environment data will be stored in different geographies.
  - Migration between two non-data resident geos is supported (e.g. migration from US to UK or US to Canada is supported)
  - Migrating between commercial non-data resident geos will not change environment URL (e.g. (e.g. Moving from US to UK will keep URL same as <https://NAME.operations.dynamics.com/>)

## Environment migration process

We recommend that you migrate Sandbox environments first and validate them before you trigger a Production migration.

After Sandbox migration validation is successfully complete project team can plan the time for Production environment migration and follow same steps described above starting with raising the Support ticket. 

| Step | Responsible party | Description | Additional comments |
|---|---|---|---|
|0|Customer/Partner|Refresh Sandbox with Production data|Optional step before Sandbox migration.|
|1|Customer/Partner|Submit support request to migrate a specific environment|Create your support request for migration at least 10 days before you want the environment to be migrated. Information required in ticket is: Customer name, Tenant ID, Environment ID, LCS Project ID (associated with environment), source geography, target geography, and preferred date and time.|
|2|Microsoft|Review the geo-to-geo migration request and approve it||
|3|Customer/Partner|Before the start of downtime uninstall any microservices or add-ins||
|4|Microsoft|Execute migration|Associated Dataverse environment (if any) will also be migrated in same time frame. **Premigration** work begins 12 hours before the scheduled downtime. During premigration the environment remains available for use but is put into an Infrastructure Maintenance state so that no lifecycle management operations can be performed. During the **migration** finance and operations apps and Dataverse environments ar unlinked, both environments are migrated and relinked after migration is complete.|
|5|Microsoft|Confirm completion of the migration to customer/partner||
|6|Customer/Partner|Validate environment functionality in target geo||
|7|Customer/Partner|Reconfigure any add-ins, Commerce/ POS, 3rd party integrations etc)||



______
**KEEPING BELOW ALL ORIGINAL TEXT FOR NOW IN CASE WE WANT TO COMPARE/BRING BACK SOMETHING**
- Suggested environment migration process steps are,
  1. Refresh Sandbox with Production data (if required)
  2. Submit support request to migrate only Sandbox environment from source to target geo
  3. Validate Sandbox functionality in target geo
  4. Ensure that all microservices add-ins and external 3rd party integrations with production environment are disconnected, as they will be impacted during production migration
  5. Submit support request to migrate Production environment from source to target geo. Associated Dataverse environment (if any) will also be migrated in same time frame.
  6. Validate Production functionality in target geo
  7. Reconfigure any integrations (Add-ins, Commerce/ POS, etc)
- Environment migrations are not self-serve and require customer initiated support ticket.
  1. To request a geo-to-geo migration, contact your account manager, and open a support ticket with the Microsoft Support team.  
  2. Create your support request for migration at least 10 days before you want the environment to be migrated.
  3. Information required in ticket is, Customer name, Tenant ID, Environment ID, LCS Project ID (associated with environment), source geography, target geography, and preferred date and time.


## Migration process

The geo-to-geo migration process consists of three phases:

1. **Premigration** – The environment remains available for use but is put into an Infrastructure Maintenance state so that no lifecycle management operations can be performed.
1. **Migration** – The resources are moved to the new geography. The environment requires downtime of up to 48 hours and isn't available for use during this time.

## How the move works

The following table describes customer and Microsoft responsibilities before, during, and after the migration.

| Responsible party | Before the migration | During the migration | After the migration |
|---|---|---|---|
| **Customer** | Submit a support request for geo-to-geo migration. After the request is approved, uninstall any microservices or add-ins. | | Reinstall any microservices or add-ins. Optionally migrate Dynamics 365 Commerce components. |
| **Microsoft** | Review the geo-to-geo migration request and approve it. Premigration work begins 12 hours before the scheduled downtime. | Unlink Dynamics 365 Finance and Dataverse environments and perform the migration of both environments. Relink the Finance and Dataverse environments after migration is completed. | Microsoft Technical Support will notify customers about migration updates. |
