---
# required metadata

title: Analytics, aggregate measurements, and KPI modeling
description: This article discusses the embedded business intelligence (BI), aggregate measurements, dimensions, and data entities, and aggregate programming model.
author: MilindaV2
manager: AnnBe
ms.date: 06/20/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: robinr
ms.search.scope: AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 24491
ms.assetid: 6603a84c-00b2-4358-84a7-dd6fee3055ab
ms.search.region: Global
# ms.search.industry: 
ms.author: milindav
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Analytics, aggregate measurements, and KPI modeling

[!include[banner](../includes/banner.md)]


This article discusses the embedded business intelligence (BI), aggregate measurements, dimensions, and data entities, and aggregate programming model.

Embedded business intelligence
------------------------------

The term embedded business intelligence (BI) refers to experiences that use highly intuitive and fluid visualizations to provide insights that are relevant to a task, so that user is more informed and can make better choices. For example, a rental clerk in a car rental organization views the previous rental preferences of a customer when the customer makes a reservation. In this case, the clerk can see the vehicles and colors that the customer has selected in the past, and therefore can offer options that are likely to please the customer. Embedded BI is used throughout the user interface. At a technical level, building rich visualizations requires a powerful charting framework, and also an efficient way to access aggregated data that enables the display of fluid visualizations. Finance and Operations meets both of these requirements, so that application developers can build rich and deep embedded BI–enabled scenarios.

## Where are the perspectives?
Perspectives were a concept that was designed to present data from a reporting point of view. Perspectives have evolved over the past three releases for analytical scenarios.

| Version                               | Description                                                                                                                                    |
|---------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| Microsoft Dynamics AX 4.0             | Perspectives provided the ability to model ad-hoc reporting models.                                                                            |
| Microsoft Dynamics AX 2009            | Perspectives added support for modeling analysis cubes.                                                                                        |
| Microsoft Dynamics AX 2012            | Perspective modeling capabilities were improved through richer modeling support and deeper integration with the Application Object Tree (AOT). |
| Microsoft Dynamics 365 for Finance and Operations | Perspectives are a first-class citizen in the data access framework. They can be consumed via X++ or C\# code, and also in a model-driven way. |

In Finance and Operations, perspectives reside within the analytics collection in the Application Explorer. Perspectives have undergone a major upgrade and now incorporate the following improvements:

-   You can model new aggregate models and customize existing aggregate models as a star schema within Application Explorer.
-   Modeling for key performance indicators (KPIs) in Application Explorer is supported.
-   You can model data entities by referencing aggregate models. Data entities can be exposed to external reporting tools, such as PowerBI, as OData endpoints. Data entities can also be consumed within Microsoft Dynamics 365 for Finance and Operations.
-   You can consume aggregate models directly in the programming model by using X++ or C\# code. You no longer have to write MDX code to consume aggregate data.
-   Aggregate data is a first-class citizen within Finance and Operations data access. Its behavior is similar to the behavior of detailed data. For example, aggregate data can be enriched with extended data types (EDTs) and enumerations, and you can help secure them by using Finance and Operations security concepts.
-   The aggregate data infrastructure is maintained completely within the environment. By default, aggregate measurements are real-time. As a system administrator, you can manage the latency of aggregate data and controls based on available resources and business needs, without having to deal with the complexity of scheduling and external tools.
-   Finance and Operations perspectives enable an easier and more predictable modeling experience that takes advantage of business concepts that are already available throughout Finance and Operations. This lets developers reuse existing business models, and makes the modeling process quicker and easier.

Projects that were generated by using perspectives from Dynamics AX 2012 and later can be upgraded to Finance and Operations metadata equivalents.

## Aggregate measurements and aggregate dimensions
An aggregate measurement is a model that contains a collection of measures together with their corresponding dimensions. Measures are aggregate numbers, such as Total Sales or Number of Orders. Dimensions are slicers, such as Product, Vendor, or Customer, that help you analyze the measure. For example, the measure of Total Sales isn't useful unless it can be sliced by Product, Region, and Customer. Aggregate measurements are the evolution of AX 2012 analysis cubes. Whereas a cube was based on a multidimensional online analytical processing (OLAP) technology, an aggregate measurement abstracts the underlying technology. Therefore, you no longer have to know a lot about the underlying implementation technology. Additionally, the underlying technology infrastructure can take advantage of improvements in in-memory real-time technology without requiring the developer to rewrite the program. Aggregate dimensions are shared across an implementation. Aggregate measurements associate themselves with relevant aggregate dimensions. For example, Total Sales can be associated with Customer, Product, and Sales Region dimensions. However, Total Sales can't be associated with Vendor and Warehouse dimensions. Aggregate dimensions and aggregate measurements are modeled by using Visual Studio tools. The Upgrade tool lets customers and partners migrate existing Dynamics AX 2012 cubes to Finance and Operations.

## Aggregate data entities
By using the model-driven approach, you can create data entities by directly referencing aggregate measurements and aggregate dimensions. These are known as aggregate data entities. Aggregate data entities are read-only data entities that are used for reporting purposes. To consume aggregate data when you build charts and other client controls, add the aggregate data to a form as a data source. You can also consume aggregate data entities programmatically in C\# or X++ code.

## Aggregate programming model
The Aggregate programming model lets a developer consume aggregate data programmatically by using either X++ or C\# code. Data that you retrieve by using the Aggregate programming model can be used as a data source in forms and reports. A developer can add aggregate data that is modeled in perspectives to an **AXQuery** object. The developer can also use an existing aggregate data entity to create an query that can be extended by adding filters and additional columns that aren't present in the aggregate data entity. Bulk Move is a capability that is associated with the Aggregate programming model. When a query is run by the kernel, the developer can move all the records to a temporary or regular table without iterating row by row. Bulk Move provides a very efficient way to move data from aggregate models to temporary tables.

## Method expressions
Method expressions are a programming model for constructing rich calculations that are used to define fields in a data entity. Method expressions enhance the computed column capability that was introduced in AX 2012 views. Method expressions let you build expressions by using the C\# or X++ programming language. You can also create calculations on aggregate data that was previously coded by using MDX. Method expressions can be shared across the program.

## Inmemory, nearrealtime aggregate measurements
In Finance and Operations, aggregate measurements are deployed to Microsoft SQL Server non-clustered column store indexes (NCCI). Therefore, they can take advantage of the in-memory computing (IMC) engine that is built into Microsoft SQL Server 2016 as Azure DB. Aggregate measurements that have the IMC engine as their destination are referred to as in-memory, near-real-time (IM-NRT) aggregate measurements. These aggregate measurements don't require that a Microsoft SQL Server Analysis Services (SSAS) server be used. Because these models don't involve data updates, the queries that are sent to them reflect the latest state of data in the operational database. That is why it's referred to as near-real-time.

## KPI modeling and customization
In AX 2012 and earlier versions, KPIs and business indicators had to be modeled by using native SQL Server development tools. Although users could pin a KPI or business indicator to a Role Center by using the **Business Overview** Web Part, they could not modify a KPI definition, such as the goal. In Finance and Operations, users can use a rich client form to modify a KPI definition that was built and shipped by a developer. Users can also define new KPIs by using the aggregate data that is contained in aggregate measurements. A developer can model a KPI definition in Microsoft Visual Studio and ship it to a customer, either as a project or together with an independent software vendor (ISV) solution. After a KPI is defined, users can customize it at run time.




