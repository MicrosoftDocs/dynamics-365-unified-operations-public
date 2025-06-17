---
title: Associate a fuel index with a carrier as an accessorial charge
description: Learn how to create an accessorial assignment, accessorial master for fuel surcharge, and associate carrier fuel indexes with a carrier.
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSRatingProfile
ms.topic: how-to
ms.date: 06/17/2025
ms.custom: 
  - bap-template
---

# Associate a fuel index with a carrier as an accessorial charge

[!include [banner](../../includes/banner.md)]

This guide shows how to create an accessorial assignment, carrier accessorial charge, and accessorial master for fuel surcharge. It also shows how to associate a carrier fuel index with a carrier. A carrier fuel index must already exist before you run this guide (learn more in [Set up a carrier fuel index](set-up-carrier-fuel-index.md)). These setup tasks are typically done by a logistics manager.

## Create an accessorial master

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Accessorial masters**.
1. Select **New**.
1. In the **Accessorial master** field, type a value.
1. In the **Name** field, type a value.
1. Select **Save**.

## Create a carrier accessorial charge

1. Go to **Transportation management** \> **Setup** \> **Rating** \> **Carrier accessorial charges**.
1. Select **New**.
1. In the **Carrier accessorial ID** field, type a value.
1. In the **Shipping carrier** field, find and select the desired record.
1. In the **Carrier service** field, select the link in the selected row.
1. In the **Accessorial master** field, select the desired record.
1. Select **Save**.

## Create an accessorial assignment

1. Select **Accessorial assignments**.
1. Select **New**.
1. In the **Name** field, type a value.
1. Expand the **Criteria** FastTab. Here, you can choose to always apply the fuel surcharge or, for this example, choose that it only applies within a certain region.  
1. In the **ZIP/postal code from** field, type a value.
1. In the **ZIP/postal code to** field, type a value.
1. Expand the **Calculation** FastTab. Here, you can specify how to calculate the fuel surcharge. This calculation depends on the accessorial unit that you chose as the base for your calculation.  
1. In the **Accessorial fee type** field, select a fee type (such as *Fuel surcharge*).
1. In the **Accessorial unit** field, select a unit (such as *Mileage*).
1. In the **Region** field, select the link in the selected row.
1. Select **Save**.

## Update the carrier rating profile

1. Go to **Transportation management** \> **Setup** \> **Carriers** \> **Shipping carriers**.
1. In the list, find and select the desired record.
1. Expand the **Rating profiles** FastTab.
1. Select **Edit**.
1. In the **Carrier fuel index** field, select the link in the selected row.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
