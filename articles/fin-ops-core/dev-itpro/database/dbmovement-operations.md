---
# required metadata

title: Database movement operations home page
description: This topic provides links to quick start guides and tutorials available for Database Movement features in Lifecycle Services. 
author: laneswenka
ms.date: 02/20/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
# ms.custom: [used by loc for topics migrated from the wiki]
ms.search.region: Global
# ms.search.industry: 
ms.author: laswenka
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Database movement operations home page

[!include [banner](../includes/banner.md)]

Database movement operations are a suite of self-service actions that can be used as part of Data Application Lifecycle Management (also referred to as *DataALM*).  These actions provide structured processes for common implementation scenarios such as golden configuration promotion, debugging/diagnostics, destructive testing, and general refresh for training purposes.

In this topic, you will learn how to use database movement operations to perform refresh, export, import, and various flavors of point-in-time restore.

## Database movement scenarios and quick start guides
Below find the various scenarios that are supported and a link to a quick start guide for each:

| Source Environment | Target Environment | Quick Start Guide | Available via API | Tutorials 
|---|---|---|---|---|
|Production|	Sandbox|	[Refresh database](database-refresh.md) | [Create refresh](api/v1/reference-create-refresh.md) | [Refresh for training purposes](dbmovement-scenario-general-refresh.md)
[Debug a copy of the production database](dbmovement-scenario-debugdiag.md) |
|Sandbox|	Production| [Refresh database](database-refresh.md) | Not supported | [Golden configuration promotion](dbmovement-scenario-goldenconfig.md) |
|Sandbox|	Sandbox|	[Refresh database](database-refresh.md) | [Create refresh](api/v1/reference-create-refresh.md) | [Refresh for training purposes](dbmovement-scenario-general-refresh.md)|
|Sandbox|	DevTest|	[Export a database](export-database.md) | [Create export](api/v1/reference-create-export.md) | [Export a copy of the standard user acceptance testing (UAT) database](dbmovement-scenario-exportuat.md) |
|DevTest|	Sandbox|	[Import a database](import-database.md)| Not supported | [Golden configuration promotion](dbmovement-scenario-goldenconfig.md) |
Production|	DevTest|	Not directly supported | Not supported | Recommend [Export a copy of the standard user acceptance testing (UAT) database](dbmovement-scenario-exportuat.md) |
|Sandbox Point-in-time | Sandbox |[Point-in-time restore (PITR)](database-point-in-time-restore.md) | Not supported | [Destructive testing](dbmovement-scenario-destructivetests.md) |
|Production Point-in-time| Sandbox| [Point-in-time restore of the production database to a sandbox environment](database-pitr-prod-sandbox.md) | Not supported | [Destructive testing](dbmovement-scenario-destructivetests.md)

>[!Important]
>Database movement operations are very lengthy operations.  The amount of time they take varies by data volume, schema complexity, and whether or not the target of the operation is a flat file like a .bacpac in the case of Export operation.  In general, these can take up to 24 hours to complete, and during the operation there is no means to cancel.  In addition, if the target of the operation is an environment like in the Production to Sandbox scenario, the Sandbox will go offline at an undetermined time, when the datatabase copy operation has completed but before the Database Synchronization steps begin.  This will happen at no warning to end-users in the environment, and as such it is best to schedule these types of operations during off hours.

## Database Movement API
The Database Movement application programming interface (API) lets you integrate several of the previously mentioned database movement operations into your overall ALM process. In addition, by using the API together with your preferred scheduling engine, you can build recurrence into the process, so that it runs daily or on demand.

* [Overview](./api/dbmovement-api-overview.md)
* [Versioning and support](./api/dbmovement-api-versioning-support.md)
* [Authentication](./api/dbmovement-api-authentication.md)
* [Throttling](./api/dbmovement-api-throttling.md)
* [Reference](./api/v1/dbmovement-api-v1-overview.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]