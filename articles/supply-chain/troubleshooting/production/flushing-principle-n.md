---
title: Flushing principle settings on BOM lines aren't respected
description: Flushing principle settings on bill of materials (BOM) lines aren't respected.
author: johanhoffmann
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: PurchTable,ProdParameters
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: johanho
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Flushing principle settings on BOM lines aren't respected

KB number: 4612725

## Symptoms

This issue occurs when the **Automatic BOM consumption** field on the **Automatic update** tab of the **Production control parameters** page is set to *Flushing principle*. This setting indicates that all bill of materials (BOM) lines should automatically be consumed when a purchase order is received. If the **Flushing principle** field on BOM lines is explicitly set to *Manual*, you might expect that the BOM lines won't automatically be consumed. However, when this issue occurs, BOM lines where the **Flushing principle** field is set to *Manual* are automatically consumed anyway.

## Resolution

If you're experiencing this issue, your production control parameters might be set up to override the **Flushing principle** setting on BOM lines. On the **Production control parameters** page, on the **Automatic update** tab, check the value of the **Automatic BOM consumption** field. If it's set to *Always*, the system will disregard the **Flushing principle** setting on all BOM lines and will always flush the lines. To make the system respect the **Flushing principle** setting on BOM lines, change the value of the **Automatic BOM consumption** field to *Flushing principle*.
