---
title: Transition from Analysis Services cubes to aggregate models
description: Learn about how in-memory, real-time aggregate models are used for analytics, and why we transitioned from using Server Analysis Services (SSAS) cubes.
author: MilindaV2
ms.author: johnmichalak
ms.topic: article
ms.date: 01/20/2026
ms.reviewer: johnmichalak
audience: Developer, IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: 
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 877db646-da4b-48b5-83ab-61ae59d91921
---

# Transition from Analysis Services cubes to aggregate models

[!include [banner](../includes/banner.md)]

This article explains how to use in-memory, real-time aggregate models for analytics and why Microsoft transitioned from using Server Analysis Services (SSAS) cubes.

The world is moving to real-time, proactive analytics. Reporting and trending on historical data is being replaced by up-to-the-second visualizations and proactive guidance. In-memory, real-time aggregate models now replace the perspectives that were previously used for analytics.

## A historical look at perspectives and cubes

Embedded insights play a key role in the finance and operations user experience. This vision drives Microsoft to invest in building analytic capabilities within the product. In Dynamics AX 4.0, Microsoft introduced the concept of *perspectives*. The objective was to present a simpler view of the ERP schema, specifically modeled for reporting. This simpler view was referred to as perspectives. In Dynamics AX 4.0, the system generated reporting models (SMDL models) that enabled you to create ad-hoc reports by using SQL Server Report Builder. In Dynamics AX 2009, Microsoft added the capability to generate SQL Server Analysis Services (SSAS) projects by using metadata definitions in perspectives. These projects become cubes when deployed to an SSAS server. In Dynamics AX 2012, Microsoft improved modeling in perspectives and improved tooling support for managing the lifecycle of SSAS projects. You could use Excel, and Power View, to explore data and create reports with cubes in Dynamics AX 2012. The SMDL technology was also deprecated. In Dynamics AX 2012, Microsoft stopped generating SMDL models.

## How perspectives are used now

As a developer, your contract with the system was a perspective. The system generated resources to help you achieve your end goal. In Dynamics AX 2012, the generated resources were SSAS projects. So the contract between you (the developer) and the system (the BI framework) was as follows:

- You modeled perspectives.
- The system generated the resources needed to enable you to build visuals and reports.

Developers now model perspectives by using add-ins for Visual Studio. (Visual Studio is now the development environment.) Perspectives are composed of *aggregate measurements* and *aggregate dimensions*. As a developer, you can model simpler schemas for answering business questions by using aggregate measurements and aggregate dimensions. Use aggregate measurements to define data entities (called *aggregate data entities*) that can be directly bound to finance and operations forms as a data source. You can also use aggregate data entities to

- Expose data to Power BI.
- Access data programmatically by using the AXQuery object.

:::image type="content" source="./../media/how-perspectives-are-used.png" alt-text="Screenshot of how perspectives are used diagram.":::

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
