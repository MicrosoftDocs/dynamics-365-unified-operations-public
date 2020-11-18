---
# required metadata

title: Troubleshoot inbound warehouse operations
description: This topic describes how to fix common issues that you might encounter while you work with inbound warehouse operations in Microsoft Dynamics 365 Supply Chain Management.
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

This topic describes how to fix common issues that you might encounter while you work with inbound warehouse operations in Microsoft Dynamics 365 Supply Chain Management.

## I receive the following error message: "Quality order %1 has been generated. Cluster profile could not be found please check your configuration."

### Issue description

This error message is related to a receiving process where quality management (QMS) is turned on. Depending on the configurations in your environment, additional details about the transaction that is generating the error message might help fix the issue.

### Issue resolution

First, review the [cluster picking](set-up-cluster-picking.md) setup, and make sure that your cluster profiles are set up correctly. You can't use a mobile device menu item for cluster picking unless cluster profiles are set up. Depending on your environment, you might also have to review other related configurations.

## Mixed license plate receiving doesn't work for any disposition code except Credit.

### Issue description

When the **Action** field for a disposition code is set to *Credit* or *Scrap*, you can use only the [Mixed license plate receiving](mixed-license-plate-receiving.md) menu item to process returned items.

### Issue resolution

Microsoft has evaluated this issue and has determined that it's a feature limitation. Currently, only [disposition codes](../service-management/set-up-disposition-codes.md) where the **Action** field is set to *Credit* or *Scrap* are supported for mixed license plate receiving.

## When I run the Update product receipts periodic task, unconfirmed purchase orders are confirmed.

### Issue description

After you run the *Update product receipts* periodic task, the system automatically confirms unconfirmed purchase orders that have an inventory transaction status of *Registered*.

### Issue resolution

A new inbound load handling feature, *Over receipt of load quantities*, fixes this issue. To turn on this feature, go to [Feature management](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md), and turn on the following features (in the order that they are listed in):

1. Associate purchase order inventory transactions with load
1. Over receipt of load quantities

For more information, see [Post registered product quantities against purchase orders](inbound-load-handling.md#post-registered-quantities).
