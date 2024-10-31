---
title: Financial tag rule reference
description: Learn about financial tags rules with PowerFx formulas
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 10/27/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

[!include [banner](../includes/banner.md)]

# Additional reference information for Financial tag rules. 

## Supported list of fields for all Journals

| Field name | PowerFx | Description | SQL field |
| --- | --- | --- | --- |
| Account | doc.Account.MainAccount<br><br>doc.Account.&lt;DimensionFields&gt; | The account field has all of the available dimension fields\* that are associated with the account field entered when the account type is set to Ledger. | Join to DimensionAttributeValueCombination to the proper field selected. |
| Account Type | doc.AccountType | refers to the account type value in the journal line | LedgerJournalTrans.AccountType |
| Approved | doc.Approved | The true/false value whether the journal line has been approved. | LedgerJournalTrans.Approved |
| Approved by | doc.ApprovedBy | The user who approved the journal. | LedgerJournalTrans.Approver |
| Bank | doc.Bank.Account<br><br>doc.Bank.Name | The bank account ID or the bank account name fields. Available when the account type is set to Bank. | Join to BankAccountTable.AccountID and .Name |
| Company | doc.Company | The Account company value set on the journal line. | LedgerJournalTrans.Company |
| Currency | doc.Currency.Code | The Currency value for the journal line. | LedgerJournalTrans.Currencycode |
| Customer | doc.Customer.Account<br><br>doc.Customer.Group (Pending ID/Name change)<br><br>doc.Customer.Name | The customer account ID, customer account name, or the customer group id field. Available when the account type is set to Customer. | Joins to:  <br>CustTable.AccountNum<br><br>CustTable.CustGroup<br><br>CustGroup.Name<br><br>DirPartyTable.Name |
| Fixed Asset | doc.FixedAsset.Account<br><br>doc.FixedAsset.Group<br><br>doc.FixedAsset.Name | The fixed asset account ID, fixed asset name, or the fixed asset group id field. Available when the account type is set to fixed asset. | Join to:<br><br>AssetTable.AssetID<br><br>AssetTable.AssetGroup<br><br>AssetTable.Name |
| Invoice | doc.Invoice | The Invoice field on the journal line. | LedgerJournalTrans.Invoice |
| Journal Description | doc.JournalDescription | The journal line description field. | LedgerJournalTrans.Txt |
| Journal Batch number | doc.JournalNum | The journal batch number for the set of journal lines.<br><br>This field is available for both the Header, and the Account and offset Account tags. | **LedgerJournalTable.JournalNum (Header)**<br><br>**LedgerJournalTrans.JournalNum (Account/OffsetAccount)** |
| Document | doc.Document | The Document field from the invoice tab of the journal line | LedgerJournalTrans.DocumentNum |
| Financial Dimensions\* | doc.Dimensions.&lt;DimensionFields&gt; | The Dimension field has all of the available dimension fields that are associated with the account field entered when the account type is set to anything other than Ledger | Join to DimensionAttributeValueCombination to the proper field selected. |
| Offset Account\* | doc.OffsetDimensions.&lt;DimensionFields&gt; | The offset account field has all of the available dimension fields\* that are associated with the offset account field entered when the offset account type is set to Ledger. | Join to DimensionAttributeValueCombination to the proper field selected. |
|     | doc.PaymentReference | The journal line payment reference field. | LedgerJournalTrans. PaymReference |
|     | doc.PostingProfile | The journal line posting profile field. | LedgerJournalTrans. PostingProfile |
|     | doc.Project.Account<br><br>doc.Project.Group<br><br>doc.Project.Name | The project account ID, project account name, or the project group id field. Available when the account type is set to Customer. | Join to:<br><br>ProjTable.ProjID<br><br>ProjTable.ProjGroupID<br><br>ProjTable.Name |
|     | doc.Reason<br><br>doc.ReasonComment | The reason ID and the reason comment values related to a journal line. | Join to ReasonTableRef.Reason and .ReasonComment |
|     | doc.Vendor.Account<br><br>doc.Vendor.Group<br><br>doc.Vendor.Name | The vendor account ID, vendor account name, or the vendor group id field. Available when the account type is set to vendor. | Join to:  <br>VendTable.AccountNum<br><br>VendTable.VendGroup<br><br>\*VendGroup.Name<br><br>DirPartyTable.Name |
| Voucher number | doc.Voucher | The voucher field from the journal line. | LedgerJournalTrans.Voucher |
