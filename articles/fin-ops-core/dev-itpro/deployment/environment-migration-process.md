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

Microsoft continues to open datacenters for business service in both existing regions and new regions. The Geo migration feature lets you move your finance and operations environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move. 

If your tenant resides in a Microsoft 365 environment in a single tenant, when you move your environment, the Microsoft 365 environment isn't moved. Your environment and the Microsoft 365 environment are separate services. Your environment will still appear alongside the Microsoft 365 environment in your tenant.

- The Geo migration capability lets you move your environments in a single tenant from source geography to another geography. When F&O environment (Sandbox or Production) is deployed in a geo, there are multiple Azure resources associated with it. As part of migration process these resources will also move from source geo to target geo.
- Only Sandbox and Production environments can be migrated from one geo to another. Cloud Hosted Environment (CHE) migration is not supported.
- Suggested environment migration process steps are,
  1. Refresh Sandbox with Production data (if required)
  2. Submit support request to migrate only Sandbox environment from source to target geo
  3. Validate Sandbox functionality in target geo
  4. Ensure that all microservices add-ins and external 3rd party integrations with production environment are disconnected, as they will be impacted during production migration
  5. Submit support request to migrate Production environment from source to target geo. Associated Dataverse environment (if any) will also be migrated in same timeframe
  6. Validate Production functionality in target geo
  7. Reconfigure any integrations (Add-ins, Commerce/ POS, etc)
- Environment migrations are not self-serve and require customer initiated support ticket . 
  1. To request a geo-to-geo migration, contact your account manager, and open a support ticket with the Microsoft Support team.  
  2. Create your support request for migration at least 10 days before you want the environment to be migrated. 
  3. Information required in ticket is, Customer name, Tenant ID, Environment ID, LCS Project ID (associated with environment), source geography, target geography, and preferred date and time.

## Supported environments

- Sandbox environments
- Production environments

We recommend that you migrate sandbox environments first and validate them before you trigger a production migration.

CHE environments are not supported.

## Migration process

The geo-to-geo migration process consists of three phases:

1. **Premigration** – The environment remains available for use but is put into an Infrastructure Maintenance state so that no lifecycle management operations can be performed.
1. **Migration** – The resources are moved to the new geography. The environment requires downtime of up to 48 hours and isn't available for use during this time.

## How the move works

The following table describes customer and Microsoft responsibilities before, during, and after the migration.

| Responsible party | Before the migration | During the migration | After the migration |
|---|---|---|---|
| Customer | <ul><li>Submit a support request for geo-to-geo migration.</li><li>After the request is approved, uninstall any microservices or add-ins.</li></ul> | | <ul><li>Reinstall any microservices or add-ins.</li><li>Optionally migrate retail components.</li></ul> |
| Microsoft | <ul><li>Review the geo-to-geo migration request.</li><li>Approve the geo-to-geo migration request.</li><li>Premigration work begins 12 hours before the scheduled downtime.</li></ul> | <ul><li>Unlink Dynamics 365 Finance and Dataverse environments.</li><li>Perform the migration of the Finance environment.</li><li>Perform the migration of the Dataverse environment.</li><li>Relink the Finance and Dataverse environments.</li></ul> | <ul><li>Microsoft Technical Support will notify customers about migration updates.</li></ul> |
