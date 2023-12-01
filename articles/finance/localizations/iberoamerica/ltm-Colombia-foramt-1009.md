---
title: Format 1009 file for Colombia configuration
description: This article explains how to set up and issue a format 1009 file for Colombia. 
author: Fhernandez0088 
ms.date: 12/01/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1009 file for Colombia configuration

This article explains how to set up and issue a format 1009 file. The format 1009 file provides information about the company's liabilities during a specified period.

## Prerequisites

Before you print the report, the following prerequisites must be met:
-The address that's set for the legal entity must be in a country within Latin America.
- Enable the country-specific LATAM globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository:
  - LTM Tax Report
  - Format 1009 file

  For more information, see [ER download reports](/../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure ER parameters. To learn more, see [ER configuration](/../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of documents classification IDs and ledger account numbers that's used in transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** > **Format 1009**.
3. On the Action Pane, select **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** sectio,n select the first lookup, **IsApplicable**. Use this lookup to select the document classes that are used for vendor invoices, credit notes, debit notes, and payments transactions.
5. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Yes**.
  2. In the **Document classification id.** field, select the appropriate document class. 

6. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**

7. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions that are listed on the report.

8. In the **Lookups** section select **MainAccountGroups**.
9. In the **Conditions** section, select **Add**

  1. In the **Lookup result** field, select a concept:

   - **2201**: Liabilities with national vendors.
   - **2202**: Liabilities with related companies, shareholders, and partners.
   - **2203**: Ginancial liabilities.
   - **2204**: Liabilities for taxes, levies, and fees.
   - **2206**: Other liabilities
   - **2207**: Total liabilities determined by an actuarial calculation.
   - **2208**: Liabilities supported by a document with a certain date.
   - **2209**: Liabilities of insurance companies.
   - **2211**: Liabilities for judicial deposits.
   - **2212**: Liability for deferred income for award points awarded in loyalty training programs.
   - **2213**: Liability for deferred income contemplated in the E.T. art.23-1.
   - **2214**: Liabilities for parafiscal contributions, health, pension, and severance pay.
   - **2215**: Labor liabilities held by the worker, without layoffs.

  2. In the **Main Account** field, select a ledger account from the list. 

10. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Blank**.

11. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Not Blank**.

  > [!NOTE]
  > The ledger accounts selected in this configuration must be used in the company transactions that are listed in the report.

## Issue a file 1009 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select a **Format 1009**.
3. Select **OK**.
4. Select a date range.
6. Select **OK**.
