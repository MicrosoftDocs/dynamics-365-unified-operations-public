---
title: Format 1003 file for Colombia configuration
description: This article provides information about the required configuration for issuing the Format 1003 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/20/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1003 file for Colombia configuration

This article explains the configurations needed to issue a format 1009 file.
This report informs withholding taxes that were incurred by the company during a period of time and the related entities.

## Prerequisites

To print the report, the following prerequisites must be met: 

- The legal entity must have an address in a country within the LATAM localization.
- The country-specific LATAM feature and the general feature must be activated.
- The following configurations must be imported from the Global repository:

  - LTM Tax Report
  - Format 1003 file

    To learn more, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

  - Configure ER parameters

    For more detailed information, see [ER configuration]( ../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1003

Lookups and conditions are designed so you can choose the combination of documents classification IDs, tax codes, and ledger accounts used in the transactions that are shown in this report.

After the prerequisites listed above have been met, complete the following steps.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and select **Reporting configuration**.
2. In the left tree select **LTM Tax Report deployment** > **Format 1003**
3. In the top menu, go to **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. This lookup allows you to select the document classes that are used for posting third sales transactions.
5. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **Yes**.
   2. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (usually the sales invoices or debit notes). 

6. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **No**.
   2. In the **Document classification id.** field, select **Blank**.

7. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **No**.
   2. In the **Document classification id.** field, select **Not Blank**.

   > [!NOTE]
   > The document classes selected in this configuration must be used in the company transactions that will be listed in this report.

8. In the **Lookups** section select **Concept**.
9. In the **Conditions** section, select **Add**

   1. In the **Lookup Result** field select one or more of the following options:

      - **1301**: Withholding for salaries, benefits, and other labor payments.
      - **1302**: Sales withholdings.
      - **1303**: Withholding taxes for services.
      - **1304**: Withholding taxes for fees.
      - **1305**: Withholding taxes for commissions.
      - **1306**: Withholding taxes for interest and financial returns.
      - **1307**: Withholding taxes for leases.
      - **1308**: Withholding taxes for other concepts.
      - **1309**: Sales tax withholdings.
      - **1310**: Withholding for dividends and participations. This doesn't include the value reported in concept 1320.
      - **1311**: Withholding taxes for the sale of fixed assets of natural persons.
      - **1312**: Withholding taxes for deposits from debit and credit cards.
      - **1313**: Withholding taxes for lotteries, raffles, bets, and similar.
      - **1314**: Withholding taxes for stamp taxes.

10. In the **Tax code** field, select a tax code from the list that represents the concept.  
11. In the **Conditions** section, select **Add**.

    1. In the **Lookup result** field, select **N/A**.
    2. In the **Type of tax** field, select **Blank**.

12. In the **Conditions** section, select **Add**.
23. In the **Lookup result** field, select **N/A**.
24. In the **Type of tax** field, select **Not Blank**.

> [!NOTE]
> The tax codes selected in this configuration must be used in the company transactions that will be listed in this report.


## Issue file 1003 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select **Format 1003**.
3. Select **OK**.
4. Select a date range.
6. Select **OK**.
