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

According to Egyptian legal requirements, the invoices issued for customers must be submitted to the Tax authority in an electronic format.
The submission requires the system configuration which consists of 2 parts:
1. **Electronic invoicing add-on** configuration. Please refer to this article for details: [Get started with the Electronic invoicing add-on service administration](e-invoicing-get-started-service-administration.md)
2. **Microsoft Dynamics 365 Finance** configuration which is covered in this article.

## Prerequisites

In the Feature management workspace, turn on the **Electronic invoicing add-on integration** feature. For more information, see [Feature management overview](../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).

## Enable electronic invoicing for Egypt
Complete the following steps to nable electronic invoicing for Egypt.

1. Go to **Organization administration** > **Setup** > **Electronic document parameters** 
2. On the **Features** tab, select feature reference for **EG00008 E-invoicing for Egypt** 
3. Turn on **Enabled** option for the selected feature reference.



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
