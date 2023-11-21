---
title: Report 1007 for Colombia configuration
description: This article provides information about how to set up and issue Format 1007 file for Colombia.  
author: Fhernandez0088 
ms.date: 11/21/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1007 file for Colombia configuration

This article explains how to set up and issue a format 1007 file. The format 1007 file provides informationa about the revenue received in a span of time by the company.

## Prerequisites

Before you print the report, the following prerequisites must be met.

- The legal entity address must be set in Colombia.
- Enable the country-specific LATAM globalization feature and the general LATAM feature.
- Import the following configurations from the Global repository: 

  - LTM Tax Report
  - Format 1007 format

   To learn more, see [Download ER Configuration](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure ER parameters

  For more details, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters

Lookups and conditions are designed so you can select the combination of documents classification IDs and sales tax codes used in transactions.

Follow these steps to set up the parameters for the report. 

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1007**
3. On the Action Pane, go to **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup **InvoiceAndCreditNoteIsApplicable**. Use this lookup to select the document classes that are used for invoice and credit note transactions that contain the company revenue.
5. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Yes**.
  2. In the **Document classification id.** field, select a value.

6. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**.

7. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions listed in the report.

8. In the **Lookups** section, select **MainAccountGroup**.
9. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select one of the following values:

     - 4001: Common activities revenue
     - 4002: Other activities revenue
     - 4003: Financial interest revenue
     - 4004: Mortgage interest revenue

  2. In the **Main Account** field, select a value. 

10. On the **Conditions** section select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Blank**.

11. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Main account** field, select **Not Blank**.

  > [!NOTE]
  > The ledger accounts selected in this configuration must be used in the company transactions for the report.

## Issue a format 1007 file

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
2. In the **Format mapping** field, select **Format 1007**.
3. Select **OK**.
4. Select a date range.
6. Select **OK**.
