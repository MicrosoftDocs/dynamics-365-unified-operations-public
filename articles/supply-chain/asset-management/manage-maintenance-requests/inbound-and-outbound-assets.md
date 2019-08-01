---
# required metadata

title: Inbound and outbound assets
description: This topic explains how to register inbound and outbound assets in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 06/26/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: CatProcureCatalogEdit, CatProcureCatalogListPage
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 2214
ms.assetid: 2f3e0441-414d-402b-b28b-7ab0d650d658
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Inbound and outbound assets


If your company makes repair jobs or maintenance jobs on assets received from other locations or customers, **Asset Management** can keep track of inbound assets on the way to your company and outbound (returned) assets.

>[!NOTE]
>If you want to use Inbound and Outbound lifecycle states to manage assets coming in and being returned, you must set up maintenance request lifecycle states and lifecycle models to support these actions. Refer to [Setup for maintenance requests](../setup-for-requests/requests.md).

Whether you are able to work with inbound and outbound assets depends on the setup of **Asset Management**.

## Register asset as inbound

1. Click **Asset management** > **Common** > **Maintenance requests** > **Active maintenance requests**.
2. Select the maintenance request.
3. Click **Update maintenance request state**.
4. Select **Inbound** (or the lifecycle state you have created for inbound assets), and click **OK**.

![Figure 1](media/07-manage-maintenance-requests.png)


## Register inbound assets as received

1. Click **Asset management** > **Common** > **Inbound/outbound** > **Inbound assets**.
2. Select the asset / maintenance request.
3. Click **Receive assets**.
4. Insert date and time in the **Received** field, and click **OK**. The record is removed from the **Inbound assets** list.

![Figure 2](media/08-manage-maintenance-requests.png)


## Register asset as outbound

When you have completed the maintenance or repair job, you can register the asset as returned.

1. Click **Asset management** > **Common** > **Maintenance requests** > **Active maintenance requests**.
2. Select the maintenance request.
3. Click **Update maintenance request state**.
4. Select **Outbound** (or the lifecycle state you have created for outbound assets), and click **OK**.


## Register outbound assets as delivered

1. Click **Asset management** > **Common** > **Inbound/outbound** > **Outbound assets**.
2. Select the asset / maintenance request.
3. Click **Deliver assets**.
4. Insert date and time in the **Delivered** field, and click **OK**. The record is removed from the **Outbound assets** list.

