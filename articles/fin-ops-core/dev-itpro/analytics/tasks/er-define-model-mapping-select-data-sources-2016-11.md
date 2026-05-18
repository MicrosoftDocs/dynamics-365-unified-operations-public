---
title: Define ER model mappings and select data sources for them
description: This article describes how a System Administrator or an Electronic Reporting Developer can select data sources for an Electronic reporting data model.
author: twheeloc
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula
---

# Define ER model mappings and select data sources for them

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can select data sources for an Electronic reporting (ER) data model. Bind the data sources to individual components of the selected data model at design time. The data sources populate business data to that data model at runtime. In this example, you select data sources for an existing data model created for the sample company Litware, Inc.

## Open the Electronic Reporting configurations tree

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Reporting configurations**.

## Insert a new model mapping

1. In the tree, select **Payments (simplified model)**.
1. Select **Designer**.
1. Select **Map model to datasource**.
1. Select **New**.
    * This action creates a new record that maps the data model to data sources. In this example, you map the data model to data sources for the desired payment type: credit transfer. You can design more than one mapping for a particular data model. For example, you could create a mapping for different types of payments, such as for direct debit or for credit transfers. In this example, you create a mapping for credit transfers.  
1. In the **Name** field, type **CT mapping**.  
1. In the **Description** field, type **Payment model mapping CT**.
1. In the **Definition** field, type **CustomerCreditTransferInitiation**.
1. Resolve changes the Definition.
1. Select **Save**.

## Define required data sources for the current model mapping

1. Select **Designer**.
1. In the tree view, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
    * Enter this data source to access payment transactions.  
1. In the **Name** field, type **Transactions**.
1. In the **Label** field, enter **Transactions**.
1. In the **Help** field, enter **Ledger journal lines**.
1. In the **Ask for query** field, select **Yes**.  
1. In the **Table** field, type **LedgerJournalTrans**.
1. Select **OK**.
    * Select the LedgerJournalTrans table as a data source for the current data model.  
1. In the tree view, select **Functions\Calculated field**.
1. Select **Add** to add a new calculated field.  
1. In the **Name** field, type **$EndToEndID**.
1. Select **Edit formula**.
1. In the tree view, select **String\CONCATENATE**.
1. Select **Add function**.
1. In the tree view, expand **Transactions**.
1. In the tree view, select **Transactions\Voucher**.
1. Select **Add data source**.
1. In the **Formula** field, enter **CONCATENATE(Transactions.Voucher, "-",**.
    * Type `, "-",` at the end of the formula.  
1. In the tree view, select **String\TEXT**.
1. Select **Add function**.
1. In the tree view, select **Transactions\Record-ID(RecId)**.
1. Select **Add data source**.
1. In the **Formula** field, enter **CONCATENATE(Transactions.Voucher, "-", TEXT(Transactions.RecId))**.
    * Type `))` at the end of the formula.  
1. Select **Save**.
    * Make sure that no errors exist for the created formula. See the **ERRORS** tab below the formula editor control.  
1. Close the page.
1. Select **OK**.
    * Add the calculated field to this data source.  
1. Select **Add** to add a new calculated field.  
1. In the **Name** field, type **$Amount**.
1. Select **Edit formula**.
1. In the tree view, expand **Transactions**.
1. In the tree view, select **Transactions\Debit(AmountCurDebit)**.
1. Select **Add data source**.
1. In the **Formula field**, enter **Transactions.AmountCurDebit -**.
    * Type `-` at the end of the formula.  
1. In the tree view, select **Transactions\Credit(AmountCurCredit)**.
1. Select **Add data source**.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
    * This step adds the **$Amount** calculated field to the selected data source for the current data model.  
1. In the tree view, select **Transactions\$Amount**.
1. In the tree view, expand **Transactions**.
1. In the tree view, expand or collapse **Transactions\$Amount**.
1. In the tree view, expand or collapse **Transactions**.
1. In the tree view, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
    * Enter this data source to access the company's bank account details.  
1. In the **Name** field, type **BankAccount**.
1. In the **Label** field, enter **Bank Account**.
1. In the **Help** field, enter **Bank Account**.
1. Select **Yes** in the **Ask for query** field.
1. In the **Table** field, type **BankAccountTable**.
1. Select **OK**.
    * Select the **BankAccountTable** table as a data source for the current data model.  
1. Select **Add root**.
    * Enter this data source to access the company's requisites.  
1. In the **Name** field, type **Company**.
1. In the **Label** field, type a value.
1. In the **Help** field, enter **Company information**.
1. Select **Yes** in the **Ask for query** field.
1. In the **Table** field, type **CompanyInfo**.
1. Select **OK**.
    * Select the **CompanyInfo** table as a data source for the current data model.  
1. In the tree view, select **Functions\Calculated field**.
1. Select **Add root**.
    * Insert a calculated field as a new data source.  
1. In the **Name** field, type **ProcessingDateTime**.
1. In the **Label** field, enter **Processing date & time**.
1. Select **Edit formula**.
1. In the tree, select `Date/time\SESSIONNOW`.
1. Select **Add function**.
1. Select **Save**.
1. Close the page.
1. Select **OK**.
    * Add the **ProcessingDateTime** calculated field as a data source for the current data model.  
1. Select **Save**.
1. Close the page.

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
