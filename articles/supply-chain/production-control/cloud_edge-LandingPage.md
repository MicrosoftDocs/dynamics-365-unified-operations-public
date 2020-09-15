---
# required metadata

title: Cloud and Edge
description: Cloud and Edge scale units for manufacturing and warehouse management workloads
author: cabeln
manager: 
ms.date: 11/03/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: JmgShopSupervisorWorkspace, ProdTable, ProdTableListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: cabeln
ms.search.validFrom: 2020-09-23
ms.dyn365.ops.version: AX 10.0.15
---

# Cloud and Edge scale units for manufacturing and warehouse management workloads

This feature enables shop floor and warehouse execution workloads to be distributed between cloud and edge scale units, which can help improve performance, prevent service interruptions, and maximize up time.

:::image type="content" source="../Cloud and Edge/media/HeroDiagram.png" alt-text="Dynamics 365 with Scale Units":::

Companies working with manufacturing and distribution must be able to execute key business processes 24/7, without interruption and at scale. But complications may arise due to issues ranging from basic connectivity (such as provider outages, Azure outages, unreliable connections, or network latency) to multiple business processes competing for the same system resources. Cloud and edge features enable companies to execute key mission-critical manufacturing and warehouse processes without interruption, even in situations such as these.

> [!TIP]
> Navigate directly to the scale unit management environment for your Dynamics 365 Supply Chain Management environment. [Click Here](https://sum.dynamics.com)   

## Scale units for dedicated workloads

Scale units for supply chain management extend your central Dynamics 365 Supply Chain Management cloud hub environment with dedicated processing capacity. Scale units can run in the cloud or on the edge in your local facility premises. Scale units are always connected to the cloud hub environment and receive all information to run the dedicated processing for assigned workloads.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit. As of today two types of workloads are supported:

- Manufacturing execution
- Warehouse management

Within manufacturing execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable machine operators and shop floor supervisors to access the operational production plan.
- Enable machine operators to keep the plan current by executing discrete and process manufacturing jobs.
- Enable the shop floor supervisor to adjust the operational plan.
- Enable workers to access time and attendance for clock-in and clock-out on the edge to ensure correct worker pay calculation.

For warehouse execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable warehouse workers and warehouses to access planned warehouse work.
- Enable warehouse workers to execute warehouse work using the warehouse mobile application.
- Enable warehouse workers and managers to perform inquiries into on-hand inventory.
- Enable warehouse workers and managers to create and execute inventory movements.
- Enable warehouse workers to register receipts and do put-away.
- Enable warehouse workers to ship orders with outbound document printing on the edge.

## Onboarding to to using scale units for your Dynamics 365  Supply Chain Management environment

## Creating an edge scale unit for preview using your custom on-premises hardware appliance  

## Managing scale units and workloads

## Architecture details for Cloud and Edge topologies

## Monitoring and troubleshooting data synchronization