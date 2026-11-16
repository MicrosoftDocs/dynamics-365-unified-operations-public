---
title: NF203 Computerized Accounting Certification in France
description: This article provides an overview of the official NF203 certification for computerized accounting in France. 
author: liza-golub
ms.author: egolub
ms.topic: overview
ms.date: 11/16/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.search.form:
ms.dyn365.ops.version: AX 7.0.0
---

# NF203 Computerized Accounting Certification in France

[!INCLUDE [banner](../../includes/banner.md)]

This article provides an overview of the official NF203 certification for computerized accounting in France.  

Microsoft Dynamics 365 Finance version 10.0 passed an audit according to the NF203 certification requirements in France and was granted a certificate of compliance.

| Certification No **203/346-6** issued by INFOCERT in France <br> Version number 10.0 certified on October 14, 2026 <br>in accordance with NF203 V7.0 rules <br> Computerized Accounting <br> Category F: <br>- Accounting; <br>- Sales Management;<br>- Purchasing Management;<br>- Fixed Assets;<br>- Inventories and Stocks | :::image type="content" source="../media/france-nf203.png" alt-text="Screenshot of the INFOCERT NF203 certification logo."::: |
|:------------|-----------|

You can find an up-to-date certificate on the [portal of the certification body](https://certificates.infocert.org/).

INFOCERT is a French specialist in software certification. It acts as the technical secretariat and as an inspection body for Association Française de Normalisation (AFNOR) Certification.

## NF203 compliance documentation

The following table shows the Finance documentation that relates to the NF203 certification.

| Document | Description | Links |
|----------|-------------|-------|
| High-level design <br> Technical architecture</p> | This documentation describes the software product, its components, and data flows, and also the technical design of the product. | [Finance home page](../../finance-welcome.md) and nested links<br>[Finance and operations application architecture](../../../fin-ops-core/dev-itpro/organization-administration/architecture-overview.md) |
| Functional specification<br>User documentation | This documentation describes the functions of the software. | [Finance home page](../../finance-welcome.md) and nested links<br>[France-specific functionality](france.md) <br> [Cash register functionality for France](/dynamics365/commerce/localizations/france/emea-fra-cash-registers) |
| Versioning strategy | This documentation describes the versioning approach and the version management procedure for the software product.<br>The current major Dynamics 365 Commerce version is **10.0**. Service updates for this version are indicated by a consecutive number after the version number: **10.0.X**. For more information about the software lifecycle policy and service updates, use the links in this table.</p>| <p>[One Version service updates overview](../../../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md)<br>[Software lifecycle policy and cloud releases](../../../fin-ops-core/dev-itpro/migration-upgrade/versions-update-policy.md)<br>[Service update availability](../../../fin-ops-core/dev-itpro/get-started/public-preview-releases.md)</p><p>[Dynamics 365 release plans](/dynamics365/release-plans/)<br>[What's new or changed in finance and operations apps home page](../../../fin-ops-core/fin-ops/get-started/whats-new-changed.md) |
| Organizational documentation | This documentation describes the process that is established to control software product compliance. | [Globalization resources](../../../fin-ops-core/fin-ops/lcs/globalization-resources.md) |
| Maintenance documentation | This documentation describes implementation and maintenance of the software solution. | [Service description](../../../fin-ops-core/dev-itpro/get-started/service-description.md)<br>[Before you buy](../../../fin-ops-core/fin-ops/get-started/before-you-buy.md)</p><p>[Dynamics 365 Licensing Guide](https://www.microsoft.com/licensing/docs/grid/Microsoft-Dynamics-365)<br>[Implementation lifecycle management home page](../../../fin-ops-core/dev-itpro/organization-administration/implementation-lifecycle.md)<br>[Dynamics 365 Support](https://dynamics.microsoft.com/support/)<br>[Submit service requests](../../../fin-ops-core/dev-itpro/lifecycle-services/submit-request-dynamics-service-engineering-team.md)<br>[One Version service updates overview](../../../fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview.md) |

## Software Requirements in France

### Number of opening exercises

According to the software requirements in France, limit the number of opening exercises to two.

To satisfy this requirement, set up Finance as follows. Set the value of the **Limited number of open fiscal years** field in **General ledger parameters** to no more than **2**. 
This field limits the total number of fiscal years that can be open at the same time. Article 1031-4 of the General Accounting Plan (Plan comptable général, formerly article 921-4) states that a closing procedure must be executed no later than the end of the next period.

### Number sequences

Set up number sequences for vouchers. Each voucher series must contain a piece of text that the [FEC file](emea-fra-fec-audit-file.md) considers as a value for the **JournalCode** field. For example, define the voucher series for vendor invoice journals as **FRSIFACF-\#\#\#\#\#\#\#\#** to get the value **FRSIFACF** in the **JournalCode** field in the FEC.

Set the **Continuous** field to **Yes** for number sequences that you use for invoice numbers and for general ledger transactions for vouchers. This setting accommodates article 100 of BOI-CF-IOR-60-40-20. The numbering  must increase over time, and it shouldn't include any break. The numbering must be either unique throughout the fiscal period or specific to each journal. (The original French text states, "La numérotation dans le champ «EcritureNum» doit être croissante dans le temps et ne pas comporter de rupture. Cette numérotation peut être unique sur l'ensemble du fichier ou être propre à chaque journal."). For more information about set up and use chronological numbers for invoices and vouchers, see [Chronological invoice and voucher numbers](emea-fra-chronological-invoices-vouchers.md).

### Chart of accounts

The chart of accounts that the legal entity uses with primary address in France must comply with the standard chart of accounts of France (Livre des procédures fiscales, article A47 A-1, chapter VII: "Le numéro de compte, dont the three first characters must correspond to numbers that respect the standards of the French accounting plan").
Use only main accounts that start with **1**, **2**, **3**, **4**, **5**, **6**, or **7**.

For more information about chart of accounts in Finance, see [Plan your chart of accounts](../../general-ledger/plan-chart-of-accounts.md) and [Plan your local chart of accounts](../../general-ledger/plan-local-chart-of-accounts.md).

Finance doesn't restrict the format of main account numbers, because the same chart of accounts can serve several countries/regions and internal management needs. If the chart of accounts of a legal entity in France also contains main accounts that don't follow the French chart of accounts (for example, accounts that start with letters and that are used for operational purposes, such as production or manufacturing), follow these rules: 

- Don't use these accounts for entries that must appear in the accounting books and in the FEC. 
- Make sure that the FEC contains only main accounts that start with 1, 2, 3, 4, 5, 6, or 7. Document which accounts and entries are excluded from the FEC and why, and keep this documentation in the tax archive. 
- Keep the origin of every entry traceable. To trace an entry back to the source document and the business event that created it, use the **Voucher transactions** page and the [Accounting source explorer](../../accounts-payable/accounting-source-explorer.md). 

### Posting profiles

Use a posting profile for all customer and supplier balance accounts. These main accounts start with **41** and **40**. Enable the **Do not allow manual entry** parameter for these accounts.

For more information about posting profiles in Finance, see:

- [Posting profiles overview](../../general-ledger/pstg-prfles-ovrvw.md)
- [Accounts receivable posting](../../general-ledger/accts-recvble-posting.md)
- [Customer posting profiles](../../accounts-receivable/customer-posting-profiles.md)
- [Accounts payable posting](../../general-ledger/accts-payble-posting.md)
- [Vendor posting profiles](../../accounts-payable/vendor-posting-profiles.md)
- [Recommended practices for posting profiles](../../general-ledger/recommended-practices-pstg-prfles.md)

### Source documents for general ledger transactions

Keep all supporting documents (*pièces justificatives*) for general ledger transactions, and the data you use to create them, for the retention period that French law requires. 
For the applicable periods, see article *L102 B* of the *Livre des procédures fiscales* and article *L123-22* of the *Code de commerce*. 
You must keep documents that you create or receive in electronic form in electronic form.

Finance helps you meet this requirement in the following ways:

- For entries that you create from source documents, such as invoices, Finance keeps the link between the voucher and the source document. Use the [Accounting source explorer](../../accounts-payable/accounting-source-explorer.md) to trace ledger balances back to the original documents.
- You can store the business documents that Electronic reporting (ER) generates, such as customer invoices, by using the [Archive ER destination type](/dynamics365/fin-ops-core/dev-itpro/analytics/er-destination-type-archive).
- Include the supporting documents and the related data in the tax archive of each fiscal year. For more information, see [Tax archive in France](emea-france-tax-archive.md).

### Currency

You must post accounting documents that require an [FEC file](emea-fra-fec-audit-file.md) in euros and in French.

For more information about configuring currencies for the ledger in Finance, see [Configuring currencies for the ledger](../../general-ledger/configure-ledger.md#configuring-currencies-for-the-ledger).

### Fichier des écritures comptables (FEC)

For specific settings in Finance recommended for [FEC file](emea-fra-fec-audit-file.md) generation in compliance with regulatory requirements in France, see [Prerequisites to generate an FEC audit file in France](emea-fra-fec-audit-file-pre-requisites.md).

### Transfer of subledger journal entries to the general ledger 

The batch transfer rules in **General ledger parameters** control when subledger journal entries are transferred to the general ledger. For legal entities in France, use the **Asynchronous** transfer mode, so that vouchers are recorded in the general ledger as soon as possible after the source document is posted. Before you close a period, ensure that all entries are transferred: go to **General ledger** \> **Periodic tasks** \> **Subledger journal entries not yet transferred**, and transfer the remaining entries. For more information, see [Subledger transfer to the general ledger](../../general-ledger/subledger-transfer.md). 

### Invoice dates 

To ensure that a customer invoice isn't posted with an invoice date that's earlier than the delivery date, set the **Allow invoice posting only if invoice date is after confirmed receipt date** parameter to **Yes** on the **Sales setup** tab of the **Accounts receivable parameters** page. For more information, see [Validate invoice dates for French regulation](../../accounts-receivable/invoice-date-france.md). 

### Tax archive 

French rules for computerized accounting require that you produce a tax archive (*archivage fiscal*) when you close each fiscal year, and before you purge any data. The archive must use an open format that can be read without Finance, it must be protected against changes, and you must keep it for the legal retention period. For the content of the archive, and for information about how to produce, store, and protect it, see [Tax archive in France](emea-france-tax-archive.md). 

### Corrections to a closed fiscal year 

After the closing procedure, a closed fiscal year must not be reopened, and validated entries must not be changed or deleted. Corrections are recorded as new reversing and correcting entries. Before the final closing, post adjustments in the closing period of the fiscal year instead of reopening the operating periods. If you must reverse the year-end close, restrict this function to authorized users, and follow a traceable procedure. For more information, see [Correct a closed fiscal year in France](emea-france-closed-fiscal-year-corrections.md). 

### Protection of data that's included in the FEC 

The FEC contains names and descriptions that come from master data and from posted entries, such as main account names, journal names, customer and vendor names, and entry descriptions. If you change these values after you validate the entries, an FEC that you generate again for a closed fiscal year can differ from the FEC that you generated at closing. To protect this data: 

- Grant the security privileges that allow changes to main account names, journal names, and customer and vendor names only to a small group of authorized users. 
- If you use the [Allow edits to internal data on general ledger vouchers](../../general-ledger/allow-edits-internal-data-gl-vouchers.md) functionality, assign the related roles only to authorized users. Users enter a reason for each edit. Every edit is recorded on the **Audit trail of voucher edits** page (**General ledger** \> **Periodic tasks** \> **Audit trail of voucher edits**), together with the previous and new values, the user, and the date and time. Include this audit trail in the tax archive. 
- Use [database logging](/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log) to record changes to these master data fields, and include the log in the tax archive. 
- Generate the FEC as part of the closing procedure, and keep this file in the tax archive as the reference version for the closed fiscal year.
  
## Registration of audit events

This section describes how audit mechanisms in Finance ensure traceability, integrity, and compliance for all NF203-certified computerized accounting events. These mechanisms include logging, monitoring, and verification of key actions.

For information about database logging in Finance, see [Configure database logging](../../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

### Code 10 or 15 - Change in the continuous sequence management mode

#### Continuous numbering management

Finance uses **Number Sequences** to manage continuous numbering for vouchers and other documents. These sequences ensure that document numbers are assigned without gaps, meeting French legal requirements.

*Documentation links*

- [Number Sequence Overview](../../../fin-ops-core/fin-ops/organization-administration/number-sequence-overview.md)

#### Change handling

An administrator makes changes in numbering configuration (such as scope, format, or periodicity) through the **Number Sequence** setup.
The system logs these changes in system administration history, ensuring traceability.

#### Immutability of existing documents

Documents you already created keep their original numbers. Finance doesn't allow retroactive renumbering, preserving integrity and compliance.

#### Audit trail

The system logs administrative changes to number sequences. You can review these logs for compliance audits.

### Code 30 - Fiscal year archiving 

Finance supports fiscal year archiving through the tax archive procedure that you run as part of the year-end closing. You generate the required files by using [Electronic Reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) (ER) and other standard reports, and you store them in a secure location by using the [Archive ER destination type](/dynamics365/fin-ops-core/dev-itpro/analytics/er-destination-type-archive) (Microsoft SharePoint or Azure Storage), with access restricted to authorized users. When the Archive destination is enabled, each generated file is saved with its job record on the **Electronic reporting jobs** page (**Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**). For the content of the archive and the detailed procedure, see [Tax archive in France](emea-france-tax-archive.md). 

### Code 50 - Period closing

#### Period closing functionality

Finance provides functionality to close fiscal periods (daily, monthly, or yearly) through the [Fiscal calendars, fiscal years, and periods](../../budgeting/fiscal-calendars-fiscal-years-periods.md) and [Financial period close workspace](../../general-ledger/financial-period-close-workspace.md). 
Once you close a period, no new postings or modifications can occur in that period, ensuring data integrity and compliance.

*Documentation links*

- [Year-end close](../../general-ledger/year-end-close.md)

#### Audit trail

The system logs all postings and period status changes. Users can't modify transactions in closed periods. Corrections require reversing entries in an open period.

### Code 60 - Fiscal year closing

Finance provides the year-end close process (**General ledger** \> **Period close** \> **Year-end close**), which transfers balances to the next fiscal year. The **Year-end close** page lists each run and each reversal of the year-end close for every legal entity, and the year-end close vouchers are available on the **Voucher transactions** page. For more information, see [Year-end close](../../general-ledger/year-end-close.md). 

Until the fiscal year is set to **Permanently closed**, an authorized user can reverse the year-end close or run it again. A reversal deletes the closing and opening entries of the previous run. In France, follow the procedure in [Correct a closed fiscal year in France](emea-france-closed-fiscal-year-corrections.md) so that these operations stay traceable. After the final closing, set the fiscal year to **Permanently closed** so that it can't be reopened and no transactions can be posted to it.

#### Audit trail

The system logs all postings and period status changes. The audit trail includes user identity, timestamps, and job execution details, ensuring traceability for compliance audits.

### Code 90 - Detection of an integrity flaw in secure data or in a tax archive

In Finance, the [FEC file](emea-fra-fec-audit-file.md) generated by using [Electronic Reporting](../../../fin-ops-core/dev-itpro/analytics/general-electronic-reporting.md) (ER) and [Audit Trail](../../general-ledger/view-journal-entries-transactions.md#audit-trail) features satisfies the data security and immutability requirements.

When you generate and archive the FEC, you store the file in a secure location, such as Azure Blob or SharePoint, with access controlled by a system administrator.
Finance doesn't allow modification of archived files through the standard UI - storage and permissions defined by a system administrator enforce immutability.
In Finance, the accounting entries are stored in the `GeneralJournalEntry` and `GeneralJournalAccountEntry` tables, together with their related references.
The transaction records contain date, amount, text, creation date, and created-by fields. You can correct an accounting entry only by adding new reversing and correcting entries, not by changing the existing records. Finance doesn't provide any way for users to alter these records.

*Documentation links*

- [View journal entries and transactions, Audit trail](../../general-ledger/view-journal-entries-transactions.md#audit-trail)
- [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview)

For information about database logging in Finance, see [Configure database logging](../../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

### Code 180 - Generating an export file of accounting entries

Event 180 occurs when you use the [FEC file](emea-fra-fec-audit-file.md) export functionality in Finance, combined with the [Archive ER destination type](../../..//fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) setup and batch logging mechanism.

#### Archive destination setup

The [FEC file](emea-fra-fec-audit-file.md) generation process requires that you configure an [Archive ER destination type](../../..//fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) in the system. This setup ensures that the exported file is stored in a designated, secure archive location.

#### Audit logging

The batch execution automatically records metadata about the generation process, including:

- Who initiates the export (user identity)
- When the export is performed (timestamp)
- Job status and execution details

*Documentation links*

- [Batch processing overview](../../../fin-ops-core/dev-itpro/sysadmin/batch-processing-overview.md)
- [Electronic reporting (ER) destinations](../../../fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations.md)

### Code 250 - Installation of a new major version 

Finance follows the One Version policy: all customers run the current major version (10.0), and Microsoft delivers service updates that are identified by a consecutive number (10.0.X). Each update of an environment is recorded in the environment history in Microsoft Dynamics Lifecycle Services or the Power Platform admin center. To view the installed version, select the **Help & support** (**?**) button in Finance, and then select **About**. For more information, see [One Version service updates overview](/dynamics365/fin-ops-core/dev-itpro/lifecycle-services/oneversion-overview).

### Mapping of technical event log codes 

Finance records the events of the dictionary \[R19\] by using the alternative traceability mechanisms in the following table. X = mandatory, C = mandatory if the functionality exists, O = optional. *Purgeable* shows whether the event can be partially purged according to the dictionary. 

| Code | Event | NF203 | Purgeable | How Finance records the event | Where to review it | 
|---|---|---|---|---|---| 
| 10 or 15 | Change in the continuous sequence management mode | C | No | Changes to number sequences, such as the **Continuous** setting, the format, or the scope. Turn on database logging for number sequences. | Database log | 
| 20 | Periodic tax archiving | C | Yes | Each file that's generated for a periodic archive by an ER format that has an Archive destination. | Electronic reporting jobs | 
| 30 | Tax archiving for a fiscal year | X | No | See [Code 30](#code---30-fiscal-year-archiving). | Electronic reporting jobs, tax archive | 
| 50 | Period closing | X | Yes | Changes to the status of ledger periods (**Open**, **On hold**, **Permanently closed**). Turn on database logging for ledger period statuses. | Database log, Financial period close workspace | 
| 60 | Fiscal year closing | X | No | Runs and reversals of the year-end close, and the year-end close vouchers. | Year-end close, Voucher transactions, Batch job history | 
| 90 | Detection of an integrity flaw in secured data or in a tax archive | X | No | Alternative solution: amounts, accounts, and dates of posted entries can't be changed through the application. Tax archives are stored in protected storage that keeps access and audit logs. The archived FEC can be compared with an FEC that's generated from current data. | Storage audit logs, tax archive | 
| 95 | Detection of a break in the continuous sequence | C | No | The FEC Missing numbers justification report lists breaks in voucher numbering and their reasons. | [Missing numbers justification](emea-fra-fec-audit-file-structure.md#missing-numbers-justification) | 
| 100, 105 | Start and end of a special function | C | No | Finance separates training and testing from live operations by environment, not by a special operating mode. Every subscription includes a sandbox environment for user acceptance testing, integration testing, and training, and you can add more sandbox environments. The production environment is used to run the business. For more information, see [Environment planning](/dynamics365/fin-ops-core/dev-itpro/organization-administration/environment-planning). | Environment details in Lifecycle Services or the Power Platform admin center |
| 110 | Data export | C | Yes | Exports by Data management projects and by ER formats, with the user and the date and time. | Data management job history, Electronic reporting jobs | 
| 130 | User authorization and rights management | C | Yes | Changes to user role assignments. Turn on database logging for user role assignments and users. | Database log | 
| 140 | Import of external data | C | Yes | Imports by Data management projects and by ER import formats, with the user and the date and time. | Data management job history, Electronic reporting jobs | 
| 160 | Recording of entries in accounting | O | No | Each voucher keeps the user who created it and the date and time of creation. | Voucher transactions | 
| 180 | Generation of an export file of accounting entries | X | Yes | See [Code 180](#code-180---generating-an-export-file-of-accounting-entries). | Electronic reporting jobs | 
| 200 | Data purge | C | No | Cleanup and archiving jobs run as batch jobs. If you decide, based on your business needs, to purge data, do so only after the fiscal year is closed and its tax archive is complete. | Batch job history | 
| 205 | Partial purge of the JET | C | No | Cleanup of the database log runs as a batch job. If you decide, based on your business needs, to clean up the database log, do so only after you export the log to the tax archive. | Batch job history | 
| 210 | Data migration from other software | C | No | Data management import projects that are used for the migration. | Data management job history | 
| 220, 230 | Restore and backup of a database | C | No | Database operations, such as point-in-time restore, are requested and recorded in the environment history in Lifecycle Services or the Power Platform admin center. | Environment history | 
| 240 | Maintenance interventions | C | No | Updates and maintenance operations on an environment are recorded in the environment history. | Environment history | 
| 250 | Installation of a new major version | X | No | See [Code 250](#code-250---installation-of-a-new-major-version). | Environment history | 
| 255 | Installation of a new minor version | C | Yes | Service updates are recorded in the environment history. | Environment history | 
| 260 | Data initialization | C | No | Initial data loads by Data management projects. | Data management job history | 
| 270 | Change of a compliance parameter | C | No | Turn on database logging for the parameters that affect compliance (general ledger, accounts receivable, and accounts payable parameters, number sequences, and fiscal calendars). ER configuration versions keep the author, date, and description, and a completed version can't be changed. | Database log, ER configurations | 
| 280 | Start and end of a tax audit operation | C | Yes | If you create a dedicated user account for a tax auditor, the sign-ins of this account are recorded in the user log. | User log | 
| 290 | Exchange with a chartered accountant | O | Yes | Generation of the FEC and other exports by ER formats. | Electronic reporting jobs | 
| 295 | File transfer at the request of the tax administration | C | No | Generation of the requested files, such as the FEC, by ER formats. Record the transfer in the tax archive. | Electronic reporting jobs, tax archive | 
| 300 | Activation of an authorized and documented parameter | C | No | Replaced by code 270. | Database log | 
| 330 | Start of the period-end closing | O | Yes | Period-end tasks in the Financial period close workspace. | Financial period close workspace | 
| 400 | Change in the duration of the fiscal year | C | No | Turn on database logging for fiscal calendars, fiscal years, and periods. | Database log | 
| 410 | Change of data that identifies the taxable person | C | No | Turn on database logging for legal entity data, such as the name, address, and registration numbers (SIREN, SIRET, and VAT number). | Database log | 
| 440 | Transfer of tax archives to external media | O | No | Files that are stored by the Archive destination, and the access and audit logs of the storage. | Storage audit logs | 
| 450 | Change of the key pair that's used for signing | C | No | Not applicable. Finance doesn't sign accounting data with a key pair. | Not applicable |

### Settings that protect non-purgeable events 

To ensure you don't lose events that the dictionary \[R19\] says you can't purge, set up Finance as follows: 

1. Turn on database logging for the following data. Use the **Logging database changes** wizard (**System administration** \> **Setup** \> **Database log** \> **Database log setup**). For more information, see [Configure database logging](/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log).  

    - Number sequences (codes 10 and 15) 
    - Ledger period statuses and fiscal year statuses (codes 50 and 60) 
    - Fiscal calendars, fiscal years, and periods (code 400) 
    - General ledger, accounts receivable, and accounts payable parameters (code 270) 
    - Legal entity data and registration numbers (code 410) 
    - User role assignments and users (code 130) 
    - Main accounts and journal names (data that's included in the FEC)  

1. Don't clean up database log entries, batch job history, or Electronic reporting job records for a fiscal year until the tax archive of that fiscal year includes them. 
1. Restrict access to the **Database log setup** page and to the **Clean up log** function to system administrators. 
1. Before you run any job that purges or archives accounting data, close the fiscal year and complete its tax archive. 

### Review the recorded events 

Tax auditors and administrators can review the recorded events on the following pages. 

| Page | Navigation | Events | 
|---|---|---| 
| Database log | **System administration** > **Inquiries** > **Database** > **Database log** | Changes to logged tables and fields (codes 10, 15, 50, 130, 270, 400, and 410) | 
| Electronic reporting jobs | **Organization administration** > **Electronic reporting** > **Electronic reporting jobs** | Generation of the FEC and other archive files (codes 20, 30, 180, 290, and 295) | 
| Batch job history | **System administration** > **Inquiries** > **Batch jobs** > **Batch job history** | Year-end close, cleanup, and purge jobs (codes 60, 200, and 205) | 
| Data management job history | **Data management** workspace > **Job history** | Data imports and exports (codes 110, 140, 210, and 260) | 
| Year-end close | **General ledger** > **Period close** > **Year-end close** | Runs and reversals of the year-end close (code 60) | 
| Audit trail of voucher edits | **General ledger** > **Periodic tasks** > **Audit trail of voucher edits** | Changes to the description and financial tags of posted vouchers | 
| User log | **System administration** > **Inquiries** > **Users** > **User log** | Sign-ins, including the account of a tax auditor (code 280) | 

### Export the event log for the tax archive 

At each year-end closing, export the events of the fiscal year from the pages in the previous table to an open format, such as CSV or Excel. For example, export the database log entries of the fiscal year. Store the files in the tax archive together with this mapping. For more information, see [Tax archive in France](emea-france-tax-archive.md). 

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
