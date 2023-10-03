---
title: Print payment checks
description: This article explains how print payment checks for Latin America. 
author: Fhernandez0088
ms.date: 10/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Print payment checks
[!include [banner](../../includes/banner.md)]

This article explains the configuration needed to set up and print a payment check.

## Prerequisites
Before you complete the steps in this article to print payment checks, the following prerequisites must be met. 

- The legal entity address is loacted in a country within the LATAM localization. 
- The country-specific LATAM feature and the general LATAM feature must be enabled.
- Import the following electronic ER configurations from the Global repository:

  - Payment check model
  - Payment check model LATAM
  - Check Printing Report

   To learn more about ER configurations, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Post payment journals using the **LATAM Payments** feature to issue checks.

## Check printing
Follow these steps to print checks.

1. Go to **Accounts payable** > **Inquiries and Reports** > **LATAM** > **Checks** > **Check printing**.
2. In the **Document class** field, select a value.
3. In the **Salespoint** field, select a value.
4. In the **From voucher number** and **To voucher number** fields, select a specific range of vouchers
5. Select the **Needs reprint** check box to display previously printed checks. The checks are displayed in the **General view**.
6. Select one and print the report.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
