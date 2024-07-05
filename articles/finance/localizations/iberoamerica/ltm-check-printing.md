---
title: Print payment checks
description: Learn how print payment checks for Latin America, including prerequisites and an outline and step-by-step process for printing checks.
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: article
ms.date: 10/03/2023
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Print payment checks

[!include [banner](../../includes/banner.md)]

This article explains the configuration that's required to set up and print a payment check.

## Prerequisites

Before you complete the steps in this article to print payment checks, the following prerequisites must be met:

- The legal entity's address must be in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general LATAM feature must be enabled.
- You must download the following Electronic reporting (ER) configurations from the Global repository:

    - Payment check model
    - Payment check model LATAM
    - Check Printing Report

    To learn more about ER configurations, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- To issue checks, you must post payment journals by using the **LATAM Payments** feature.

## Print checks

Follow these steps to print checks.

1. Go to **Accounts payable** \> **Inquiries and Reports** \> **LATAM** \> **Checks** \> **Check printing**.
2. In the **Document class** field, select a value.
3. In the **Salespoint** field, select a value.
4. In the **From voucher number** and **To voucher number** fields, select a specific range of vouchers
5. Select the **Needs reprint** checkbox to show previously printed checks. The checks are shown in the **General** view.
6. Select a check, and print the report.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
