---
title: Print a Ledger Posting report for LATAM
description: This article explains how to print a Ledger Posting for Latin America.
author: Fhernandez0088
ms.date: 10/06/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Print a Ledger Posting report for LATAM

[!include [banner](../includes/banner.md)]

This article explains how to print a Ledger Posting report for Latin America.

## Prerequisites
Before you can print a Ledger posting report, the following prerequisites must be met.

- The legal entity must have an address in a country within the LATAM localization.
- You must have enabled the country-specific LATAM feature and the general feature.
- The following ER configurations must be imported.

   - Ledger accounting reports
   - Ledger Accounting LATAM
   - Ledger posting

   For more information about ER configurations, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Create a new SSRS Reports/Services references and configure it as follows:

  - **Report/Service Id**: LedgerPosting
  - **Report/Service name**: LedgerPost
  - **Report/Service type**: Select an ER configuration
  - In the **Model mapping name** field, select **Ledger accounting LTM**
  - In the **Data model definition** field, select **LedgerPosting**
  - In the **Format mapping** field, select **Ledger Posting LATAM**
  - In the list of Report/Service types, enable **Ledger Posting**

## Print the Ledger posting report for Latin America

1. Go to **General Ledger** > **Inquiries and Reports** > **LATAM** > **Ledger Posting Report**.
2. On the **Ledger posting report** slider, configure the filters for the report.
3. In the **Report ID** field, select the corresponding Report/Service ID.
4. In the **From date** and **To date** fields, select the date range of the transactions you want to print.
5. In the **Account number** field, select the account number if you want to print for a specific account.
6. Select the posting layers to include in the report.
4. Select **Print**. 

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
