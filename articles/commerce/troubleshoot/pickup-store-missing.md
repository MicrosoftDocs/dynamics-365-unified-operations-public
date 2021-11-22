---
# required metadata

title: Retail store doesn't appear in the list of stores to pick up from
description: This topic provides troubleshooting guidance that can help when a retail store doesn't appear in the list of stores where items can be picked up.
author: Reza-Assadi
ms.date: 03/11/2021
ms.topic: Troubleshooting
ms.prod: 
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

This topic provides troubleshooting guidance that can help when a retail store doesn't appear in the list of stores where items can be picked up.

## Description

A retail store doesn't appear in the list of stores where items can be picked up.

## Resolution

### Configure the longitude and latitude for the store address in Commerce headquarters

To configure the longitude and latitude for the store address in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Stores \> All stores**.
1. Find the store that you want to appear among the pickup options on the e-commerce site. Make a note of its **Operating unit number** value.
1. Go to **Organization administration \> Organizations \> Operating units**.
1. Search for the operating unit number that you noted earlier, and then select the operating unit in the search results.
1. On the **Addresses** FastTab, select **More options**, and then select **Advanced**.
1. On the **General** FastTab, make sure that the **Longitude** and **Latitude** fields are correctly set. As part of this step, make sure that the values are correctly specified as positive or negative numbers.

### Configure fulfillment groups in Commerce headquarters

To configure fulfillment groups in Commerce headquarters, follow these steps.

1. Go to **Retail and Commerce \> Channels \> Online stores**.
1. Select the online store to configure.
1. On the Action Pane, select **Set up**, and then select **Fulfillment group assignment**.
1. On the **Fulfillment group assignment** page, select the fulfillment group for the online store.
1. Under **Setup**, make sure that the retail store is correctly configured for the fulfillment group.

## Additional resources 

[Create an operating unit](../../fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit.md)

[Set up an online channel](../channel-setup-online.md)