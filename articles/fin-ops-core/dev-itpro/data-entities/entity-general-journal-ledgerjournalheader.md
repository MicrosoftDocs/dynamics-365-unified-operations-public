---
title: LedgerJournalHeader entity
description: Learn about the LedgerJournalHeader data entity in finance and operations migration projects with Dynamics 365.
author: edupont04
ms.author: epegors
ms.topic: conceptual
ms.date: 02/02/2024
ms.collection: FastTrack
---

# LedgerJournalHeader entity

The **LedgerJournalHeader** entity supports creating and updating general journal headers.

## When to use this entity

Use the **LedgerJournalHeader** entity for synchronous scenarios with OData. For high volume scenarios, we recommend you use the **General journal** entity that uses the data management framework.

## Summary

| **Data management entity name**        | LedgerJournalHeader                                        |
|----------------------------------------|-----------------------------------------------------|
| **OData public entity**                | LedgerJournalHeader                                 |
| **OData public collection**            | LedgerJournalHeaders                                |
| **Related menu item**                  | General ledger / Journal entries / General journals |
| **Related entities**                   | LedgerJournalLine, General journal                  |
| **Performance pattern**                | N/A                                                 |
| **Application Object Tree (AOT) name** | LedgerJournalHeaderEntity                           |

## Fields

| **Field name** | **Comments** |
|--|--|
| JOURNALBATCHNUMBER | Specifies the primary key. This field is required. |
| LINENUMBER | Specifies the second segment of the primary key. This field isn't required for an insert. |
| JOURNALNAME | Specifies the journal name template. This field is required. |
| DESCRIPTION | Specifies the description for the journal. The default value is based on the value of the JOURNALNAME field. |
| POSTINGLAYER | Specifies the posting layer for the journal. The default value is based on the value of the JOURNALNAME field. |

## Issues and considerations

This entity doesn't support intercompany transactions.

## Related resources

- [General journal processing](/dynamics365/finance/general-ledger/general-journal-processing)
- [Importing vouchers by using the General journal entity](tips-tricks-import-general-journal-entity.md)
- [Financial tags](/dynamics365/finance/general-ledger/financial-tag)
- [Financial journal posting performance](/dynamics365/finance/general-ledger/posting-performance)
- [Journal posting failure because of imbalance](/dynamics365/finance/general-ledger/posting-fail-imbalance)
- [Data import and export jobs overview](data-import-export-job.md)
- [Import general journals in Dynamics 365 projects](/dynamics365/guidance/resources/import-general-journals)  
