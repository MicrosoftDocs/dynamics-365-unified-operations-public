---
# required metadata

title: Automatic update of asset counters
description: This topic describes automatic update of asset counters in Asset Management.
author: josaw1
manager: AnnBe
ms.date: 08/15/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: josaw
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: mkirknel
ms.search.validFrom: 2019-08-15
ms.dyn365.ops.version: 10.0.5

---

# Automatic update of asset counters

[!include [banner](../../includes/banner.md)]

[!include [banner](../../includes/preview-banner.md)]

In the previous section, manual registration of asset counters is described. Setup of asset counters is described in [Counters](../setup-for-objects/counters.md).

Counter values can also be automatically updated from production registrations, based on production hours or production quantity. This is done in **Update asset counters**. You can update one or several assets by inserting one parameter, **From date**. This parameter specifies the start date for production registrations (hours or quantity produced), meaning the start date from which counter values should be updated.

All assets that are related to a resource *and* have asset counters, which are set up to be updated based on produced quantity or production hours, will be included in an automatic update, and new counter values will be created.

Regarding counters based on production quantity, good quantity as well as error quantity registered are included in the count. If the unit used for produced quantity registration is different from the unit used on the counter, quantity is converted to correspond with the counter unit.

As mentioned above, automatic counters can be updated from production registrations. Therefore, the asset for which you want to automatically update counters must be related to a resource (machine). The following descriptions provide an overview of the setup and processing of production orders (in the **Production control** module), which is used as a basis for automatic update of counters on an asset in the **Asset management** module.

When produced quantities or production hours have been registered on the resource, you can update the related asset counters.

1. Click **Asset management** > **Periodic** > **Assets** > **Update asset counters**.

2. Select the start date of the automatic update in the **From date** field.

>[!NOTE]
>The date in this field is the "work in progress" date from **Route transactions** (**Production control** > **Inquiries and reports** > **Production** > **Route transactions** > **Physical date** field).

3. If you want to select specific assets, asset types, or resources for the automatic update, click **Filter** on the **Records to include** FastTab, and make the relevant selections.

4. If required, you can set up the automatic update as a batch job on the **Run in the background** FastTab.

![Figure 1](media/12-work-orders.png)

5. Click **OK**. When the automatic asset counter update is done, you can see the counter registrations related to the asset in **Asset counters** (**Asset management** > **Common** > **Assets** > **All assets** > select asset > **Counters** button).

In **Asset counter totals**, you can get an overview of the latest registration made on all counter types on all assets. Click **Asset management** > **Inquiries** > **Assets** > **Asset aggregated value**. The view is very similar to **Asset counters**, but you cannot add or edit registrations in **Asset aggregated value**. It is for overview only.

![Figure 2](media/13-work-orders.png)


- It is still possible to create manual counter value registrations for counter types that are automatically updated. Refer to the "Manual update of asset counters" section for more information.
- You can set up counters related to another counter, which means that when a counter is updated, related counters are automatically updated at the same time. Refer to [Counters](../setup-for-objects/counters.md) regarding setup of related counters.
