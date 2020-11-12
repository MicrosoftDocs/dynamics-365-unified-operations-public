---
# required metadata

title: Generate forced electronic invoices
description: This topic explains how to set up and use functionality to force generating electronic invoices.
author: ilkond
manager: AnnBe
ms.date: 11/12/2020
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

This article describes how to configure a forced generation of electronic invoices files immediately after related customer invoices are posted regardless of the selected printing options.

## Prerequisites

1. In the **Feature management** workspace, turn on the **Forced electronic invoices generation** feature. For more information, see [Feature management overview](../../fin-and-ops/get-started/feature-management/feature-management-overview.md).
2. Configure the system to enable electronic invoice generation. Although Electronic invoices configuration is a country-specific process, it contains the steps which are in common for all supported countries. For example, see how to configure [Norwegian electronic invoices](emea-nor-e-invoices.md).

## Post invoices
When you post invoices with the **Forced electronic invoices generation** feature enabled, two scenarios are possible.

- If no electronic reporting destinations are defined, output files for electronic invoices will be generated in **Electronic reporting jobs**. To view the files of generated electronic invoices, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**, select a required job, and then select **Show files**. Select **Open** to download the file with the electronic invoice.

- If there are electronic reporting destinations defined for electronic invoices formats,  generated output files will be sent to a related file destination that is configured for Electronic reporting destination.
For more details about Electronic reporting destinations, see [Electronic reporting destinations](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE]
> The **Forced electronic invoices generation** feature is not applicable to Italy. Italian electronic invoices depend only on the existance of related Electronic reporting destinations and always disregard printing options used during invoices posting.

