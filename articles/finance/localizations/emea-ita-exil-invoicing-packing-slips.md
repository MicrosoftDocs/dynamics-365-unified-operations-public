---
# required metadata

title: Sort sales invoice lines by packing slip
description: This topic explains how to set up and print accompanying invoices that include required packing slips details.
author: ilkond
manager: AnnBe
ms.date: 10/28/2019
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
ms.dyn365.ops.version: 10.0.8

---

# Sort sales invoice lines by packing slip

[!include [banner](../includes/banner.md)]

In Italy, companies must often issue *accompanying invoices*. Accompanying invoices are combinations of an ordinary invoice and a transport document or packing slip (documento di trasporto, or DDT).

## Prerequisites

- The primary address of the legal entity must be in Italy.
- In the **Feature management** workspace, verify that the **Sales invoice lines sorting by packing slips** feature is turned on. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).
- Customer invoices must use the new **SalesInvoice.Report\_IT** layout. Go to **Accounts receivable** /> **Setup** /> **Forms** /> **Form setup**, and then, on the **General** tab, select **Print management**. On the **Print management setup** page, under **Module - accounts receivable \> Customer invoice**, select **Original \<Default\>**. Then, in the **Report format** field, select **SalesInvoice.Report\_IT**.

    ![New layout selected for customer invoices](media/emea-ita-exil-invoice-packing-slip-pic2.jpg)

> [!NOTE]
> When the **Sales invoice lines sorting by packing slips** feature is turned on, the system ignores the setting of the **Print packing slip specifications** check box on the **Invoice** tab of the **Form setup** page (**Accounts receivable \> Setup \> Forms \> Form setup**). Even if this check box is selected, it's treated as if it's cleared.
>
> ![Print packing slip specifications check box](media/emea-ita-exil-invoice-packing-slip-pic3.jpg)

## Printing accompanying invoices

After you've turned on and set up the feature, the printed invoice report will contain invoice lines that are grouped and sorted by packing slip.

![Example of an invoice where invoice lines are grouped and sorted by packing slip](media/emea-ita-exil-invoice-packing-slip-pic.jpg)

> [!NOTE]
> The new layout is applicable only to invoices that are based on sales orders. It isn't applicable to free-text invoices, because they don't use packing slips.
