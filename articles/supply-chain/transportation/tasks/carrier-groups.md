--- 
# required metadata 
 
title: Carrier groups
description: This article describes how to set up data for carrier groups.
author: Weijiesa
ms.date: 10/30/2020
ms.topic: how-to 
ms.prod:  
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSCarrierGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2020-10-30 
ms.dyn365.ops.version: 10.0.15
---

# Carrier groups

[!include [banner](../../includes/banner.md)]

A carrier group is a collection of shipping carriers and carrier services. Each carrier group specifies the preferred sequence for the shipping carriers and carrier services that belong to it.

When multiple shipping carriers and carrier services exist for the same route segment, you can specify a carrier group instead of a specific shipping carrier and carrier service in the route plan or route guide.

## Create a carrier group

1. Go to **Transportation management &gt; Setup &gt; Carriers &gt; Carrier group**.
1. Select **New**.
1. In the **Carrier group** field, enter a unique identifier (ID) for the group.
1. In the **Name** field, enter a descriptive name for the group.
1. On the **Details** FastTab, add a row, and select a shipping carrier and a carrier service for it. Repeat this step until you've added as many carriers as you require for the group.
1. Close the page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]