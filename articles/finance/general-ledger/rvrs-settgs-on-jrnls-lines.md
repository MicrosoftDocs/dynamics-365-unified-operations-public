---
# required metadata

title: Reverse settings on journals and lines 
description: This topic addresses why a reversing entry that was entered on a general journal might not be included on the posted transaction. 
author: kweekley
ms.date: 04/29/2021
ms.topic: index-page
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: roschlom
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Global 
# ms.search.industry: 
ms.author: kweekley
ms.search.validFrom: 2021-5-05
ms.dyn365.ops.version: 10.0.14

---

# Reverse settings on journals and lines

[!include [banner](../includes/banner.md)]

This topic addresses why a reversing entry that was entered on a general journal might not be included on the posted transaction.  

## Symptom

A general journal includes a reversing entry and reversing date on the journal. When you post the journal, none of the vouchers are reversed. Why does this happen?

## Resolution

When the journal is posted, the reversing process looks only at the **Revering entry** and **Reversing date** settings on the **Lines** section of the voucher. This approach allows a journal to include some vouchers that are marked for reversing, and others that are not.

The values from the journal are only used as defaults when adding *new* lines. Changing the values on the journal doesn’t affect existing lines. In this example, the voucher lines were entered first. When you enter the line detail before designating the journal as reversing, the designation as a reversing entry and date won't be applied to any existing lines.

Changing the reversing entry or reversing date on an existing line propagates that change to other lines in the same voucher. To optimize performance, the grid is not refreshed after propagating changes to other Lines. You can display the updated values by refreshing the grid.


