---
# required metadata

title: Invoicing of packing slips
description: Invoicing of packing slips.
author: ilkond
manager: AnnBe
ms.date: 27/08/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: Italy
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-11-29
ms.dyn365.ops.version: 10.0.7

---

# Invoicing of packing slips

[!include [banner](../includes/banner.md)]

In Italy, companies often need to issue so-called accompanying invoices which combine an ordinary invoice with DDT (transposrt document or packing slip).
This topic explains how to set up and print accompanying invoices which also contain all the rquired packing slips details.
 
## Prerequisites

- The primary address of the legal entity must be in Italy.
- In **Feature management**, enable the feature, **Invoicing of packing slips**. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md)

## Accompanying invoices printing
No specific setup required. Once enabled with **Invoicing of packing slips** feature, the layout of invoice report will be changed from a standard to the layout that contains packing slips details.

The example of an invoice printout with packing slips details:
*...replace the picture below...*
![Clearing the main account](media/emea-ita-exil-separate-account-credit-pic2.JPG)

> [!NOTE]
> The new layout is applicable only to invoices that are based on sales orders. It isn't applicable to free-text invoices, because free-text invoices do not assume packing slips.

