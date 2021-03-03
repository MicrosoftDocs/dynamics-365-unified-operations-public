---
# required metadata

title: Retail store doesn't appear in the list of stores to pick up from
description: This topic provides troubleshooting guidance for when a retail store doesn't appear in the list of stores to pick up from. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/23/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: v-chgri
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Retail store doesn't appear in the list of stores to pick up from

[!include [banner](../../includes/banner.md)]

This topic provides troubleshooting information for when a retail store doesn't appear in the list of stores to pick up from. 

## Description

This topic provides troubleshooting guidance for when a retail store doesn't appear in the list of stores to pick up from.

## Resolution

### Configure longitude and latitude for the store address in Commerce headquarters

To configure longitude and latitude for the store address in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Find the store that you want to be displayed in the pickup options on the e-commerce site, and take note of the **Operating unit number** value.
1. Go to **Organization administration \> Organizations \> Operating units**.
1. Search for the operating unit number that you noted previously. and select the operating unit in the search results list.
1. On the **Addresses** FastTab, select **More options**, and then select **Advanced**.
1. On the **General** FastTab, ensure that the **Longitude** and **Latitude** values are set correctly, including whether they are positive or negative numbers.

### Configure fulfillment groups in Commerce headquarters

To configure fulfillment groups in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the online store that you want to configure.
1. On the Action Pane, select **Set up**, and then select **Fulfillment group assignment**.
1. On the **Fulfillment group assignment** page, select the fulfillment group for the online store.
1. Under **Setup**, ensure the retail store is configured correctly for the fulfillment group.

## Additional resources 

[Create an operating unit](https://docs.microsoft.com/dynamics365/fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit)

[Set up an online channel](../channel-setup-online.md)
