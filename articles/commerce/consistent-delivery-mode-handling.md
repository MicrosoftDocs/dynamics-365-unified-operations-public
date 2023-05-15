---
title: Enable consistent delivery mode handling in e-commerce channels
description: This article describes how to enable consistent delivery mode handling to address possible issues that are related to charges flows in Microsoft Dynamics 365 Commerce e-commerce channels.
author: gvrmohanreddy
ms.date: 02/24/2022
ms.topic: article
audience: Application User, Developer, IT Pro
ms.reviewer: v-chgriffin
ms.search.region: Global
ms.author: gmohanv
ms.search.validFrom: 2022-02-10
---

# Enable consistent delivery mode handling in e-commerce channels 

[!include [banner](includes/banner.md)]

This article describes the impact of the feature **Enable consistent delivery mode handling in channel** and some of the recommended tests organizations should run to ensure their the system behavior meets their expectations.
  > [!NOTE]
  > This feature has been made mandatory since 10.0.31

This feature was originally created to resolve the issues related to charges calculation on e-commerce channels. For example, without this feature, the users could see one or both of the following issues in e-commerce channels:
- Non-prorated header-level charges don't appear.
- Charges for delivery modes aren't consistent between the mode of delivery selection and the checkout order summary.

Additionally, this feature unifies the logic for handling the pickup and ship mode of deliveries for a customer order. With this feature enabled, the pickup order lines use the selected store's main warehouse, whereas, the ship order lines use the store's shipping warehouse. We recommend performing the following tests to validate the system behavior meets your expectations.

1. [Ecommerce test] Create an e-commerce shipping order and validate the warehouse at the header and lines.
2. [Ecommerce test] Create an e-commerce pick up order for a store and validate the warehouse at the header and lines. 
3. [Ecommerce test] Create an e-commerce order which contains both ship and pickup lines and make sure the order lines appear on the correct store selected for shipping and pickup as expected. For such orders, the header warehouse is not relevant as the lines are being fulfilled from different warehouses.
4. [POS test] Create a customer order on POS and choose ship all from a different store that uses different warehouses for shipping and pickup. Validate the warehouse at the header and lines.
5. [POS test] Create a customer order on POS and choose pick up all from a different store that uses different warehouses for shipping and pickup. Validate the warehouse at the order header and lines.
