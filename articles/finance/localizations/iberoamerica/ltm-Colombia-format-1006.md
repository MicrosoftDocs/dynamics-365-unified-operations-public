---
title: Format 1006 file for Colombia configuration
description: This article provides information about the configuration required to issue the Format 1006 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/21/2023 
ms.topic: articule
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1006 file for Colombia configuration

This article explains how to set up and issue a format 1006 file. This report includes VAT that is generated in sales and purchase transactions, and consumption taxes.

## Prerequisites

To print the report, the following prerequisites must be met: 

- The legal entity must have an address in a country within the LATAM localization.
- Activate the country-specific LATAM feature and the general feature.
- Import the configurations needed from the **Global** repository:

  - LTM Tax Report
  - Format 1006 file

    To learn more, see [ER download reports](../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

- Configure ER parameters

  For more details, see [ER configuration](../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1006

Lookups and conditions are designed so you can select the combination of document classification IDs and tax codes used in the transactions that are shown in the report.

After the prerequisites are met, complete the following steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configuration**.
2. On the left, select **LTM Tax Report deployment** \> **Format 1006**.
3. On the Action Pane, select **Configurations** \> **Application specific parameters** \> **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableCreditNote**. Use this lookup to select the document classes to use for purchases that contain VAT.
5. In the **Conditions** section, select **Add**

  1. In the **Lookup result** field, select **Yes**.
  2. In the **Document classification id.** field, select a value. 

6. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**.

7. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions listed in the report.

8. In the **Lookups** section, select **TaxType**.
9. In the **Conditions** section, select **Add**.

  1. In the **Lookup Result** field select **Consumption tax**.
  2. In the **Tax code** field, select an option from the list that represents consumption taxes. 

10. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Generated tax**.
  2. In the **Tax code** field, select a value from the list that represents the VAT generated in sales. 

11. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Tax refund**.
  2. In the **Tax code** field, select an option from the list that represents the VAT returns in purchases returns. 

12. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Type of tax** field, select **Blank**.

13. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Type of tax** field, select **Not Blank**.

  > [!NOTE]
  > The tax codes selected in this configuration must be used in the company transactions listed in the report.

14. In the **Lookups** section select **ApplicableInvoice**.
15. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Yes**.
  2. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (purchase invoices). 

16. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**

17. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions listed in the report.

## Issue file 1006 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select **Format 1006**.
3. Select **OK**.
4. Select a date range.
6. Select **OK**.
