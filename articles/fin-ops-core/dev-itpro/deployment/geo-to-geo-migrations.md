---
title: Geo to geo migrations
description: This article describes hot to move your environment from one geography to another.
author: matapg007
ms.author: matgupta
ms.reviewer: johnmichalak
ms.service: dynamics-365-finance
ms.topic: how-to
ms.date: 10/19/2022
ms.custom:
---

# Geo to geo migrations

Microsoft continues to open datacenters for business service in both existing and new regions. The Geo migration feature lets you move your environments in a single tenant from geography (or geo) to another geography. No user-interface or version changes occur part of this move.

When your tenant resides in a Microsoft 365 environment in a single tenant, moving the environment doesn't move the Microsoft 365 environment; they're separate services. Your environment will still appear in your tenant alongside the Microsoft 365 environment.

## Important information

- Support for geo migration is limited, and generally isn't available everywhere.
- Create your support request for migration at least 10 days in advance of when you would like the environment to migrate.
- Geo migrations aren't supported into or out of a sovereign cloud environment. For example, US GCC and China.
- Decide the source and target geographies based on availability of products in [local geographies](../dev-itpro/deployment/deployment-options-geo.md).
- Review the availability of features in the target geography.
  - Microsoft strives to maintain functional parity between our commercially available services across geographies. We continue to evaluate these services and capabilities for inclusion and updates in future releases. Use the documents below to get an overview of services and their availability in the geographies you're planning to use.
    - [Microsoft Business Application Feature Availability - Americas](https://aka.ms/bapfunctionalparityamericas)
    - [Microsoft Business Application Feature Availability - EMEA](https://aka.ms/bapfunctionalparityemea)
    - [Microsoft Business Application Feature Availability - APAC](https://aka.ms/bapfunctionalparityapac)
- During this preview, migration is supported only within US, EU, Norway, and UAE. Other local geographies will be made available in other areas after the geo migration feature is made publicly available.
- Microservices (add-ins) aren't covered by the migration process. You'll need to uninstall the add-ins prior to migration, and then reinstall them post migration.
- If your environment that is being migrated has power platform integration enabled, then corresponding Dataverse organization will be migrated at the same time. If you don't want to migrate the Dataverse Organization, then explicitly mention that in the support request.
- To request a geo migration, contact your account manager and open a support ticket with the Microsoft team [Technical Support](../dev-itpro/lifecycle-services/lcs-support.md).
  - Provide the following details: Tenant ID, Environment ID, Source Geo, Target Geo, Preferred Date and time in support ticket
  - Technical support will notify you about migration updates

## Supported environments

- Sandbox environments
- Production environments – It's suggested to migrate Sandbox first and validate before triggering Production migration.

## Migration process

The geo migration process consists of three phases:

1. Premigration:
   - The environment is available for end-user use but is put into an Infrastructure Maintenance state so no Lifecycle management operations can be performed.
1. Migration:
   - The environment requires downtime of up to 48 hours and isn't available for use during this time.
   - The resources move to the new geography.
1. Postmigration:
   - The environment is available for use, and after confirmation you're your customers the environment is working as expected, cleanup operations are performed.

## How the move works

You'll be provided with a list of prerequisites and post-requisites for your migration. The following table describes Customer and Microsoft responsibilities does before, during, and after migration process.

| Responsible party | Before the migration | During the move | After the migration |
| --- | --- | --- | --- |
| Customer | - Submit a geo to geo migration support request. <br> - After the request is approved, uninstall any microservices or add-ins. |   | - Reinstall any microservices or add-ins <br> - May choose to migrate retail components. |
| Microsoft | - Reviews the geo to geo migration request. <br> - Approves the geo to geo migration request. <br> - Premigration work begins 12 hours prior to scheduled downtime. | - Unlinks Microsoft Dynamics 365 Finance and Microsoft Dataverse environments. <br> - Performs migration of the Dynamics 365 Finance environment. <br> - Performs migration of the Dataverse environment. <br>- Relinks Dynamics 365 Finance and Dataverse environments.  | - Microsoft technical support will notify customers about migration updates.  |
