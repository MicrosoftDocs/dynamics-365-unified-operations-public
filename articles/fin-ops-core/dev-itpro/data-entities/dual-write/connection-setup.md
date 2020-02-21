---
# required metadata

title: Supported scenarios for dual-write setup
description: 
author: RamaKrishnamoorthy
manager: AnnBe
ms.date: 01/06/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User, IT Pro
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: global
ms.search.industry: 
ms.author: ramasri
ms.dyn365.ops.version: 
ms.search.validFrom: 2020-01-06

---

# Supported scenarios for dual-write setup

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

You can set up a dual-write connection between a Finance and Operations environment and a Common Data Service environment. Depending on your subscription and the environment, the connection setup mechanism varies.

+ For new Finance and Operations instances, the dual-write connection setup experience starts in Lifecycle Services (LCS). Microsoft Power Platform license holders will get a new Common Data Service environment if their tenant does not have one.
+ For existing Finance and Operations instances, the dual-write connection setup starts from the Finance and Operations environments.

The supported setup scenarios are:
+ [A new Finance and Operations instance and a new Common Data Service instance](#new-new)
+ [A new Finance and Operations instance and an existing Common Data Service instance](#new-existing)
+ [A new Finance and Operations instance with demo data and a new Common Data Service instance](#new-demo-new)
+ [A new Finance and Operations instance with demo data and an existing Common Data Service instance](#new-demo-existing)
+ [An existing Finance and Operations instance and a new Common Data Service instance](#existing-new)
+ [An existing Finance and Operations instance and a new or existing Common Data Service instance](#existing-existing)

## <a id="new-new"/>New Finance and Operations instance and new Common Data Service instance

To set up a dual-write connection between a new Finance and Operations instance with no data and a new Common Data Service instance, follow the steps in the [Out-of-the-box setup from Lifecycle Services](lcs-setup.md). When the connection setup is complete, the following happens automatically:

- A new empty Finance and Operations environment is provisioned.
- A new empty Common Data Service instance (with CRM prime solution installed) is provisioned.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live sync.

As a result, both the environments are ready for live data sync.

## <a id="new-existing"/>A new Finance and Operations instance and existing Common Data Service instance

To set up a dual-write connection between a new Finance and Operations instance with no data and an existing Common Data Service instance, follow the steps in the [Out-of-the-box setup from Lifecycle Services](lcs-setup.md). When the connection setup is complete, the following happens automatically:

- A new empty Finance and Operations environment is provisioned.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live sync.

As a result, both the environments are ready for live data sync.

To sync the existing Common Data Service data to the Finance and Operations instance, perform the following steps:
1. Create a new company in the Finance and Operations instance.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data with a three-letter ISO company code.

Since dual-write is in live sync mode, the data from Common Data Service will start flowing to Finance and Operations automatically.

## <a id="new-demo-new"/>New Finance and Operations instance with demo data and new Common Data Service instance

To set up a dual-write connection between a new Finance and Operations instance with demo data and a new Common Data Service instance, follow the steps explained in [A new Finance and Operations instance and a new Common Data Service instance](#new-new). After the connection setup is complete, if you want to sync the demo data to Common Data Service instance, then do the following:
- Launch the Finance and Operations application from Life Cycle Services page, or log in to the Finance and Operations application and go to **Data Management > Dual-write**.
- Run **Initial sync** functionality for entities you wish to data sync.

## <a id="new-demo-existing"/>New Finance and Operations instance with demo data and existing Common Data Service instance

To set up a dual-write connection between a new Finance and Operations instance with demo data and an existing Common Data Service instance, follow the steps explained in  [A new Finance and Operations instance and an existing Common Data Service instance](#new-existing). After the connection setup is complete, if you want to sync the demo data to Common Data Service instance, then do the following:
- Launch the Finance and Operations application from Life Cycle Services page, log in to the Finance and Operations application and go to **Data Management > dual-write**.
- Run “Initial sync” functionality for entities you wish to data sync.

To sync the existing Common Data Service data to the Finance and Operations instance, perform the following steps:
1.	Create a new company in Finance and Operations instance.
2.	Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data with a three-letter ISO company code.

Since dual-write is in live sync mode, the data from Common Data Service will start flowing to Finance and Operations automatically.

## <a id="existing-existing"/>Existing Finance and Operations instance and new or existing Common Data Service instance
Dual-write connection setup between an existing Finance and Operations instance and a new or existing Common Data Service instance happens in the Finance and Operation environment. 
1. Follow the [manual set up from Finance and Operations](fin-ops-setup.md) to establish the connection.
2. To sync the existing Common Data Service data to the Finance and Operations instance, [bootstrap](bootstrap-company-data.md) the Common Data Service data with a three-letter ISO company code. 

Since dual-write is in live sync mode, the data from Common Data Service will start flowing to Finance and Operations automatically.
