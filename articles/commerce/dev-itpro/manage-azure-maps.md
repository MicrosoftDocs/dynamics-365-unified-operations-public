---
title: Manage Azure Maps for your organization (preview)
description: Learn how to manage Microsoft Azure Maps in Dynamics 365 Commerce.
author: ritakimani1
ms.date: 01/27/2025
ms.topic: how-to
ms.reviewer: v-chrgriffin
ms.search.region: Global
ms.author: ritakimani
ms.search.validFrom: 2025-01-15
ms.search.industry: Retail
ms.search.form: RetailSharedParameters
ms.custom: 
  - bap-template
---

# Manage Azure Maps for your organization (preview)

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes how to manage Microsoft Azure Maps in Dynamics 365 Commerce.

When Azure Maps is enabled in Commerce headquarters, you can use it with the Commerce distributed order management (DOM) feature.

## Enable Azure Maps

To enable Azure Maps, follow these steps.

1. In headquarters, go to **Commerce shared Parameters** \> **Azure Maps**.
1. Select **Enable Azure Maps** to turn on Azure Maps functionality.

## Enter an Azure Maps key

> [!NOTE]
> Learn how to obtain an Azure Maps key on the [Azure Maps pricing](https://azure.microsoft.com/pricing/details/azure-maps/) page and in [Manage authentication in Azure Maps](/azure/azure-maps/how-to-manage-authentication).

To enter an Azure Maps key, follow these steps.

1. In headquarters, go to **Commerce shared Parameters** \> **Azure Maps**.
1. In the **Azure Maps Key** field, enter the license key.

## Privacy notice

If you enable the Azure Maps feature, address information is automatically sent over the internet to the Azure Maps service, so that an online map of the address can be shown in the application. Your use of Azure Maps is governed by the [Azure Maps Terms of Use](https://azure.microsoft.com/support/legal/). Learn about Azure Map's geographic scope and how to limit data residency in [Consent management](/azure/azure-maps/consent-management).

Administrators can turn the Azure Maps feature on or off in headquarters at **Commerce shared Parameters** \> **Azure Maps**. Turning the Azure Maps app off makes the feature unavailable in Commerce.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
