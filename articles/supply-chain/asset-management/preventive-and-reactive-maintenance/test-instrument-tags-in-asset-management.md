---
title: Test instrument tags in asset management
description: Learn about define test instrument tags that links physical test instruments to an asset.
author: johanhoMSFT
ms.author: johanho
ms.reviewer: kamaybac
ms.search.form:
ms.topic: how-to
ms.date: 10/08/2025
ms.custom: 
  - bap-template
---

# Test instrument tags in asset management

[!include [banner](../../includes/banner.md)]

A test instrument tag represents the physical test instrument and also links to the test instrument asset in asset management.

Follow these steps to create a test instrument tag with an asset assigned:

1. Go to **Inventory management > Setup > Quality control > Test instruments** to open the test instruments page.
2. Select or create a test instrument type record where an asset type is assigned.
3. On the Action Pane, select **Test instrument tags** to create a test instrument tag.
4. Click new, and make the following settings:
    - **Tag number** – Enter a unique name, number, or code for the instrument.
    - **Test instrument type** – The field is pre-filled with the test instrument type in context.
    - **Asset** – Select the asset representing the test instrument that require scheduled calibration in asset management.
    - **Usage increment** – If the field Fixed increment counter type is set on the related instrument type record, then this field is incremented each time a quality order is validated with the increment specified in the field Usage increment, on the related instrument type record.
