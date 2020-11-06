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

This error is related to a receiving process where quality management (QMS) is enabled. Depending on the configurations in your environment, additional details about the transaction generating the error could further enhance the resolution.

### Issue resolution

First, check the [cluster picking](set-up-cluster-picking.md) setup and make sure your cluster profiles are set up correctly. You can't use a cluster picking mobile device menu item without the cluster profiles. Depending on your environment, other related configurations may need to be reviewed too.

## Mixed license plate receiving doesn't work for disposition codes other than credit.

### Issue description

You can only use the [Mixed license plate receiving](mixed-license-plate-receiving.md) menu item to process returned items when the disposition code **Action** is *Credit* or *Scrap*.

### Issue resolution

Microsoft has evaluated this issue and determined it to be a feature limitation. Only [disposition codes](../service-management/set-up-disposition-codes.md) with the **Action** set to *Credit* or *Scrap* are currently supported for mixed license plate receiving.

## When I run the "Update product receipts" periodic task, unconfirmed purchase orders are getting confirmed.

### Issue description

After running the periodic task *Update product receipts*, the system automatically confirms unconfirmed purchase orders with an inventory transaction status of *Registered*.

### Issue resolution

This issue is solved by the new inbound load handling feature *Over receipt of load quantities*. To enable this feature, go to [feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md) and enable the following features in the following order:

1. *Associate purchase order inventory transactions with load*
1. *Over receipt of load quantities*

For more information, see [Post registered product quantities against purchase orders](inbound-load-handling.md#post-registered-quantities)
