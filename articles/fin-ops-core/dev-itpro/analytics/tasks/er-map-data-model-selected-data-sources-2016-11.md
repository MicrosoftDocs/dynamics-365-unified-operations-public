---
title: ER Map data model to selected data sources
description: This article describes how to map an Electronic reporting (ER) data model to selected Microsoft Dynamics 365 Finance data sources.
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERWorkspace, ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner
---

# ER Map data model to selected data sources

[!include [banner](../../includes/banner.md)]

The following steps explain how a user in the System Administrator or Electronic Reporting Developer role can map an Electronic reporting (ER) data model to selected data sources. You use this model mapping as a data source in a format configuration that manages electronic payment documents. In this example, you map a data model for sample company, Litware, Inc. to data sources. To complete these steps, you must first complete the steps in the "Select data sources for model mapping" procedure.

## Open ER configurations tree

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
1. Select **Configurations**.

## Select created model mapping

1. In the tree, select **Payments (simplified model)**.
   - Make sure that you created the model configuration **Payments (simplified model)**. Otherwise, stop now and return after completion of the task guide **Create a new configuration with data model of the selected domain**.  
1. Select **Model designer**.
1. Select **Map model to datasource**.
1. Select the **CT mapping** record.
   - CT mapping  

## Bind created data sources to data model elements

1. Click Designer.
1. In the tree, select 'Processing date & time(ProcessingDateTime)'.
1. In the tree, select 'Processing date(ProcessingDateTime)'.
1. Click Bind.
1. In the tree, select 'Payment message identification(MessageIdentification)'.
1. In the tree, expand 'Transactions'.
1. In the tree, select 'Transactions\Journal batch number(JournalNum)'.
1. Click Bind.
1. In the tree, select 'Payments'.
1. In the tree, select 'Transactions'.
1. Click Bind.
1. In the tree, expand 'Payments= Transactions'.
1. In the tree, expand 'Payments= Transactions\Creditor'.
1. In the tree, expand 'Payments= Transactions\Creditor\Account'.
1. In the tree, select 'Payments= Transactions\Creditor\Account\Currency code(Currency)'.
1. In the tree, expand 'Transactions\vendBankAccountInTransactionCompany()'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Currency(CurrencyCode)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Creditor\Account\IBAN code(IBAN)'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\IBAN(BankIBAN)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Creditor\Account\Number'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Bank account number(AccountNum)'.
1. Click Bind.
1. In the tree, expand 'Payments= Transactions\Creditor\Agent'.
1. In the tree, select 'Payments= Transactions\Creditor\Agent\Name'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Name'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Creditor\Agent\Routing number(RoutingNumber)'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\Routing number(RegistrationNum)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Creditor\Agent\SWIFT code(SWIFT)'.
1. In the tree, select 'Transactions\vendBankAccountInTransactionCompany()\SWIFT code(SWIFTNo)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Creditor\Name'.
1. In the tree, expand 'Transactions\findVendTable()'.
1. In the tree, select 'Transactions\findVendTable()\name()'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Currency code(Currency)'.
1. In the tree, expand 'Transactions\>Relations'.
1. In the tree, expand 'Transactions\>Relations\Currency table(Currency)'.
1. In the tree, select 'Transactions\>Relations\Currency table(Currency)\Currency code(CurrencyCodeISO)'.
1. Click Bind.
1. In the tree, expand 'Payments= Transactions\Debtor'.
1. In the tree, expand 'Payments= Transactions\Debtor\Account'.
1. In the tree, select 'Payments= Transactions\Debtor\Account\Currency code(Currency)'.
1. In the tree, select 'Bank Account(BankAccount)'.
1. In the tree, expand 'Bank Account(BankAccount)'.
1. In the tree, select 'Bank Account(BankAccount)\Currency(CurrencyCode)'.
1. Click Bind.
1. In the tree, select 'Bank Account(BankAccount)\IBAN'.
1. In the tree, select 'Payments= Transactions\Debtor\Account\IBAN code(IBAN)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Debtor\Account\Number'.
1. In the tree, select 'Bank Account(BankAccount)\Bank account number(AccountNum)'.
1. Click Bind.
1. In the tree, expand 'Payments= Transactions\Debtor\Agent'.
1. In the tree, select 'Payments= Transactions\Debtor\Agent\Name'.
1. In the tree, select 'Bank Account(BankAccount)\Name'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Debtor\Agent\Routing number(RoutingNumber)'.
1. In the tree, select 'Bank Account(BankAccount)\Routing number(RegistrationNum)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Debtor\Agent\SWIFT code(SWIFT)'.
1. In the tree, select 'Bank Account(BankAccount)\SWIFT code(SWIFTNo)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Debtor\Name'.
1. In the tree, select 'Company information(Company)'.
1. In the tree, expand 'Company information(Company)'.
1. In the tree, select 'Company information(Company)\Name'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Description'.
1. In the tree, select 'Transactions\Description(Txt)'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\End to end identification code(End2EndID)'.
1. In the tree, select 'Transactions\$EndToEndID'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Instructed amount(InstructedAmount)'.
1. In the tree, select 'Transactions\$Amount'.
1. Click Bind.
1. In the tree, select 'Payments= Transactions\Transaction date(TransactionDate)'.
1. In the tree, select 'Transactions\Date(TransDate)'.
1. Click Bind.

## Validate created mapping

1. Click Validate.
    * Validate the new mapping to ensure that all bindings are okay.  
1. Click the arrow to expand or collapse the Error List section.
1. Click Save.
1. Close the page.
1. Close the page.
1. Close the page.

## Change the status of the current version of model configuration

1. Click Change status.
    * Change the status of designed model configuration – from Draft to Completed to make it available for payment format design.  
1. Click Complete.
    * Select Complete.  
1. In the Description field, type a value.
    * For example, 'version 1'.  
1. Click OK.
1. Select the completed version of the current configuration.
    * Note that the created configuration is saved as completed version 1.    

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
