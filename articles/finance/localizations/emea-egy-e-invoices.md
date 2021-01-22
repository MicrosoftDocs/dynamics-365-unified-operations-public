---
# required metadata

title: Customer electronic invoices in Egypt
description: This topic explains how to configure and submit customer electronic invoices in Egypt.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 01/22/2021
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form:  
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: Core, Operations
# ms.tgt_pltfrm: 
ms.custom: 547940
ms.search.region: Egypt
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-02-01
ms.dyn365.ops.version: 10.0.17

---

# Customer electronic invoices in Egypt

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In some countries, there is a legal requirement.

## Prerequisites

In the Feature management workspace, turn on the **Archive printed customer invoices with hash numbers** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Configure customers master data
Complete the following steps to configure customers data in order to activate automatic saving of printed invoices as attachments.

1. Go to **Accounts receivable** > **All customers** 
2. Select a specific customer
3. On the **Invoice and delivery** FastTab > in the **E-INVOCE** section, select **Yes** in the **eInvoice attachment** field.

## Print invoices
Post and print any Customer/Freetext/Project invoice for the customer configured in the previous step.
Go to...

![Posting date control](media/emea-ita-post-date-control.jpg)

> [!NOTE]
> For some countries, .
