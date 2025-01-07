---
title: Configure printing for the Ecuador Sales book by establishment report
description: Learn how to set up and use the Ecuador Sales book by establishment report.
author: Fhernandez0088
ms.date: 01/03/2025
ms.topic: how-to
ms.custom: bap-template
ms.reviewer: johnmichalak
ms.author: v-federicohe
---

# Configure printing for the Ecuador Sales book by establishment report

The **Ecuador Sales book by establishment** report is the record document that businesses use to keep a record of their sales transactions for each active establishment. Although the specific value-added tax (VAT) report requirements might vary from one country or region to another, they typically include the transaction date, customer information, and tax information details.

## Prerequisites

Before you can print the **Ecuador Sales book by establishment** report, the following prerequisites must be met:

- The legal entity's address must be in a country that is within the LATAM localization (in this case, Ecuador).
-Both the country/region-specific LATAM function and the general LATAM function must be activated.
- You must download the relevant report configuration from the Microsoft Dataverse repository. Learn more in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).
- You must configure the Electronic reporting (ER) parameters. Learn more in [Configure the Electronic reporting (ER) framework](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-er-configure-parameters.md).
- You must post sales invoices that include LATAM information.
- You must configure the tax applications of the sales points that are used with an **"F"** for a physical document and an **"E"** for an electronic document. Learn more in [Document classes for Latin America](ltm-core-document-class.md).

## Configure application-specific parameters

Lookups and conditions are designed so that you can select the combination of document classes IDs and sales tax codes that is used in sales transactions. The conditions that are applicable to Ecuador are shown.

1. Open the **Electronic Reporting** workspace, select **Report Configurations**, and then select **LTM Tax Report**.
1. Select the **EC Sales book by establishment** report, and then, on the Action Pane, on the **Configuration** tab, in the **Application-specific parameters** group, select **Setup**.
1. On the **Lookups** FastTab, in the **Name** column, select **IsApplicable**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **SalesId**.
1. In the **Document classification Id (VoucherClassid)** field, select a value.
1. Repeat steps 5 and 6 to add as many more tax codes as you need.
1. After you finish adding tax codes, add two final lines to the grid on the **Conditions** FastTab:

    - On the first of the two lines, select **NotApplicable** in the **Lookup result** field and **Blank** in the **Document classification Id (VoucherClassid)** field.
    - On the second of the two lines (the last line in the grid), select **NotApplicable** in the **Lookup result** field **Not blank** in the **Document classification Id (VoucherClassid)** field.

1. On the **Lookups** FastTab, in the **Name** column, select **SalesPoint**.
1. On the **Conditions** FastTab, select **Add**.
1. In the **Lookup result** field, select **Yes**.
1. In the **Sales Point Id** field, select a value.
1. Repeat steps 11 and 12 to add as many more sales points as you need.
1. After you finish adding sales points, add two final lines to the grid on the **Conditions** FastTab:

    - On the first of the two lines, select **No** in the **Lookup result** field and **Blank** in the **Sales Point Id (SalesPointid)** field.
    - On the second of the two lines (the last line in the grid), select **No** in the **Lookup result** field and **Not blank** in the **Sales Point Id (SalesPointid)** field.

> [!NOTE]
> VAT sales books are formats that depend on the **LTM tax report** template. Therefore, it's important that the sales points that are configured on this report are used in the posted transactions. The codes that you select here must match the codes that are recorded in transactions.

## Run the Ecuador Sales book by establishment report

1. Go to **Tax** \> **Inquiries and reports** \> **LATAM** \> **Tax reporting**.
1. In the **Format mapping** field, select **EC Sales book by establishment**.
1. Select **OK**.
1. In the **From** date field, enter a date.
1. In the **To** date field, enter a date.
1. Select **OK**.
