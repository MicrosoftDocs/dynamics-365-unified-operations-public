---
title: NF203 Computerized Accounting Certification
description: This topic provides an overview of the official NF203 certification for computerized accounting in France. 
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 10/12/2025
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# NF203 Computerized Accounting Certification

[!include [banner](../../includes/banner.md)]

This topic provides an overview of the official NF203 certification for computerized accounting in France.  

Microsoft Dynamics 365 for Finance and Operations, version 10.0 has passed an audit according to the NF203 certification requirements in France and is granted a certificate of compliance.

| Certification No **203/346-4** issued by INFOCERT in France <br> Computerized Accounting <br> Category F: <br>- Accounting; <br>- Sales Management;<br>- Purchasing Management;<br>- Fixed Assets;<br>- Inventories and Stocks | <img src="../media/fr-nf203.png" alt="INFOCERT" width="150"/> |
|:------------|-----------|

An up-to-date certificate can be found on the [portal of the certification body](https://certificates.infocert.org/).

INFOCERT is a French specialist in software certification, acting as the technical secretariat and as an inspection body for Association Française de Normalisation (AFNOR) Certification.

## NF203 compliance documentation

The following table shows the Dynamics 365 Finance documentation that is related to the NF203 certification.

| Document | Description | Links |
|----------|-------------|-------|
| High-level design <br> Technical architecture</p> | This documentation describes the software product, its components, and data flows, and also the technical design of the product. | [Finance home page](../../finance-welcome.md) and nested links<br>[Finance and operations application architecture](../../../fin-ops-core/dev-itpro/organization-administration/architecture-overview.md) |
| Functional specification<br>User documentation | This documentation describes the functions of the software. | [Finance home page](../../finance-welcome.md) and nested links<br>[France-specific functionality](france.md) <br> [Cash register functionality for France](../../../../dynamics365/commerce/localizations/france/emea-fra-cash-registers.md) |
| Versioning strategy | This documentation describes the versioning approach and the version management procedure for the software product.<br>The current major Dynamics 365 Commerce version is **10.0**. Service updates for this version are indicated by a consecutive number after the version number: **10.0.X**. For more information about the software lifecycle policy and service updates, use the links in this table.</p>| <p>[One Version service updates overview](../../../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md)<br>[Software lifecycle policy and cloud releases](../../../fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy.md)<br>[Service update availability](../../../fin-ops-core/dev-itpro/get-started/public-preview-releases.md)</p><p>[Dynamics 365 release plans](/dynamics365/release-plans/)<br>[What's new or changed in finance and operations apps home page](../../../fin-ops-core/fin-ops/get-started/whats-new-changed.md) |
| Organizational documentation | This documentation describes the process that is established to control software product compliance. | [Globalization resources](../../../fin-ops-core/fin-ops/lcs/country-region.md) |
| Maintenance documentation | This documentation describes implementation and maintenance of the software solution. | [Service description](../../../fin-ops-core/dev-itpro/get-started/service-description.md)<br>[Before you buy](../../../fin-ops-core/fin-ops/get-started/before-you-buy.md)</p><p>[Dynamics 365 Licensing Guide](https://www.microsoft.com/licensing/docs/grid/Microsoft-Dynamics-365)<br>[Implementation lifecycle management home page](../../../fin-ops-core/dev-itpro/organization-administration/implementation-lifecycle.md)<br>[Dynamics 365 Support](https://dynamics.microsoft.com/support/)<br>[Submit service requests](../../../fin-ops-core/dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team.md)<br>[One Version service updates overview](../../../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md) |

## 

## Registration of audit events

This section describes how audit mechanisms in Dynamics 365 Finance ensure traceability, integrity, and compliance for all NF203-certified computerized accounting events, 
including logging, monitoring, and verification of key actions.

### Code 10 or 15 - Change in the continuous sequence management mode

#### Continuous numbering management

Dynamics 365 Finance uses **Number Sequences** to manage continuous numbering for vouchers and other documents. 
These sequences ensure that document numbers are assigned without gaps, meeting French legal requirements.

*Documentation links*
- [Number Sequence Overview](../../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md)

#### Change handling

Any change in numbering configuration (such as scope, format, or periodicity) is performed through the **Number Sequence** setup by an administrator. 
These changes are logged in system administration history, ensuring traceability.

#### Immutability of existing documents

Documents already created retain their original numbers. Dynamics 365 Finance does not allow retroactive renumbering, preserving integrity and compliance.

#### Audit trail

Administrative changes to number sequences are recorded in the system logs, which can be reviewed for compliance audits.

### Code 30 - Fiscal year archiving

In Dynamics 365 Finance, fiscal year archiving is satisfied through the combination of: [Electronic Reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) (ER) 
for generating the legally required [VAT declaration](emea-fra-vat-declaration-preview-france.md), fiscal documents and [FEC file](emea-fra-fec-audit-file.md) at year-end and [Archive ER destination type](../../..//fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) setup to store these electronic reports and related fiscal documents in a secure location (e.g., Azure Blob Storage or SharePoint) with access controlled by system administrators.

#### Immutability and audit trail

Archived files cannot be modified through the ERP interface. Posting logic ensures that once a fiscal period is closed, accounting entries cannot be altered; corrections are made only through reversing and adjusting entries. 
Audit trail logs capture metadata such as user, timestamp, and job execution details for the archiving process.

### Code 50 - Period closing

#### Period closing functionality

Dynamics 365 Finance provides functionality to close fiscal periods (daily, monthly, or yearly) through the [Fiscal calendars, fiscal years, and periods](../../budgeting/fiscal-calendars-fiscal-years-periods.md) and [Financial period close workspace](../../general-ledger/financial-period-close-workspace.md). 
Once a period is closed, no new postings or modifications can occur in that period, ensuring data integrity and compliance.

*Documentation links*
- [Year-end close](../../general-ledger/year-end-close.md)

#### Audit trail

All postings and period status changes are logged. Users cannot modify transactions in closed periods; corrections require reversing entries in an open period.

### Code 60 - Fiscal year closing

#### Year-end closing process

Dynamics 365 Finance provides a dedicated [Year-end close](../../general-ledger/year-end-close.md) process through the **General Ledger** > **Year-end close** functionality. 
This process transfers balances to the next fiscal year and marks the previous year as closed.

*Documentation links*
- [Year-end close](../../general-ledger/year-end-close.md)

#### Immutability of closed periods

In Dynamics 365 Finance transactions cannot be modified. Any corrections must be made using reversing and adjusting entries in an open period, preserving the integrity of historical data. 
When a fiscal year status is set to **Permanently closed**, the closed year can't be reopened, no transactions can be posted in this period.

*Documentation links*
- [Close the fiscal year](../../general-ledger/tasks/close-fiscal-year.md)
  
#### Audit Trail

All postings and period status changes are logged in the system. The audit trail includes user identity, timestamps, and job execution details, ensuring traceability for compliance audits.

### Code 90 - Detection of an integrity flaw in secure data or in a tax archive

In Dynamics 365 Finance the data security and immutability are satisfied with [FEC file](emea-fra-fec-audit-file.md) generated using [Electronic Reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) (ER) and [Audit Trail](../../general-ledger/view-journal-entries-transactions.md#audit-trail) features. 

When FEC is generated and archived, the file is stored in a secure location (e.g., Azure Blob or SharePoint) with access controlled by a system administrator.
The Dynamics 365 Finance does not allow modification of archived files through standard UI - immutability is enforced by storage and permissions defined by a system administrator.
In Dynamics 365 Finance the accounting entries are stored in the `GeneralJournalEntry` and `GeneralJournalAccountEntry` tables, together with their related references. 
The transaction records contain date, amount, text, creation date, and created-by fields. An accounting entry can be corrected only by adding new reversing and correcting entries, not by changing the existing records. Dynamics 365 Finance doesn't provide any way for users to alter these records.

*Documentation links*
- [View journal entries and transactions, Audit trail](../../general-ledger/view-journal-entries-transactions.md#audit-trail)
- [Data retention, deletion, and destruction in Microsoft 365](../../../../compliance/assurance/assurance-data-retention-deletion-and-destruction-overview.md)

### Code 180 - Generating an export file of accounting entries

Event 180 is satisfied by the [FEC file](emea-fra-fec-audit-file.md) export functionality in Dynamics 365 Finance, combined with the [Archive ER destination type](../../..//fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) setup and batch logging mechanism. 

#### Archive destination setup

The [FEC file](emea-fra-fec-audit-file.md) generation process requires that an [Archive ER destination type](../../..//fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) be configured in the system. This ensures that the exported file is stored in a designated, secure archive location.

#### Audit logging

The batch execution automatically records metadata about the generation process, including:
- Who initiated the export (user identity)
- When the export was performed (timestamp)
- Job status and execution details

*Documentation links*
- [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md)
- [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md)
