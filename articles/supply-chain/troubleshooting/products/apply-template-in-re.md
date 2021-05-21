---
title: You can't apply a template to a released product
description: You can't apply a template to a released product.
author: t-benebo
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: EcoResProductDetailsExtended
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: myvakalo
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# You can't apply a template to create a released product

KB number: 4612097

## Symptoms

When you create a new released product by using the **New released product** dialog box, you can select a template. The template is supposed to provide default settings for many fields of the new released product. However, some or all of the fields aren't set after you select the template.

## Cause

Many pages in Microsoft Dynamics 365 Supply Chain Management let you create a template that establishes initial settings for the records that are shown on those pages. You can create one of these templates by selecting **Record info** on the **Options** tab of the Action Pane. However, released products are much more complex than most other types of records. Although you can select **Record info** on the **Released products** page to create a template, and although you can select that template when you create a released product, the template won't provide the expected field values for the new released product. Therefore, you can't use "record info" templates for released products. Instead, you must create dedicated product templates.

## Resolution

To create a product template, use the **Template** menu on the **Product** tab of the Action Pane, not the **Record info** button on the **Options** tab.

1. Go to **Product information management \> Products \> Released products**.
1. On the Action Pane, on the **Product** tab, in the **New** group, select **Template**, and then select either **Create personal template** or **Create shared template**, as appropriate.
