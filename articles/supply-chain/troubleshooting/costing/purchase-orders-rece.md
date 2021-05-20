---
title: Physically received purchase orders don't appear on the inventory closing report
description: Physically received purchase orders don't appear on the Check open quantities inventory closing report.
author: niwang
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: InventOpenQtyCritical
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Physically received purchase orders don't appear on the inventory closing report

KB number: 4612595

## Symptoms

Physically received purchase orders don't appear on the **Check open quantities** inventory closing report.

## Resolution

The **Check open quantities** report shows issue transactions that can't be settled against financially updated inventory receipts as of the selected closing date. You can choose to include physical receipts on the report. In that case, physical receipts will be shown if they can cover the issue transactions that can't be settled. For more information, see [Preparing to run inventory close](/dynamicsax-2012/appuser-itpro/preparing-to-run-inventory-close).
