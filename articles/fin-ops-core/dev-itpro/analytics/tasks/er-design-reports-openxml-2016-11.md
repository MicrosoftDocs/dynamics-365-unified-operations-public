---
title: ER Design a configuration for generating reports in OPENXML format (November 2016)
description: This article describes how to create a new Electronic reporting configuration that contains a template for generating electronic documents in OPENXML format.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: 
  - ERWorkspace, ERVendorPart, ERSolutionRepositoryTable, ERSolutionRepositoryCreateDropDialog, ERSolutionImport
  - ERSolutionTable, ERSolutionCreateDropDialog, EROperationDesigner, ERDataSourceAddDropDialog, ERModelGroupByFunctionEditor, VendPaymMode, LedgerJournalTable, LedgerJournalTransVendPaym
---

# ER Design a configuration for generating reports in OPENXML format (November 2016)

[!include [banner](../../includes/banner.md)]

This article explains how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a template for generating electronic documents in OPENXML format. Use this configuration for processing vendor payments.

In this example, you create a configuration for sample company, Litware, Inc. You can perform these steps in GBSI company.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure. You must also have an Excel file that you import when creating the template. You can access this file from the [Template of Payment Report](https://download.microsoft.com/download/3/f/0/3f0658b2-042c-43cf-a776-0f4c7f7cfe4e/SampleVendPaymWsReport.xlsx).

## Upload the Payments data model configuration

1. In the navigation pane, go to **Modules > Organization administration > Workspaces > Electronic reporting**.
1. In the list, select the configuration provider for sample company, Litware, Inc. If you don't see this configuration provider, you must first complete the steps in [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).
1. Select **Set active**.
1. Select **Repositories**. Select a repository for the Operations Resources type, if available. If it's available, skip the following steps about creating a new repository.  
1. Select **Add** to open the drop dialog.
1. In the **Configuration repository type** field, enter `Operations resourcesdd`.
1. Select **Create repository**.
1. Select **OK**.
1. Select **Open**.
1. In the tree, select **Payment model**.
1. Select **Import**. Import this data model. It serves as a data source in a new format configuration. Skip this step if this configuration is already imported.  
1. Select **Yes**.
1. Close the pages until you return to the Electronic reporting page.

## Create a new format configuration

1. Select **Reporting configurations**.
1. In the tree, select **Payment model**.
1. Select **Create configuration** to open the drop dialog.
1. In the **New** field, enter `Format based on data model PaymentModel`. Create a format that is based on the PaymentModel data model.
1. In the **Name** field, type `Sample worksheet report`. Sample worksheet report  
1. In the **Description** field, type `Sample worksheet report for vendors' payments`. Sample worksheet report for vendors' payments.  
1. In the **Data model definition** field, enter or select a value. Select the **CustomerCreditTransferInitiation** definition.  
1. Select **Create configuration**.

## Design a new document in OPENXML worksheet format

1. In the tree, select **Payment model\Sample worksheet report**.
1. Select **Designer**.
1. On the Action Pane, select **Import**.
1. Select **Import from Excel**.
1. Select **Attachments**. Attach the existing Excel document as a template.  
1. Select **New**.
1. Select **File**. Point to the existing Excel file.  
1. Close the page.
1. In the **Template** field, enter or select a value. Select the attached Excel file to be used as a template.  
1. Select **OK**. Note that ER format components are created in the designing format based on the structure of the referring MS Excel document (named ranges).    

## Create a new data source to calculate totals by currency codes

1. Select the **Mapping** tab.
1. Select **Add root** to open the drop dialog.
1. In the tree, select **Functions\Group by**.
1. In the **Name** field, type `PaymentByCurrency`.
1. Select **Edit group by**.
1. In the tree, expand **model**, and then select **model\Payments**.
1. Select **Add field to**.
1. Select **What to group**.
1. In the tree, expand **model\Payments**, and then select **model\Payments\Currency**.
1. Select **Add field to**.
1. Select **Grouped fields**.
1. In the tree, select **model\Payments\Instructed Amount(InstructedAmount)**.
1. Select **Add field to**, and then select **Aggregation fields**.
1. In the **Method** field, select an option. Select the **SUM aggregation** function.  
1. In the **Name** field, type `TotalInstructuredAmount`.
1. Select **Save**.
1. Close the page.
1. Select **OK**.

## Map format components to data sources

1. In the tree, select **model\Payments\Initiating Party(InitiatingParty)\Name** and **Excel\ReportHeader\CompanyName**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Creditor\Identification\Source ID(SourceID)** and **Excel\PaymLines\VendAccountName**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Creditor\Name** and **Excel\PaymLines\VendName**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Creditor Agent(CreditorAgent)\Name** and **Excel\PaymLines\Bank**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Creditor Agent(CreditorAgent)\Routing Number(RoutingNumber)** and **Excel\PaymLines\RoutingNumber**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Creditor Account(CreditorAccount)\Identification\Number** and **Excel\PaymLines\AccountNumber**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Instructed Amount(InstructedAmount)** and **Excel\PaymLines\Debit**.
1. Select **Bind**.
1. In the tree, select **model\Payments\Currency** and **Excel\PaymLines\Currency**.
1. Select **Bind**.
1. In the tree, select **PaymentByCurrency\grouped\Currency** and **Excel\SummaryLines\SummaryCurrency**.
1. Select **Bind**.
1. In the tree, select **PaymentByCurrency\aggregated\TotalInstructuredAmount** and **Excel\SummaryLines\SummaryAmount**.
1. Select **Bind**.
1. In the tree, select **PaymentByCurrency** and **Excel\SummaryLines**.
1. Select **Bind**.
1. In the tree, select **model\Payments** and **Excel\PaymLines**.
1. Select **Bind**.
1. Select **Save**, and then close the page.

## Use the created configuration for payments processing

1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.
1. In the navigation pane, go to **Modules > Accounts payable > Payment setup > Methods of payment**.
1. Use the Quick Filter to filter on the **Method of payment** field with a value of **Electronic**.
1. Select **Edit**.
1. Expand the **File formats** section.
1. Select **Yes** in the **Generic electronic reporting** field.
1. In the **Export format configuration** field, enter or select a value. Select the **Sample worksheet report** configuration.  
1. Select **Save**.
1. Close the page.

## Use the created configuration to test payment journal processing

1. In the navigation pane, go to **Modules > Accounts payable > Payments > Payment journal**.
1. Select **New** to create a new payment journal.
1. In the **Name** field, type **VendPay**.
1. Select **Lines**.
1. In the **Account** field, enter the value `GB_SI_000001`.
1. Set **Debit** to `1000`.
1. Select **New**.
1. In the **Account** field, enter the value `GB_SI_000005`.
1. Set **Debit** to `2000`.
1. In the **Currency** field, type `EUR`.
1. In the **Offset account** field, enter the value `GBSI OPER`.
1. In the **Method of payment** field, type `Electronic`.
1. Select **Save**.
1. Select **Generate payments**.
1. In the **Method of payment** field, type `Electronic`.
1. In the **File name** field, type `Payments`.
1. In the **Bank account** field, type `GBSI OPER`.
1. Select **OK**, and then select **OK** again. Review the created worksheet, including details of payment lines as well as totals for each currency code used in this payment message.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
