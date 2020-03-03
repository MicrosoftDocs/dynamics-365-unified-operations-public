---
# required metadata

title: Supported scenarios for dual-write setup
description: This topic describes the scenarios that are supported for dual-write setup.
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

You can set up a dual-write connection between a Finance and Operations environment and a Common Data Service environment. The setup mechanism varies, depending on your subscription and the environment.

+ For new instances of Finance and Operations apps, the setup of a dual-write connection begins in Microsoft Dynamics Lifecycle Services (LCS). If you have a license for Microsoft Power Platform, you will get a new Common Data Service environment if your tenant doesn't have one.
+ For existing instances Finance and Operations apps, the setup of a dual-write connection begins in the Finance and Operations environments.

The following setup scenarios are supported:

+ [A new Finance and Operations app instance and a new Common Data Service app instance](#new-new)
+ [A new Finance and Operations app instance and an existing Common Data Service app instance](#new-existing)
+ [A new Finance and Operations app instance that has demo data and a new Common Data Service appinstance](#new-demo-new)
+ [A new Finance and Operations app instance that has demo data and an existing Common Data Service app instance](#new-demo-existing)
+ [An existing Finance and Operations app instance and a new or existing Common Data Service app instance](#existing-existing)

## <a id="new-new"></a>A new Finance and Operations app instance and a new Common Data Service app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and a new instance of a Common Data Service app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions occur automatically:

- A new empty Finance and Operations environment is provisioned.
- A new empty instance of a Common Data Service app is provisioned, where the CRM prime solution is installed.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

## <a id="new-existing"></a>A new Finance and Operations app instance and an existing Common Data Service app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has no data and an existing instance of a Common Data Service app, follow the steps in [Dual-write setup from Lifecycle Services](lcs-setup.md). When the connection setup is completed, the following actions occur automatically:

- A new empty Finance and Operations environment is provisioned.
- A dual-write connection is established for DAT company data.
- Entity maps are enabled for live synchronization.

Both environments are then ready for live data synchronization.

To sync the existing Common Data Service data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter International Organization for Standardization (ISO) company code.

Because dual-write is in live synchronization mode, the data from Common Data Service automatically starts to flow to the Finance and Operations app.

## <a id="new-demo-new"></a>A new Finance and Operations app instance that has demo data and a new Common Data Service app instance

To set up a dual-write connection between a new instance of a Finance and Operations app that has demo data and a new instance of a Common Data Service app, follow the steps in the [A new Finance and Operations app instance and a new Common Data Service app instance](#new-new) section earlier in this topic. When the connection setup is completed, if you want to sync the demo data to the Common Data Service app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the entities that you want to sync data for.

## <a id="new-demo-existing"></a>A new Finance and Operations app instance that has demo data and an existing Common Data Service app instance

To set up a dual-write connection between a new Finance and Operations app instance that has demo data and an existing Common Data Service app instance, follow the steps in the [A new Finance and Operations app instance and an existing Common Data Service app instance](#new-existing) section earlier in this topic. When the connection setup is completed, if you want to sync the demo data to the instance of the Common Data Service app, follow these steps.

1. Open the Finance and Operations app from the LCS page, sign in, and then go to **Data Management \> Dual-write**.
2. Run the **Initial sync** functionality for the entities that you want to sync data for.

To sync the existing Common Data Service data to the Finance and Operations app, follow these steps.

1. Create a new company in the Finance and Operations app.
2. Add the company to the dual-write connection setup.
3. [Bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter ISO company code.

Because dual-write is in live synchronization mode, the data from Common Data Service automatically starts to flow to the Finance and Operations app.

## <a id="existing-existing"></a>An existing Finance and Operations app instance and a new or existing Common Data Service app instance

The setup of a dual-write connection between an existing instance of a Finance and Operations app and a new or existing instance of a Common Data Service app occurs in the Finance and Operation environment.

1. Follow the instructions for [manual setup from Finance and Operations](fin-ops-setup.md) to establish the connection.
2. To sync the existing Common Data Service data to the Finance and Operations app, [bootstrap](bootstrap-company-data.md) the Common Data Service data by using a three-letter ISO company code.

Because dual-write is in live synchronization mode, the data from Common Data Service automatically starts to flow to the Finance and Operations app.

