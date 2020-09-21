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

# Cloud and Edge scale units for manufacturing and warehouse management workloads - public preview

This feature enables shop floor and warehouse execution workloads to be distributed between cloud and edge scale units, which can help improve performance, prevent service interruptions, and maximize up time.

Companies working with manufacturing and distribution must be able to execute key business processes 24/7, without interruption and at scale. But complications may arise due to issues ranging from basic connectivity (such as provider outages, Azure outages, unreliable connections, or network latency) to multiple business processes competing for the same system resources. Cloud and edge features enable companies to execute key mission-critical manufacturing and warehouse processes without interruption, even in situations such as these.

### Public preview information

The Cloud & Edge preview for Dynamics 365 Supply Chain Management is made available on the condition you agree to these Preview Terms. [**LINK MISSING**]
>
> [!IMPORTANT]
> In order to sign up to the Cloud & Edge preview for Dynamics 365 Supply Chain Management your organization must already have a live Dynamics 365 Supply Chain Management cloud environment.
> The scale units capability are in public preview at the moment.
As the one signing up, your user account must be user in the specific tenant and also a project owner or an environment admin in LCS for an active Dynamics 365 LCS project in that tenant.
>
> When you  sign up for the preview, you will select the tenant and go through the sign up steps. As soon as a preview capacity can be allocated an email will be sent with provisioning details and the promotion codes for two environments (a cloud hub and a scale unit) for the respective LCS project. You will then be able to deploy the two environment as Tier 2 sandbox environments. Those are valid 60 days from creation date of the promo code.
>After confirmation to Microsoft, the one of the environments will be configured to function as cloud hub the other as a scale unit. You can then configure the scale units and deploy select Warehouse management an manufacturing workloads using the Scale Unit Manager portal.
>
>Please note! Preview environments will be deleted automatically after 60 days. After the preview environment has been deleted, you may sign up and queue for a new preview deployment.
>
>Navigate here to sign up for the preview> https://SUM.DYNAMICS.COM

> [!WARNING]
> Please note that certain business functionality is not fully supported in the public preview when using workloads scale units.  

The preview will allow you receive one environment that will function as a cloud based hub of your supply chain management environment and one environment that will function as a cloud scale unit. For the preview both environment will be hosted in a data center in northern USA.
You will also have the possibility to configure an on-premise environment using LBD and configure this as an edge scale unit to the cloud hub that you have received as part of the preview program. 

:::image type="content" source="./media/cloud_edge-HeroDiagram.png" alt-text="Dynamics 365 with Scale Units":::

## Scale units for dedicated workloads

Scale units for supply chain management extend your central Dynamics 365 Supply Chain Management cloud hub environment with dedicated processing capacity. Scale units can run in the cloud or on the edge in your local facility premises. Scale units are always connected to the cloud hub environment and receive all information to run the dedicated processing for assigned workloads.

A workload is a defined set of business functionality that can be factored out and delegated to a scale unit. As of today two types of workloads are supported:

- Manufacturing execution
- Warehouse management

### Dedicated manufacturing workload capabilities in a scale unit

Within manufacturing execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable machine operators and shop floor supervisors to access the operational production plan.
- Enable machine operators to keep the plan current by executing discrete and process manufacturing jobs.
- Enable the shop floor supervisor to adjust the operational plan.
- Enable workers to access time and attendance for clock-in and clock-out on the edge to ensure correct worker pay calculation.

### Dedicated warehouse management workload capabilities in a scale unit

For warehouse execution, cloud and edge scale units deliver the following capabilities, even when edge units aren't connected to the cloud:

- Enable warehouse workers to execute warehouse work using the warehouse mobile application.
- Enable warehouse workers and managers to perform inquiries into on-hand inventory.
- Enable warehouse workers and managers to create and execute inventory movements.
- Enable warehouse wave methods processing, for replenishment and containerization on Edge.
- Enable warehouse worker to register returns and purchase orders and conduct put away on Edge.
- Enable warehouse worker to adjust inventory quantities on Edge.

## Onboarding to to using scale units for your Dynamics 365  Supply Chain Management environment

### Managing cloud scale units and workloads

### Creating an edge scale unit for preview using your custom on-premises hardware appliance
  
In the public preview you can create on-premises edge scale units on your custom hardware using the Local Business Data environments.
Please find more details [here](cloud_edge-EdgeScaleUnitsUsingLBD.md).

### Architecture details for Cloud and Edge topologies

### Monitoring and troubleshooting data synchronization
