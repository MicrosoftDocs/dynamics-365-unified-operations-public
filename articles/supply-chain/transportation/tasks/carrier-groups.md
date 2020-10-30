--- 
# required metadata 
 
title: Set up Carrier group
description: This procedure shows how to set up data for carrier group. 
author: Henrikan
manager:  
ms.date: 10/30/2020
ms.topic: business-process 
ms.prod:  
ms.service: dynamics-ax-applications 
ms.technology:  
 
# optional metadata 
 
ms.search.form: TMSCarrierGroup   
audience: Application User 
# ms.devlang:  
ms.reviewer: kamaybac
ms.search.scope: Core, Operations 
# ms.tgt_pltfrm:  
# ms.custom:  
ms.search.region: Global
ms.search.industry: Distribution
ms.author: henrikan
ms.search.validFrom: 2020-10-30 
ms.dyn365.ops.version: 10.0.15
---

# Set up carrier groups

A carrier group is a collection of shipping carriers and carrier services. Each group specifies a preferred sequence for each shipping carrier and carrier service in the group.

When multiple shipping carriers and carrier services exist for the same route segment, a carrier group may be specified instead of a specific shipping carrier and carrier service in the route plan or route guide.

## Create a carrier group

To create a carrier group, follow these steps:

1. Go to **Transportation management &gt; Setup &gt; Carriers &gt; Carrier group**.
1. Select **New**.
1. In the **Carrier group** filed, enter a unique ID for the group.
1. In the **Name** field, enter a descriptive name for the group.
<!-- KFM: What is the **Carrier count** field for? -->
1. On the **Details** FastTab, add a row and select a **Shipping carrier** and a **Carrier service** for it. Repeat this step to add as many carriers as you need for this group.
1. Close the page.
