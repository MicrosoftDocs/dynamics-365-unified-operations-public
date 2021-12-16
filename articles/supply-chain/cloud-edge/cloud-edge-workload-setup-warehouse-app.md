---
# required metadata

title: Setup Warehouse Management mobile app for cloud and edge scale unit workloads
description: This topic provides information about how to setup the Warehouse management mobile app in warehouse management workloads.
author: perlynne
ms.date: 12/15/2021
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: SysAADClientTable, SysUserManagement
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid:
ms.search.region: global
ms.search.industry: SCM
ms.author: perlynne
ms.search.validFrom: 2022-01-31
ms.dyn365.ops.version: 10.0.25
---

# Setup Warehouse Management mobile app for cloud and edge scale unit workloads

[!include [banner](../includes/banner.md)]

In the following section you can read about how to setup your _Warehouse Management mobile apps_ when running cloud and edge scale unit warehouse workloads.
As a prerequisite, validate that your devices can connect to the enterprise hub by following [Install and connect the Warehouse Management mobile app](../warehousing\install-configure-warehouse-management-app.md).

## Additional setup for warehouse mobile app on scale units

As part of the warehouse scale unit workload [deployment process](cloud-edge-landing-page.md#scale-unit-manager-portal) most of the needed data to connect your warehouse mobile app devices will automatically get synchronized from the enterprise hub to the scale unit. But you will need to record the **Azure Active Directory applications** data on the scale unit deployment and you might as well need to update the default **Company** value for the **User ID** (or create a new user). In case the user is associated with a company that does not exists on the scale unit deployment it will not be possible to connect the Warehouse management mobile app against the scale unit deployment.

Lastly, remember that the **Azure AD resource** must be against the scale unit rather than the enterprise hub.
