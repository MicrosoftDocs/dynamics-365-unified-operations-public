---
title: Imported purchase orders show incorrect line numbers
description: When purchase orders are imported through data management, purchase order line numbers don't follow the increment defined in system parameters
author: kamaybac
ms.date: 05/31/2021
ms.topic: troubleshooting
ms.search.form: PurchTable, PurchTablePart
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: yanansong
ms.search.validFrom: 2021-05-31
ms.dyn365.ops.version: 10.0.13
---

# Imported purchase orders show incorrect line numbers

## Symptoms

By default, automatically generated line numbers for purchase order lines that are imported through the *Purchase order lines V2* data entity don't use the system line number increment that is specified in system parameters. If you manually create a purchase order and add lines through the user interface (UI), the line numbers are incremented correctly. However, if you use the data management framework (DMF), they aren't incremented correctly.

This issue occurs because, when you import lines via DMF, if line numbers aren't already assigned in the imported entity, the system uses DMF's method for assigning them. That method always increments line numbers by one.

## Workaround

Make sure that the desired line numbers are already given in the data entity line number fields when you import the purchase order lines. In this case, DMF won't overwrite the line numbers.
