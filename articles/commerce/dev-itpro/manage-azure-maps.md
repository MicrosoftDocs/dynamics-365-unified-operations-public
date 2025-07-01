---
title: Manage Azure Maps for your organization
description: Learn how to manage Microsoft Azure Maps in Dynamics 365 Commerce.
author: ritakimani1
ms.date: 04/01/2025
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

When Azure Maps is enabled in Commerce headquarters, you can use it with the Commerce distributed order management (DOM) feature and Store Commerce app.

> [!NOTE]
> Azure Maps is only available for DOM in the Commerce 10.0.43 release. Azure Maps will be made available for store locator functionality in Commerce and the Store Commerce app in version 10.0.45. To use Azure Maps in version 10.0.44, contact Microsoft Support.

## Enable Azure Maps

To enable Azure Maps, follow these steps.

1. In headquarters, go to **Commerce shared Parameters \> Azure Maps**.
1. Select **Enable Azure Maps** to turn on Azure Maps functionality.

## Enter an Azure Maps key

> [!NOTE]
> You must obtain your own Azure Maps license and key. For information on how to obtain an Azure Maps license and key, see [Azure Maps pricing](https://azure.microsoft.com/pricing/details/azure-maps/) and [Manage authentication in Azure Maps](/azure/azure-maps/how-to-manage-authentication).

To enter an Azure Maps key, follow these steps.

1. In headquarters, go to **Commerce shared Parameters \> Azure Maps**.
1. In the **Azure Maps Key** field, enter the license key.

## Security

To manage your Azure Maps key securely, rotate it frequently. Learn more in [Manage and rotate shared keys](/azure/azure-maps/how-to-manage-authentication#manage-and-rotate-shared-keys).

## Privacy notice

If you enable the Azure Maps feature, address information is automatically sent over the internet to the Azure Maps service, so that an online map of the address can be shown in the application. Your use of Azure Maps is governed by the [Azure Maps Terms of Use](https://azure.microsoft.com/support/legal/). Learn about Azure Map's geographic scope and how to limit data residency in [Consent management](/azure/azure-maps/consent-management).

Administrators can turn the Azure Maps feature on or off in headquarters at **Commerce shared Parameters \> Azure Maps**. Turning the Azure Maps app off makes the feature unavailable in Commerce.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
