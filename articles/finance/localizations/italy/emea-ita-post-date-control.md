---
title: Unified posting date control
description: Learn how to configure chronology control for invoices posting dates, including prerequisites and an outline on configuring posting date control.
author: mrolecki
ms.author: mrolecki
ms.topic: article
ms.date: 02/01/2021
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 2021-03-15
ms.search.form: NumberSequenceGroup
ms.dyn365.ops.version: 10.0.17
---

# Unified posting date control

[!include [banner](../../includes/banner.md)]


This article explains how to configure chronology control of invoices posting dates within a specific sales tax book section.

## Prerequisites

- The primary address of the legal entity must be in Italy.
- Italian sales tax books and sections are configured in the system. For more information, see [Italian sales tax books](emea-ita-fiscal-books.md).
- In the Feature management workspace, turn on the **(Italy) Unified posting date control** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure posting date control
Complete the following steps to configure posting date control.

1. Go to **Tax** > **Setup** > **Sales tax** > **Italian sales tax book sections**. 
2. In the **Skip posting date control** column, select whether posting date control is required for a selected sales tax book section.

![Posting date control.](../media/emea-ita-post-date-control.jpg)

 - If the field isn't enabled, which is the default option, the system doesn't allow posting of new invoices with dates earlier than the date of the latest posted invoice.  
 - If the field is enabled, the system allows posting with any date.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
