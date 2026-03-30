---
title: Set up a carrier fuel index
description: Learn how to create a fuel index region, a fuel index, and a carrier fuel index, including step-by-step processes using the USMF demo data company. 
author: lisascholz91
ms.author: lisascholz
ms.reviewer: kamaybac
ms.search.form: TMSFuelIndexRegion,TMSCarrierFuelIndexTable,TMSFuelIndex
ms.topic: how-to
ms.date: 11/19/2025
ms.custom:
  - bap-template
---

# Set up a carrier fuel index

[!include [banner](../../includes/banner.md)]

This guide shows how to create a fuel index region, a fuel index, and a carrier fuel index. The fuel index region specifies which region the fuel index applies to, and the fuel index specifies a fuel price for a particular period of time. To reflect the change in fuel prices over time, you can associate multiple fuel indexes with a carrier. A transportation coordinator normally performs these tasks. You can use this procedure in demo data company *USMF* or with your own data.

## Create a fuel index region

First, you need to create the different regions where you operate and calculate different fuel surcharges by following these steps:

1. Go to **Transportation management** \> **Setup** \> **Fuel indexes** \> **Fuel index regions**.
1. Select **New**.
1. In the **Region** field, type a value.
1. In the **Name** field, type a value.
1. Select **Save**.

## Create a fuel index

For the regions you set up, enter the current prices for the fuel by following these steps:

1. Go to **Transportation management** \> **Setup** \> **Fuel indexes** \> **Fuel indexes**.
1. Select **New**.
1. In the **Region** field, select the region.
1. In the **Price per gallon** field, enter a number.
1. In the **Effective start date and time** field, enter a date and time.
1. Select **Save**.

## Create a carrier fuel index

1. Go to **Transportation management** \> **Setup** \> **Fuel indexes** \> **Carrier fuel indexes**.
1. Select **New**.
1. In the **Carrier fuel index** field, enter a value.
1. In the **Description** field, enter a value.
1. Select **New**.
1. In the **Effective start date and time** field, enter a date and time.
1. In the **PPG from** field, enter a number. If you're working with *USMF* sample data, enter *1.95*.  
1. In the **PPG to** field, enter a number. If you're working with *USMF* sample data, set the PPG To field to *2*.
1. In the **Percentage** field, enter a number. If you're working with *USMF* sample data, set the percentage to *3*.
1. In the **Currency** field, select the currency.
1. Select **Save**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
