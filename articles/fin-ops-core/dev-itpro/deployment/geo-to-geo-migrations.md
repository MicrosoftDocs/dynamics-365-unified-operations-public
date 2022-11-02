---
title: Geo-to-geo migrations
description: This article describes hot to move your environment from one geography to another.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 10/19/2022
ms.custom:
---

# Geo-to-geo migrations

Microsoft continues to open datacenters for business service in both existing regions and new regions. The Geo migration feature lets you move your finance and operations environments that are in a single tenant from one geography (or geo) to another. No changes to the user interface or version occur as part of the move. 

If your tenant resides in a Microsoft 365 environment in a single tenant, when you move your environment, the Microsoft 365 environment isn't moved. Your environment and the Microsoft 365 environment are separate services. Your environment will still appear alongside the Microsoft 365 environment in your tenant.

## Important information

- Support for geo-to-geo migration is limited and isn't generally available everywhere.
- Create your support request for migration at least 10 days before you want the environment to be migrated.
- Geo-to-geo migrations into or out of a sovereign cloud environment (for example, US Government Community Cloud \[GCC\] and China) aren't supported.
- Decide on the source and target geographies, based on the availability of products in [local geographies](deployment-options-geo.md).
- Review the availability of features in the target geography.

    Microsoft strives to maintain functional parity between our commercially available services across geographies. We continue to evaluate these services and capabilities for inclusion and updates in future releases. Use the following documents to get an overview of services and their availability in the geographies that you're planning to use:

    - [Microsoft Business Application Feature Availability - Americas](https://aka.ms/bapfunctionalparityamericas)
    - [Microsoft Business Application Feature Availability - EMEA](https://aka.ms/bapfunctionalparityemea)
    - [Microsoft Business Application Feature Availability - APAC](https://aka.ms/bapfunctionalparityapac)

- During this preview, migration is supported only within the United States and the European Union (EU). Other local geographies will be made available in other areas after the Geo migration feature becomes publicly available.
- Microservices (add-ins) aren't covered by the migration process. You will have to uninstall the add-ins before the migration and then reinstall them afterward.
- Retail environments may require special handling. Retail integrations will not be migrated, but will remain functional. The customer may choose to have these migrated at a later date. Many of the retail integrations can be migrated in a self-service manner by the customer
- If Microsoft Power Platform integration is enabled for the environment that is being migrated, the corresponding Dataverse organization will be migrated at the same time. If you don't want to migrate the Dataverse organization, explicitly mention this fact in your support request.
- To request a geo-to-geo migration, contact your account manager, and open a support ticket with the Microsoft [Technical Support](../lifecycle-services/lcs-support.md) team.

    - In the support ticket, provide the following details: tenant ID, environment ID, project ID, source geography, target geography, and preferred date and time.
    - Technical Support will notify you about migration updates.

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
