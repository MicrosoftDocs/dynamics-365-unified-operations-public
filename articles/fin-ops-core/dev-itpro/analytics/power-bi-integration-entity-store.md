---
title: Power BI integration with Entity store
description: Learn about how Entity store enables Power BI integration and understand how to stage aggregate measurements in Entity store.
author: MilindaV2
ms.author: johnmichalak
ms.topic: how-to
ms.date: 06/16/2020
ms.reviewer: johnmichalak
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-05-31
ms.search.form: BIMeasurementDeployManagementEntityStore
ms.dyn365.ops.version: Platform update 1
ms.assetid: 434b5d9f-9877-4769-ad96-d4e8d460a7fa
---

# Power BI integration with Entity store

[!include [banner](../includes/banner.md)]

Entity store is an operational data store that's included with Microsoft Dynamics 365 Finance. This article describes how Entity store enables Power BI integration.

Entity store is an operational data store that's included with the application. The Microsoft Dynamics AX platform update 1 (May 2016) release introduced the Entity store feature. This feature lets an administrator or power user stage aggregate measurements in a dedicated data store for reporting and analytics. (Aggregate measurements are a star schema that is modeled by using entities.) This data store is called Entity store. It's a database that's optimized for reporting purposes. Entity store uses the in-memory, clustered columnstore index (CCI) functionality that is built into Microsoft SQL Server to optimize reporting and queries. Customers can use Microsoft Power BI DirectQuery models together with Entity store to enable high-volume, near-real-time analytical reporting over large volumes of data.

## Power BI DirectQuery mode

In the February 2016 release of Microsoft Dynamics AX, you could create Power BI reports by using OData endpoints that data entities expose. Both aggregate data entities and detailed or regular data entities expose these OData endpoints. Although this approach is still supported, Entity store also lets power users create Power BI DirectQuery reports.

:::image type="content" source="./media/entity-store-architecture.jpg" alt-text="Screenshot of DirectQuery mode." lightbox="./media/entity-store-architecture.jpg":::

As the preceding illustration shows, DirectQuery is a reporting mode that runs reports directly on Entity store. In this reporting mode, data isn't staged in Power BI caches. This mode provides two immediate benefits:

- You can create Power BI reports over large data volumes.
- Reports don't have to be updated by using Power BI. When Entity store is updated, reports reflect the latest data.

Additionally, data doesn't leave your environment, because no data is cached in the Power BI service.

## Stage aggregate measurements in Entity store

Aggregate measurements use a star schema that's designed for analytical scenarios. In the February 2016 release, real-time, in-memory aggregate measurements were introduced. By using real-time aggregate measurements, you can enable embedded charts and key performance indicators (KPIs) that react to real-time operations on data. For more information, see [Transition from Analysis Services cubes to aggregate models](../migration-upgrade/in-memory-real-time-aggregate-models.md). Real-time aggregate measurements take advantage of the in-memory, nonclustered columnstore index (NCCI) technology. Visuals and aggregate calculations that are built over real-time aggregate measurements reflect transactions within seconds. In the platform update 1 (May 2016) release, aggregate measurements that you can stage in Entity store were introduced. You can use aggregate measurements that are staged in Entity store for near-real-time analytical scenarios where you need to explore large volumes of data by using Power BI. As a developer, you learned how to model an aggregate measurement for real-time analytics in [Model aggregate data](model-aggregate-data.md). In the platform update 1 (May 2016) release, the capability to model aggregate measurements that you can stage in Entity store was added. In Microsoft Visual Studio, you can specify **StagedEntityStore** as the usage property of an aggregate measurement. This new property was added in May 2016. Previously, **InMemoryRealTime** was available as the usage property.

:::image type="content" source="media/new-usage-property-in-VS.png" alt-text="Screenshot of new StagedEntityStore usage property in Visual Studio.":::

However, you might wonder why you would model an aggregate measurement for staging. Why wouldn't you use in-memory real-time aggregate measurements all the time? Several reasons exist for using the **StagedEntityStore** pattern:

- You need to explore and analyze large amounts of data.
- You migrated Analysis projects (that is, cubes) from Microsoft Dynamics AX 2012 R3 as part of the code upgrade process. Because of the complex views and joins that are present in the schema, query response times might not be acceptable for embedded visuals. However, you might not want to refactor the visuals to take advantage of NCCI technology immediately.
- Unlike the operational database schema, the schema in Entity store is modeled specifically for reporting. Therefore, it's easier to build new reports from the schema in Entity store.
- Your scenario doesn't require that analytical data be updated within seconds of an operation. Most Power BI reports that are built to enable data exploration fall into this category. If data freshness of approximately 10 minutes is acceptable for your scenario, you might want to use the staged pattern.

If one of the preceding reasons covers your situation, stage your aggregate measurement in Entity store and use it for Power BI integration.

## Update Entity store

The system automates and manages Entity store refresh. In the client, you can find the **Entity Store** page at **Systems administration** &gt; **Setup** &gt; **Entity Store**. For more information, see [Automated Entity store refresh](./automated-entity-store-refresh.md).

### Connecting to the Entity store database

For troubleshooting and diagnostics, you can connect to the Entity store database directly from a related sandbox environment. To connect:

1. Use Remote Desktop to access the sandbox. You can download the RDP file from the **Environment Details** page after you include your IP address in a safe list.
1. Open SQL Server Management Studio, and connect to the server specified on the **Environment Details** page.  
    - Find the section titled **Database Accounts**  Locate the entry for the user with the name **axdwadmin**.  
    - The server name is the first portion of the **SQL Server\Database Name** field. Use the format **SQLServerName.database.windows.net**, where SQLServerName is the value from LCS.
    - Change the authentication type from Windows Authentication to SQL Server Authentication.
    - Use **axdwadmin** as the sign-in name and use the password from LCS.
1. Use the **Options** button or browse to the **Connection Properties** tab. Change the **Connect to database** property from the default value to your **Database Name** value from LCS.
1. Select **Connect** to access the database.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
