---
# required metadata

title: References to original invoices in credit notes
description: This topic explains how to set up and print original invoice numbers in credit notes.
author: ilkond
manager: AnnBe
ms.date: 01/11/2021
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
ms.search.region: Global
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2021-03-19
ms.dyn365.ops.version: 10.0.17

---

# References to original invoices in credit notes

[!include [banner](../includes/banner.md)]

[!include [banner](../includes/preview-banner.md)]

In some countries, there is a legal requirement to print the references to original invoices in related credit notes. 
This topic explains how to set up and print the references to original invoices in credit notes.

## Prerequisites

- In the **Feature management** workspace, turn on the **Credit invoicing layout for sales and project invoice reports** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).
- The printable formats of required documents are preliminary configured in Print management.

The functionality is applicable to the following documents:

**Accounts receivable**
- Customer credit note
- Free text credit note

**Project management**
- Project credit note

## Configure Accounts receivable parameters

Complete the following steps to activate printing of the references to original invoices in related credit notes:

1. Go to **Accounts receivable** > **Setup** > **Accounts receivable parameters** > **Updates** Tab > **Invoice** FastTab. 
2. In the **Apply credit invoicing layout into sales and project invoice reports** field, select **Yes** to activate printing of the references to original invoices in related credit notes.

![Set up AR parameters](media/original-invoice-number-in-credit-note.jpg)

## Define references to original invoices

![Define rederences for FTI](media/reference-original-invoice-FTI.jpg)

## Print invoices
Create and print any Customer/Free text/Project invoice for the customer configured in the previous step.
Go to...
![Credit note prinout](media/credit-note-FTI.jpg)

> [!NOTE]
> Make sure that documents printable formats are properly configured and assume printing of the references to original invoices.

