---
title: Enable camera-based product identification in Store Commerce
description: Learn how to use a sample Commerce Runtime (CRT) extension to enable camera-based product identification in Microsoft Dynamics 365 Commerce point of sale (POS), using Azure Custom Vision or any preferred vision model.
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 12/3/2025
ms.reviewer: 
ms.custom: 
  - bap-template
---

[!INCLUDE[banner](../includes/banner.md)]

# Enable camera-based product identification in Store Commerce

This article explains how to use a sample Commerce Runtime (CRT) extension to enable camera-based product identification in Microsoft Dynamics 365 Commerce point of sale (POS), using Azure Custom Vision or any preferred vision model.

The sample CRT extension shows how to enable camera-based product identification in the Dynamics 365 Commerce Store Commerce app. It introduces a CRT extension that lets you trigger image-based recognition from any POS surface area, including transaction pages, search screens, and inventory workflows.

## What the sample CRT extension does

The sample CRT extension does the following things:

- Adds a camera button near the search screen.
- Captures a product image and sends it to a vision model endpoint.
- Receives the product identifier and inserts it into the commerce flow.
- Renders a list of matches if multiple products are returned and allows users to select the correct product before adding it.
  
While the sample integrates with Azure Custom Vision to help you get started quickly, it's fully model-agnostic. You can train your catalog images with any preferred vision model and configure the API endpoint in the extension to call into it for product recognition.

## Sample location

You can access the sample CRT extension at [Product recognition sample](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.56/src/StoreCommerceSamples/Solutions/ProductRecognition).

## How the sample CRT extension works

The sample CRT extension works in the following ways:

- User adds a camera button to the POS or search page.
- User snaps a photo of the product.
- The CRT extension sends the image to the configured model endpoint.
- The model returns one or more product identifiers (IDs).
- If multiple matches are found, the sample displays a list for user selection.
- The selected item is inserted into the transaction or search flow.

## Use cases

The sample CRT extension has the following use cases:

- **POS transactions**: Quickly look up a product without typing or scanning.
- **Inventory counting**: Walk the aisle and capture product images for faster stock checks.
- **Price audits**: Snap a product image to verify catalog price against shelf tags.
- **Kiosks and self-service**: Enable customers to find products or similar items by taking a photo.
- **AI-powered discovery**: Go beyond identification—call APIs to find similar products, suggest alternatives, or recommend complementary items.


[!INCLUDE[footer-include](../includes/footer-banner.md)]
