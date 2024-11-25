---
title: Database Movement API
description: Learn about an overview of the Microsoft Dynamics Lifecycle Services (LCS) Database Movement application programming interface (API) about database movement APIs.
author: laneswenka
ms.author: laswenka
ms.topic: overview
ms.date: 02/20/2020
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2019-09-30
ms.search.form: 
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


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]