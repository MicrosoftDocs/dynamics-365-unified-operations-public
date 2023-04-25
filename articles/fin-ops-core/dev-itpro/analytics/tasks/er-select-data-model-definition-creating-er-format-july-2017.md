---
title: Select data model definitions when you create formats
description: To complete the steps in this procedure, you must first complete the procedure, ER Create a configuration provider and mark it as active.
author: kfend
ms.date: 06/19/2017
ms.topic: how-to
ms.prod: 
ms.technology: 
audience: Application User
ms.reviewer: kfend
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---
# Select data model definitions when you create formats

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, ER Create a configuration provider and mark it as active. 

This procedure shows how a model's root item can be selected as a data model definition for inserting an Electronic reporting (ER) format configuration that is designed to generate electronic documents. In this procedure, you will add a new ER format configuration for the sample company Litware, Inc. 

This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. The steps can be completed by using any dataset.

1. Go to Organization administration > Workspaces > Electronic reporting.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as Active. If you don't see this configuration provider, complete the steps in the procedure, Create a configuration provider and mark it as active.  
2. Click Reporting configurations.

## Add a new ER data model configuration
1. Click Create configuration to open the drop dialog.
    * We add a new ER model configuration containing a data model that is designed to be used as data source for generation ER reports.  
2. In the Name field, type 'Payment model (fictitious)'.
    * Payment model (fictitious)  
3. Click Create configuration.
4. Click Designer.
    * Open the ER designer to specify the structure of data model of this configuration.  
    * Assume that we design the data model for payments business domain to support 2 payment methods – credit transfer and direct debit ones.  
5. Click New to open the drop dialog.
6. In the Name field, type 'Payments – credit transfer'.
    * Payments – credit transfer  
7. Click Add.
8. Click New to open the drop dialog.
9. In the New node as a field, enter 'Model root'.
10. In the Name field, type 'Payments – direct debit'.
    * Payments – direct debit  
11. Click Add.
12. Click Save.
13. Close the page.
14. Click Change status.
    * Complete the draft version of the model to make it available in new model mappings and formats.  
15. Click Complete.
16. Click OK.

## Start to enter a new ER format configuration
1. Click Create configuration to open the drop dialog.
2. In the New field, enter 'Format based on data model Payment model (fictitious)'.
3. In the Data model definition field, enter or select a value.
    * Note that all root items of the selected data model are currently available for selection as a data model definition. You can continue to design your format by using any of the required root items of the data model. A missing model mapping for the selected root item doesn't prevent you from continuing.  
4. Close the page.

## Add a new ER model mapping configuration
1. Click Create configuration to open the drop dialog.
2. In the New field, enter 'Model Mapping based on data model Payment model (fictitious)'.
3. In the Name field, type 'Payment model mappings (fictitious)'.
    * Payment model mappings (fictitious)  
4. In the Data model definition field, enter or select a value.
5. Click Create configuration.

## Design ER model mappings
1. Click Designer.
    * Use the ER designer to specify the model mappings for the required root items.  
2. Click Designer.
    * Simulate setting of selected model mapping for the selected model's root item.  
3. In the tree, select 'Dynamics 365 for Operations\Table records'.
4. Click Add root.
5. In the Name field, type 'Ledger'.
6. In the Table field, type 'LedgerJournalTrans'.
    * LedgerJournalTrans  
7. Click OK.
8. Click Save.
9. Close the page.
10. Close the page.

## Start to enter another new ER format configuration
1. In the tree, select 'Payment model (fictitious)'.
2. Click Create configuration to open the drop dialog.
3. In the New field, enter 'Format based on data model Payment model (fictitious)'.
4. In the Data model definition field, enter or select a value.
    * Note that now only one root item is available to map to the application data sources. When at least one model mapping is introduced, only the model's root items that are mapped to application data sources can be selected as a model definition while the ER format is added.   
5. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
