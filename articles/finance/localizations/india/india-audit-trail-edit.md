---
title: Audit trail and edit logs for accounting software in India
description: Learn about the new Indian tax requirements of Rule 3 of the Companies (Accounts) Rules.
author: liza-golub
ms.author: egolub
ms.topic: article
ms.date: 04/08/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: India
---

# Audit trail and edit logs for accounting software in India

[!include [banner](../../includes/banner.md)]

This article is intended to help organizations meet the requirements of Rule 3 of Companies (Accounts) Rules, 2014, and the following amendments to it:

- GSR 205 (E) dated March 24, 2021
- GSR 247 (E) dated April 1, 2021
- GSR 235 (E) dated March 31, 2022

The rule and its amendments were all issued by the Indian Ministry of Corporate Affairs (MCA).

The MCA requires that accounting software records an audit trail of financial transactions. Microsoft Dynamics 365 Finance is designed to help customers meet these requirements. The record change logging that is available in Dynamics 365 Finance exceeds the requirements of the legislation. It allows for additional tracking of changes that are made to records outside the formal "books of accounts."

## The legislation

Principal notification No. GSR 205 (E) dated March 24, 2021, and amended vide notification GSR 247 (E) dated April 1, 2021, states that, as of April 1, 2022, all businesses that use accounting software to maintain books of accounts should have an audit trail feature that includes the following functionality:

- Recording an audit trail of every books of accounts transaction
- Creating an audit log of every change (edit) that is made in the books of accounts
- Capturing the date details when the changes are made
- Ensuring that the audit trail can't be disabled

## Books of accounts

Dynamics 365 Finance defines the books of accounts as the official accounting entries that are created and posted to the general ledger. The accounting entries are stored in the `GeneralJournalEntry` and `GeneralJournalAccountEntry` tables, together with their related references. The transaction records contain date, amount, text, creation date, and created-by fields. An accounting entry can be corrected only by adding new reversing and correcting entries, not by changing the existing records. Dynamics 365 Finance doesn't provide any way for users to alter these records.

Learn how to view transactions in [View journal entries and transactions](../../general-ledger/view-journal-entries-transactions.md).

Although the software is intended to help customers meet the requirements of the legislation, customers are responsible for operating in accordance with the legislation and ensuring that their practices and policies meet the requirements. For example, to meet the in-country requirements in the legislation, customers must ensure that data is maintained in India. Therefore, they must select the India geo when they first provision the environment.

Learn about data residency practices and data retention policies in [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview).

### Preservation of information in electronic records

Transactions that are posted in Dynamics 365 Finance remain complete and in the format that they were originally generated in. The solution includes no functionality or process for changing the format or content of a posted transaction in an active company.

However, note that customers can delete a company or leave the Dynamics 365 Finance service in accordance with the Microsoft terms. These actions ultimately result in data deletion. If customers choose to delete their company completely or leave the Dynamics 365 Finance service, data is removed from Microsoft's systems in accordance with our data deletion obligations to customers.

### Preservation of branch transaction information

Transactions that are received from branch offices remain complete and in the format that they were originally generated in. The solution includes no functionality or process for changing the format or content of a posted transaction in an active company.

If an accounting entry must be corrected, accounting standards specify that the correction should be done through a reversal and correcting entry. Alternatively, new documents can be received from the branch to address the required correction. Examples of these documents include credit notes and tax journals. All reversals and new correcting documents update the audit log as new entries. The original entries remain unchanged.

### Display of electronic records in legible format

The information in the electronic record of a document is shown in Dynamics 365 Finance. The Electronic reporting (ER) format configurations feature in Dynamics 365 Finance allows for at least one output component per file. Typically, configurations contain multiple file output components of different types (for example, XML, TXT, XLSX, DOCX, and PDF). These components are grouped into one or more folders. ER destination management lets you preconfigure what occurs when each component is run. By default, a dialog appears when a configuration is run. You can use the dialog to save or open the file. The file is opened in the defined output components.

### Maintenance of a proper storage system for electronic records

There is a proper system for storing, retrieving, displaying, and printing electronic records. Electronic records aren't disposed of or become inaccessible, except as permitted by law or unless the customer leaves Dynamics 365 Finance.

Customers use Microsoft Dynamics 365 Lifecycle Services to select the geography that Dynamics 365 Finance is deployed to. Dynamics 365 Finance is generally available in datacenters in various geographical locations around the world. Although Microsoft might replicate data to other regions within the selected geographical location to ensure data durability, customer data is never replicated or moved outside that geographical location.

If a region-wide outage occurs, Microsoft provides business continuity and disaster recovery for production instances of Dynamics 365 software as a service (SaaS) applications. Learn more in [Business continuity and disaster recovery for Dynamics 365 SaaS apps](/power-platform/admin/business-continuity-disaster-recovery).

### Continuous accessibility of books of accounts in India

#### Requirements

In March 2021, the MCA introduced amendments to Rule 3 of Companies (Accounts) Rules. These amendments concern the maintenance of books of accounts in electronic form. The key modifications are as follows.

**I. Accessibility requirement:** Amended Rule 3 (1) emphasizes that books of accounts and other relevant documents that are maintained in electronic mode must remain accessible in India at all times for later reference.

**II. Daily backup requirement:** Amended Rule 3 (5) requires that companies maintain a daily backup of their electronic books of accounts and other relevant documents on servers that are physically located in India, even if backups are also maintained outside the country.

**III. Annual intimation requirement:** Rule 3 (6) requires that companies inform the Registrar about details such as the service provider's name, IP address, and location annually, when they file financial statements. If books of accounts are maintained in the cloud, the address that the service provider provided must also be disclosed.

#### Supported scope

##### I. Accessibility requirement

Books of accounts and other relevant documents that are maintained in electronic mode in Dynamics 365 Finance remain accessible in India for later reference. Access to the data and functionality of Dynamics 365 Finance is determined by the role-based security concept. Learn more in [Role-based security](../../../fin-ops-core/dev-itpro/sysadmin/role-based-security.md).

##### II. Daily backup requirement

To use Dynamics 365 Finance, companies must deploy a Dynamics 365 Finance environment through Lifecycle Services. Dynamics 365 Finance environments are deployed in a customer-selected Azure region where customer data is stored. Companies that use Dynamics 365 Finance select where they want to deploy their environments when they create those environments through Lifecycle Services.

Although Microsoft might replicate data to other regions within the selected geographical location to ensure data durability, customer data isn't replicated or moved outside that geographical location. Learn more in [Paired regions](/azure/reliability/regions-paired#azure-paired-regions).

The specific activities that are required to meet the daily backup requirement might vary, depending on whether the geographical location that was selected for deployment of Dynamics 365 Finance environments is inside or outside India.

###### Dynamics 365 Finance environments that are deployed in India

- A full database backup isn't required to create backups of the books of accounts, because the books of accounts are specifically the `GeneralJournalEntry` and `GeneralJournalAccountEntry` tables and related reference data. These tables and data can be exported through multiple mechanisms, including Open Data Protocol (OData), the Data Import/Export Framework (DIXF), and Azure Synapse Link for Dataverse. Customers are responsible for scheduling and performing additional backups of the books of accounts as they desire.
- The Dynamics 365 Finance infrastructure ensures that backups of a company's books of accounts and other records that are maintained electronically in Dynamics 365 Finance are stored on servers that are physically located in India.
- A customer's representative who has an administrator role in Dynamics 365 Finance can determine where the database is deployed by looking at the **Database backup location** field in Lifecycle Services.
- Databases are protected by Microsoft Power Platform's automatic backups of production environments. These backups are kept for up to 28 days. Learn more in [Back up and restore environments](/power-platform/admin/backup-restore-environments). The underlying technology is Azure SQL Database. Learn more in [Automated backups in Azure SQL Database](/azure/azure-sql/database/automated-backups-overview).
- Administrators can view evidence about which environments daily backups are enabled for. They can capture a screenshot to create a log of this evidence.
- Administrators in Lifecycle Services can use the Environment Metadata API to create a daily log of evidence that pertains to the database backup location and the enabled status of daily backup. Learn more in [Fetch environment metadata](../../../fin-ops-core/dev-itpro/lifecycle-services/api/v1/reference-environment-metadata.md). Any software that supports HTTP and RESTful APIs can be used for this task.
- Administrators can restore their environments to a specific point in time in the past by using Lifecycle Services. Learn more in [Database point-in-time restore (PITR)](../../../fin-ops-core/dev-itpro/database/database-point-in-time-restore.md).

###### Changes to software

Like any major enterprise resource planning (ERP) system, Dynamics 365 Finance lets customers extend the functionality of the system through code. Customers that choose to extend the system or change how it behaves are responsible for ensuring that their changes comply with the Indian tax legislation guidelines. Learn more in [Best practices for ALM in Dynamics 365 applications](/dynamics365/guidance/implementation-guide/application-lifecycle-management-product).

Customers are also responsible for demonstrating to auditors that their application lifecycle management (ALM) practices comply with the guidelines and don't allow rogue code to negatively change product behavior. For example, customers should require code reviews on all changes, deploy software updates only from official branches, and require sign-off on the release of product extensions to production.

###### Live site

The [Azure + Dynamics 365 + Online Services (Public & Government) SOC Bridge Letter](https://servicetrust.microsoft.com/DocumentPage/12d47f3e-ad90-4e63-a505-1cfd6c24145a) describes Microsoft policies and practices that are related to the protection of production systems and engagement in live site issues at the request of customers. Any back-end changes to the product or data are made in accordance with the policies and practices that are described in that document. The document is regularly updated.

###### Dynamics 365 Finance environments that are deployed outside India

If a Dynamics 365 Finance environment is deployed outside India, a company can consider using the following options to meet India's daily backup requirement:

- **Option 1:** Geo to geo migration

    Under some conditions, a company that operates in India but deployed its Dynamics 365 Finance environment outside India can consider migrating the Dynamics 365 Finance environment that has an Indian legal entity to a datacenter in India. Learn more in [Geo to geo migration overview](../../../fin-ops-core/dev-itpro/deployment/geo-to-geo-migrations.md). After a Dynamics 365 Finance environment that contains the data that is required to meet the daily backup requirement is migrated to a datacenter in India, the information in the [Dynamics 365 Finance environments that are deployed in India](#dynamics-365-finance-environments-that-are-deployed-in-india) section is applicable.

- **Option 2:** Multi-instance installation

    Under some conditions, a company that operates in India but deployed its Dynamics 365 Finance environment outside India can consider a multi-instance installation. In this type of installation, the Indian legal entities are installed in a Dynamics 365 Finance environment that is located in a datacenter in India. Other legal entities can then be installed in environments in different geographical locations, depending on other countries' legal requirements and the company's needs. Learn more in [Plan your environment strategy for Dynamics 365](/dynamics365/guidance/implementation-guide/environment-strategy-overview). When Dynamics 365 Finance legal entities that have an address in India are installed in a Dynamics 365 Finance environment that is located in a datacenter in India, the information in the [Dynamics 365 Finance environments that are deployed in India](#dynamics-365-finance-environments-that-are-deployed-in-india) section is applicable.

- **Option 3:** Azure Synapse Link for Dataverse with Azure Data Lake Storage

    For Dynamics 365 Finance environments that are deployed outside India, companies can consider using Azure Synapse Link for Dataverse for daily replication of their electronic books of accounts and other relevant documents from Dynamics 365 Finance to a data lake in a datacenter in India. Learn more in [What is Azure Synapse Link for Dataverse?](/power-apps/maker/data-platform/export-to-data-lake)

    The Azure Synapse Link for Dataverse service enables the selection of both standard and custom Dynamics 365 Finance entities and tables. It supports continuous replication of entity and table data, including create, update, and delete (CUD) transactions. Learn more in [Create an Azure Synapse Link for Dataverse with Azure Data Lake](/power-apps/maker/data-platform/azure-synapse-link-data-lake).

    > [!NOTE]
    > We recommend that you use Dynamics 365 Finance tables for data replication to Data Lake Storage.

    1. **Enable Data Lake Storage.** Data Lake Storage is a powerful Microsoft-provided cloud service that lets you store and analyze large volumes of data. Learn more in [Introduction to Azure Data Lake Storage](/azure/storage/blobs/data-lake-storage-introduction). To meet the daily backup requirement, create a storage account in India to use with your Data Lake Storage instance. Learn more in [Create an Azure storage account](/azure/storage/common/storage-account-create?tabs=azure-portal).

        > [!NOTE]
        > As of August 15, 2024, when you select tables in Dynamics 365 Finance for replication to your organization's Azure Synapse Data Lake Storage instance in India, the data from the selected tables is replicated regardless of the association with legal entities in your organization's Dynamics 365 Finance instance. For example, if you set up a legal entity in France or the United States and India, the data in the selected tables for those legal entities is replicated and stored in your Azure Synapse Data Lake Storage instance in India.

    1. **Select data.** In Power Apps, select the desired Azure Synapse Link instance in the list, and open the Azure Synapse workspace. Expand **Databases**, and select your Dataverse container. The exported tables appear under the **Tables** directory in the left pane. Learn more in [Choose finance and operations data in Azure Synapse Link for Dataverse](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data).
    1. **Perform data replication.** Data from Dynamics 365 Finance is continuously replicated to Azure Synapse Data Lake Storage by using Azure Synapse Link. The data is stored in Common Data Model format to ensure semantic consistency across apps and deployments.
    1. **Query and transform data.** After the data is exported, you can use tools such as Apache Spark to query and transform it. Learn more in [Transform Azure Synapse Link for Dataverse data with Apache Spark](/power-apps/maker/data-platform/azure-synapse-link-spark).

> [!IMPORTANT]
> It's outside the purview of Microsoft's support to determine the scope of data sources for books of accounts and other relevant books and papers that are maintained in electronic mode for data replication to meet the daily backup requirement in a specific company by using Dynamics 365 Finance.

##### III. Annual intimation requirement

Companies must inform the Registrar about the following details annually, when they file financial statements:

- The name of the service provider
- The IP address of the service provider
- The location of the service provider (wherever applicable)
- If the books of accounts and other books and papers are maintained in the cloud, the address that is provided by the service provider
- If the service provider is located outside India, the name and address of the person who is in control of the books of account and other books and papers in India
