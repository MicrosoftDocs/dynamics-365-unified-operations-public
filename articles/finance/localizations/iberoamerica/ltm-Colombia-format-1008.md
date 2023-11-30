---
title: Format 1008 file for Colombia configuration
description: This article explains how to set up and issue a Format 1008 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/30/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1008 file for Colombia configuration

This article explains how to set up and issue a format 1008 file. The format 1008 file provides information about the company's credit assets.

## Prerequisites

Before you print the report, the following prerequisites must be met:

- The address that's set for the legal entity must be in a country within the LATAM localization.
- Enable the country-specific LATAM globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository:
  - LTM Tax Report
  - Format 1008 file

    For more information, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure ER parameters. For more information, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1008 file.

Lookups and conditions are designed so that you can select the combination of documents classification IDs and ledger account numbers that's used in the transactions that are shown on the report.

Follow these steps to set up the parameters for the report.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** > **Format 1008**
3. On the Action Pane, select **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** section, select the first lookup, **IsApplicable**. This lookup allows you to select the document classes that are used for customer invoices, credit notes, debit notes, and customer payments transactions.
5. In the **Conditions** section, select **Add**.
   
  1. In the **Lookup result** field, select **Yes**.
  2. In the **Document classification id.** field, select the appropriate document class. 

6. In the **Conditions** section, select **Add**.
   
  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**.

7. In the **Conditions** section select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions to be listed in this report.

8. In the **Lookups** section, select **MainAccountGroups**.
9. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select one of the following options:

   - **1315**: Accounts receivable from customers.
   - **1316**: Accounts receivable from shareholders, partners, community members, cooperative members, and related companies
   - **1317**: Other accounts receivable.
   - **1318**: The tax value of the portfolio impairment.

  2. In the **Main Account** field, select a ledger account from the list that is used for the concept selected in the **Lookup result** field. 

10. In the **Conditions** section select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Blank**.

11. On the **Conditions** section select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Not Blank**.

  > [!NOTE]
  > The ledger accounts selected in this configuration must be used in the company transactions to be listed in this report.

## Run file 1008 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select **Format 1008**.
3. Select **OK**.
4. Select a date range.
6. Select **OK**.
