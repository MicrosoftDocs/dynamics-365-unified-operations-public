---
title: ER Design a configuration for generating reports in OPENXML format (November 2016)
description: This article describes how to create a new Electronic reporting configuration that contains a template for generating electronic documents in OPENXML format.
author: kfend
ms.date: 04/23/2021
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
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

This article explains how a user in the System Administrator or Electronic Reporting Developer role can create a new Electronic reporting (ER) configuration that contains a template for generating electronic documents in OPENXML format. This configuration will be used for processing vendor payments.

In this example, you will create a configuration for sample company, Litware, Inc. These steps can be performed in GBSI company.

To complete these steps, you must first complete the steps in the "Create a configuration provider and mark it as active" procedure. You must also have an Excel file which will be imported when creating the template. This file can be accessed from the [Template of Payment Report](https://download.microsoft.com/download/3/f/0/3f0658b2-042c-43cf-a776-0f4c7f7cfe4e/SampleVendPaymWsReport.xlsx).


## Upload the Payments data model configuration
1. In the navigation pane, go to **Modules > Organization administration > Workspaces > Electronic reporting**.
2. In the list, mark the configuration provider for sample company, Litware, Inc. If you don't see this configuration provider, you must first complete the steps in [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).
3. Select **Set active**.
4. Select **Repositories**. Select a repository for the Operations Resources type, if available. If its available, skip the following steps about creating a new repository.  
5. Select **Add** to open the drop dialog.
6. In the **Configuration repository type** field, enter `Operations resourcesdd`.
7. Select **Create repository**.
8. Select **OK**.
9. Select **Open**.
10. In the tree, select **Payment model**.
11. Select **Import**. Import this data model. It will be used as a data source in a new format configuration. Skip this step if this configuration has been already imported.  
12. Select **Yes**.
13. Close the pages until you return to the Electronic reporting page.

## Create a new format configuration
1. Select **Reporting configurations**.
2. In the tree, select **Payment model**.
3. Select **Create configuration** to open the drop dialog.
4. In the **New** field, enter `Format based on data model PaymentModel`. Create a format that is based on the PaymentModel data model.
5. In the **Name** field, type `Sample worksheet report`. Sample worksheet report  
6. In the **Description** field, type `Sample worksheet report for vendors' payments`. Sample worksheet report for vendors' payments.  
7. In the **Data model definition** field, enter or select a value. Select the **CustomerCreditTransferInitiation** definition.  
8. Select **Create configuration**.

## Design a new document in OPENXML worksheet format
1. In the tree, select **Payment model\Sample worksheet report**.
2. Select **Designer**.
3. On the Action Pane, select **Import**.
4. Select **Import from Excel**.
5. Select **Attachments**. Attach the existing Excel document as a template.  
6. Select **New**.
7. Select **File**. Point to the existing Excel file.  
8. Close the page.
9. In the **Template** field, enter or select a value. Select the attached Excel file to be used as a template.  
10. Select **OK**. Note that ER format components have been created in the designing format based on the structure of the referring MS Excel document (named ranges).  

## Create a new data source to calculate totals by currency codes
1. Select the **Mapping** tab.
2. Select **Add root** to open the drop dialog.
3. In the tree, select **Functions\Group by**.
4. In the **Name** field, type `PaymentByCurrency`.
5. Select **Edit group by**.
6. In the tree, expand **model**, then select **model\Payments**.
7. Select **Add field to**.
8. Select **What to group**.
9. In the tree, expand **model\Payments**, then select **model\Payments\Currency**.
10. Select **Add field to**.
11. Select **Grouped fields**.
12. In the tree, select **model\Payments\Instructed Amount(InstructedAmount)**.
13. Select **Add field to**, then select **Aggregation fields**.
14. In the **Method** field, select an option. Select the **SUM aggregation** function.  
15. In the **Name** field, type `TotalInstructuredAmount`.
16. Select **Save**.
17. Close the page.
18. Select **OK**.

## Map format components to data sources
1. In the tree, select **model\Payments\Initiating Party(InitiatingParty)\Name** and **Excel\ReportHeader\CompanyName**.
2. Select **Bind**.
3. In the tree, select **model\Payments\Creditor\Identification\Source ID(SourceID)** and **Excel\PaymLines\VendAccountName**.
4. Select **Bind**.
5. In the tree, select **model\Payments\Creditor\Name** and **Excel\PaymLines\VendName**.
6. Select **Bind**.
7. In the tree, select **model\Payments\Creditor Agent(CreditorAgent)\Name** and **Excel\PaymLines\Bank**.
8. Select **Bind**.
9. In the tree, select **model\Payments\Creditor Agent(CreditorAgent)\Routing Number(RoutingNumber)** and **Excel\PaymLines\RoutingNumber**.
10. Select **Bind**.
11. In the tree, select **model\Payments\Creditor Account(CreditorAccount)\Identification\Number** and **Excel\PaymLines\AccountNumber**.
12. Select **Bind**.
13. In the tree, select **model\Payments\Instructed Amount(InstructedAmount)** and **Excel\PaymLines\Debit**.
14. Select **Bind**.
15. In the tree, select **model\Payments\Currency** and **Excel\PaymLines\Currency**.
16. Select **Bind**.
17. In the tree, select **PaymentByCurrency\grouped\Currency** and **Excel\SummaryLines\SummaryCurrency**.
18. Select **Bind**.
19. In the tree, select **PaymentByCurrency\aggregated\TotalInstructuredAmount** and **Excel\SummaryLines\SummaryAmount**.
20. Select **Bind**.
21. In the tree, select **PaymentByCurrency** and **Excel\SummaryLines**.
22. Select **Bind**.
23. In the tree, select **model\Payments** and **Excel\PaymLines**.
24. Select **Bind**.
25. Select **Save**, then close the page.

## Use the created configuration for payments processing
1. Select **Change status**.
2. Select **Complete**.
3. Select **OK**.
4. In the navigation pane, go to **Modules > Accounts payable > Payment setup > Methods of payment**.
5. Use the Quick Filter to filter on the **Method of payment** field with a value of **Electronic**.
6. Select **Edit**.
7. Expand the **File formats** section.
8. Select **Yes** in the **Generic electronic reporting** field.
9. In the **Export format configuration** field, enter or select a value. Select the **Sample worksheet report** configuration.  
10. Select **Save**.
11. Close the page.

## Use the created configuration for testing of payment journals processing
1. In the navigation pane, go to **Modules > Accounts payable > Payments > Payment journal**.
2. Select **New** to create a new payment journal.
3. In the **Name** field, type **VendPay**.
4. Select **Lines**.
5. In the **Account** field, specify the values `GB_SI_000001`.
6. Set **Debit** to `1000`.
7. Select **New**.
8. In the **Account** field, specify the values `GB_SI_000005`.
9. Set **Debit** to `2000`.
10. In the **Currency** field, type `EUR`.
11. In the **Offset account** field, specify the values `GBSI OPER`.
12. In the **Method of payment** field, type `Electronic`.
13. Select **Save**.
14. Select **Generate payments**.
15. In the **Method of payment** field, type `Electronic`.
16. In the **File name** field, type `Payments`.
17. In the **Bank account** field, type `GBSI OPER`.
18. Select **OK**, then select **OK** again. Review the created worksheet, including details of payment lines as well as totals for each currency code used in this payment message.  



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
