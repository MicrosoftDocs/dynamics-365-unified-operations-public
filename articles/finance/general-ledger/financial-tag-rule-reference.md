---
title: Financial tag rule reference (preview)
description: Learn about financial tags rules with Microsoft Power Fx formulas.
author: twheeloc
ms.author: twheeloc
ms.topic: article
ms.date: 02/12/2025
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

[!include [banner](../includes/banner.md)]

# Financial tag rule reference 

## Fields supported for all journals

| Field name | Microsoft Power Fx | Description | SQL field |
| --- | --- | --- | --- |
| Account | <ul><li>`doc.Account.MainAccount`</li><li>`doc.Account.<DimensionFields>`</li></ul> | When the account type is set to **Ledger**, all the available dimension fields that are associated with the **Account** field are entered in the **Account** field. | Join to `DimensionAttributeValueCombination` to the correct selected field |
| Account type | `doc.AccountType` | This field refers to the account type value on the journal line. | `LedgerJournalTrans.AccountType` |
| Approved | `doc.Approved` | A `true`/`false` value that indicates whether the journal line was approved. | `LedgerJournalTrans.Approved` |
| Approved by | `doc.ApprovedBy` | The user who approved the journal. | `LedgerJournalTrans.Approver` |
| Bank | <ul><li>`doc.Bank.Account`</li><li>`doc.Bank.Name`</li></ul> | <p>The **Bank account ID** or **Bank account name** field.</p><p>This field is available when the account type is set to **Bank**.</p> | <p>Join to:</p><ul><li>`BankAccountTable.AccountID`</li><li>`BankAccountTable.Name`</li></ul> |
| Company | `doc.Company` | The **Account company** value that is set on the journal line. | `LedgerJournalTrans.Company` |
| Currency | `doc.Currency.Code` | The **Currency** value for the journal line. | `LedgerJournalTrans.Currencycode` |
| Customer | <ul><li>`doc.Customer.Account`</li><li>`doc.Customer.Group` </li><li>`doc.Customer.GroupName` </li><li>`doc.Customer.Name`</li></ul> | <p>The **Customer account ID**, **Customer account name**, **Customer group id** or **Customer group name** field.</p><p>This field is available when the account type is set to **Customer**.</p> | <p>Joins to:</p><ul><li>`CustTable.AccountNum`</li><li>`CustTable.CustGroup`</li><li>`CustGroup.Name`</li><li>`DirPartyTable.Name`</li></ul> |
| Document | `doc.Document` | The **Document** field from the **Invoice** tab of the journal line. | `LedgerJournalTrans.DocumentNum` |
| Financial dimensions | `doc.Dimensions.<DimensionFields>` | When the account type is set to anything except **Ledger**, all the available dimension fields that are associated with the **Account** field are entered in the **Dimension** field. | Join to `DimensionAttributeValueCombination` to the correct selected field |
| Fixed Asset | <ul><li>`doc.FixedAsset.Account`</li><li>`doc.FixedAsset.Group`</li><li>`doc.FixedAsset.GroupName`</li><li>`doc.FixedAsset.Name`</li></ul> | <p>The **Fixed asset account ID**, **Fixed asset name**, **Fixed asset group id**, or **Fixed asset group name** field.</p><p>This field is available when the account type is set to **Fixed asset**.</p> | <p>Join to:</p><ul><li>`AssetTable.AssetID`</li><li>`AssetTable.AssetGroup`</li><li>`AssetGroup.Name`</li><li>`AssetTable.Name`</li></ul> |
| Invoice | `doc.Invoice` | The **Invoice** field on the journal line. | `LedgerJournalTrans.Invoice` |
| Journal batch number | `doc.JournalNum` | <p>The **Journal batch number** field for the set of journal lines.</p><p>This field is available for the header, account, and offset account tags.</p> | <ul><li>`LedgerJournalTable.JournalNum` (header)</li><li>`LedgerJournalTrans.JournalNum` (account/offset account)</li></ul> |
| Journal description | `doc.JournalDescription` | The **Journal line description** field. | `LedgerJournalTrans.Txt` |
| Offset account | `doc.OffsetDimensions.<DimensionFields>` | When the offset account type is set to **Ledger**, all the available dimension fields that are associated with the **Offset account** field are entered in the **Offset account** field. | Join to `DimensionAttributeValueCombination` to the correct selected field |
| Payment reference | `doc.PaymentReference` | The **Journal line payment reference** field. | `LedgerJournalTrans. PaymReference` |
| Posting profile | `doc.PostingProfile` | The **Journal line posting profile** field. | `LedgerJournalTrans. PostingProfile` |
| Project | <ul><li>`doc.Project.Account`</li><li>`doc.Project.Group`</li><li>`doc.Project.GroupName`</li><li>`doc.Project.Name`</li></ul> | <p>The **Project account ID**, **Project account name**, **Project group id**, or **Project group name** field.</p><p>This field is available when the account type is set to **Project**.</p> | <p>Join to:</p><ul><li>`ProjTable.ProjID`</li><li>`ProjTable.ProjGroupID`</li><li>`ProjGroup.Name`</li><li>`ProjTable.Name`</li></ul> |
| Reason / Reason comment | <ul><li>`doc.Reason`</li><li>`doc.ReasonComment`</li></ul> | The reason ID and reason comment values that are related to a journal line. | <p>Join to:</p><ul><li>`ReasonTableRef.Reason`</li><li>`ReasonTableRef.ReasonComment`</li></ul> |
| Vendor | <ul><li>`doc.Vendor.Account`</li><li>`doc.Vendor.Group`</li><li>`doc.Vendor.GroupName`</li><li>`doc.Vendor.Name`</li></ul> | <p>The **Vendor account ID**, **Vendor account name**, **Vendor group id**, or **Vendor group name** field.</p><p>This field is available when the account type is set to **Vendor**.</p> | <p>Join to:</p><ul><li>`VendTable.AccountNum`</li><li>`VendTable.VendGroup`</li><li>`VendGroup.Name`</li><li>`DirPartyTable.Name`</li></ul> |
| Voucher number | `doc.Voucher` | The **Voucher** field from the journal line. | `LedgerJournalTrans.Voucher` |
