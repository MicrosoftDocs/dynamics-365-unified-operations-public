---
# required metadata

title: Audit trail and edit logs for accounting software 
description:  This topic provides information about the new Indian tax legislation guidelines for accounting software.
author: EricWangChen
ms.date: 02/07/2022
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

# ms.search.form: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
# ms.tgt_pltfrm: 
# ms.custom: 
ms.search.region: India
# ms.search.industry: 
ms.author: wangchen
ms.search.validFrom: 
ms.dyn365.ops.version: 

---

# Audit trail and edit logs for accounting software 

[!include [banner](../includes/banner.md)]

As of 1 March, 2022, Microsoft Dynamics 365 Finance is in compliance with the new Indian tax legislation guidelines for accounting software for recording the audit trail of all transactions. Additionally, an edit log is created for each change made to an account along with the date on which the change was made.   

## The legislation
According to the principal notification No. GSR 205 (E) dated 24th March 2021 amended vide notification G.S.R.247(E) dated 01.04.2021, it is stated that w.e.f.  01.04.2022, all the businesses who are using accounting software for maintaining books of accounts should have an audit trail feature comprising of the following:

- Recording audit trail of every transaction
- Create an audit log of each change made in the books of accounts,
- Capture the date details when such changes (edits) are made,
- Software to ensure that the audit trail cannot be disabled.

Further, the rules state the Audit Trail feature should have been operated throughout the year for all the transactions recorded in the software, the Audit Trail feature has not been tampered with, and the audit trail feature has been preserved by the company.

## Compliance

### Compliance 1
Under new guidelines of companies’ act which specify the manner of account books which must be kept in electronic mode and every company which uses accounting software for maintaining its books of accounts, shall use only such accounting software which has a feature of recording audit trail. The following is the key compliance for the audit trail.

- **Recording audit trails for each transaction** - Under the audit trail, the system records and traces the data sources. The data traced normally is made up of:

    - **Accounting data of a transaction** - Entries that are posted in the General ledger.
    - **Trade data of a transaction** - This includes credit limits and payment terms, among other types.
    - **Other data of a transaction** - This can include user log information.

#### Accounting data

Finance is fully compliant regarding the recording of accounting data. The **Audit trail** function on the **Voucher transaction inquiry** page fetches the financial transaction entries posted in the general ledger and reports. The function can show who posted the transaction, when, and from which document type. There is a created date and time that represents the actual date when the transaction was posted. The **Audit trail inquiry** page also allows users to view the voucher transactions. For more information, see [View journal entries and transactions](../general-ledger/view-journal-entries-transactions.md).

#### Trade data

You can use the database logging in Finance to track specific types of changes to tables and fields. Changes that can be tracked include creating, reading, updating, deleting, and renaming key operations. When you enable a database log for any table, it's important to note that different types of a table may have different performance implications. Generic observation of the database log indicates that performance is impacted as shown in the following table.

|  Table category   |  Data volume  |  Performance impact  |
|-------------------|---------------|----------------------|
| Transaction table | High          |  High                |
| Master table      | Medium        |  Medium              |
| Setup table       | Low           |  Low                 |

> [!NOTE]
> This is a general guideline. The guideline may vary based on a specific business scenario.

When you configure the logging for a table or field, a record of every change to that table or field is stored in the database log table, **sysdatabaselog**. This log table is stored in the environment database. With this feature, you can track changes in any trade data such as credit limit or payment terms.

Companies using Finance to maintain books of accounts are fully compliant to the new notifications and can track transaction data to the source. For more information, see [Configure database logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

#### Other data

- **User log**: System administrators can use the **User log** page to keep an audit log of users who have logged on to the system. Users can protect an organization’s data by keeping track of logging information. For more information, see [Manage access to sensitive data](../../fin-ops-core/dev-itpro/gdpr/gdpr-auditing-sensitive-data.md).

    ![User log page.](media/user-log-page.png)
    
- **Workflow** - Finance provides a report to view the status of a document that was submitted to the workflow system for processing and approval. Through this report, you can view approvals with a date stamp and document type. For more information, see [View workflow history](../../fin-ops-core/fin-ops/organization-administration/tasks/view-workflow-history.md).
- **Log edits made to the book of accounts** - In Finance, changes to posted financial data isn't allowed. Financial transactions that are posted can't be edited, but they can be reversed. The audig logs provide information about the transaction, including:

    - The user who accessed the system and when
    - The user who updated the field value on the record and when the update was made
    - The field value before it was changed
    - The recent actions taken by the user
    - The user who deleted the record
    - The locale used to make the update

  For more information, see [Set up the audit log connector](/power-platform/guidance/coe/setup-auditlog).

- **Ensure the audit trail can't be turned off** - Finance doesn't allow you to turn off the **Audit trail** feature. The **Audit trail** report is generated by default for a legal entity. You can filter the period frequency to display data immediately. However, the option is provided in the system to start or stop the auditing and retention policy for audit logs. For more information, see [Audit data and user activity for security and compliance](/power-platform/admin/audit-data-user-activity). 

### Compliance 2
The books of accounts and other relevant books and papers will be retained in one of the following formats: 

  - The format that they were originally generated, sent, or received 
  - A format that accurately presents the information generated, sent, or received 

The information contained in the electronic records shall remain complete and unaltered.

Transactions posted in Finance remain complete and in the format in which they were originally generated. There is no process in Finance to change the format or content of a posted transaction. 

### Compliance 3
The information received from branch offices isn't updated and is kept as it was originally received from the branches.

In Finance, changes to posted financial data aren't allowed. After they are posted, financial transactions can't be edited directly, they can be only reversed. Data that is sent from a branch to a head office, can't be changed by the head office. However, you can make adjustments in the posted transaction through the specified mode of the transaction posted in the ledger of both the branch and the head office. 

### Compliance 4
The information in the electronic record of the document is displayed on a page in Finance. The **Electronic Reporting (ER) format configurations** feature available in Finance allows at least one output component per file. Typically, configurations contain multiple file output components of different types. For example, XML, TXT, XLSX, DOCX, or PDF. These components are grouped into either one or multiple folders. The ER destination management lets you preconfigure what occurs when each component is run. By default, when a configuration is run, a dialog box appears that lets you save or open the file. The file opens in the defined output components. 

### Compliance 5
There is a proper system for storage, retrieval, display, and printout of the electronic records. These electronic records are not to be disposed of or rendered unusable unless permitted by law. Provided that the back-up of the account books and other books and papers of the company are maintained in electronic mode, including a location outside of India, they qill be kept in servers that are physically located in India.

Finance can be deployed into a subset of Microsoft Azure datacenters using Dynamics Lifecycle Services (LCS). Azure is generally available in data centers and geographical locations around the world. With Finance, customers can specify the region or datacenter where their customer data will be stored. Microsoft may replicate data to other regions for data durability, but customer data will not be replicated or moved outside the geographical location.
Microsoft provides business continuity and disaster recovery for production instances of Dynamics 365 software as a service (SaaS) applications if a Microsoft Azure region-wide outage occurs. Paired regions reside within the same geography as their enabled set to meet data residency requirements for tax and law enforcement jurisdiction purposes. For more information, see [Business continuity and disaster recovery](../../fin-ops-core/dev-itpro/sysadmin/business-continuity-disaster-recovery.md).

### Compliance 6
On an annual basis, the company will provide the following information to the Registrar when filing a financial statement.

  - The name of the service provider.
  - The internet protocol address of service provider.
  - The location of the service provider, wherever applicable.
  - The location of where the books of accounts and other books and papers are maintained in the cloud, such as the address provided by the service provider.

This information is protected under server security. We don't recommend that you include this information on any publicly available financial report. You can manually add this information to any specific report. 


[!INCLUDE[footer-include](../../includes/footer-banner.md)]
