---
title: Audit trail and edit logs for accounting software in India
description: Learn about the new Indian tax legislation guidelines for accounting software, including overviews on legislation and compliance.
author: liza-golub
ms.author: egolub
ms.topic: conceptual
ms.date: 04/08/2025
ms.custom: 
  - bap-template
ms.reviewer: johnmichalak 
ms.search.region: India
---

# Audit trail and edit logs for accounting software in India

[!include [banner](../../includes/banner.md)]

This topic provides information intended to aid an organization to meet the requirements of the Rule (3) of Companies (Accounts) Rules, 2014 and its amendments G.S.R. 205(E) dated 24.03.2021, G.S.R. 247(E) dated 
01.04.2021, G.S.R. 235(E) dated 31.03.2022, issued by the Indian Ministry of Corporate Affairs (MCA).  

Microsoft Dynamics 365 Finance has been designed to help customers meet the requirements defined by the MCA for accounting software to record an audit trail of financial transactions. Record-change logging is 
available in Dynamics 365 Finance that exceeds the requirements of the legislation and allows additional tracking of changes made to records outside the formal “book of accounts”. 

## The legislation 

Principal notification No. GSR 205 (E) dated March 24, 2021, and amended vide notification G.S.R.247(E) dated April 1, 2021, states that, as of April 1, 2022, all businesses that use accounting software to 
maintain books of accounts should have an audit trail feature that includes the following functionality: 

 - Recording an audit trail of every books of account transactions
 - Creating an audit log of every change that is made in the books of accounts
 - Capturing the date details when those changes (edits) are made
 - Ensuring that the audit trail cannot be disabled. 

## Books of account 

Dynamics 365 Finance defines the books of account as the official accounting entries created and posted to the general ledger. The accounting entries are stored within the GeneralJournalEntry and 
GeneralJournalAccountEntry tables, together with their related references. The transaction records contain the date, amount, text, created date, and created by fields. An accounting entry can only be corrected 
by adding new reversing and correcting entries, not by changing the existing records. There is no capability provided to users in Dynamics 365 Finance to alter these records.  

For information on viewing transactions, see [View journal entries and transactions](/finance/general-ledger/view-journal-entries-transactions.md). 

While the software is intended to help customers meet the requirements of the legislation, it is the responsibility of the customer to operate in accordance with the legislation and ensure its practices and policies meet the requirements. For example, to achieve the in-country requirements in the legislation, the customer must select the India geo when first provisioning the environment to ensure data is maintained within India. For information on data residency practices and data retention policies, see [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview.md). . 

### The information in the electronic records will remain complete and unaltered

Transactions that are posted in Dynamics 365 Finance remain complete and in the format that they were originally generated in. The solution includes no functionality or process for changing the format or content
of a posted transaction within an active company. Note that customers can delete a company or leave the Dynamics 365 Finance service in accordance with the Microsoft terms, which will ultimately result in data
deletion. If the customer chooses to delete their company completely or leave the Dynamics 365 Finance service, data will be removed from Microsoft’s systems in accordance with our data deletion obligations to 
customers. 

### Preservation of branch transactions information 

Transactions received from branch offices remain complete and in the format that they were originally generated in. The solution includes no functionality or process for changing the format or content of a posted
transaction within an active company. 

If a correction is necessary to an accounting entry, by accounting standards it should be accomplished through a reversal and correcting entry or through new documents being received from the branch, such as a
credit note or tax journal to address the needed correction. All reversals and new correcting documents update the audit log as new entries, while the original entries remain unchanged. 

### Display of electronic record in legible format 

The information in the electronic record of the document is shown in Dynamics 365 Finance. The Dynamics 365 Finance Electronic Reporting (ER) format configurations feature enables at least one output component
per file. Typically, configurations contain multiple file output components of different types (for example, XML, TXT, XLSX, DOCX, and PDF). These components are grouped into one or multiple folders. Electronic
reporting (ER) destination management lets you preconfigure what occurs when each component is run. By default, when a configuration is run, a dialog box appears that lets you save or open the file. The file is
opened in the defined output components. 

### Maintain proper system of storage of electronic record 

There is a proper system for storing, retrieving, displaying, and printing the electronic records.  These electronic records are neither disposed of nor are they inaccessible unless permitted by law or the 
customer leaves Dynamics 365 Finance.  

The customer selects which geography Dynamics 365 Finance is deployed to by using Microsoft Dynamics Lifecycle Services (Lifecyle Services). Dynamics 365 Finance is generally available in datacenters in various 
geographical locations around the world. Although Microsoft might replicate data to other regions of the selected geographical location for data durability, customer data won't be replicated or moved outside the
geographical location. Microsoft provides business continuity and disaster recovery for production instances of Dynamics 365 software as a service (SaaS) applications if region-wide outage occurs. For more 
information, see [Business continuity and disaster recovery for Dynamics 365 SaaS apps](power-platform/admin/business-continuity-disaster-recovery.md).  

### Books of account must remain accessible in India 

Requirement 

In March 2021, the Ministry of Corporate Affairs (MCA) in India introduced amendments to Rule 3 of the Companies (Accounts) rules concerning the maintenance of books of accounts in electronic form. The key 
modifications are as follows. 

I. Accessibility requirement: Amended Rule 3 (1) emphasizes that books of accounts and other relevant documents that are maintained in electronic mode must remain accessible in India at all times for later 
reference. 
II. Daily backup requirement: Under amended Rule 3 (5), companies are required to maintain a daily backup of their electronic books of accounts and other relevant documents on servers that are physically located
in India, even if backups are also maintained outside the country. 
III. Annual intimation requirement: Rule 3 (6) requires that companies inform the Registrar about details such as the service provider's name, IP address, and location annually, when they file financial 
statements. If books of accounts are maintained in the cloud, the address that the service provider provided must also be disclosed. 

### Supported scope 

I. Accessibility requirement 
Books of account and other relevant documents that are maintained in electronic mode in Dynamics 365 Finance and accessible in India for later reference. Access to the data and functionality of Dynamics 365 
Finance is determined by the role-based security concept. For more information, see [Role-based security](/fin-ops-core/dev-itpro/sysadmin/role-based-security.md). 

II. Daily backup requirement 
To use Dynamics 365 Finance, companies must deploy a Dynamics 365 Finance environment through Lifecycle Services. Dynamics 365 Finance environments are deployed in a customer-selected Azure region where customer
data is stored. Companies that use Dynamics 365 Finance choose where they want to deploy their environments when they create the environment through Lifecycle Services. Although Microsoft might replicate data to
other regions within the geographical location for data durability, customer data isn't replicated or moved outside the geographical location. For more information, see [Azure paired regions](azure/reliability/regions-paired#azure-paired-regions.md). The specific activities that are required to meet the daily backup requirement may vary, based on the geographical location (whether inside or outside of India) that was chosen for deployment of Dynamics 365 Finance environments. 

### Dynamics 365 Finance environments that are deployed in India 

 - To create backups of the Books of Account, a full database backup is not required since the Books of Account is specifically the GeneralJournalEntry and GeneralJournalAccountEntry tables and related reference
data. These are exportable through various mechanisms including OData, the Data Import Export Framework, Export to the Data Lake, and multiple other mechanisms. It is the customer’s responsibility to schedule
and perform additional backups of the Books of Account if they wish. 
 - Dynamics 365 Finance infrastructure ensures that backups of the company's Books of Account, along with other records maintained electronically within  Dynamics 365 Finance, are stored on servers that are
physically located in India.
 - A customer's representative who has an administrator role in Dynamics 365  Finance can check where the database is deployed by looking at the Database backup location field in Lifecycle Services.
 - Databases are protected by Microsoft Power Platform's automatic backups of production environments. These backups are kept for up to 28 days. For more information, see Back up and restore environments. The
underlying technology is Azure SQL Database. For more information, see [Automated backups in Azure SQL database](/azure/azure-sql/database/automated-backups-overview?view=azuresql).
 - Administrators can view evidence about which environments have daily backups enabled. They can capture a screenshot to create a log of this evidence.
 - Administrators in Lifecycle Services can use the Environment Metadata API to create a daily log of evidence that pertains to the database backup location and the enabled status of daily backup. For more
information, see [Fetch environment metadata](fin-ops-core/dev-itpro/lifecycle-services/api/v1/reference-environment-metadata). Any software that supports HTTP and RESTful APIs can be used for this task. 
 - Administrators can restore their environments to a specific point in time in the past by using Lifecycle Services. For more information, see [Database point-in-time restore](/fin-ops-core/dev-itpro/database/database-point-in-time-restore). 


### Changes to software 
Like any major ERP system, Dynamics 365 Finance allows customers to further extend the functionality of the system through code. If the customer chooses to extend or change how the system behaves, it is the
customer’s responsibility to ensure their changes are compliant with the India tax legislation guidelines. For more information, see [Best practices for healthy application lifecycle management practices](/dynamics365/guidance/implementation-guide/application-lifecycle-management-product.md). It is the customer’s responsibility to demonstrate to auditors that their application
lifecycle management practices comply with the guidelines and do not allow rogue code to negatively change product behavior. Examples include requiring code reviews on all changes, only deploying software 
updates from official branches, and requiring signoff on the release of product extensions to production. 

### Live site  

Microsoft’s policies and practices related to protection of production systems and engagement in live site issues at the request of customers are described in the [Azure + Dynamics 365 + Online Services –
Public & Government SOC 1 Type II Report]( which is regularly updated. Any back-end changes to product or data are made in accordance with the policies and practices described in this report. 

### Dynamics 365 Finance environments that are deployed outside of India 

If a Dynamics 365 Finance environment is deployed outside of India, a company can consider using the following options to fulfill India's daily backup requirement. 

 - Option 1 - Geo to geo migration 
Under some conditions, to fulfill India's daily backup requirement, a company that operates in India and has its Dynamics 365 Finance environment deployed outside of India can consider migrating the Dynamics 365
Finance environment that has an Indian legal entity to a datacenter in India. For more information, see [Geo to geo migration overview](fin-ops-core/dev-itpro/deployment/geo-to-geo-migrations). When a Dynamics 365 Finance environment that contains data necessary to
fulfill the daily backup requirement is migrated to a datacenter in India, the approach that is described in the Dynamics 365 Finance environments that are deployed in India section is applicable. 

 - Option 2 - Multi-instance installation 
Under some conditions, a company that operates in India and has its Dynamics 365 Finance environment deployed outside of India can consider a multi-instance installation, where the Indian legal entities are
installed in a Dynamics 365 Finance environment that is located in a datacenter in India. Other legal entities can be installed in environments in different geolocations, depending on other countries' legal
requirements and the company's needs. For more information, see Plan your environment strategy for Dynamics 365. When Dynamics 365 Finance legal entities that have an address in India are installed in a Dynamics
365 Finance environment that is located in a datacenter in India, the approach that is described in the Dynamics 365 Finance environments that are deployed in India section is applicable. 

 - Option 3 - Azure Synapse link for Dataverse with Azure Data Lake Storage 
For Dynamics 365 Finance environments that are deployed outside of India, companies can consider using Azure Synapse Link for Dataverse for daily replication of their electronic books of accounts and other
relevant documents from their Dynamics 365 Finance to a data lake in a datacenter in India. For more information, see [What is Azure Synapse Link for Dataverse?](/power-apps/maker/data-platform/export-to-data-lake).

This service enables the selection of both standard and custom Dynamics 365 Finance entities and tables. It supports continuous replication of entity and table data, including create, update, and delete (CUD) 
transactions. For more information, see [Create an Azure Synapse Link for Dataverse with Azure Data Lake](power-apps/maker/data-platform/azure-synapse-link-data-lake). 

>[!Note]
> We recommend that you use Dynamics 365 Finance tables for data replication to Data Lake Storage. 

1. Enable Data Lake Storage - Data Lake Storage is a powerful Microsoft-provided cloud service that lets you store and analyze large volumes of data. For more information, see [Introduction to Azure Data Lake
Storage Gen2](azure/storage/blobs/data-lake-storage-introduction). To fulfill the daily backup requirement, create a storage account in India to use with your Azure Data Lake Storage instance. For more information, see [Create an Azure storage account](azure/storage/common/storage-account-create?tabs=azure-portal). 

>[!Note]
> Beginning August 15, 2024, when you select tables in the Dynamics 365 Finance for replication in your organization's Azure Synapse Data Lake Storage in India, the data from these selected tables will be
> replicated regardless of the association to legal entities in your organization's Dynamics 365 Finance. For example, if you setup a legal entity in France or US and India, the data in the selected tables for
> those legal entities will be replicated and stored in your Azure Synapse Data Lake Storage in India. 

2. Choose data - In Power Apps, select the desired Azure Synapse Link in the list, and go to the Azure Synapse workspace. Expand Databases, and select your Dataverse container. The exported tables appear under
the Tables directory in the left pane. For more information, see [Choose finance and operations data in Azure Synapse Link for Dataverse](/power-apps/maker/data-platform/azure-synapse-link-select-fno-data). 

3. Data replication - Data from Dynamics 365 Finance is continuously replicated to Azure Synapse Data Lake Storage by using Azure Synapse Link. The data is stored in Common Data Model format to ensure semantic
consistency across apps and deployments. 

4. Query and transform - After the data is exported, you can use tools such as Apache Spark to query and transform it. For more information, see [Transform Azure Synapse Link for Dataverse data with Apache Spark](power-apps/maker/data-platform/azure-synapse-link-spark). 

>[!Important]
> Determining the scope of data sources for books of accounts and other relevant books and papers that are maintained in electronic mode for data replication to fulfill the daily backup requirement in a specific
> company by using Dynamics 365 Finance is outside the purview of Microsoft's support. 

### Annual intimation requirement 

Companies must inform the Registrar about the following details annually, when they file financial statements: 
 - The name of the service provider.
 - The IP address of the service provider.
 - The location of the service provider (wherever applicable).
 - If the books of accounts and other books and papers are maintained in the cloud, the address that is provided by the service provider.
 - If the service provider is located outside of India, the name and address of the person who is in control of the books of account and other books and papers in India. 
