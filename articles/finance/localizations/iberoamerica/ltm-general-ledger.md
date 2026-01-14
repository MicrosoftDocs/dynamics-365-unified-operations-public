---
title: Printing configuration for General Ledger LATAM
description: Learn about the configuration that's required to print a general ledger report for Latin America, including a process for printing the general ledger report. 
author: Fhernandez0088
ms.author: v-federicohe
ms.topic: how-to
ms.date: 01/05/2026
ms.custom: bap-template
ms.reviewer: johnmichalak
---

# Printing configuration for General Ledger LATAM

[!include [banner](../../includes/banner.md)]

[!include [does not apply to](includes/does-not-apply-to.md)]

This article describes the steps that are required to set up and print the general ledger report for Latin America (**General Ledger LATAM**).

## Prerequisites

Before you print the general ledger report, the following prerequisites must be met:

- The legal entity must have an address in a country/region that's within the LATAM localization.
- The country/region-specific LATAM feature and the general feature must be enabled.
- The following ER configurations must be imported from the Global repository:

  - Ledger accounting reports
  - Ledger Accounting LATAM
  - General Ledger LATAM

    For more information, see [Download ER configurations from the Global repository of Configuration service](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- The SSRS Reports/Services references must be configured in the following way:

  - **Report/Service Id:** Enter **GeneralLedger**.
  - **Report/Service name:** Enter **GeneralLedger**.
  - **Report/Service type:** Select an ER configuration.
  - **Model mapping name:** Select **Ledger Accounting**.
  - **Data model definition:** Select **GeneralLedger**.
  - **Format mapping:** Select **General Ledger LATAM**.
  - **Report/Service type:** Set the **General Ledger** option to **Yes**.

- You must have transactions that have been posted.

## Print the General Ledger LATAM report

Follow these steps to print the general ledger report for Latin America.

1. Go to **General Ledger** \> **Inquiries and Reports** \> **LATAM** \> **General Ledger**.
1. In the **General Ledger** dialog box, in the **Report Id** field, select **General Ledger**.
1. In the **From date** and **To date** fields, select the date range of the transactions that you want to print.
1. Set the **Initial legal number** field.
1. Set the **Starting page** field.
1. Set the **Starting transport value** field to continue the accumulated sum.
1. Select the posting layer to include on the report.
1. Set the **Print customer/vendor** option to **Yes** to print information per transaction.
1. Select **Print**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
