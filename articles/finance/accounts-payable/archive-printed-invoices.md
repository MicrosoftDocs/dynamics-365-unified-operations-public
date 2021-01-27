---
# required metadata

title: Archive printed customer invoices with hash numbers
description: This topic explains how to configure archiving of printed customer invoices with hash numbers.  
author: Ilya Kondratenko
manager: AnnBe
ms.date: 01/11/2021
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
ms.custom: 539093
ms.search.region: Global
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-03-05
ms.dyn365.ops.version: 10.0.18

---

# Archive printed customer invoices with hash numbers

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In some countries, there is a legal requirement to store culculated hash numbers in the system together with printed outputs of some documents. Hash numbers can be used then for reporting to authirities and during audits.
This topic explains how to configure archiving of printed customer invoices with hash numbers.

## Prerequisites

- In the Feature management workspace, turn on the **Archive printed customer invoices with hash numbers** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
- The printable formats of required documents are preliminary configured in Print management.

The functionality is applicable to the following documents:

**Accounts receivable**
- Customer invoice
- Customer credit note
- Free text invoice
- Free text credit note

**Project management**
- Project Invoice
- Project credit note

## Configure customers master data
Complete the following steps to configure customers data in order to activate automatic saving of printed invoices as attachments.

1. Go to **Accounts receivable** > **All customers** 
2. Select a specific customer
3. On the **Invoice and delivery** FastTab > in the **E-INVOCE** section, select **Yes** in the **eInvoice attachment** field.

## Print invoices
Post and print any Customer/Freetext/Project invoice for the customer configured in the previous step.
Go to...

![Attachment hash number](media/attach-hash-num.jpg)

> [!NOTE]
> For some countries, .
