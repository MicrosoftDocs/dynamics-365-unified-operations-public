---
# required metadata

title: Tax plafond
description: Tax plafond.
author: ilkond
manager: AnnBe
ms.date: 11/13/2019
ms.topic: article
ms.prod: plafond
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
ms.search.validFrom: 2020-06-01
ms.dyn365.ops.version: 10.0.9

---

# Tax plafond

[!include [banner](../includes/banner.md)]

Companies in Italy which engage in resale activities outside of Italy can be exempt from VAT under tax plafond arrangement.
VAT exempt under plafond arrangement can be provided for companies fulfilling the following conditions:
 - Company must be considered as usual exporter.
 - Company must release an intent letter to vendor, in which status of usual exporter is declared.

This topic describes how to:
 - Set up the system to use **Tax plafond** feature;
 - Work with **Tax plafond** and **Intent letter**;
 - Report Tax payments including tax plafond information.


## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, turn on the **Tax plafond** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Set up

In **Accounts payable** > **Setup** > **Accounts payable parameters** > **Number sequences** fast tab specify number sequences for:
 - Plafond number;
 - Intent letter number.

In **Accounts payable** > **Setup** > **Accounts payable parameters** > **Intent letters - Telematic model** fast tab specify the reference to Intent letter telematic model configuration.

## Use...

### Post

When you post...

> [!NOTE]
> Warning...
