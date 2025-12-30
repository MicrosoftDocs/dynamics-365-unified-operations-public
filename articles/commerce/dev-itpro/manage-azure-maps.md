---
title: Manage Azure Maps for your organization
description: Learn how to manage Microsoft Azure Maps in Dynamics 365 Commerce.
author: ritakimani1
ms.date: 11/13/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2025-01-15
ms.search.form: RetailSharedParameters
ms.custom: 
  - bap-template
---

# Manage Azure Maps for your organization

[!include [banner](../includes/banner.md)]

This article describes how to manage Microsoft Azure Maps in Dynamics 365 Commerce.

When you enable Azure Maps in Commerce headquarters, you can then use Azure Maps with the Commerce Distributed Order Management (DOM) feature, the store locator in Commerce e-commerce, and the Store Commerce app to allows customers to view a map of a store, warehouse, or other location when placing orders.

> [!NOTE]
> - Azure Maps is available for use with DOM starting with the Commerce version 10.0.43 release.
> - Azure Maps is available for use with the store locator in Commerce e-commerce and the Store Commerce app starting with the Commerce version 10.0.45 release.

## Enable Azure Maps

To enable Azure Maps, follow these steps:

1. In headquarters, go to **Commerce shared Parameters \> Azure Maps**.
1. Select **Enable Azure Maps** to turn on Azure Maps functionality.

## Enter an Azure Maps key

> [!NOTE]
> You must obtain your own Azure Maps license and key. For information on how to obtain an Azure Maps license and key, see [Azure Maps pricing](https://azure.microsoft.com/pricing/details/azure-maps/) and [Manage authentication in Azure Maps](/azure/azure-maps/how-to-manage-authentication).

To enter an Azure Maps key, follow these steps:

1. In headquarters, go to **Commerce shared Parameters \> Azure Maps**.
1. In the **Azure Maps Key** field, enter the license key.

## Security

To manage your Azure Maps key securely, rotate it frequently. Learn more in [Manage and rotate shared keys](/azure/azure-maps/how-to-manage-authentication#manage-and-rotate-shared-keys).

## Privacy notice

If you enable the Azure Maps feature, address information is automatically sent over the internet to the Azure Maps service, so that an online map of the address can be shown in the application. Your use of Azure Maps is governed by the [Azure Maps Terms of Use](https://azure.microsoft.com/support/legal/). Learn about Azure Map's geographic scope and how to limit data residency in [Consent management](/azure/azure-maps/consent-management).

Administrators can turn the Azure Maps feature on or off in headquarters at **Commerce shared Parameters \> Azure Maps**. Turning off the Azure Maps app makes the feature unavailable in Commerce.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
