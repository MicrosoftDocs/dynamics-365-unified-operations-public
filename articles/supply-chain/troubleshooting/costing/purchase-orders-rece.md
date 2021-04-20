---
title: Physically received purchase orders don't appear in the inventory closing report
description: Physically received purchase orders don't appear in the "Check open quantities" inventory closing report.
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

# Physically received purchase orders don't appear in the inventory closing report

KB Number: 4612595

## Symptoms

Physically received purchase orders don't appear in the *Check open quantities* inventory closing report.

## Resolution

The *Check open quantities* report shows issue transactions that can't be covered by financial on-hand. You can also choose to include receipts in the report. Physical receipts will only be shown if they can cover the issues that can't be covered by financial on-hand. For more information ,see [Preparing to run inventory close](/dynamicsax-2012/appuser-itpro/preparing-to-run-inventory-close).
