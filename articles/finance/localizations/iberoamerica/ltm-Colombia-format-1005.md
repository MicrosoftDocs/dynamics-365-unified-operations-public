---
title: Format 1005 file for Colombia configuration
description: This article provides information about the configuration required to issue the Format 1005 file for Colombia. 
author: Fhernandez0088 
ms.date: 11/20/2023 
ms.topic: article
ms.reviewer: kfend
ms.author: v-federicohe
ms.custom: bap-template
---

# Format 1005 file for Colombia configuration

This article provides explains the configurations that are required to issue a format 1009 file. This report informs the VAT generated in purchases and sales transactions.

## Prerequisites

Before you print the report, the following prerequisites must be met: 

- The legal entity must have an address in a country within the LATAM localization.
- The country-specific LATAM feature and the general feature must be activated.
- Import the following configurations from the **Global** repository:

  - LTM Tax Report
  - Format 1005 file

    To learn more, see [ER download reports](../../../fin-ops-core/dev-itpro/analytics/er-download-configurations-global-repo.md).

  - Configure ER parameters

    To learn more, see [ER configuration](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for format 1005

Lookups and conditions are designed so you can select the combination of document classification IDs and tax codes used in the transactions that are shown in this report.

After the prerequisites are met, complete the following steps.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting** and select **Reporting configuration**.
2. In the left tree, of select **LTM Tax Report deployment** > **Format 1005**.
3. In the top menu, go to **Configurations** > **Application specific parameters** > **Setup**.
4. In the **Lookups** section, select the first lookup, **ApplicableInvoice**. This lookup allows you to select the document classes that are used for vendor invoices that contain VAT.
5. In the **Conditions** section, select **Add**

   1. In the **Lookup result** field, select **Yes**.
   2. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor invoices). 

6. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **No**.
   2. In the **Document classification id.** field, select **Blank**.

7. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **No**.
   2. In the **Document classification id.** field, select **Not Blank**

8. In the **Lookups** section select **ApplicableDebitNote**.
9. In the **Conditions** section, select **Add**.

   1. In the **Lookup result** field, select **Yes**.
   2.  In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor debit note). 

10. In the **Conditions** section ,select **Add**.

   1. In the **Lookup result** field, select **No**.
   2. In the **Document classification id.** field, select **Blank**.

11. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

  > [!NOTE]
  > The document classes selected in this configuration must be used in the company transactions that are included in the report.

12. In the **Lookups** section select **TaxType**.
13. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Tax credit **.
  2. In the **Tax code** field, select an option from the list that represents the VAT. 

14. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **Vat Return**.
  2. In the **Tax code** field, select an option from the list that represents the VAT returns in sales returns. 

15. In the **Conditions** section select **Add**

  1. In the **Lookup result** field, select **N/A**.
  2. In the ** the type of tax.** field, select **Blank**.

16. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **N/A**.
  2. In the **Type of tax** field, select **Not Blank**.

  > [!NOTE]
  > The tax codes selected in this configuration must be used in the company transactions that are included in the report.

17. In the **Lookups** section, select **ApplicableCreditNote**.
18. In the **Conditions** section. select **Add**.

  1. In the **Lookup result** field select **Yes**.
  2. In the **Document classification id.** field, select an option from the list. Select the appropriate document class (vendor credit note). 

19. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Blank**.

20. In the **Conditions** section, select **Add**.

  1. In the **Lookup result** field, select **No**.
  2. In the **Document classification id.** field, select **Not Blank**.

## Issue file 1005 format

1. Go to **Tax** > **Inquiries and reports** > **LATAM** > **Tax reporting**.
2. In the **Format mapping** field, select  **Format 1009** and then select **OK**.
3. Select a date range.
4. Select **OK**.
