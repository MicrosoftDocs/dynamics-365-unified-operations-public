---
# required metadata

title: Reverse settings on journals and lines 
description: This topic describes 
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

This topic describes

## Question

The General journal I created includes a reversing entry and reversing date on the journal. When I posted the journal, none of the vouchers were reversed. Why?

## Answer

When the journal is posted, the reversing logic only looks at the **Revering entry** and **Reversing date** settings on the **Lines** section of the voucher. This allows a journal to have some vouchers marked for reversing, and others not.

The values from the journal are only used as defaults when adding *new* lines. Changing the values on the journal doesn’t affect existing lines. In this example, the voucher lines and were entered first, and then the Reversing entry and Reversing date were set on the journal. This doesn’t update the existing lines. 

Changing the reversing entry or reversing date on an existing line propagates that change to other lines in the same voucher. Note that to optimize performance, the grid is not refreshed after propagating changes to other Lines. If you refresh the grid or enter a record the updated values will be shown.


