---
# required metadata

title: Forced electronic invoices generation
description: This topic explains how to set up and use forced electronic invoices generation.
author: ilkond
manager: AnnBe
ms.date: 11/03/2020
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
ms.search.region: Europe
# ms.search.industry: 
ms.author: ilyako
ms.search.validFrom: 2019-12-01
ms.dyn365.ops.version: 10.0.17

---

# Forced electronic invoices generation

[!include [banner](../includes/banner.md)]

This article describes how to configure forced generation of electronic invoices files right after posting of related customer invoices regardless of the selected printing options.

## Prerequisites

- In the **Feature management** workspace, turn on the **Forced electronic invoices generation** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).
- Configure the system to enable electronic invoices generation. Although Electronic invoices configuration is country-specific process, it contains the steps which are in common for all the supported countries. For example, please see how to configure [Norwegian electronic invoices](emea-nor-e-invoices.md).

## Posting invoices
When posting invoices with **Forced electronic invoices generation** feature enabled, two scenarios are available.

- If no **Electronic reporting destinations** are defined then output files for electronic invoices will be generated in **Electronic reporting jobs**. To inquire about XML files of generated electronic invoices, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs** and select a required job, then select **Show files**, and then select **Open** to download the file with the electronic invoice:
![Show e-invoice](media/emea-nor-ger-einvoice-open.jpg)

- If **Electronic reporting destinations** are defined for electronic invoices formats then generated output files will be sent to a related **File destination** configured for Electronic reporting destination.
For more details about Electronic reporting destinations, see [Electronic reporting destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE]
> **Forced electronic invoices generation** feature is not applicable to Italy. Italian electronic invoices depend only on the existance of related Electronic reporting destinations and always disregard printing options used during invoices posting.

