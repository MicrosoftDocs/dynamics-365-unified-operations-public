---
title: Set up rate masters
description: Learn how to set up a rate master, including a step-by-step process for setting up break masters using the USMF demo data company. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSBreakMaster,TMSRateMaster,TMSRateMasterBase,TMSRateBaseType, TMSRouteWorkbench
ms.topic: how-to
ms.date: 02/12/2025
ms.custom: 
  - bap-template
---

# Set up rate masters, rate bases, and break masters

[!include [banner](../../includes/banner.md)]

This procedure shows you how to set up rates that are returned when using the rate route workbench as part of load planning or building. Rate engines use the configuration of rating profiles, rate masters, rate base assignments, rate bases, and break masters to determine the query structure and therefore ra. The logistic manager usually sets these up depending on the contracts signed with the carriers.

Due to the relationship between each of these rating elements, they must be configured in the following order:

1. First, you must set up rating metadata and break masters.
1. Secondly, you must set up a rate base, which must be associated with only one break master.
1. Then, you must set up a rate base assignment, which is associated with only one rate base.
1. Then, you must set up a rate master, which can be associated with one or more rate base assignments and only one rating metadata.
1. Finally, you must set up a rating profile, which can be associated with only one rate master.

## Set up break master

Break masters are used as part of rate bases to define the pricing structure and its breakpoints. The pricing structure uses tiered pricing that is based on physical dimensions. If the shipping carrier charges a certain rate per uit of distance or weight for example, the break master can be used to reflect this in the rate base.

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Break master**.   
1. Select **New**.
1. In the **Break master** field, enter a value.
1. In the **Name** field, enter a value.
1. In the **Data type** field, select the data type.
1. In the **Comparison** field, enter the kind of comparison requested (using operators).
1. In the **Break unit** field, enter the break unit.
1. In the **Details** section, create as many breaks as needed for the pricing structure.
1. Select **Save**.

## Set up rate base

The rate base determines the rate of the carrier, and can be used to set up a tariff structure as it structures the rates in the breakpoints defined in the break master.  

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**. Select **Rate base** in the navigation pane at the top of the form.
1. Select **New**.
1. In the **Rate base** field, type a value.
1. In the **Name** field, type a value.
1. In the **Break master** field, select the drop-down button to open the lookup.  
1. In the list, select the link in the highlighted row.
1. Expand the **Details** section.
1. Select **New**.
1. In the **Drop-off Postal Code From** field, type a value.
1. In the **Drop-off Postal Code To** field, type a value.
1. In the **Drop-off Country Region** field, type a value.
1. Depending on the selection of the break master, type a value to represent the rate per break master. For example, if the break master is weight, the unit is pounds, and the break master has been set up at 5 pound intervals, insert the rate for if the total weight of the load is less than 5, 10, 15 pounds and so on.  
1. Select **Save**.

## Set up rate master and assign rate bases

Rate masters represent carrier rates. Each rate master can have multiple rate base assignments, which define different price points for each carrier depending on destinations, services or different rate bases. 

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Rate master**.
1. Select **New**.
1. In the **Rate master** field, type a value.
1. In the **Name** field, type a value.
1. In the **Rating metadata ID** field, select the drop-down button to open the lookup. The rating metadata ID determines the data needed for the rate master, as it defines the metadata expected by the transportation management engine using this rate master.  
1. In the list, select the link in the selected row.
1. Expand the **Rate base assignments** section.
1. Select **New**.   
1. In the **Name** field, type a value.
1. In the **Rate base** field, select the drop-down button to open the lookup.
1. In the list, select the link in the highlighted row.
1. In the **Service** field, select the drop-down button to open the lookup.
1. In the list, find and select the desired record.
1. In the list, select the link in the highlighted row.
1. In the **Pick-up Postal Code** field, type a value. Specify which postal code this rate base assignment should be valid from.
1. In the **Pick-up Country Region** field, type a value.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
