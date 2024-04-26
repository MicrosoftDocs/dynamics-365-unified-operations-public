---
title: General journal entity
description: Learn about the General journal data entity in finance and operations migration projects with Dynamics 365 via a summary.
author: edupont04
ms.author: epegors
ms.topic: conceptual
ms.date: 02/02/2024
ms.collection: FastTrack
---

# General journal entity

***Applies to:*** ***Dynamics 365 Commerce, Dynamics 365 Finance, Dynamics 365 Intelligent Order Management, Dynamics 365 Project Operations, Dynamics 365 Supply Chain Management***

The **General journal** entity supports creating and updating general journal headers and lines for the Bank, Customer, Ledger, and Vendor account types.

## When to use this entity

The **General journal** entity should be used for all high volume import scenarios. Using the data management framework (DMF) is recommended for high volume scenarios, and the **General journal** entity supports set-based processing that performs well with high volume. This documentation assumes the **General journal** entity is using set-based processing.

## Summary

| **Data management entity name** | General journal |
|-------------------------|-------------------------|
| **OData public entity** | N/A |
| **OData public collection** | N/A |
| **Related menu item** | General ledger / Journal entries / General journals</br>General ledger / Journal entries / Journal post |
| **Related entities** | LedgerJournalHeader, LedgerJournalLine |
| **Performance pattern** | Set-based: Disabling set-based processing or using multiple threads isn't recommended. |
| **Application Object Tree (AOT) name** | LedgerJournalEntity |

## Fields

| **Field name** | **Comments** |
|--|--|
| JOURNALBATCHNUMBER | Contains the primary key for the header and the first segment of the primary key for the line. You can specify a placeholder value that you then replace with a value from the number sequence during the import. Exclude this field if the lines in the import file are all for the same header. |
| LINENUMBER | Contains the second segment of the primary key. This field is required. |
| JOURNALNAME | Contains a header value, and it must have the same value for every row with the same **JOURNALBATCHNUMBER**. |
| DESCRIPTION | Contains a header value, and it must have the same value for every row with the same **JOURNALBATCHNUMBER**. |
| POSTINGLAYER | Contains a header value, and it must have the same value for every row with the same **JOURNALBATCHNUMBER**. |
| ACCOUNTTYPE | Contains the type for the account. The supported values are Bank, Customer, Ledger, and Vendor. If this field isn't specified, the default value is Ledger. |
| ACCOUNTDISPLAYVALUE | Contains the string value for the account. When **ACCOUNTTYPE** is Ledger, using this field requires configuring the **Ledger dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **ACCOUNTTYPE** is something other than Ledger, this field contains the primary key value. |
| ACCOUNTDEFAULTDIMENSIONDISPLAYVALUE | Contains the string value for the account default dimensions. When **ACCOUNTTYPE** is something other than Ledger, using this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **ACCOUNTTYPE** is Ledger, this field isn't applicable. |
| FINTAGDISPLAYVALUE | Contains the string value for the account financial tags. Using this field requires setting the financial tag separator and configuring at least the number of financial tags that are included. Learn more at [Financial tags](/dynamics365/finance/general-ledger/financial-tag). |
| OFFSETACCOUNTTYPE | Contains the type for the offset account. The supported values are Bank, Customer, Ledger, and Vendor. If this field isn't specified, the default value is Ledger. |
| OFFSETACCOUNTDISPLAYVALUE | Contains the string value for the offset account. When **OFFSETACCOUNTTYPE** is Ledger, using this field requires configuring the Ledger **dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **OFFSETACCOUNTTYPE** is something other than Ledger, this field contains the primary key value. |
| OFFSETDEFAULTDIMENSIONDISPLAYVALUE | Contains the string value for the offset account default dimensions. When **OFFSETACCOUNTTYPE** is something other than Ledger, using this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **OFFSETACCOUNTTYPE** is Ledger, this field isn't applicable. |
| OFFSETFINTAGDISPLAYVALUE | Contains the string value for the offset account financial tags. Using this field requires setting the financial tag separator and configuring at least the number of financial tags that are included. Learn more at [Financial tags](/dynamics365/finance/general-ledger/financial-tag). |
| TRANSDATE | Contains the date for the transaction. This field is required. The combination of VOUCHER and TRANSDATE determines the physical vouchers. This means TRANSDATE must be same for all the rows with the same VOUCHER; otherwise another physical voucher is created. |
| VOUCHER | Contains the voucher for the transaction. This field is required. The value can be a placeholder that is replaced during posting. The combination of VOUCHER and TRANSDATE determines the physical vouchers. This means TRANSDATE must be same for all rows with the same VOUCHER; otherwise another physical voucher is created. Learn more at [Importing vouchers by using the General journal entity](tips-tricks-import-general-journal-entity.md). |
| CURRENCYCODE | Contains the transaction currency. This field is required. |
| EXCHANGERATE | Contains the exchange rate used to convert the transaction currency to the accounting currency. If this field isn't included, the exchange rate is based on the value of the TRANSDATE field. |
| EXCHANGERATESECONDARY | Contains the secondary exchange rate used to convert the transaction currency to the accounting currency. |
| REPORTINGCURRENCYEXCHRATE | Contains the exchange rate used to convert the transaction currency to the reporting currency. If this field isn't included, the exchange rate is based on the value of the TRANSDATE field. |
| REPORTINGCURRENCYEXCHRATESECONDARY | Contains the secondary exchange rate used to convert the transaction currency to the reporting currency. |

## Issues and considerations

Values for JOURNALBATCHNUMBER should have a large number of lines. We recommend about 10,000 lines for each JOURNALBATCHNUMBER.

We also recommend that the physical vouchers be kept relatively small, such as 10 lines or less.

When an import contains many combinations of dimensions (with or without a main account) that haven't been used before, the import might take longer to complete. When it happens repeatedly, the dimension with many new values is known as a *high cardinality dimension*. A high cardinality dimension likely causes more performance issues in Dynamics 365 Finance. We recommend that you review it to determine if it can be reduced or avoided. A common way to avoid a high cardinality dimension is to use a *financial tag* for the high cardinality values, instead of a dimension. For example, an import using the **General journal** entity with 3,000 rows imports in less than 30 seconds if it uses existing dimension combinations, while it could take over 4 minutes if it contains mostly new dimension combinations. Learn more about financial tags at [Financial tags](/dynamics365/finance/general-ledger/financial-tag).

This entity doesn't support intercompany transactions.

## Example

| **Field**           | **Line 1**          | **Line 2**          |
|---------------------|---------------------|---------------------|
| JOURNALNAME         | GenJrn              | GenJrn              |
| DESCRIPTION         | Journal description | Journal description |
| JOURNALBATCHNUMBER  | PLACEHOLDER1        | PLACEHOLDER1        |
| ACCOUNTTYPE         | Ledger              | Ledger              |
| ACCOUNTDISPLAYVALUE | 401100---           | 110160---           |
| LINENUMBER          | 1                   | 2                   |
| TRANSDATE           | 11-Nov-2023         | 11-Nov-2023         |
| VOUCHER             | PLACEHOLDER2        | PLACEHOLDER2        |
| CURRENCYCODE        | GBP                 | GBP                 |
| DEBITAMOUNT         | 0.00                | 10.00               |
| CREDITAMOUNT        | 10.00               | 0.00                |

## Related content

[Import general journals](/dynamics365/guidance/resources/import-general-journals)  

<!-- ## Tags

*Industries:* Healthcare, Financial services, Retail, Manufacturing

*Stakeholders:* Functional consultant, Business analyst, Solution architect, Developer, Data migration lead, Integration lead
 -->
