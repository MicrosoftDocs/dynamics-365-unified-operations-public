---
# required metadata

title:  Configure the Warehouse Management mobile app for cloud and edge scale units
description: This topic explains how to set up your _Warehouse Management mobile apps_ for warehouses served bu a cloud or edge scale unit.

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

# Configure the Warehouse Management mobile app for cloud and edge scale units

[!include [banner](../includes/banner.md)]

This topic explains how to set up your _Warehouse Management mobile apps_ for use at warehouses served by a cloud or edge scale unit.

## Prerequisites

Before you start to set up your mobile devices to connect to a cloud or edge scale unit, confirm that they can connect to the enterprise hub by following the instructions provided in [Install and connect the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md)

## Additional setup when running the Warehouse Management mobile app against a scale unit

As part of the [warehouse scale unit workload deployment process](cloud-edge-landing-page.md#scale-unit-manager-portal), most of the data needed to connect your Warehouse Management mobile app devices will automatically get synchronized from the enterprise hub to the scale unit. But you will also need to record the **Azure Active Directory applications** data on the scale unit deployment and you might need to update the default **Company** value for the **User ID** (or create a new user). Users associated with a company that doesn't exist on a scale unit deployment won't be able sign in when the Warehouse Management mobile app is connected to that scale unit.

> [!NOTE]
> Because the **Azure Active Directory applications** data is not synchronized, you must manually maintain this data if you want to move your warehouse workloads to another scale unit.

Remember that, as part of the Warehouse Management mobile app connection setup, the **Azure AD resource** must be against the scale unit rather than the enterprise hub.
