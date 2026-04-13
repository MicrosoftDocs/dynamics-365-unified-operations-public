---
title: ER Use financial dimensions as a data source (Part 2 - Model mapping)
description: This article describes how to configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. (Part 2)
author: kfend
ms.date: 04/10/2026
ms.topic: how-to
audience: Developer, IT Pro
ms.reviewer: johnmichalak
ms.search.region: Global
ms.author: filatovm
ms.search.validFrom: 2016-06-30
ms.dyn365.ops.version: Version 7.0.0
ms.search.form: ERSolutionTable, ERDataModelDesigner, ERModelMappingTable, ERModelMappingDesigner, ERExpressionDesignerFormula
---

# ER Use financial dimensions as a data source (Part 2 - Model mapping)

[!include [banner](../../includes/banner.md)]

The following steps explain how a user assigned to the system administrator or electronic reporting developer role can configure an Electronic reporting (ER) model to use financial dimensions as a data source for ER reports. You can perform these steps in any company.

To complete these steps, you must first complete the steps in the "ER Use financial dimensions as a data source (Part 1: Design data model" procedure.

## Add required data sources to model mapping

1. Go to **Organization administration** > **Electronic reporting** > **Configurations**.
1. In the tree, select **Financial dimensions sample model**.
1. Select **Designer**.
1. Select **Map model to datasource**.
1. Select **New**.
1. In the **Definition** field, select **Entry**.
1. In the **Name** field, type **Dimensions data mapping**.
1. In the **Description** field, type **Dimensions data mapping**.
1. Select **Save**.
1. Select **Designer**.
1. In the tree, select **Dynamics 365 for Operations\Table**.
1. Select **Add root**.
1. In the **Name** field, type **Company**.
1. In the **Table** field, type **CompanyInfo**.
1. Select **OK**.
1. In the tree, select **Functions\Financial dimensions details**.
1. Select **Add root**.
    * This data source specifies how the scope of financial dimensions is defined for any report that uses this model as a data source.  
1. In the **Name** field, type a value.
1. Select **Yes** in the **Ask for dimensions** field.
    * Select **Yes** to allow the user to select dimensions at run-time on the User dialog form. If set to **No**, all financial dimensions of the current instance are used by default.  
1. In the **Financial dimensions selection** field, select **Legal entity**.
    * Select **All** to allow the user to select desired dimensions for the current instance in the **Lookup** field. Select **Legal entity** to allow the user to select dimensions for the company in the **Lookup** field. Select **Dimension** to allow the user to select dimensions using a single dimension set.  
1. Select **Yes** in the **Ask for main account** field.
    * Set **Ask for main account** to **Yes** to allow users to select the main account as part of the list of dimensions. If set to **No**, the main account isn't included in the list of dimensions and the **Is main account mandatory** option is enabled. If **Is main account mandatory** is set to **Yes**, include the main account in the list of dimensions regardless of the user's selection.  
1. Select **OK**.

   :::image type="content" source="../media/er-financial-dimensions-guides-model-mapping1.png" alt-text="Screenshot of financial dimensions details data source properties slide out.":::

1. In the tree, select **Dynamics 365 for Operations\Table records**.
1. Select **Add root**.
1. In the **Name** field, type **LedgerJournal**.
1. Select **Yes** in the **Ask for query** field.
1. In the **Table** field, type **LedgerJournalTable**.
1. Select **OK**.

   :::image type="content" source="../media/er-financial-dimensions-guides-model-mapping2.png" alt-text="Screenshot of model mapping designer page, Table records data source type.":::

## Map data model elements to added data sources

1. In the tree, expand **Journal**.
1. In the tree, expand **Journal\Transaction**.
1. In the tree, expand **Journal\Transaction\Dimensions data**.
1. In the tree, expand **Dimensions setting**.
1. In the tree, expand **LedgerJournal**.
1. In the tree, expand **LedgerJournal\<Relations**.
1. In the tree, expand **LedgerJournal\<Relations\LedgerJournalTrans**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Voucher**.
1. In the tree, select **Journal\Transaction\Voucher**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)**.
    * For any reference to financial dimensions that you set to, for example, `LedgerDimension`, a corresponding data source item is available (`LedgerDimension.Dimension`). This data source item offers the financial dimensions of that dimensions set as the record's list.  
1. In the tree, expand **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)**.
1. In the tree, expand **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions**.
1. In the tree, expand **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions\Value**.
1. In the tree, expand **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions\Definition**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions\Definition\Name**.
1. In the tree, select **Journal\Transaction\Dimensions data\Name**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions\Value\Description**.
1. In the tree, select **Journal\Transaction\Dimensions data\Description**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions\Value\Code**.
1. In the tree, select **Journal\Transaction\Dimensions data\Code**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Account.Dimension(LedgerDimension.Dimension)\Main account and dimensions**.
1. In the tree, select **Journal\Transaction\Dimensions data**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Debit(AmountCurDebit)**.
1. In the tree, select **Journal\Transaction\Debit**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Date(TransDate)**.
1. In the tree, select **Journal\Transaction\Date**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Currency(CurrencyCode)**.
1. In the tree, select **Journal\Transaction\Currency**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans\Credit(AmountCurCredit)**.
1. In the tree, select **Journal\Transaction\Credit**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\<Relations\LedgerJournalTrans**.
1. In the tree, select **Journal\Transaction**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal\Journal batch number(JournalNum)**.
1. In the tree, select **Journal\Batch**.
1. Select **Bind**.
1. In the tree, select **LedgerJournal**.
1. In the tree, select **Journal**.
1. Select **Bind**.
1. In the tree, expand **Dimensions**.
1. In the tree, expand **Dimensions\Main account and dimensions**.
1. In the tree, expand **Dimensions\Main account and dimensions\Definition**.
1. In the tree, select **Dimensions\Main account and dimensions\Definition\Name**.
1. In the tree, select **Dimensions setting\Code**.
1. Select **Bind**.
1. In the tree, select **Dimensions\Main account and dimensions\Definition\Report column name**.
1. In the tree, select **Dimensions setting\Name**.
1. Select **Bind**.
1. In the tree, select **Dimensions\Main account and dimensions**.
1. In the tree, select **Dimensions setting**.
1. Select **Bind**.
1. In the tree, select **Company**.
1. Click **Edit**.
1. In the **expressionAsStringText** field, enter `Company.'find()'.'name()'`.
    * `Company.'find()'.'name()'`  
1. Select **Save**.

   :::image type="content" source="../media/er-financial-dimensions-guides-model-mapping4.png" alt-text="Screenshot of ER model mapping designer page.":::

1. Close the page.
1. Select **Save**.
1. Close the page.

## Complete this draft model's version

1. Close the page.
1. Close the page.
1. Select **Change status**.
1. Select **Complete**.
1. Select **OK**.

   :::image type="content" source="../media/er-financial-dimensions-guides-model-mapping5.png" alt-text="Screenshot of ER Configurations page.":::

[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]
