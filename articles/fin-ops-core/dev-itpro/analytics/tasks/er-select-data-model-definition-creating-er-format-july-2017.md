---
title: Select data model definitions when you create formats
description: To complete the steps in this procedure, you must first complete the procedure, ER Create a configuration provider and mark it as active.
author: kfend
ms.date: 02/26/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: AX 7.0.0
---

# Select data model definitions when you create formats

[!include [banner](../../includes/banner.md)]

To complete the steps in this procedure, you must first complete the procedure, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).

This procedure shows how to select a model's root item as a data model definition for inserting an Electronic reporting (ER) format configuration that's designed to generate electronic documents. In this procedure, you add a new ER format configuration for the sample company Litware, Inc. 

This procedure is intended for users who have the System administrator or Electronic reporting developer role assigned to them. You can complete the steps by using any dataset.

1. Go to **Organization administration** > **Workspaces** > **Electronic reporting**.
    * Make sure that the configuration provider for the sample company, Litware, Inc., is available and marked as **Active**. If you don't see this configuration provider, complete the steps in the procedure, [Create configuration providers and mark them as active](er-configuration-provider-mark-it-active-2016-11.md).    
1. Select **Reporting configurations**.

## Add a new ER data model configuration

1. Select **Create configuration** to open the **Drop** dialog.
    * Add a new ER model configuration containing a data model that is designed for use as a data source in generating ER reports.    
1. In the **Name** field, enter `Payment model (fictitious)`.
    * Payment model (fictitious)  
1. Select **Create configuration**.
1. Select **Designer**.
    * Open the ER designer to specify the structure of the data model for this configuration.  
    * Design the data model for the payments business domain to support two payment methods – credit transfer and direct debit.  
1. Select **New** to open the form.
1. In the **Name** field, enter `Payments – credit transfer`.
    * Payments – credit transfer  
1. Select **Add**.
1. Select **New** to open the form.
1. In the **New node as a field**, enter `Model root`.
1. In the **Name** field, enter `Payments – direct debit`.
    * Payments – direct debit  
1. Select **Add**.
1. Select **Save**.
1. Close the page.
1. Select **Change status**.
    * Complete the draft version of the model to make it available in new model mappings and formats.  
1. Select **Complete**.
1. Select **OK**.

## Start to enter a new ER format configuration

1. Select **Create configuration** to open the **Drop** dialog.
1. In the **New** field, enter *Format based on data model Payment model (fictitious)*.
1. In the **Data model definition** field, enter or select a value.
    * You can select any root item from the chosen data model as the data model definition. You can use any required root item from the data model to design your format. If a model mapping is missing for the selected root item, you can still continue.  
1. Close the page.

## Add a new ER model mapping configuration

1. Select **Create configuration** to open the **Drop** dialog.
1. In the **New** field, enter *Model Mapping based on data model Payment model (fictitious)*.
1. In the **Name** field, enter *Payment model mappings (fictitious)*.
    * Payment model mappings (fictitious)  
1. In the **Data model definition** field, enter or select a value.
1. Select **Create configuration**.

## Design ER model mappings

1. Select **Designer**.
    * Use the ER designer to specify the model mappings for the required root items.  
1. Select **Designer**.
    * Simulate setting of selected model mapping for the selected model's root item.  
1. In the tree, select `Dynamics 365 for Operations\Table records`.
1. Select **Add root**.
1. In the **Name** field, type `Ledger`.
1. In the **Table** field, type `LedgerJournalTrans`.
    * LedgerJournalTrans  
1. Select **OK**.
1. Select **Save**.
1. Close the page.
1. Close the page.

## Start to enter another new ER format configuration

1. In the tree, select `Payment model (fictitious)`.
1. Select **Create configuration** to open the **Drop** dialog.
1. In the **New** field, enter *Format based on data model Payment model (fictitious)*.
1. In the **Data model definition** field, enter or select a value.
    * Only one root item is available to map to the application data sources. When you add at least one model mapping, you can select only the model's root items that are mapped to application data sources as a model definition while the ER format is added.
1. Close the page.



[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
