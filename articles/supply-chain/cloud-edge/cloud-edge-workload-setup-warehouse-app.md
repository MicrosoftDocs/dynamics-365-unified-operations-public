---
# required metadata

title: Configure the Warehouse Management mobile app for cloud and edge scale units
description: This topic explains how to set up your Warehouse Management mobile apps for warehouses that are served by a cloud or edge scale unit.

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

This topic explains how to set up your Warehouse Management mobile apps so that they can be used at warehouses that are served by a cloud or edge scale unit.

## Prerequisites

Before you start to set up your mobile devices to connect to a cloud or edge scale unit, confirm that they can connect to the enterprise hub. For instructions, see [Install and connect the Warehouse Management mobile app](../warehousing/install-configure-warehouse-management-app.md).

## Additional setup when you run the Warehouse Management mobile app against a scale unit

As part of the [deployment process for warehouse scale unit workloads](cloud-edge-landing-page.md#scale-unit-manager-portal), most of the data that is required to connect your Warehouse Management mobile app devices is automatically synced from the enterprise hub to the scale unit. However, you must enter the data on the **Azure Active Directory applications** page (**System administration \> Setup \> Azure Active Directory applications**) on the scale unit deployment. Additionally, you might have to update the default **Company** value for the user ID or create a new user. Users that are associated with a company that doesn't exist on a scale unit deployment won't be able sign in when the Warehouse Management mobile app is connected to that scale unit.

> [!NOTE]
> Because the data on the **Azure Active Directory applications** page isn't synced, you must manually maintain this data if you want to move your warehouse workloads to another scale unit.

Remember that, as part of the connection setup of each Warehouse Management mobile app, the specified Azure Active Directory resource URL must be for the scale unit instead of the enterprise hub.
