---
title: LedgerJournalLine entity
description: Learn about the LedgerJournalLine data entity in finance and operations migration projects with Dynamics 365 via a summary.
author: edupont04
ms.author: epegors
ms.topic: conceptual
ms.date: 02/02/2024
ms.collection: FastTrack
---

# LedgerJournalLine entity

The **LedgerJournalLine** entity supports creating and updating general journal lines.

## When to use this entity

The **LedgerJournalLine** entity should be used for synchronous scenarios with OData. The **General journal** entity uses Data management and is recommended for high volume scenarios.

## Summary

| **Data management entity name**        | N/A                                                 |
|----------------------------------------|-----------------------------------------------------|
| **OData public entity**                | LedgerJournalLine                                   |
| **OData public collection**            | LedgerJournalLines                                  |
| **Related menu items**                 | General ledger / Journal entries / General journals |
| **Related entities**                   | LedgerJournalHeader, General journal                |
| **Performance pattern**                | N/A                                                 |
| **Application Object Tree (AOT) name** | LedgerJournalLineEntity                             |

## Fields

| **Field name** | **Comments** |
|--|--|
| JOURNALBATCHNUMBER |Specifies the first segment of the primary key. This field is required. It must reference an existing, unposted header to be able to create or update lines. |
| LINENUMBER |Specifies the second segment of the primary key. This field isn't required for an insert. |
| ACCOUNTTYPE |Specifies the type for the account. The supported values are Bank, Customer, Ledger, and Vendor. If this field isn't specified, the default value is Ledger. |
| ACCOUNTDISPLAYVALUE |Specifies the string value for the account. When **ACCOUNTTYPE** is Ledger, using this field requires configuring the **Ledger dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **ACCOUNTTYPE** is something other than Ledger, this field contains the primary key value. |
| ACCOUNTDEFAULTDIMENSIONDISPLAYVALUE |Specifies the string value for the account default dimensions. When **ACCOUNTTYPE** is something other than Ledger, using this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **ACCOUNTTYPE** is Ledger, this field isn't applicable. |
| FINTAGDISPLAYVALUE |Specifies the string value for the account financial tags. Using this field requires setting the financial tag separator and configuring at least the number of financial tags that are included. Learn more at [Financial tags](/dynamics365/finance/general-ledger/financial-tag). |
| OFFSETACCOUNTTYPE |Specifies the type for the offset account. The supported values are Bank, Customer, Ledger, and Vendor. If this field isn't specified, the default value is Ledger. |
| OFFSETACCOUNTDISPLAYVALUE |Specifies the string value for the offset account. When **OFFSETACCOUNTTYPE** is Ledger, using this field requires configuring the Ledger **dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **OFFSETACCOUNTTYPE** is something other than Ledger, this field contains the primary key value. |
| OFFSETDEFAULTDIMENSIONDISPLAYVALUE |Specifies the string value for the offset account default dimensions. When **OFFSETACCOUNTTYPE** is something other than Ledger, using this field requires configuring the **Default dimension format** using the **Financial dimension configuration for integrating applications** menu item. When **OFFSETACCOUNTTYPE** is Ledger, this field isn't applicable. |
| OFFSETFINTAGDISPLAYVALUE |Specifies the string value for the offset account financial tags. Using this field requires setting the financial tag separator and configuring at least the number of financial tags that are included. Learn more at [Financial tags](/dynamics365/finance/general-ledger/financial-tag). |
| TRANSDATE |Specifies the date for the transaction. This field is required. The combination of VOUCHER and TRANSDATE determines the physical vouchers for this field. This means TRANSDATE must be same for all rows with the same VOUCHER; otherwise another physical voucher is created. |
| VOUCHER |Specifies the voucher for the transaction. This field is required. In most cases, it defaults to the journal name. The combination of VOUCHER and TRANSDATE determines the physical vouchers for this field. This means TRANSDATE must be same for all rows with the same VOUCHER; otherwise another physical voucher is created. |
| CURRENCYCODE |Specifies the transaction currency. This field is required. |
| EXCHANGERATE | The exchange rate used to convert the transaction currency to the accounting currency. If this field isn't included, the exchange rate is based on the value of the TRANSDATE field. |
| EXCHANGERATESECONDARY | The secondary exchange rate used to convert the transaction currency to the accounting currency. |
| REPORTINGCURRENCYEXCHRATE | The exchange rate used to convert the transaction currency to the reporting currency. If this field isn't included, the exchange rate is based on the value of the TRANSDATE field. |
| REPORTINGCURRENCYEXCHRATESECONDARY | The secondary exchange rate used to convert the transaction currency to the reporting currency. |

## Issues and considerations

The physical vouchers should be relatively small, such as 10 lines or less.

This entity doesn't support intercompany transactions.

## Related resources

- [General journal processing](/dynamics365/finance/general-ledger/general-journal-processing)
- [Importing vouchers by using the General journal entity](tips-tricks-import-general-journal-entity.md)
- [Financial tags](/dynamics365/finance/general-ledger/financial-tag)
- [Financial journal posting performance](/dynamics365/finance/general-ledger/posting-performance)
- [Journal posting failure because of imbalance](/dynamics365/finance/general-ledger/posting-fail-imbalance)
- [Data import and export jobs overview](data-import-export-job.md)
- [Import general journals in Dynamics 365 projects](/dynamics365/guidance/resources/import-general-journals)  
