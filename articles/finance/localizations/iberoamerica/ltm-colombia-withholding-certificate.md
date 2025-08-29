---
title: Configure printing for the Withholding certificate format for Colombia
description: Learn how to set up and generate three withholding certificate formats for Colombia.
ms.date: 08/28/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
author: Fhernandez0088
ms.author: v-federicohe
---

# Configure printing for the Withholding certificate format for Colombia

[!INCLUDE[banner](../includes/banner.md)]

This article explains how to set up and generate three withholding certificate formats for Colombia in Microsoft Dynamics 365 Finance: VAT withholdings, income withholdings, and ICA withholdings.

It includes information from vendor transactions like invoices, debit notes, and credit notes, and it shows the calculated withholdings for income tax (FTE), industry and commerce tax (ICA), and value-added tax (IVA). These certificates are official documents for the amounts withheld and reported to the DIAN. They ensure fiscal transparency and legal compliance.

## Prerequisites

Before generating the report, ensure the following prerequisites are met:

- The legal entity's address must be in Colombia.
- Enable the general Latin American (LATAM) feature, and the country/region-specific LATAM feature for Colombia.
- Download the specific report configuration from the Dataverse configuration repository. For more information, see [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

- Download these formats from Dataverse:
  - :::no-loc text="LTM Tax Report":::
  - :::no-loc text="LTM Tax Report mapping":::
  - :::no-loc text="COL Withholding Certificate FTE":::
  - :::no-loc text="COL Withholding Certificate ICA":::
  - :::no-loc text="COL Withholding Certificate IVA":::
 - Configure the Electronic reporting (ER) parameters. For more information, see [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).

## Configure application-specific parameters for the Withholding certificate format for Colombia

To configure application-specific parameters, complete the following configurations:

- Configure the COL withholding certificate FTE format.
- Configure the COL withholding certificate ICA format.
- Configure the COL withholding certificate IVA format.

### Configure the COL withholding certificate FTE format

To configure the COL withholding certificate FTE format, follow these steps.

1. Go to **Organization administration** \> **Workspaces** > **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report**.
1. Select the **COL Withholding Certificate FTE** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. Ensure the report shows transactions that meet the configured conditions by setting the **Lookup result** fields to **No**, and specifying both **Blank** and **Non-blank** conditions.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as income withholding tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

### Configure the COL withholding certificate ICA format

To configure the COL withholding certificate ICA format, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report** 
1. Select the **COL Withholding Certificate ICA** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all Credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as ICA withholding tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

### Configure the COL withholding certificate IVA format

To configure the COL withholding certificate IVA format, follow these steps.

1. Go to **Organization administration** \> **Workspaces** \> **Electronic reporting**, and select **Reporting configurations** \> **LTM Tax Report** 
1. Select the **COL Withholding certificate IVA** format.
1. On the Action Pane, in the **Configurations** tab, in the **Application specific parameters** group, select **Setup**.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendInvoiceIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all invoices document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Application specific parameters** page, on the **Lookups** tab, select **VendCreditNoteIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Document classification Id (VoucherClassId)** field, select all Credit note document classes that are required for vendor transactions.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.
1. On the **Lookups** FastTab, select **TaxIsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Tax code** field, select the tax codes that are used as VAT withholding tax.
1. To ensure that the report shows the transactions that meet the configured conditions, set the **Lookup result** fields to **No**, and specify both **Blank** and **Non-blank** conditions.

> [!NOTE]
> The **Concept** column on the certificate shows the name of the ledger account used for the withholding tax line.

> [!NOTE]
> Use the tax codes and document classes configured in lookups for transactions beforehand to make them appear in the certificate formats.

## Generate the withholding certificate format for Colombia

To generate the certificate, follow these steps.

1. In Dynamics 365 Finance, go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, enter or select the name of the format you need to generate (:::no-loc text="COL Withholding Certificate FTE":::, :::no-loc text="COL Withholding Certificate ICA":::, or :::no-loc text="COL Withholding certificate IVA":::), and then select **OK**.
1. In the **From date** and **To date** fields, enter the date range for the report.
1. Select **OK**.

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
