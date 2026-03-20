---
title: DAS-2 report
description: Learn about the process of generating the Standard Audit File for France (FEC) in Microsoft Dynamics 365 Finance with an overview on vendor configuration.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.custom: 
  - bap-template
ms.date: 03/11/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
---

# DAS-2 report

[!include [banner](../../includes/banner.md)]

French legal entities that do business with self-employed professionals must provide a DAS-2 declaration report to the tax authorities. The DAS-2 report is an annual fiscal declaration that includes all payments to vendors of this type that exceed €1,200. You generate the report in Microsoft Excel format. After you generate the report, save the file in your third-party software environment. The file is then validated, converted into the electronic data interchange (EDI) structure, and transmitted.

Use the Electronic reporting (ER) tool to generate the DAS-2 Excel report. It includes the following worksheets:

- **Details** – All vendor invoices that you paid during the selected period and by using a specific vendor profile that has a DAS-2 classification
- **Summary by vendor** – The DAS-2 declaration grouped by vendor. Each column represents the amounts per DAS-2 classification.
- **DAS-2 form** – A summary of the declaration for each vendor. There's one form for each vendor.

Before you generate the report for the first time, download the following models and formats from Microsoft Dynamics Lifecycle Services (LCS):

- Statistics on invoices.version.36.xml or later versions.
- Statistics on invoices model mapping.version.36.37.xml or later versions.
- Statistics on invoices for DAS-2 model mapping.version.36.37.8 or later versions. This derived model supports partial payments and amounts with taxes.
- DAS-2 report.version.36.30 (FR) or later versions.
- DAS-2 form.version.36.30.15 (FR) or later versions.

> [!NOTE]
> For more information about how to download ER formats, see [Download Electronic reporting configurations from Lifecycle Services](../../../fin-ops-core/dev-itpro/analytics/download-electronic-reporting-configuration-lcs.md).

After you finish downloading the ER configurations from LCS, follow these steps:

1. In Microsoft Dynamics 365 Finance, select the related French company.
2. Go to **Workspaces** > **Electronic reporting**, and set the **Microsoft** provider to **Active**.
3. Select **Configurations** > **Exchange**, and load the configurations from the XML files to import the Statistics model, model mapping, DAS-2 report, and DAS-2 form format file.
4. Select **DAS-2 report** format.
5. In the **Electronic reporting** workspace, select **Configurations** > **Setup**.
6. On the **Conditions** tab, select version **36.30** or later, and create the configuration that you use to set up the mapping between the main accounts that you configure in your company and the related tax authority classification of the DAS-2 report.

    1. In the **Lookup result** field, select the related classification.
    1. In the **Main account** field, select the main account that you use to post the related transactions that belong to the selected classification.
    1. Set the **Status** field to **Completed**.

### Example

:::image type="content" source="../media/emea-fra-das2-report-configuration.png" alt-text="Screenshot of an example of a configuration.":::

On line 1 of the preceding configuration, main account **622000**, which you use to post fee expense transactions, maps to classification **C** (**Commissions**), which the tax authority establishes.

Line 5 includes the configuration that has the classification **ZZ** and maps to **Not Blanks**. Use it when the invoice journal has other expense transactions that you don't detail on the DAS-2 report. This line should always be the last line. If you need to introduce additional classifications, remove this line and introduce the new ones.

> [!NOTE]
> Create the same configuration for the DAS-2 form format.

## Vendor configuration

Because the report includes the SIRET Système d'identification du répertoire des établissements (SIRET) registration and profession, follow these steps to add the related information.

1. Go to **Accounts payable > Vendors > All vendors**.
1. Select the vendor record that you want to update.
1. Expand the **Purchasing demographics** section.
1. Select **Edit**.
1. In the **French Siret** fields, enter a value.
1. In the **NAF code** field, enter a value to identify the profession.

## Statistics on invoices process

Before you generate the DAS-2 report, run the **Statistics on invoices** process to calculate and generate all transactions that the report includes. You can run the process in real time or schedule it to run in the background by using batch processing.

1. Go to **Accounts payable** > **Periodic tasks** > **Statistics on invoices**.
1. Select **Calculate statistics**.
1. Select the from and to dates.
1. Select the vendor posting profile. Vendor posting profiles let you easily include vendor transactions for all vendors, a group of vendors, or a single vendor on the report that you generate. This option requires you to select one or more vendor posting profiles. 
1. (Optional) Select the vendor group. This selection adds an extra transaction filter.  
1. Select **OK** to run the process.

## Generate the DAS-2 report

Follow these steps to generate the tax declaration report.

1. Go to **Accounts payable** \> **Inquiries and reports** \> **DAS-2 report**.
1. Select the format for the report:

    - **DAS-2 report (FR)** – Generate a detailed report that includes all transactions.
    - **DAS-2 form (FR)** – Generate a separate report for each vendor.

1. Select the from and to dates.
1. Select the vendor posting profile. 
1. Select the vendor group.

> [!NOTE]
> The DAS-2 report doesn't support transactions that are created and posted from a general journal entry, the accrual schema scenario, or one voucher functionality. 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
