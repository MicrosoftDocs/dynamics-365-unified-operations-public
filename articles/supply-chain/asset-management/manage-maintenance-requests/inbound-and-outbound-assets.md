---
# required metadata

title: Inbound and outbound objects
description: This topic explains how to register inbound and outbound objects in Enterprise Asset Management.
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

# Inbound and outbound objects



This topic explains how to register inbound and outbound objects in Enterprise Asset Management. If your company makes repair jobs or maintenance jobs on objects received from other locations or customers, **Enterprise Asset Management** can keep track of inbound objects on the way to your company and outbound (returned) objects.

>[!NOTE]
>If you want to use Inbound and Outbound stages to manage objects coming in and being returned, you must set up request stages and stage groups to support these actions. Refer to [Setup for requests](../setup-for-requests/requests.md).

Whether you are able to work with inbound and outbound objects depends on the setup of **Enterprise Asset Management**. The functionality can only be used if the **Inbound/outbound** check box is selected in the **License configuration** form (**System administration** > **Setup** > **Licensing** > **License configuration**).

## Register object as inbound

1. Click **Enterprise asset management** > **Common** > **Requests** > **Active requests**.
2. Select the request.
3. Click **Request stage** > **Inbound** (or the stage you have created for inbound objects).

The figure below shows a screenshot of the interface.

![Figure 1](media/06-manage-requests.png)

## Register inbound objects as received

1. Click **Enterprise asset management** > **Common** > **Inbound/outbound** > **Inbound objects**.
2. Select the object / request.
3. Click **Receive objects**.
4. Insert date and time in the **Received** field, and click **OK**. The record is removed from the **Inbound objects** list.

The following figure shows a screenshot of the interface.

![Figure 2](media/07-manage-requests.png)

## Register object as outbound

When you have completed the maintenance or repair job, you can register the object as returned.

1. Click **Enterprise asset management** > **Common** > **Requests** > **Active requests**.
2. Select the request.
3. Click **Request stage** > **Outbound** (or the stage you have created for outbound objects).

## Register outbound objects as delivered

1. Click **Enterprise asset management** > **Common** > **Inbound/outbound** > **Outbound objects**.
2. Select the object / request.
3. Click **Deliver objects**.
4. Insert date and time in the **Delivered** field, and click **OK**. The record is removed from the **Outbound objects** list.
