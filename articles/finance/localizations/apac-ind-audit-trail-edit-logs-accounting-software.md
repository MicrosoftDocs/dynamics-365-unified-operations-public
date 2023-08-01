---
# required metadata

title: Audit trail and edit logs for accounting software
description: This article provides information about the new Indian tax legislation guidelines for accounting software.
author: EricWangChen
ms.date: 04/21/2023
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

As of March 1, 2022, Microsoft Dynamics 365 Finance is in compliance with the new Indian tax legislation guidelines for accounting software to record an audit trail of all transactions. Additionally, an edit log is created for each change that is made to an account. This log records the date when the change was made.

## The legislation

Principal notification No. GSR 205 (E) dated March 24, 2021, and amended vide notification G.S.R.247(E) dated April 1, 2021, states that, as of April 1, 2022, all businesses that use accounting software to maintain books of accounts should have an audit trail feature that includes the following functionality:

- Recording an audit trail of every transaction
- Creating an audit log of every change that is made in the books of accounts
- Capturing the date details when those changes (edits) are made
- Ensuring that the audit trail can't be disabled

Additionally, the rules state that the audit trail feature should meet these conditions:

- It has used throughout the year, for all transactions that are recorded in the software.
- It hasn't been tampered with.
- The audit logs that it generated have been preserved by the company.

## Compliance

### Compliance 1: Recording an audit trail

Under new guidelines of the Companies Act that specify how account books must be kept in electronic format, every company that uses accounting software to maintain its books of accounts must use only accounting software that has a feature for recording an audit trail. For compliance, the system must record and trace the data sources in the audit trail.

Typically, the following data is traced for a transaction:

- **Accounting data** – Entries that are posted in the general ledger.
- **Trade data** – This data includes credit limits and payment terms, among other types.
- **Other data** – This data can include user log information.

#### Accounting data

Finance is fully compliant with the requirement to record accounting data. The **Audit trail** function on the **Voucher transaction inquiry** page fetches the financial transaction entries that are posted in the general ledger and on reports. The function opens the **Audit trail inquiry** page, which shows who posted the transaction, when, and from which document type. The following graphic shows the autidt trail option in Finance. 

   ![Standard view of audit trail page.](media/standard-view-page.png)
    
Additionally, a creation date and time value represents the date when the transaction was posted. The **Audit trail inquiry** page also lets users view the voucher transactions. For more information, see [View journal entries and transactions](../general-ledger/view-journal-entries-transactions.md).

#### Trade data

You can use the database logging in Finance to track specific types of changes to tables and fields. Changes that can be tracked include create, read, update, delete, and rename key operations. When you enable a database log for any table, note that the impact on performance might vary, depending on the category of table. In general, performance is affected as shown in the following table.

| Table category    | Data volume | Performance impact |
|-------------------|-------------|--------------------|
| Transaction table | High        | High               |
| Master table      | Medium      | Medium             |
| Setup table       | Low         | Low                |

> [!NOTE]
> This guideline is a general guideline. It might vary, depending on the specific business scenario.

When you configure logging for a table or field, a record of every change to that table or field is stored in the database log table, **sysdatabaselog**. This log table is stored in the environment database. You can use this feature to track changes in any trade data, such as credit limits or payment terms.

   ![Database log page.](media/database-log-page.png)

Companies that use Finance to maintain books of accounts are fully compliant with the new notifications and can track transaction data to the source. For more information, see [Configure database logging](../../fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log.md).

> [!IMPORTANT]
> Enabling database logs for tables and fields can track changes including insert, update, delete, and rename key operations. However, enabling the functionality might also impact performance. We recommend that you contact Microsoft support before you enable this functionality.

#### Other data

- **User log** – System administrators can use the **User log** page to keep an audit log of users who have signed in to the system. Users can help protect an organization's data by tracking logging information. For more information, see [Manage access to sensitive data](../../fin-ops-core/dev-itpro/privacy/privacy-auditing-sensitive-data.md).

    ![User log page.](media/user-log-page.png)

- **Workflow history** – Finance provides a report that shows the status of a document that was submitted to the workflow system for processing and approval. You can use this report to view approvals. A date stamp and document type are shown. 

    ![Workflow system approvals.](media/workflow-history.png)

    For more information, see [View workflow history](../../fin-ops-core/fin-ops/organization-administration/tasks/view-workflow-history.md).
    
- **Log of edits that are made to the book of accounts** – In Finance, changes can't be made to posted financial data. Therefore, financial transactions can't be edited after they are posted. However, they can be reversed. The audit logs provide information about the transaction. Here are some examples:

    - The user who accessed the system and when
    - The user who updated the field value on the record and when
    - The field value before it was changed
    - Recent actions that the user has taken
    - The user who deleted the record
    - The locale that was used to make the update

    In the case of data corruption, you can correct minor data inconsistencies without disruptive downtime. You can upload and run deployable packages that contain custom X++ scripts to correct the data. For more information, see [Run custom X++ scripts with zero downtime](../../fin-ops-core/dev-itpro/deployment/run-custom-scripts.md).
    
- **Ensuring that the audit trail can't be turned off** – Finance doesn't allow you to turn off the **Audit trail** feature. By default, the **Audit trail** report is generated for a legal entity. You can filter the period frequency so that data is shown immediately. However, the system provides an option that lets you to start or stop the auditing and retention policy for audit logs. 

### Compliance 2: Retain books of accounts in the original format

The books of accounts and other relevant books and papers are retained in one of the following formats:

- The format that they were originally generated, sent, or received in
- A format that accurately presents the information that was generated, sent, or received

The information in the electronic records will remain complete and unaltered.

Transactions that are posted in Finance remain complete and in the format that they were originally generated in. Finance includes no process for changing the format or content of a posted transaction.

### Compliance 3: Preservation of branch transactions information

The information that is received from branch offices isn't updated and is kept as it was originally received from the branches.

In Finance, changes can't be made to posted financial data. Therefore, financial transactions can't be edited after they are posted. However, they can be reversed. Data that is sent from a branch to a head office can't be changed by the head office. However, you can adjust the posted transaction through the specified mode of the transaction, such as a credit note or tax journal, that was posted in the ledger of both the branch and the head office.

### Compliance 4: Display of electronic record in legible format

The information in the electronic record of the document is shown in Finance. The **Electronic Reporting (ER) format configurations** feature that is available in Finance enables at least one output component per file. Typically, configurations contain multiple file output components of different types (for example, XML, TXT, XLSX, DOCX, and PDF). These components are grouped into one or multiple folders. Electronic reporting (ER) destination management lets you preconfigure what occurs when each component is run. By default, when a configuration is run, a dialog box appears that lets you save or open the file. The file is opened in the defined output components.

### Compliance 5: Maintain proper system of storage of electronic record

There is a proper system for storing, retrieving, displaying, and printing the electronic records. These electronic records must not be disposed of or rendered unusable unless those actions are permitted by law. Provided that a backup of the company's books of accounts and other books and papers is maintained in electronic mode, even in a location that is outside India, it will be kept on servers that are physically located in India.

Finance can be deployed into a subset of Azure datacenters by using Microsoft Dynamics Lifecycle Services (LCS). Azure is generally available in datacenters and geographical locations around the world. Finance lets customers specify the region or datacenter where their customer data will be stored. Although Microsoft might replicate data to other regions for data durability, customer data won't be replicated or moved outside the geographical location.
Microsoft provides business continuity and disaster recovery for production instances of Dynamics 365 software as a service (SaaS) applications if an Azure region-wide outage occurs. Paired regions reside within the same geography as their enabled set to meet data residency requirements for tax and law enforcement jurisdiction purposes. For more information, see [Business continuity and disaster recovery](../../fin-ops-core/dev-itpro/sysadmin/business-continuity-disaster-recovery.md).

### Compliance 6: Information for filling of annual financial statement

On an annual basis, the company will provide the following information to the Registrar when it files a financial statement:

- The name of the service provider
- The Internet Protocol (IP) address of the service provider
- The location of the service provider, wherever applicable
- The location where the books of accounts and other books and papers are maintained in the cloud (for example, the address that was provided by the service provider)

This information is protected by server security. We don't recommend that you include it on any publicly available financial report. You can manually add this information to any specific report.

[!INCLUDE[footer-include](../../includes/footer-banner.md)]
