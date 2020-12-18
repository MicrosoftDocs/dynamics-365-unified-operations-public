---
# required metadata

title: Unified posting date control
description: This topic explains how to configure chronology control for invoices posting dates.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 12/18/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  NumberSequenceGroup
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 537707
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-03-15
ms.dyn365.ops.version: 10.0.17

---

# Unified posting date control

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

This article explains how to configure chronology control for invoices posting dates. 

## Prerequisites

- The primary address of the legal entity must be in Italy.
- Italian sales tax books and sections are configured in the system. For more information, see [Italian sales tax books](https://docs.microsoft.com/en-us/dynamics365/finance/localizations/emea-ita-fiscal-books).
- In the Feature management workspace, turn on the **(Italy) Unified posting date control** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure posting date control

In **Tax** > **Setup** > **Sales tax** > **Italain sales tax book sections**, in the colulmn **Skip posting date control**, select a required option for a selected sales tax book section.

![Posting date control](media/emea-ita-post-date-control.jpg)

 - If **turned off** (default option) – then the system will forbid posting of new invoices with dates earlier than the date of the latest posted invoice. The exception is for Customer invoices and Free text invoices - to enable posting, a reason code must be entered either in an invoice/order header or in one of the lines. 
 - If **turned on** – then the system allows posting with any date.

## Documents posting
When you post a document, the system performs document posting date control:

### Reason codes for customer invoices

- 
 -A warning is raised if the new invoice date is later than the system date.


> [!NOTE]
> For some ...
