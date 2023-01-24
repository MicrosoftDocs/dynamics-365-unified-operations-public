---
# required metadata

title: Financial tags and financial dimensions
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

Financial dimensions are used to code accounting entries for reporting, such as to identify sales per department or expenses per cost center. Financial tags (tags) are an alternative to using financial dimensions. An organization can define up to 20 user-defined fields financial tags and enter the values on transactions. The tag values, which are stored on the accounting entries created for the transaction, similar to financial dimensions. Tags values are not stored in any subledger tables, such as Customer or Vendor transactions. Both financial dimensions and financial tags can be used for reporting and also some processes such as ledger settlement. 

This article describes the differences between financial dimensions and financial tags, to help organizations determine which feature should be used. 
Financial dimensions are very structured, with setup that is used to control which dimensions are required, which dimension values are valid, and which dimension combinations are valid. The design of financial tags have limited structure, no validation and very limited defaulting. Both are available for analytical reporting and ledger settlement.


The following table describes the differences between financial dimensions and financial tags.

|Functionality |Financial dimensions | Financial tags |
|--------------|--------------|---------------------------|
|Account structures| Dimensions must be included within an account structure to be used within an legal entity. The account structure determines the dimensions required with the main account and the valid combinations.| Tags are not part of the account structure.  |
|Validation	|Dimension values within the ledger account are validated against the account structures and determine if the dimension value is active or not, validation of combinations, and validation that the value exists. | Tag valuess are not validated during transaction entry or posting. Any value can be entered, even if the tag is defined with a type of **List** or **Custom list**. A value is not required to be selected from the list. There's not a way to require a tag value.| 
|Defaulting	|Dimension values default from master data, such as from customers, vendors, products, projects, etc. Defaulting of dimension values also includes from the header of a document to the lines. For journals, from the journal header to the Account, and from the Account to the Offset account. | Tag values don't default from master data. Defaulting of tag values also includes defaulting from the header of a document to the lines. For journals, from the journal header to the Account, and from the Account to the Offset account.|
|Reporting| Dimension values can be used for reporting in multiple ways. Dimensions can be included in a dimension set, which is used to calculate totals for the ledger account and includes the selected dimensions. Dimension values can also be viewed on each detailed transaction. The segments can be parsed out and then used for sorting and filtering of the detailed transactions. |	Tag values are not part of the dimension sets. In Dynamics 365 Finance, a trial balance can't be generated to view balances for tag values. When drilling down from the balances on the trial balance, tag values are shown on each detailed transaction. The tag values are in separate columns, making it easy to sort and filter on transactions within Voucher transactions or the Transactions for main account inquiries. The detailed transactions can be exported to Excel or PowerBI.| 
|Impact on General ledger processes| While dimensions are considered to unlimited, the more dimensions created and used within a dimension set, the slower transaction entry, importing and processes will become.| Because tags have no structure or validation, there is a minimal impact when using tags on transactions or when importing them via an entity.|
|Non-reusable values	|Dimensions should never be used to track non-reusable values, such as document numbers or reference numbers. This type of data will cause your chart of accounts to explode due to the uniqueness of so many ledger accounts, which will negatively impact performance, especially around the year end close, foreign currency revaluation and consolidations.| Tags should be used to track non-reusable values, such as document numbers or reference numbers. |
|Ability to activate or deactivate| New financial dimensions can be activated, but the system must be in maintenance mode. Financial dimensions can't be deactivated, but instead can be removed from an account structure so it’s not longer used by all legal entities using that account structure.| Tags can be activated or deactivated at any time.| 
|Ability to delete	|Dimensions can't be deleted if they are referenced anywhere, such as on a posted transaction. If the dimension references an entity, the entity and entity values can't be deleted in order to maintain referential integrity. |Tags can't be deleted in order to maintain the tag values that have been entered on posted transactions. The tag can be deactivated at any time. If a tag is referencing an entity for a list, there is no reference maintained to that entity. For example, if the tag is mapped to Customer name, customers can be deleted because the tag values hold no reference to the customer. This also means that if a customer name is changed, the customer name isn't updated on the tag values. |
|Editing after posting	|Dimension values can't be edited on posted transactions because any change to the ledger account will directly impact financial statements. |	Tag values are only used for internal analysis and processing, so tag values can be added, removed, or edited on posted transactions using the **Allow edits to internal data on general ledger vouchers** feature. An audit trail is maintained for all edits made to the tag values after posting. |
|Global or legal entity specific?	|Dimensions are set up globally, and are ‘assigned’ to each legal entity through the account structures. Dimensions also have legal entity overrides, allowing the same dimension to be active in one legal entity or not active in a different legal entity. |	Tags are set up at the legal entity level. They can be shared by using the Shared data feature. The tags and tag custom tag values can be copied to each legal entity by using the data management entities. | 
		



