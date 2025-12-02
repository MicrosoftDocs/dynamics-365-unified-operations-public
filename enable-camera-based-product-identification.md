---
title: Enable Camera-Based Product Identification in Store Commerce
description: Learn how to use a sample CRT extension to enable camera-based product identification in POS, leveraging Azure Custom Vision or any preferred vision model
author: anush6121
ms.author: anvenkat 
ms.topic: how-to 
ms.date: 12/2/2025
ms.reviewer: 
ms.custom: 
  - bap-template
---
## Overview
This sample demonstrates how to enable **camera-based product identification** in the Dynamics 365 Commerce Store Commerce app. It introduces a **Commerce Runtime (CRT) extension** that allows you to trigger image-based recognition from **any POS surface area**—including transaction pages, search screens, and inventory workflows

## What This Sample Does
- Adds a camera button near the search screen.
- Captures a product image and sends it to a vision model endpoint.
- Receives the product identifier and inserts it into the commerce flow.
- If multiple products are returned, the sample renders a list of matches and allows the user to select the correct product before adding it
  
**While the sample integrates with Azure Custom Vision to help you get started quickly, it’s fully model-agnostic—customers can train their catalog images with any preferred vision model and configure the API endpoint in the extension to call into it for product recognition.**

## Sample Location
[View the sample on GitHub](https://github.com/microsoft/Dynamics365Commerce.InStore/tree/release/9.56/src/StoreCommerceSamples/Solutions/ProductRecognition)

## How It Works
1. Add a camera button to the POS or search page.
2. Snap a photo of the product.
3. The extension sends the image to your configured model endpoint.
4. The model returns one or more product IDs.
5. If multiple matches are found, the sample displays a list for user selection.
6. The selected item is inserted into the transaction or search flow.

## Use Cases
- **POS transactions**: Quick product lookup without typing or scanning.
- **Inventory counting**: Walk the aisle and capture product images for faster stock checks.
- **Price audits**: Snap a product image to verify catalog price against shelf tags.
- **Kiosks & self-service**: Enable customers to find products or similar items by taking a photo.
- **AI-powered discovery**: Go beyond identification—call APIs to find similar products, suggest alternatives, or recommend complementary items.

---
