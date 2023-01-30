---
# required metadata

title: Differences between financial tags and financial dimensions
description: This article describes the differences between financal tags and financial dimensions.
author: kweekley
ms.date: 01/23/2023
ms.topic: article
ems.prod: 
ms.technology: 

# optional metadata

ms.search.form: DimensionDetails, DimensionValueDetails, SysTranslationDetail
audience: Application User
# ms.devlang: 
ms.reviewer: twheeloc
# ms.tgt_pltfrm: 
ms.custom: 25871
ms.search.region: Global
# ms.search.industry: 
ms.author: aolson
ms.search.validFrom: 2018-10-31
ms.dyn365.ops.version: 8.1

---

# Differences between financial tags and financial dimensions

Financial dimensions are used to code accounting entries for reporting (for example, to identify sales per department or expenses per cost center). Financial tags (tags) are an alternative to financial dimensions. An organization can create up to 20 user-defined financial tags and enter values for them on transactions. Like financial dimension values, tag values are stored on the accounting entries that are created for the transactions. However, tag values aren't stored in any subledger tables, such as the Customer transactions or Vendor transactions table. Both financial dimensions and financial tags can be used for analytical reporting and also for some processes, such as ledger settlement.

Financial dimensions are very structured. The setup is used to control which dimensions are required, which dimension values are valid, and which dimension combinations are valid. However, financial tags have limited structure, no validation is done, and very limited defaulting is done.

The following table describes, in detail, the differences between financial dimensions and financial tags, to help organizations determine which feature they should use. 

| Functionality | Financial dimensions | Financial tags |
|---------------|----------------------|----------------|
| Account structures | Dimensions must be included in an account structure before they can be used in a legal entity. The account structure determines the dimensions that are required for the main account and the valid combinations. | Tags aren't part of the account structure. |
| Validation | Dimension values on the ledger account are validated against the account structures to determine whether the dimension values are active, the dimension combinations are valid, and the values exist. | Tag values aren't validated during transaction entry or posting. Any value can be entered, even if the tag is defined as a tag of the **List** or **Custom list** type. A value doesn't have to be selected in the list. There's no way to require a tag value. |
| Defaulting | Default dimension values are entered from master data, such as customers, vendors, products, or projects. They're also entered from the header of a document to the lines. For journals, they're entered from the journal header to the account, and from the account to the offset account. | Default tag values aren't entered from master data. However, they're entered from the header of a document to the lines. For journals, they're entered from the journal header to the account, and from the account to the offset account. |
| Reporting | Dimension values can be used for reporting in multiple ways. Dimensions can be included in a dimension set, which is used to calculate totals for the ledger account. Dimension values can also be viewed on each detailed transaction. The segments can be parsed out, and then used to sort and filter the detailed transactions. | Tag values aren't included in dimension sets. In Microsoft Dynamics 365 Finance, you can't generate a trial balance to view balances for tag values. When you drill down from the balances on the trial balance, tag values are shown on each detailed transaction. The tag values are in separate columns. Therefore, it's easy to sort and filter on transactions in the **Voucher transactions** or **Transactions for main account** inquiry. The detailed transactions can be exported to Excel or Power BI. |
| Impact on General ledger processes | Although dimensions are considered unlimited, the more dimensions that are created and used in a dimension set, the slower transaction entry, import, and processes will become. | Because tags have no structure or validation, there's minimal impact when they're used on transactions or imported via an entity. |
| Non-reusable values | Dimensions should never be used to track non-reusable values, such as document numbers or reference numbers. This type of data will cause your chart of accounts to explode, because of the uniqueness of so many ledger accounts. Therefore, performance will be negatively affected, especially around the year-end close and during foreign currency revaluation and consolidations. | Tags should be used to track non-reusable values, such as document numbers or reference numbers. |
| Ability to activate or deactivate | New financial dimensions can be activated, but the system must be in maintenance mode. Financial dimensions can't be deactivated. Instead, they can be removed from an account structure, so that they're no longer used by any legal entities that use that account structure. | Tags can be activated or deactivated at any time. |
| Ability to delete | Dimensions can't be deleted if they're referenced anywhere, such as on a posted transaction. If the dimension references an entity, the entity and entity values can't be deleted. This restriction helps maintain referential integrity. | <p>Tags can't be deleted. This restriction helps maintain the tag values that have been entered on posted transactions. However, tags can be deactivated at any time.</p><p>If a tag references an entity for a list, no reference to that entity is maintained. For example, if the tag is mapped to the Customer name entity, customers can be deleted, because the tag values hold no reference to the customer. In addition, if a customer name is changed, the customer name isn't updated in the tag values.</p> |
| Ability to edit after posting | Dimension values can't be edited on posted transactions, because any change to the ledger account will directly affect financial statements. | Tag values are used only for internal analysis and processing. Therefore, they can be added, removed, or edited on posted transactions by using the **Allow edits to internal data on general ledger vouchers** feature. An audit trail is maintained for all edits that are made to the tag values after posting. |
| Global or legal entity specific? | Dimensions are set up globally, and they are "assigned" to each legal entity through the account structures. Dimensions also have legal entity overrides, so that the same dimension can be active in one legal entity but inactive in another legal entity. | Tags are set up at the legal entity level. They can be shared by using the **Shared data** feature. The tags and custom tag values can be copied to each legal entity by using the data management entities. |
