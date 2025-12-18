---
title: Fiscal journal report
description: Learn about the Fiscal journal report in Italy.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.custom: 
  - bap-template
ms.date: 12/18/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Italy
ms.search.validFrom: 
ms.dyn365.ops.version: 
---

# Fiscal journal report

[!INCLUDE[banner](../../includes/banner.md)]

The Italian **Fiscal journal** report is a monthly report that lists all the vouchers and journal entries in order of posting date.

> [!NOTE]
> This article describes the functionality available in Microsoft Dynamics 365 Finance as of version **10.0.46**, which introduces the **(Preview) \[Italy\] Fiscal Journal modernization in Electronic Reporting** feature. This feature is enabled in **Feature management**. It replaces the [legacy SSRS-based Fiscal Journal for Italy](emea-ita-fiscal-journal.md) report with a modern, PDF-based solution built on [Electronic Reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md). It offers improved performance and enhances the ability to process large volumes of data across extended reporting periods, including up to a full fiscal year, while ensuring compliance with Italian fiscal requirements. This is a preview feature. By enabling this feature, you're confirming that you have read and understand the [preview feature terms and conditions](https://go.microsoft.com/fwlink/?linkid=2105274).
>
> The [legacy SSRS-based Fiscal Journal for Italy](emea-ita-fiscal-journal.md) is [announced for deprecation](../../get-started/removed-deprecated-features-finance.md#italian-fiscal-journal-in-ssrs-format) and replaced with **Fiscal Journal in Electronic Reporting** ER format. The legacy SSRS-based format for the Italian Fiscal Journal is fully replaced once the **\[Italy\] Fiscal Journal modernization in Electronic Reporting** feature becomes mandatory. Until the feature becomes mandatory, you can revert to the legacy SSRS-based format by disabling the **\[Italy\] Fiscal Journal modernization in Electronic Reporting** feature via the **Feature management** workspace.

Fiscal Journal for Italy includes fields for the following information:

- Line number
- Posting date
- Competence date
- Document number (voucher number)
- Date for document
- Ledger account number and name
- Customer/vendor account number and name
- Description
- Currency
- Debit or credit amount of the document

The report can optionally include the columns on running debit and credit to provide additional information.

## Prerequisites

### Import ER configurations

In Finance, import the following ER configurations from the Global repository.

| ER configuration name                        | Configuration type |
|----------------------------------------------|--------------------|
| **Ledger accounting reports**                | Model              |
| **Fiscal journal model (IT)**                | Model under the **Ledger accounting reports** model, that contains mapping for **Fiscal journal PDF (IT)** format |
| **Fiscal journal PDF (IT)**                  | Format (exporting) |

Learn more about how to import ER configurations in [Import Electronic reporting (ER) configurations from Dataverse](../global/workspace/gsw-import-er-config-dataverse.md).

Import the most recent versions of the configurations. The version description usually includes the number of the Microsoft Knowledge Base (KB) article that explains the changes that were introduced in the configuration version.

### Enable features in Feature management

Enable features in **Feature management** by following these steps.

1. In Dynamics 365 Finance, go to **Feature management** \> **All**.
1. In the feature list, find and select the following features:

    - **\[Italy\] Fiscal Journal modernization in Electronic Reporting** – This feature is available in Finance version **10.0.46**. This feature replaces the legacy SSRS-based Fiscal Journal report with the new **Fiscal journal PDF (IT)** ER format under the **Ledger accounting reports** model in Electronic Reporting. This new format offers improved performance and enhances the ability to process large volumes of data across extended reporting periods, including up to a full fiscal year, while ensuring compliance with Italian fiscal requirements. By adopting this feature, Italian entities can efficiently meet statutory reporting obligations while benefiting from a more scalable, performant, and maintainable reporting solution. When you enable this feature, it automatically configures the **Fiscal journal PDF (IT)** format in the **Accounting electronic report** field within the **General ledger parameters**. Once enabled, this Electronic Reporting (ER) format is used when navigating to **General ledger** > **Inquiries and reports** > **Fiscal journal**.
    - **Performance enhancement for general ledger dimension set balance calculation** – This feature must be enabled if you enable the **\[Italy\] Fiscal Journal modernization in Electronic Reporting** feature. For more information about the **Performance enhancement for general ledger dimension set balance calculation** feature, see [New financial dimension sets](../../general-ledger/financial-dimension-set-new.md).

1. Select **Enable now**.

### Set up ER format in General ledger parameters

This step is optional if you enable the **[Italy] Fiscal Journal modernization in Electronic Reporting** feature and the system automatically configures the **Fiscal journal PDF (IT)** format in the **Accounting electronic report** field within the **General ledger parameters**.

To set up the ER format in **General ledger parameters**, follow these steps.

1. In Finance, go to **General ledger** \> **Ledger setup** \> **General ledger parameters**.
1. On the **General ledger parameters** page, on the **Ledger** tab, in the **Accounting electronic report** field, select **Fiscal journal PDF (IT)**.

After you configure this setting, the system uses this Electronic Reporting (ER) format when you go to **General ledger** > **Inquiries and reports** > **Fiscal journal**.

## Generate Fiscal journal PDF for Italy

To Generate Fiscal journal PDF for Italy, follow these steps.

1. In Dynamics 365 Finance, go to **General ledger** > **Inquiries and reports** > **Fiscal journal**.
1. On the **Fiscal journal** dialog page, specify the report parameters.

| Parameter                                      | Description |
|------------------------------------------------|--------------------|
| From transaction date <br> To transaction date | Specify the period for which you want to generate the Fiscal journal PDF file.|
| Posting layer                                  | Select one or many **Posting layers** to include data in the Fiscal journal PDF file. |
| Include running balance                        | Select this checkbox to include two additional columns to your report for running debit and credit amounts.  |
| Follow previous \> Change page number          | The **Last page** field displays the final page number from the previous reporting period by default. This number is the starting point for page numbering in the new report. To override it, select the **Change page number** checkbox and enter the page number you want to start from instead. |
| Follow previous \> Change line number          | The **Last line number** field displays the final line number from the previous reporting period by default. This number is the starting point for page numbering in the new report. To override it, select the **Change line number** checkbox and enter the line number you want to start from instead. |
| Follow previous \> Change amount debit         | The **Last debit** field displays the running debit amount from the previous reporting period by default. This amount is the starting point for running debit amount in the new report. To override it, select the **Change amount debit** checkbox and enter the running debit amount you want to start from instead. |
| Follow previous \> Change amount credit        | The **Last credit** field displays the running credit amount from the previous reporting period by default. This amount is the starting point for running credit amount in the new report. To override it, select the **Change amount credit** checkbox and enter the running credit amount you want to start from instead. |

1. Select **OK** to generate the report.

A Fiscal journal report for a long time period, such as a quarter or a year, can include a large amount of data and take a long time to generate.
Therefore, use batch jobs.
The dialog for the Fiscal journal report includes a **Run in the background** tab where you can set up report generation in batch mode. Set the **Batch processing** option to **Yes**. For more information about batch processing, see [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md).

To review batch jobs or find a generated file, follow these steps.

1. In Dynamics 365 Finance, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**.
1. Find a line that relates to your job, and then select **Show log**. If nothing is shown, no messages were produced when the file was generated.
1. To view a file, select **Show files**, find the file that you need, and then select **Open**.

For more information about how to configure a destination for each ER format configuration and its output component, see [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md).

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
