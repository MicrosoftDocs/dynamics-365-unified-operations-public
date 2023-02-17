--- 
# required metadata 
 
title: Rating profiles
description: This article describes how to set up data for rating profiles.
author: Weijiesa
ms.date: 10/30/2020
ms.topic: how-to 
ms.prod: 
ms.technology: 
 
# optional metadata 
 
ms.search.form: TMSRatingProfile
audience: Application User 
# ms.devlang: 
ms.reviewer: kamaybac
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global
ms.search.industry: Distribution
ms.author: weijiesa
ms.search.validFrom: 2020-10-30 
ms.dyn365.ops.version: AX 7.0.0 
---

# Rating profiles

[!include [banner](../../includes/banner.md)]

A rating profile resembles a logistics contract (but not a legal contract). It's used to determine transportation tariffs for loads. 

Each rating profile is unique to a shipping carrier. In the profile, you associate the shipping carrier with a rate master. The rate master defines the rate base assignment and the rate base. The rate base determines the rate of the carrier.

You can set up a rating profile by using a generic page that shows an overview of all existing rating profiles. Alternatively, you can set up a rating profile directly from the shipping carrier. In both cases, the information that you set up for the rating profile is the same.

## Create or edit a rating profile on the Rating profiles page

On the **Rating profiles** page, you can review all available rating profiles. You can also edit existing profiles and create new profiles.

1. Go to **Transportation management \> Setup \> Rating \> Rating profile**.
1. On the Action Pane, select **New** to add a new rating profile to the grid, or select **Edit** to edit an existing profile.
1. In the row for the new or existing rating profile, set the following fields:

    - **Rating profile** – Enter a unique identifier (ID) for the rating profile.
    - **Name** – Enter a descriptive name for the rating profile.
    - **Shipping carrier** – Select a shipping carrier. The rating profile that you're setting up will also be shown on the **Shipping carriers** page for the selected carrier.
    - **Site** and **Warehouse** – Select a site and warehouse.
    - **Rate engine** – Select the rate engine for the rating profile.
    - **Rate master** – Select the rate master for the rating profile. You can use the rate master to define a rate base type and a rate base. For more information, see [Set up rate masters](set-up-rate-masters.md).
    - **Transit time engine** – Select the transit time engine for the rating profile.
    - **Carrier fuel index** – Select the carrier fuel index for the rating profile.
    - **Effect start date and time** and **Effective end date and time** – Define the period when the rating profile should be active.

1. On the Action Pane, select **Save**.

## Create a rating profile directly on the Shipping carriers page

1. Go to **Transportation management \> Setup \> Carriers \> Shipping carriers**.
1. Select a shipping carrier in the list.
1. On the **Rating profiles** FastTab, select **New** to create a rating profile.
1. Set the fields for the new rating profile. These fields correspond to the fields on the **Rating profiles** page, as described in previous section of this article.

> [!NOTE]
> Profiles that are created on the **Shipping carriers** page are also shown on the **Rating profiles** page.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]