---
title: Manage Azure Maps for your organization
description: This article describes how to manage Microsoft Azure Maps in Microsoft Dynamics 365 Commerce.
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

# Manage Azure Maps for your organization

[!include [banner](../includes/banner.md)]
[!include [banner](../includes/preview-banner.md)]

This article describes how to manage Microsoft Azure Maps in Microsoft Dynamics 365 Commerce.

When Azure Maps is enabled in Commerce headquarters, you can then use it with the Commerce distributed order management (DOM) feature. 

## Enable Azure Maps

To enable Azure Maps, follow these steps.

1. In Commerce headquarters, go to **Commerce shared Parameters \> Azure Maps**.
2. Select **Enable Azure Maps** to turn on Azure Maps functionality.

## Enter an Azure Maps key

> [!NOTE]
> For information about how to obtain an Azure Maps key, see [Azure Maps licensing page](https://azure.microsoft.com/pricing/details/azure-maps/) and [Azure Maps Authentication](/azure/azure-maps/how-to-manage-authentication).

To enter an Azure Maps key, follow these steps.

1. In Commerce headquarters, go to **Commerce shared Parameters \> Azure Maps**.
2. Enter the license key in the **Azure Maps Key** field.

## Privacy notice

If you enable the Azure Maps feature, address information is automatically sent over the internet to the Azure Maps service to display an online map of the address within the application. Your use of Azure Maps is governed by the [Azure Maps Terms of Use](https://azure.microsoft.com/support/legal/). For information on Azure Map's geographic scope and how to limit data residency, see [Azure Maps Consent Management](/azure/azure-maps/consent-management).
  
Administrators can turn the Azure Maps feature on or off in headquarters at **Commerce shared Parameters \> Azure Maps**. Turning Azure Maps app off makes the feature unavailable in Commerce.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]

