---
title: Document handling notes are not copied to direct delivery purchase orders 
description: Document handling notes aren't copied from an original sales order to its related direct delivery purchase order.
author: SmithaNataraj
ms.date: 4/11/2021
ms.topic: troubleshooting
ms.search.form: SalesTable, PurchTable
audience: Application User
ms.reviewer: kamaybac
ms.search.region: Global
ms.author: smnatara
ms.search.validFrom: 2021-04-11
ms.dyn365.ops.version: 10.0.19
---

# Document handling notes are not copied to direct delivery purchase orders

KB Number: 4611854

## Symptoms

Document handling notes aren't copied from an original sales order to its related direct delivery purchase order.

## Resolution

The system is behaving as designed. Notes are only copied across purchase and sales orders <!-- KFM: what do you mean by "across purchase and sales orders"?  --> for intercompany <!-- KFM: intercompany what? sales orders? -->. Notes are not copied in the context of direct delivery. <!-- KFM: Are "notes" and "document handling note" always the same thing? -->
