---
title: Printing configuration for General Ledger LATAM
description: This article provides information about the required configuration for printing a general ledger for Latin America. 
author: Fhernandez0088
ms.date: 10/03/2023
ms.topic: Article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Printing configuration for General Ledger LATAM
[!include [banner](../../includes/banner.md)]

This document contains the steps needed to setup and print the General Ledger LATAM report.

## Prerequisites
Before you print the general ledger report, the following prerequisites must be met.

- The legal entity must have an address in a country within the LATAM localization.
- The country-specific LATAM feature and the general feature must be enabled.
- The following ER configurations must be imported from the **Global** repository: 

   - Ledger accounting reports
   - Ledger Accounting LATAM
   - General Ledger LATAM
  
     For more information, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure the SSRS reports/Services references as follows.

   - **Report/Service Id**: GeneralLedger
   - **Report/Service name**: GeneralLedger
   - **Report/Service type**: Delect an ER Configuration
   - **Model mapping name**: Ledger Accounting
   - **Data model definition**: GeneralLedger
   - **Format mapping**: General Ledger LATAM
   - **REPORT/SERVICE TYPE**: Set the **General Ledger** slider to **Yes**.

- Have transactions that have been posted.

## Print General eLdger LATAM report
Follow these steps to print the General ledger report for LATAM.

1. Go to **General Ledger** > **Inquiries and Reports** > **LATAM** > **General Ledger**.
2. On the **General Ledger** slider, in the **Report Id** field, select **General Ledger**.
3. In the **From date** and **To date** fields, select the date range of the transactions you want to print. 
4. Set the **Initial legal number**.
5. Set the **Starting page**.
6. Set the **Starting transport value** to continue the accumulated sum.
7. Select the posting layer to include in the report. 
8. Set the **Print customer/vendor** slider to **Yes** to print information per transaction.
9. Select **Print**. 




[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
