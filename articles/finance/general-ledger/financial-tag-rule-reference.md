---
title: Financial tag rule reference
description: Learn about financial tags rules with PowerFx formulas
author: rcarlson
ms.author: rcarlson
ms.topic: article
ms.date: 11/01/2024
ms.reviewer: twheeloc
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2023-03-23
ms.search.form: DimensionFocus, LedgerTrialBalanceListPage, FinTagRule, FinancialTags
ms.dyn365.ops.version: 10.0.42
---

[!include [banner](../includes/banner.md)]

# Additional reference information for Financial tag rules

## Supported list of fields for all journals

| Field name | PowerFx | Description | SQL field |
| --- | --- | --- | --- |
| Account | doc.Account.MainAccount<br><br>doc.Account.&lt;DimensionFields&gt; | The **Account** field has all of the available dimension fields associated with the **Account** field entered when the account type is set to **Ledger**. | Join to DimensionAttributeValueCombination to the proper field selected. |
| Account type | doc.AccountType | Refers to the account type value in the journal line. | LedgerJournalTrans.AccountType |
| Approved | doc.Approved | The true/false value if the journal line has been approved. | LedgerJournalTrans.Approved |
| Approved by | doc.ApprovedBy | The user who approved the journal. | LedgerJournalTrans.Approver |
| Bank | doc.Bank.Account<br><br>doc.Bank.Name| The **Bank account ID** or the **Bank account name** fields. Available when the **Account type** is set to **Bank**. | Join to BankAccountTable.AccountID and .Name |
| Company | doc.Company | The **Account company** value set on the journal line. | LedgerJournalTrans.Company |
| Currency | doc.Currency.Code | The **Currency** value for the journal line. | LedgerJournalTrans.Currencycode |
| Customer | doc.Customer.Account<br><br>doc.Customer.Group (Pending ID/Name change)<br><br>doc.Customer.Name | The **Customer account ID**, **Customer account name**, or the **Customer group id** fields. Available when the **Account type** is set to **Customer**. | Joins to:  <br>CustTable.AccountNum<br><br>CustTable.CustGroup<br><br>CustGroup.Name<br><br>DirPartyTable.Name |
| Fixed Asset | doc.FixedAsset.Account<br><br>doc.FixedAsset.Group<br><br>doc.FixedAsset.Name | The **Fixed asset account ID**, **Fixed asset name**, or the **Fixed asset group id** fields. Available when the **Account type** is set to **Fixed asset**. | Join to:<br><br>AssetTable.AssetID<br><br>AssetTable.AssetGroup<br><br>AssetTable.Name |
| Invoice | doc.Invoice | The **Invoice** field on the journal line. | LedgerJournalTrans.Invoice |
| Journal description | doc.JournalDescription | The **Journal line description** field. | LedgerJournalTrans.Txt |
| Journal batch number | doc.JournalNum | The **Journal batch number** for the set of journal lines.<br><br>This field is available for both the header, the account and offset account tags. | **LedgerJournalTable.JournalNum (Header)**<br><br>**LedgerJournalTrans.JournalNum (Account/OffsetAccount)** |
| Document | doc.Document | The **Document** field from the **Invoice** tab of the journal line. | LedgerJournalTrans.DocumentNum |
| Financial dimensions\* | doc.Dimensions.&lt;DimensionFields&gt; | The **Dimension** field has all of the available dimension fields that are associated with the **Account** field entered when the **Account type** is set to anything other than **Ledger**. | Join to DimensionAttributeValueCombination to the proper field selected. |
| Offset account\* | doc.OffsetDimensions.&lt;DimensionFields&gt; | The **Offset account** field has all of the available dimension fields\* that are associated with the **Offset account** field entered when the **Offset account type** is set to **Ledger**. | Join to DimensionAttributeValueCombination to the proper field selected. |
| Payment reference | doc.PaymentReference | The **Journal line payment reference** field. | LedgerJournalTrans. PaymReference |
| Posting profile | doc.PostingProfile | The **Journal line posting profile** field. | LedgerJournalTrans. PostingProfile |
| Project | doc.Project.Account<br><br>doc.Project.Group<br><br>doc.Project.Name | The **Project account ID**, **Project account name**, or the **Project group id** fields. Available when the account type is set to **Customer**. | Join to:<br><br>ProjTable.ProjID<br><br>ProjTable.ProjGroupID<br><br>ProjTable.Name |
| Reason / Reason comment | doc.Reason<br><br>doc.ReasonComment | The reason ID and the reason comment values related to a journal line. | Join to ReasonTableRef.Reason and .ReasonComment |
| Vendor | doc.Vendor.Account<br><br>doc.Vendor.Group<br><br>doc.Vendor.Name | The **Vendor account ID**, **Vendor account name**, or the **Vendor group id** fields. Available when the account type is set to **Vendor**. | Join to:  <br>VendTable.AccountNum<br><br>VendTable.VendGroup<br><br>\*VendGroup.Name<br><br>DirPartyTable.Name |
| Voucher number | doc.Voucher | The **Voucher** field from the journal line. | LedgerJournalTrans.Voucher |
