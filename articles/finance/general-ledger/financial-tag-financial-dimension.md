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

Financial dimensions are used to code accounting entries for reporting, such as to identify sales per department or expenses per cost center. Financial tags (tags) are an alternative to using financial dimensions. An  organization can create and enterdefine up to 20 user-defined fields financial tags and enter the values on transactions. The tag values , which are then stored on the accounting entries created for the transaction, similar to financial dimensions. Tags values are not stored in any subledger tables, such as Customer or Vendor transactions. Both financial dimensions and financial tags can be used for reporting and also some processes such as ledger settlement. 
This document reviews the differences between financial dimensions and financial tags, to help organizations determine which feature should be used. 
In general, financial dimensions are very structured, with setup that is used to control which dimensions are required, which dimension values are valid, and which dimension combinations are valid. The design of financial tags is the opposite, with limited structure, no validation and very limited defaulting.  But both are available for analytical reporting and ledger settlement.
The following table details the differences between dimensions and tags.

|Functionality |Financial dimensions | Financial tags |
|--------------|--------------|---------------------------|

|Account structures|	Dimensions must be included within an account structure to be used within an LElegal entity. The account structure determines the dimensions required with the main account and the validation combinations.|	Tags are not part of the account structure.  |
|Validation	|Dimension values within the ledger account are validated against the account structures, determined if the dimension value is active or not, validation of combinations, validation that the value exists, and so on. |	Tag valuess are never validated during transaction entry or posting. Any value can be entered, even if the tag is defined with a type of List or Custom list. A value is not required to be selected from the list. There is no capability functionality to make a tag value required.| 
|Defaulting	|Dimension values default from master data, such as from customers, vendors, products, projects, etc. Defaulting of dimension values also includes defaulting from the header of a document to the lines.  Or for journals, from the journal header to the Account, and from the Account to the Offset account. |	Tag values do not default from master data. Defaulting of tag values also includes defaulting from the header of a document to the lines.  Or for journals, from the journal header to the Account, and from the Account to the Offset account.|
|Reporting|	Dimension values can be used for reporting in multiple ways.  First, dimensions can be included in a dimension set,  which is used to calculate totals for the ledger account, which includes the selected dimensions. Dimension values can also be viewed on each detailed transaction.  The segments can be parsed out and then used for sorting and filtering of the detailed transactions. |	Tag values are not part of the dimension sets. Within Dynamics 365 Finance, a trial balance cannot be generated to view balances for tag values.  When drilling down from the balances on the trial balance, tag values are shown on each detailed transaction. The tag values are in separate columns, making it easy to sort and filter on transactions within Voucher transactions or the Transactions for <main account> inquiries. The detailed transactions can be exported to Excel or PowerBI.| 
|Impact on GL Processes|	While dimensions are considered ‘unlimited,’ the more dimensions created and used within a dimension set, the slower transaction entry, importing and processes will become.| Because tags have no structure or validation, there is a minimal impact when using tags on transactions or when importing them via an entity.|
|Non-reusable values	|Dimensions should never be used to track non-reusable values , such as document numbers, reference numbers, etc.  This type of data will cause your chart of accounts to explode due to the uniqueness of so many ledger accounts, which will negatively impact performance, especially around the year end close, foreign currency revaluation and consolidations.| 	Tags should be used to track non-reusable values, such as document numbers, reference numbers, etc. |
|Ability to activate/deactivate|	New financial dimensions can be activated, but the system must be in maintenance mode. Financial dimensions cannot be deactivated, but instead can be removed from an account structure so it’s not longer used by all legal entities using that account structure.| 	Tags can be activated or deactivated at any time.| 
|Ability to delete	|Dimensions cannot be deleted if they are referenced anywhere within the system, such as on a posted transaction. If the dimension references an entity, the entity and entity values cannot be deleted in order to maintain referential integrity. 	|Tags cannot be deleted in order to maintain the tag values that have been entered on posted transactions.  But, the tag can be deactivated at any time. If a tag is referencing an entity for a list, there is no reference maintained to that entity.  For example, if the tag is mapped to Customer name, customers can still be deleted because the tag values hold no reference to the customer. This also means that if a customer name is changed, the customer name is not updated on the tag values. See the Editing after posting section row for more details on edits to tags. |
|Editing after posting	|Dimension values cannot be edited on posted transactions because any change to the ledger account will directly impact financial statements. |	Tag values are only used for internal analysis and processing, so tag values can be added, removedremoved, or edited at any time on posted transactions using the feature Allow edits to internal data on general ledger vouchers. An audit trail is maintained for all edits made to the tag values after posting. |
|Global or legal entity specific?	|Dimensions are set up globally, but then are ‘assigned’ to each legal entity through the account structures.  Dimensions also have legal entity overrides, allowing the same dimension to be active in one legal entity or not active in a different legal entity. |	Tags are set up at the legal entity level. They can be shared by using the Shared data feature.  Also, the tags and tag custom tag values can be copied quickly to each legal entity by using the data management entities. | 
		



