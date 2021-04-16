---
title: Flushing principle settings on BOM lines aren't respected
description: Flushing principle settings on BOM lines aren't respected
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
<!-- KFM: Please review and confirm this edit. I added details that weren't clear in the original. -->
# Flushing principle settings on BOM lines aren't respected

KB Number: 4612725

## Issue description

This issue occurs when the **Automatic BOM consumption** setting (on the **Automatic update** tab of the **Production control parameters** page) is set to *Flushing principle*. This setting means that all bill of material (BOM) lines should automatically be consumed when a purchase order is received. However, you would expect that BOM lines with **Flushing principle** explicitly set to *Manual* should not be auto-consumed (by definition), but when this issue occurs, BOM lines set to *Manual* are still auto-consumed anyway.

## Resolution

If you are seeing this behavior, it could be because your production control parameters are set to override the **Flushing principle** setting on BOM lines. To find out, open the **Automatic update** tab of the **Production control parameters** page and then check the **Automatic BOM consumption** setting. If this is set to *Always*, then the system will disregard the **Flushing principle** set on all BOM lines and will instead always flush them. Change this setting to *Flushing principle* to instead respect the flushing principle setting for each BOM line.
