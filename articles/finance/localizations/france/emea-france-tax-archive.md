---
title: Tax archive in France
description: Learn how to set up, produce, and protect the tax archive (archivage fiscal) of a fiscal year in France by using Dynamics 365 Finance and Microsoft 365.
author: liza-golub
ms.author: egolub
ms.topic: how-to
ms.date: 11/16/2026
ms.reviewer: johnmichalak
ms.search.region: France
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Tax archive in France

[!include [banner](../../includes/banner.md)]

This article explains how legal entities that have their primary address in France can use Microsoft Dynamics 365 Finance, SharePoint, and other Microsoft 365 services to produce, store, and protect their tax archive (*archivage fiscal*). The French rules for computerized accounting require a tax archive, and the NF203 certification requirements for accounting software include it.

## Requirements

The French tax administration describes the requirements for computerized accounting in [BOI-BIC-DECLA-30-10-20-40](https://bofip.impots.gouv.fr/bofip/2899-PGP.html/identifiant=BOI-BIC-DECLA-30-10-20-40-20180720). The following paragraphs of this guidance apply to the tax archive:

- **Content (§ 490)** – No fixed list. Archive all the data in your information system that directly or indirectly justifies the accounting entries: the entries, with enough detail to rebuild the accounting books; history files, such as orders, deliveries, inventory movements, invoices, and quotations; and reference files, such as the chart of accounts, customers, vendors, prices, and code tables, as they were during the archived fiscal year.
- **Fixed date and open format (§ 550)** – The archive gives the data a fixed date for each period or fiscal year. The data is copied to durable media in a format that can be read without the software that created it, such as TXT or CSV. The data stays available in Finance for day-to-day work.
- **An archive isn't a backup (§ 560)** – A backup of the database doesn't replace the tax archive.
- **Timing (§ 570 and § 580)** – Archive the data when you close the fiscal year or the accounting period, after the period closings. Produce at least one archive per fiscal year. Monthly or quarterly archives give additional protection.
- **Protection (§ 630)** – You can protect archives and change logs with a reliable electronic signature.

In addition, the NF203 certification rules require that data is purged only after the fiscal year is closed and its tax archive is produced. Keep the tax archive for the legal retention period. For the applicable period, see article L102 B of the *Livre des procédures fiscales*.

## Overview of the solution

You can produce and keep the tax archive by using standard capabilities:

- [**Electronic reporting (ER)**](../../../fin-ops-core/dev-itpro/analytics/er-overview-components.md#format-component) formats generate the files of the archive, such as the FEC and the VAT declaration, in open formats.
- The [**Archive** ER destination](../../../fin-ops-core/dev-itpro/analytics/er-destination-type-archive.md) stores each file that an ER format generates in a dedicated SharePoint folder as soon as the file is generated. The **Electronic reporting jobs** page keeps a record of each generation.
- [**Database logging**](/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log) records changes to the data and settings that you select. You export its entries to the archive when you close the fiscal year.
- [**SharePoint permissions**](/sharepoint/modern-experience-sharing-permissions) and [**Microsoft Purview retention labels**](/purview/retention) protect the archived files against changes and deletion.
- [**Power Automate**](/power-automate/triggers-introduction) can automate the collection of other files in the archive.

## Prerequisites

- A Finance environment that Microsoft manages. SharePoint storage for documents isn't available in other environments.
- SharePoint Online in the same Microsoft Entra tenant as the Finance environment.
- The ER formats that generate content of the archive, such as [**FEC audit file (FR)**](emea-fra-fec-audit-file.md) and [**VAT Declaration Excel (FR)**](emea-fra-VAT-declaration-preview-France.md), are imported in Finance.
- Database logging is set up as described in [Registration of audit events](emea-france-nf203.md#registration-of-audit-events).

## Content of the tax archive

The following table lists the content of the tax archive for each fiscal year, and how you can produce each item.

| Content | How to produce it |
| --- | --- |
| Accounting entries file (FEC) and its description | Generate the FEC for the closed fiscal year, together with the Missing numbers justification annex, by using the **FEC audit file (FR)** format with an Archive destination. For more information, see [Audit file for France (Fichier des écritures comptables, FEC)](emea-fra-fec-audit-file.md) and [Structure of Dynamics 365 Finance data sources for the FEC](emea-fra-fec-audit-file-structure.md). |
| VAT returns and VAT tables | Generate the VAT declaration by using the **VAT Declaration Excel (FR)** format with an Archive destination. Also export the sales tax setup: sales tax codes, groups, and rates. For more information, see [VAT declaration (France)](emea-fra-VAT-declaration-preview-France.md). |
| General ledger, journals, and trial balance | Export or print the general ledger, the journals, and the trial balance of the fiscal year. For more information, see [Close the general ledger at period end](../../general-ledger/close-general-ledger-at-period-end.md). |
| Subsidiary ledgers, and customer and vendor account cards | Generate the customer and vendor account statements of the fiscal year. For more information, see [Customer and vendor account statements for France](fr-00002-customer-vendor-account-statements.md). |
| Chart of accounts and reference data | Export the main accounts, customers, vendors, products, and other reference data that the entries use, as they are at the closing date. You can use [Data management export projects](/dynamics365/fin-ops-core/fin-ops/data-entities/data-import-export-job). |
| Compliance parameters | Export the parameters that affect compliance, such as general ledger parameters, number sequences, fiscal calendars, and posting profiles, as they are at the closing date. |
| Supporting documents | Keep the business documents that Finance issued, such as customer invoices, and the original electronic documents that you received, such as vendor electronic invoices. See [Archive other content](#archive-other-content). |
| Technical event log (JET) | Export the database log entries and the other recorded events of the fiscal year. For more information, see [Registration of audit events](emea-france-nf203.md#registration-of-audit-events). |
| Images of the accounting books and tax returns | Keep the accounting books and the returns that you filed in a readable image format, such as PDF. |
| List of archived files | Keep a list of the files in the archive, with a description of the structure of each file and of the origin of the accounting entries. |

## Set up the archive location

### Create the archive folders

Create a dedicated location for the tax archive in SharePoint Online. For example, create a site or a document library named *Tax archive*. In this location, create a folder for each legal entity. In each legal entity folder, create a subfolder for each type of content.

```text
Tax archive
└── FRSI (legal entity)
    ├── 01 FEC
    ├── 02 VAT returns
    ├── 03 Accounting books
    ├── 04 Business documents
    ├── 05 Event log
    └── 06 Reference data and settings
```

To keep the files of each fiscal year together, create a subfolder for each fiscal year and move the files to it when you complete the archive of the fiscal year.

### Protect the archive

- **Access** – Manage access through the SharePoint groups of the archive site. For example, add the users who produce the archive to the Members group, and add the users who must only consult the archive, such as auditors, to the Visitors group, which has the Read permission level. Ensure that nobody can change or delete archived files. For more information, see:

  - [Sharing and permissions in the SharePoint modern experience](/sharepoint/modern-experience-sharing-permissions)
  - [Understanding permission levels in SharePoint](/sharepoint/understanding-permission-levels)
  - [Customize permissions for a SharePoint list or library](https://support.microsoft.com/office/customize-permissions-for-a-sharepoint-list-or-library-02d770f3-59eb-4910-a608-5f84cc297782)

- **Protection against changes and deletion** – Apply Microsoft Purview retention labels that declare the archived files as records. Records restrict editing and prevent deletion. To label new files automatically, set the label as the default retention label of the archive library or folders. Licensing requirements depend on the features that you use. For more information, see:

  - [Learn about retention policies and retention labels](/purview/retention)
  - [Learn about records management](/purview/records-management)
  - [Declare records by using retention labels](/purview/declare-records)
  - [Publish retention labels and apply them in apps](/purview/create-apply-retention-labels)
  - [Get started with records management](/purview/get-started-with-records-management)

    If you keep archive files in an Azure storage account that you own, use a time-based retention policy. For more information, see [Store business-critical blob data with immutable storage](/azure/storage/blobs/immutable-storage-overview).

- **Traceability** – Use the version history of the archive library and the Microsoft Purview audit log to trace who added or accessed archived files. Audit records are kept for a limited period that depends on your license, so export them if you need them for longer. For more information, see [Search the audit log](/purview/audit-search).

## Connect Finance to SharePoint

To connect Finance to SharePoint, follow these steps:

1. Go to **Organization administration** \> **Document management** \> **Document management parameters**.
1. On the **SharePoint** tab, in the **Default SharePoint server** field, verify the host name of your SharePoint tenant, such as *contoso.sharepoint.com*.
1. Test the connection. If the **SharePoint user authentication** feature is enabled, select **Test interactive SharePoint connection** and **Test batch SharePoint connection**. To generate archive files in batch mode, a tenant administrator must grant access to SharePoint for batch jobs one time. For more information, see [Configure document management](/dynamics365/fin-ops-core/dev-itpro/organization-administration/configure-document-management).

> [!NOTE]
> SharePoint managed device policies aren't compatible with the integration between Finance and SharePoint.

## Create document types for the archive

Create a document type for each archive folder. Each document type defines the SharePoint folder where Finance stores the files.

To create document types for the archive, follow these steps:

1. Go to **Organization administration** \> **Document management** \> **Document types**.
1. Select **New**, and then set the following fields:

    - **Type** – Enter a short name, such as *TA-FEC*.
    - **Name** – Enter a description, such as *Tax archive - FEC*.
    - **Class** – Select **Attach file**.
    - **Group** – Select **File**.
    - **Location** – Select **SharePoint**.
    - **SharePoint Address** – Select the archive folder, such as *Tax archive/FRSI/01 FEC*.

1. Repeat these steps for each folder of the archive.

> [!IMPORTANT]
> Use the **SharePoint** location for the archive document types. If a document type uses the **Azure storage** location, Finance stores the files as attachments in the storage of the Finance environment and deletes each file together with the record that it's attached to.

## Send Electronic reporting output to the archive

Set up an Archive destination for each ER format that generates content for the tax archive, such as **FEC audit file (FR)** and **VAT Declaration Excel (FR)**.

To send Electronic reporting output to the archive, follow these steps:

1. Go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting destination**.
1. Select **New**, and then, in the **Reference** field, select the ER format, such as **FEC audit file (FR)**.
1. On the **File destination** FastTab, select **New**. In the **Name** field, enter a name. In the **File name** field, select the file or folder component of the format.
1. Select **Settings**.
1. In the **Destination settings** dialog box, on the **Archive** tab, set the **Enabled** option to **Yes**. In the **Document type** field, select the document type of the archive folder, such as *TA-FEC*.
1. Select **OK**.
1. Repeat these steps for each ER format that generates content for the archive.

When you run the format, Finance stores the generated file in the archive folder. The file is also kept as an attachment of the job record on the **Electronic reporting jobs** page (**Organization administration** \> **Electronic reporting** \> **Electronic reporting jobs**). To see the files of a job, select **Show files**. You can also keep the results in the job archive. To set the document type of the job archive, go to **Organization administration** \> **Workspaces** \> **Electronic reporting** \> **Electronic reporting parameters**. To view the archived jobs, go to **Organization administration** \> **Electronic reporting** \> **Electronic reporting archived jobs**.

For ER formats that generate Excel output, you can create an additional file destination that converts the output to PDF, to keep a readable image of the report.

For more information, see [Archive ER destination type](/dynamics365/fin-ops-core/dev-itpro/analytics/er-destination-type-archive) and [Electronic reporting (ER) destinations](/dynamics365/fin-ops-core/dev-itpro/analytics/electronic-reporting-destinations).

> [!NOTE]
> ER destinations are company-specific. Set them up in each legal entity that you archive. By default, destinations apply only when you run a format version that has a status of **Completed** or **Shared**.

## Archive other content

- **Business documents** – Store copies of the customer invoices and other business documents that Finance issues in the *Business documents* folder. For documents that ER formats generate, use Archive destinations as described in the previous section.
- **Electronic invoices** – The Electronic Invoicing service stores the electronic documents that it generates in an Azure storage account that you own. Apply the same access and retention rules to this storage account, or copy the documents to the archive. For more information, see [Configure Azure resources for Electronic invoicing](../global/gs-e-invoicing-set-up-azure-resources.md).
- **Event log** – Export the database log entries of the fiscal year, for example, from the **Database log** page (**System administration** \> **Inquiries** \> **Database** \> **Database log**), and store the file in the *Event log* folder. You can automate this export, for example, by using Power Automate. For the events to record and the settings to use, see [Registration of audit events](emea-france-nf203.md#registration-of-audit-events).
- **Reference data and settings** – Export the reference data and the parameters, as they are at the closing date, to an open format, such as CSV or Excel. You can use [Data management export projects](/dynamics365/fin-ops-core/fin-ops/data-entities/data-import-export-job). Store the files in the *Reference data and settings* folder.
- **Automation** – You can use Power Automate flows to collect files in the archive, for example, to move the files of a fiscal year to a dedicated folder. A flow can start manually, on a schedule, or when an event occurs. The Fin & Ops Apps (Dynamics 365) connector works with data entities in Finance, and it's a premium connector. The SharePoint connector creates, copies, and moves files and folders in the archive. For more information, see:

  - [Triggers in Power Automate cloud flows](/power-automate/triggers-introduction)
  - [Application Connector](/dynamics365/fin-ops-core/dev-itpro/data-entities/fin-ops-connector)
  - [Fin & Ops Apps (Dynamics 365) connector reference](/connectors/dynamicsax/)
  - [SharePoint connector reference](/connectors/sharepointonline/)

## Produce the tax archive at year-end closing

Produce the tax archive as a step of the closing procedure of each fiscal year. To produce the tax archive at year-end closing, follow these steps:

1. Post all transactions of the fiscal year, including the adjustments in the closing period.
1. Set the periods of the fiscal year to **On hold**, and run the final year-end close.
1. Generate the FEC, the VAT declarations, and the other ER output of the fiscal year. Because Archive destinations are set up, Finance stores the files in the archive folders.
1. Export the event log, the reference data, and the settings, and store the files in the archive folders.
1. Check that the archive is complete. For example, check that the totals of the FEC match the trial balance. Update the list of archived files.
1. Apply the retention label to the files of the fiscal year, if the label isn't applied automatically.
1. Set the fiscal year to **Permanently closed**.
1. If you decide, based on your business needs, to clean up, purge, or archive data of the fiscal year in Finance, such as database log entries, do so only after you complete all the previous steps. These activities aren't required for the tax archive.

If you correct a fiscal year after you produced its archive, produce a new archive for the corrected fiscal year, and keep the earlier archive. For more information, see [Correct a closed fiscal year in France](emea-france-closed-fiscal-year-corrections.md).

## Additional resources

- [NF203 Computerized Accounting Certification in France](emea-france-nf203.md)
- [Correct a closed fiscal year in France](emea-france-closed-fiscal-year-corrections.md)
- [Archive ER destination type](/dynamics365/fin-ops-core/dev-itpro/analytics/er-destination-type-archive)
- [Configure document management](/dynamics365/fin-ops-core/dev-itpro/organization-administration/configure-document-Management)
- [Configure database logging](/dynamics365/fin-ops-core/dev-itpro/sysadmin/configure-manage-database-log)
