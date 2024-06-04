---
title: Forced electronic invoices generation
description: Learn how to set up and use the functionality for forced generation of electronic invoices, including prerequisites and an outline on post invoices.
author: ilikond
ms.author: ikondratenko
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 06/04/2024
ms.reviewer: johnmichalak

---

# Forced electronic invoices generation

[!include [banner](../../includes/banner.md)]

This article explains how to configure the forced generation of electronic invoice files immediately after related customer invoices are posted, regardless of the printing options that are selected.

## Prerequisites

1. In the **Feature management** workspace, turn on the **Forced electronic invoices generation** feature. For more information, see [Feature management overview](../../../fin-ops-core/fin-ops/get-started/feature-management/feature-management-overview.md).
2. Configure the system to enable electronic invoice generation. Although the configuration of electronic invoices is a country/region-specific process, it includes common steps that used for all supported countries and regions. For an example, see [Norwegian electronic invoices](../norway/emea-nor-e-invoices.md).

## Post invoices

After you turn on the **Forced electronic invoices generation** feature, two scenarios are possible when you post invoices:

- If no Electronic reporting (ER) destinations are defined for electronic invoice formats, output files for electronic invoices are generated on the **Electronic reporting jobs** page. To view these files, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**, select a job, and then select **Show files**. Then select **Open** to download the file for the electronic invoice.
- If ER destinations are defined for electronic invoice formats, the output files that are generated are sent to a related file destination that is configured for the ER destination.

For more information about ER destinations, see [Electronic reporting destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

> [!NOTE]
> The **Forced electronic invoices generation** feature isn't applicable to Italy. Italian electronic invoices depend only on the existence of related ER destinations. They always disregard printing options that are used during invoice posting.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
