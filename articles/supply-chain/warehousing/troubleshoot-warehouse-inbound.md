---
# required metadata

title: Troubleshoot inbound warehouse operations
description: This topic describes how to fix common issues that you might encounter while working with inbound warehouse operations in Dynamics 365 Supply Chain Management.
author: perlynne
manager: tfehr
ms.date: 10/19/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: kamaybac
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
# ms.search.industry: 
ms.author: perlynne
ms.search.validFrom: 2020-10-19
ms.dyn365.ops.version: 10.0.15
---

# Troubleshoot inbound warehouse operations

[!include [banner](../includes/banner.md)]

This topic describes how to fix common issues that you might encounter while working with inbound warehouse operations in Dynamics 365 Supply Chain Management.

## I receive the error "Quality order %1 has been generated. Cluster profile could not be found please check your configuration."

### Issue description

This error is related to a receiving process where Quality Management (QMS) is enabled. Depending upon the configurations in your environment, additional details about the transaction generating the error could further enhance the resolution.

### Issue resolution

First, check the [Cluster profile](https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/set-up-cluster-picking) setup. You can't use a cluster picking mobile device menu item without the cluster profiles. Depending on your environment, other related configurations may need to be reviewed.

## Mixed license plate receiving doesn't work for disposition codes other than credit.

### Issue description

You can only use the [Mixed license plate receiving](https://docs.microsoft.com/en-us/dynamics365/supply-chain/warehousing/mixed-license-plate-receiving) menu item when the returns **Disposition code** **Action** is *Credit* or *Scrap*.

### Issue resolution

Microsoft has evaluated this issue and determined it to be a feature limitation. The [Returns](https://docs.microsoft.com/en-us/dynamics365/supply-chain/service-management/set-up-disposition-codes) **Disposition codes** with the **Action** set to *Credit* or *Scrap* are only supported at this time.

## When I run the Update product receipts periodic task, unconfirmed purchase orders are getting confirmed.

### Issue description

After running the periodic task "Update product receipts", the system automatically confirms unconfirmed purchase orders with a status of inventory transaction *Registered*.

### Issue resolution

Use the new inbound load handling feature, *Over receipt of load quantities*. You must use [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) to enable this feature. First enable the **Associate purchase order inventory transactions with load** feature, then enable **Over receipt of load quantities**. For more information, see [Post registered product quantities against purchase orders](inbound-load-handling.md#post-registered-quantities)
