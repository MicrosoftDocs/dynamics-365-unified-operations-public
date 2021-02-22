---
# required metadata

title: Retail store doesn't display when pickup in store selected
description: This topic provides troubleshooting for when a retail store doesn't appear in the list of stores to pick up from. 
author: Reza-Assadi
manager: AnnBe
ms.date: 02/17/2021
ms.topic: Troubleshooting
ms.prod: 
ms.service: dynamics-365-retail
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application user
# ms.devlang: 
ms.reviewer: josaw
# ms.tgt_pltfrm: 
ms.custom: 
ms.assetid: 
ms.search.region: Global
ms.search.industry: Retail
ms.author: rassadi
ms.search.validFrom: 2021-01-31
ms.dyn365.ops.version: 10.0.18

---

# Retail store doesn't display when pickup in store selected

[!include [banner](../../includes/banner.md)]

## Description
A retail store that's configured for pickup scenarios isn't displayed in the results when stores are searched for.

## Resolution

### Configure longitude and latitude for the store address 

1. Go to Dynamics 365 Commerce headquarters.

1. Go to **Commerce > Channels > Stores > All stores**.

1. Select the store that you want to be displayed in the pickup scenarios on e-commerce site.

1. Make a note of the value set in the **Operating unit number** field.

1. Go to **Organization administration > Organizations > Operating units**.

1. Search for the operating unit number that you noted previously. and select the operating unit in the search results list.

1. On the **Addresses** tab, select **More options** and then select **Advanced**.

1. On the **General** tab, make sure the **Longitude** and **Latitude** are set correctly. Check the sign of the value as well.

### Configure fulfillment groups

1. Go to Commerce headquarters.

1. Go to **Retail and Commerce > Channels > Online stores**.

1. Select the online store that you want to configure.

1. In the top navigation, select the **Set up** menu, and then select **Fulfillment group assignment**.

1. On the **Fulfillment group assignment** page, select the fulfillment group for the online store.

1. Under **Setup**, make sure the retail store is configured correctly for the fulfillment group.

## Additional resources 
- [Create an operating unit](https://docs.microsoft.com/en-us/dynamics365/fin-ops-core/fin-ops/organization-administration/tasks/create-operating-unit)
- [Set up an online channel](../channel-setup-online.md)







