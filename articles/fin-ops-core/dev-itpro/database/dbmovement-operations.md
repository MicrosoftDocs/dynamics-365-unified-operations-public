---
# required metadata

title: Database movement operations home page
description: This topic provides links to quick start guides and tutorials available for Database Movement features in Lifecycle Services. 
author: laneswenka
manager: AnnBe
ms.date: 02/20/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
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

## Database movement quick start guides
Learn how to perform the individual operations on your Standard or Premier Acceptance Test environments:

* [Refresh database](database-refresh.md)
* [Export a database](export-database.md)
* [Import a database](import-database.md)
* [Point-in-time restore (PITR)](database-point-in-time-restore.md)
* [Point-in-time restore of the production database to a sandbox environment](database-pitr-prod-sandbox.md)

## Step-by-step tutorials
Learn how to achieve common implementation scenarios using DataALM to your advantage:

* [Refresh for training purposes](dbmovement-scenario-general-refresh.md)
* [Debug a copy of the production database](dbmovement-scenario-debugdiag.md)
* [Export a copy of the standard user acceptance testing (UAT) database](dbmovement-scenario-exportuat.md)
* [Golden configuration promotion](dbmovement-scenario-goldenconfig.md)
* [Destructive testing](dbmovement-scenario-destructivetests.md)

## Database Movement API
The Database Movement application programming interface (API) lets you integrate several of the previously mentioned database movement operations into your overall ALM process. In addition, by using the API together with your preferred scheduling engine, you can build recurrence into the process, so that it runs daily or on demand.

* [Overview](./api/dbmovement-api-overview.md)
* [Versioning and support](./api/dbmovement-api-versioning-support.md)
* [Authentication](./api/dbmovement-api-authentication.md)
* [Throttling](./api/dbmovement-api-throttling.md)
* [Reference](./api/v1/dbmovement-api-v1-overview.md)

