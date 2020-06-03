---
# required metadata

title: Configure invoice layout for Bahrain
description: This topic explains how to configure invoice layout for Bahrain.
author: ilkond
manager: AnnBe
ms.date: 06/03/2020
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
ms.search.validFrom: 2020-06-03
ms.dyn365.ops.version: 10.0.13

---

# Configure invoice layout for Bahrain

[!include [banner](../includes/banner.md)]

The article explains how to configure printable invoice layouts to make it compliant with Bahraini legal requiremets.

## Prerequisites

- The primary address of the legal entity must be in Bahrain.

## Features enabling

In the **Feature management** workspace, enable the following features:
- (Bahrain) Credit invoicing layout for sales and project invoice reports;
- Convert Electronic Reporting outbound documents from Microsoft Office formats to PDF.

For more information how to enable features, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).

## Import
After ...
For more information how to import Electronic Reporting configurations, see [Download Electronic reporting configurations from Lifecycle Services](../../dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

## Configure conversion to PDF
By default invoices are being generated as Excel files. To enable their conversion to PDF format do the following setup.

In **Electronic reporting** workspace > **Electronic reporting destinations**, create destinations for the related formats:
 - Sales invoice (Excel) (BH);
 - Free text invoice (Excel) (BH).
 
For each format, mark **Convert to PDF** check-box, select **Portrait** page orientation and enable printing to **Screen**.

![Enable conversion to PDF](media/emea-bhr-pdf.jpg)
aa
> [!NOTE]
> When...
