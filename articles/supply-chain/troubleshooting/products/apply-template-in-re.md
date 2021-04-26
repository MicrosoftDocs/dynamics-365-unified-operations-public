---
title: Can't apply a template to a released product
description: Can't apply a template to a released product 
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

# Can't apply a template to create a released product

KB Number: 4612097

## Symptoms

When you are creating a new released product using the **New released product** dialog box, you are able to select a template, which is supposed to provide default settings for many of the fields for the new released product. However, some or all of the fields are not populated after selecting the template.

## Cause

Many pages of Supply Chain Management provide the ability to create a template to establish initial settings for the type of records shown by that page. You can create these templates by selecting **Record info** from the **Options** tab on the Action Pane. However, released products are much more complex than most other types of records, so you can't use these templates for products. Instead, you must create dedicated product templates.

The system will allow you to create record-info templates for the **Released products** page, and will also allow you to select those templates when creating a released product. However, record-info templates won't provide the field values you may be expecting for the new released product. Create and select product templates instead.

## Resolution

To create a product template, use the command on the **Product** tab of the Action Pane, not the **Record info** functionality. To create a product template:

1. Go to **Product information management \> Products \> Released products**.
1. On the Action Pane, open the **Product** tab and, from the **New** group, select either **Template \> Create personal template** or **Template \> Create shared template** as needed.
