--- 
# required metadata 
 
title: Rating profiles
description: This procedure shows how to set up data for a rating profile. 
author: Henrikan
manager: 
ms.date: 10/30/2020
ms.topic: business-process 
ms.prod: 
ms.service: dynamics-ax-applications 
ms.technology: 
 
# optional metadata 
 
ms.search.form: TMSRatingProfile
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
ms.dyn365.ops.version: Version 7.0.0 
---

# Rating profiles

A rating profile is similar to a logistics contract (though not a legal contract).

A rating profile is used to determine transportation tariffs for loads. A rating profile is used to associate the shipping carrier with a rate master. The rate master defines the rate base assignment and the rate base. The rate base determines the rate of the carrier.

A rating profile is unique for a shipping carrier. You can set up a rating profile using a generic page, which has an overview of all existing rating profiles. You can also set up the rating profile directly from the shipping carrier. The information that you set up for the rating profile is the same, regardless of how you access the setup.

## Create or edit a rating profile from the Rating profile page

To review all available rating profiles and create a new one using a setup page, follow these steps:

1. Go to **Transportation management \> Setup \> Rating \> Rating profile**.
1. Select **New** on the Action Pane to add a new rating profile to the grid, or select **Edit** to edit an existing profile.
1. Make the following settings for a new or selected row:
    - **Rating profile** - Enter a unique identifier (ID) for the profile.
    - **Name** - Enter a descriptive name for the rating profile.
    - **Shipping carrier** - Select a shipping carrier. The profile you are setting up will also be shown on the **Shipping carriers** page for the selected carrier.
    - **Site**, and **Warehouse** - Select a site, and warehouse, respectively.
    - **Rate engine** - Select the rate engine that you want to use for the rating profile.
    - **Rate master** - Select the rate master that you want to use for the rating profile. You can use the rate master to define a rate base type and a rate base. For more information, see [Set up rate masters](https://docs.microsoft.com/en-us/dynamics365/supply-chain/transportation/tasks/set-up-rate-masters).
    - **Transit time engine** - Select the transit time engine for the rating profile.
    - **Carrier fuel index** - Select the carrier fuel index for the rating profile.
    - **Effect start date and time** and **Effective end date and time** - Establish the time span where the rating profile should be active.
1. Select **Save** on the Action Pane.

## Create a rating profile directly from the Shipping carriers page

To create a rating profile directly from the **Shipping carriers** page, follow these steps:

1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. Select a shipping carrier from the list pane.
1. On the **Rating profile** FastTab toolbar, select **New** to create a rating profile.
1. Fill out the fields for the new rating profile. These fields correspond to the settings on the **Rating profile** page, as described previously in this topic.

> [!NOTE]
> Profiles created from the **Shipping carriers** page are also shown on the **Rating profile** page.
