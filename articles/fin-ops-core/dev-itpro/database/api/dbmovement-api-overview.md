---
# required metadata

title: Database Movement API
description: This topic provides an overview of the Microsoft Dynamics Lifecycle Services (LCS) Database Movement application programming interface (API).
author: laneswenka
manager: AnnBe
ms.date: 09/30/2019
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
ms.search.validFrom: 2019-09-30
ms.dyn365.ops.version: 10.0.0

---

# Database Movement API

[!include [banner](../../includes/banner.md)]

The Database Movement application programming interface (API) is a RESTful endpoint that is used to manage the data lifecycle of Microsoft Dynamics 365 environments. It provides a versioned set of capabilities that you can currently use to copy databases between environments, and to list and download database backups. More supported actions will be added in later releases.

## What is supported by the Database Movement API?

The Database Movement API exposes RESTful endpoints for the following Dynamics 365 services:

* Dynamics 365 Finance
* Dynamics 365 Supply Chain Management
* Dynamics 365 Commerce

## Next steps

* Learn how to set up [authentication](dbmovement-api-authentication.md).
* Review the [API reference](./v1/dbmovement-api-v1-overview.md).
