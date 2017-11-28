---
# required metadata

title: Deprecated features
description: This topic describes features that have been removed, or that are planned for removal.
author: sericks007
manager: AnnBe
ms.date: 11/28/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User, Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 21821
ms.assetid: 31019808-4cbf-47d7-b1ba-d791db4281ae
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28 
ms.dyn365.ops.version: AX 7.0.0 

---

# Removed or deprecated features

[!include[banner](../includes/banner.md)]

This topic describes features that have been removed, or that are not in active development and may be removed (deprecated) in future releases of Dynamics 365 for Finance and Operations, Enterprise edition.

This list is intended to help you consider these removals and deprecations for your own planning. 

> [!Note]
> Starting with the Dynamics 365 for Finance and Operations, Enterprise edition version 7.2 (July 2017) with platform update 8 release, the type of deployments are noted for each removed or deprecated feature. All of the previous releases mentioned in this topic supported cloud deployments only.

## Features that have been removed or deprecated in Dynamics 365 for Finance and Operations, Enterprise edition 7.3 with platform update 12


### Inventory by item group and Inventory by inventory dimension aging reports

These two reports are no longer supported in Finance and Operations. Instead, the **Inventory aging** report can be used to improve the user experience.

|   |  |
|--------------|-----------------------|
| **Reason for deprecation**       | Duplicate functionality  |
| **Replaced by another feature?** | Yes. The two reports have been replaced by the **Inventory aging** report.     |
| **Product areas affected**       | Inventory management, Cost management        |
| **Deployment option**        | All|
| **Status**                       | Deprecated: The menu items for the two reports have been removed in version 7.3. However, the code for the reports still remains in the product. The plan is to remove the code in a future release. |

### Power BI content packs published to PowerBI.com
The **Cost management**, **Financial performance**, and **Retail channel performance** content packs, which were published to the PowerBI.com site, are deprecated as a consequence of product updates in Microsoft Power BI. System administration forms used to deploy these content packs to PowerBI.com are also being deprecated in Finance and Operations.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Product updates in Microsoft Power BI. |
| **Replaced by another feature?**   | Power BI content packs (published to PowerBI.com) are being replaced by analytical applications which allow for solutions integrations at the database level.  Click here for more details on analytical applications.  |
| **Product areas affected**         | Cost management, Finance, and Retail                                                                                               |
| **Deployment option**              | Cloud only (Integration with PowerBI.com is not supported in on-premises deployments.)                                                                                                            |
| **Status**                         | Deprecated: Target timeframe for the functionality removal is Q2 CY2018.    |

### Standard UI in data management workspace

The standard UI in data management is the legacy UI which is the default UI presented to the users when they visit the data management workspace.

|   |  |
|------------------|-------------------------|
| **Reason for deprecation/removal** | We are investing in providing new user experiences in the new UI.             |
| **Replaced by another feature?**   | The new UI called as the *Enhanced views* is replacing the old UI.            |
| **Product areas affected**         | Data management workspace                                                     |
| **Deployment option**              | All                                                                           |
| **Status**                         | Deprecated: Target timeframe for the functionality to be removed is Q1 2018. |

### (IND) Excise, Sales Tax, Service Tax

These taxes have been subsumed into Indian GST.

|                                             |                                                                         |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | These taxes have been subsumed into Indian GST.                          |
| **Replaced by another feature?**            | Indian GST                                                              |
| **Product areas affected**                  | Tax                                                                     |
| **Deployment option**                       | All modules                                                   |
| **Status**                                  | Deprecated: A removal date has not been set for this feature. |    

### (IND) File Validation Utility (FVU) 

|                                             |                                                                         |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.   |        

### (IND) TDS/TCS certificate 

Users can download this from goverment portal.

|                                             |                                                                         |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Indian withholding tax                                                  |
| **Deployment option**                       | All modules                                                                   |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.     |    

### (IND) EXIM

Lack of customer usage

|                                             |                                                                         |
|---------------------------------------------|-------------------------------------------------------------------------|
| **Reason for removal or deprecation**       | Lack of customer usage                                                  |
| **Replaced by another feature?**            | No                                                                      |
| **Product areas affected**                  | Import and export                                                       |
| **Deployment option**                       | All modules                                                                    |
| **Status**                                  | Deprecated: A removal date has not been set for this feature.  |    



## Features that have been removed or deprecated in Dynamics 365 for Finance and Operations, Enterprise edition (July 2017) with platform update 8

### Warehouse mobile devices portal

Warehouse mobile devices portal (WMDP) was a standalone component that was intended for on-premises self-deployment. This component is no longer supported in Microsoft Dynamics 365 for Finance and Operations, Enterprise edition. A native app that improves the user experience has replaced the functionality of WMDP.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality.       |
| **Replaced by another feature?**   | Yes. This feature has been replaced by Finance and Operations - Warehousing. For more information about setup and prerequisites, see [Install and configure Microsoft Dynamics 365 for Finance and Operations - Warehousing](https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/warehousing/install-configure-warehousing-app). |
| **Product areas affected**         | Warehouse management, Transportation management     |
| **Deployment option**              | Warehouse mobile devices portal (WMDP) was a standalone component that was intended for on-premises self-deployment.               |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### Advanced bank reconciliation matching rule for manual matching

A matching rule was used to select and mark a bank document when documents were manually matched in the reconciliation worksheet.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage.                                                                         |
| **Replaced by another feature?**   | No. Column filtering capabilities should be used to find documents for reconciliation. |
| **Product areas affected**         | Cash and bank management                                                               |
| **Deployment option**              | All                                                                                    |
| **Status**                         | Removed as of July 2017.                                                               |

### Windows 8 tablet app

The Windows 8 tablet app provided functionality for expense entry and approval.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Finance and Operations is compatible with tablets. The tablet app is no longer required.    |
| **Replaced by another feature?**   | No.          |
| **Product areas affected**         | Expense management   |
| **Deployment option**              | [All, Cloud only, or On-premises only]    |
| **Status**                         | [Deprecated – Target timeframe for the functionality to be removed is \<month/year\> or \<quarter/year\> or \<release name\>. -OR- Removed as of \<release name\>.] |

## Features that have been deprecated in Dynamics 365 for Operations 1611 with platform update 3

### AEB payment formats for Spain

The Consejo Superior Bancario payment formats are used to send remittance files to the bank for customer payments and vendor payments. The content of these formats is determined by the Asociación Española de Banca. It covers Cuaderno 19, 32, 58, 34.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                  |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer and Direct debit payment formats for Spain |
| **Product areas affected**         | Accounts payable, Accounts receivable                                    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.           |

### Bank payments transfer for Lithuania

Bank payment transfers are generated and printed by using the Payment transfer (LT) export format for Lithuania. The Lithuanian market began to use LITAS, the unified electronic banking system, in 2005.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Lithuania     |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### BBS Direkte Remittering payment formats for Norway

BBS Direkte Remittering payment formats include customer payment collection export (direct debit) and return message import.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.  |
| **Replaced by another feature?**   | The AvtaleGiro customer payment format for Norway can be used to generate direct debit messages. Return message import will be implemented in future releases. |
| **Product areas affected**         | Accounts payable, Accounts receivable   |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                                                                                                 |

### Chart of Accounts tool for Spain

This tool is used when a chart of accounts in Spain requires major changes. Users can import a new chart of accounts in Microsoft Excel or text format, and can also import financial statements.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Dom80 payment format for Belgium

Legacy Belgian payment format for payment collection (direct debit).

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Belgium         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### DTA/EZAG payment formats for Switzerland

DTA/EZAG formats are integrated into the ESR system, because they can carry on the reference number. Because the reference number isn’t mandatory, these formats can be used to process any vendor payments. These formats are used by companies that have a bank account in a location other than “Postfinance.”

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Switzerland   |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### EDIFACT-DIRDEB payment format for Austria

EDIFACT-DIRDEB payment format for payment collection (direct debit).

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO 20022 Direct debit payment format for Austria         |
| **Product areas affected**         | Accounts receivable                                            |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### EDIVAT for Belgium

EDIVAT is an obsolete Belgian standard for electronic declaration via secure mail. Microsoft Dynamics AX 2012 retains the read-only solution to enable access to the historical data.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The functionality is no longer used.                           |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### eGiro EDIFACT CREMUL payment import format for Norway

eGiro is based on the international UN EDIFACT CREMUL (Multiple Credit Advice Message) standard that is used for automatic posting of customer payments. In Microsoft Dynamics AX, eGiro is implemented as a customer payment import format.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | No. The format will be replaced by ISO 20022 statement import formats in future releases. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### External inventory for Poland

Evidence of goods that are taken from a vendor for sales without purchase. Goods that are handled in external inventory don’t affect standard inventory, and can be sold and then purchased automatically. This process creates real inventory movements.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                    |
| **Replaced by another feature?**   | Yes, the core Inbound consignment functionality                |
| **Product areas affected**         | Accounts payable, Inventory management                         |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Financial reports generator for Eastern Europe

A tool is used to set up data collection for accounting and tax reports, and to export data to XLS and DOC report templates.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                                            |
| **Replaced by another feature?**   | No. The tool will be replaced by Electronic reporting configurations in future releases. |
| **Product areas affected**         | General Ledger                                                                           |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### Import of customer payment transactions for Finland

You can select an import format for Finnish payments to import customer payment transactions from an external file that the bank provides.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | No. The format will be replaced by ISO 20022 statement import formats in future releases. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### Import of payment transactions into a general ledger journal for Finland

A format that is specific to Finland is used to import accounting transactions into the general ledger.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                                                     |
| **Replaced by another feature?**   | No. The format will be replaced by ISO 20022 statement import formats in future releases. |
| **Product areas affected**         | Accounts receivable                                                                       |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                            |

### Integration with Isabel synchronized (CIS) for Belgium

Isabel is the framework for electronic banking in Europe and is a de-facto standard in Belgium.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Integration with Isabel client has been discontinued.   |
| **Replaced by another feature?**   | No. The payment formats that are no longer used are replaced by ISO20022 Credit transfer payment format for Belgium. |
| **Product areas affected**         | Accounts payable     |
| **Status**                         | Deprecated: A removal date has not been set for this feature.    |

### Modifications in the chart of accounts and accounting rules for Spain

This feature is used for changes in the chart of accounts and accounting rules in Spain. It maps accounts to help transform the old chart of accounts into the new chart of accounts, and compares the previous fiscal year with the new fiscal year, even if they were posted to different account numbers.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Limited usage                                                  |
| **Replaced by another feature?**   | No                                                             |
| **Product areas affected**         | General ledger                                                 |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Pagamento Fornittori vendor payment format

Legacy Italian payment format for credit transfers.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment format is no longer used.                          |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Italy         |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Payment export formats for Estonia

The Telehansa and Teleservice formats are used for bank payment export.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Estonia       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Payment file archive for Norway

When payment files are generated, the file archive automatically archives all files that are created, even files that were previously written or read.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                        |
| **Replaced by another feature?**   | Yes, Electronic reporting archived jobs                            |
| **Product areas affected**         | Accounts payable, Accounts receivable, Organization administration |
| **Status**                         | Deprecated: A removal date has not been set for this feature.     |

### Payment import formats for Estonia

The Telehansa and TeleTeenus formats are used for bank payment import.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                                    |
| **Replaced by another feature?**   | No. The formats will be replaced by ISO 20022 statement import formats in future releases. |
| **Product areas affected**         | Accounts receivable                                                                        |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                             |

### Performance management goal workflow

Performance management includes goal management and integration with performance reviews.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance management was redesigned, and the number of goal pages was reduced to simplify the process.                 |
| **Replaced by another feature?**   | No. Goals are visible to managers through the Manager Self Service portal, and can be changed and viewed by the manager. |
| **Product areas affected**         | Human capital management       |
| **Status**                         | Deprecated – Removed as of Dynamics 365 for Operations version 1611    |

### Postgirot and Postgirot Utland payment formats for Sweden

Postgirot and Postgirot Utland payment formats for Sweden.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Sweden        |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Radio frequency identifier

Radio Frequency Identification (RFID) is a data-collection technology that uses electronic tags to store identification data and a no-line-of-sight requirement reader to capture the identification data.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set.   |
| **Replaced by another feature?**   | No                                              |
| **Product areas affected**         | Inventory management                            |
| **Status**                         | Removed as of Dynamics 365 for Operations 1611. |

### Report about state invoices numbering for Latvia

Latvian legislation provides specific rules about the numbering of sales invoices. The functionality lets you assign specific numbers to sales invoices, based on the user or user group. You can then generate a report or an XML file. You can also print a report about invoice numbers that are used.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The state invoice numbering no longer has to be maintained. The report about used invoice numbers is no longer required. |
| **Replaced by another feature?**   | No       |
| **Product areas affected**         | Accounts receivable    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Set up the names of the manager and general accountant of a company for Lithuania

The names of the manager and the general accountant of a company can be specified in the company information and used in different local report printouts.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Replaced by another feature                                     |
| **Replaced by another feature?**   | Yes, the setup of officials can be used for the same purpose.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Telepay payment formats for Norway

Telepay payment formats include vendor payment export (credit transfer) and customer payment collection (direct debit).

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                                                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format and AvtaleGiro customer payment format for Norway |
| **Product areas affected**         | Accounts payable, Accounts receivable                                                          |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                                 |

### Vendor payment export formats for Finland

Two formats for exporting payments are available for Finland. LM02 (FI) is used for domestic payments, and LUM2 (FI) is used for foreign payments.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The payment formats are no longer used.                        |
| **Replaced by another feature?**   | Yes, ISO20022 Credit transfer payment format for Finland       |
| **Product areas affected**         | Accounts payable                                               |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Workflow for creating goals

A workflow for managing the creation of employee goals is one of several workflows that were available to help coordinate the performance management process.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance management has been completely redesigned in Microsoft Dynamics 365 for Finance and Operations.     |
| **Replaced by another feature?**   | The redesigned Performance management feature gives more control over the content of the goals, the measurements that are used to track progress, and the attachment of supporting documentation. Goals can be stored as templates and then reused. This feature can help you set up additional goals for your employees more quickly. |
| **Product areas affected**         | Human capital management                 |
| **Status**                         | Deprecated – Removed as of Dynamics 365 for Operations version 1611 |

## Features that have been deprecated in Dynamics AX 7.0 releases


### Ability to cancel changes to a vendor invoice

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Performance enhancement        |
| **Replaced by another feature?**   | No                             |
| **Product areas affected**         | Accounts payable               |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### AIF, AxD, and AxBC integrations

In Application Integration Framework (AIF), data can be exchanged with external systems through business logic that is exposed as services. Dynamics AX includes services that are based on documents and .NET Business Connector (AxBC). A document is created by using XML. The XML includes header information that is added to create a *message* that can be transferred into or out of Dynamics AX. Examples of documents include sales orders and purchase orders. However, almost any entity, such as a customer, can be represented by a document. Services that are based on documents use the **Axd \<Document\>** classes.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The architecture of AIF and AxDs could not be scaled to a cloud service. There were performance issues around bulk import.                                        |
| **Replaced by another feature?**   | This feature is replaced by the Data Import/Export framework, which supports recurring bulk import/export. For AxBC, we recommend that you use the actual tables. |
| **Product areas affected**         | AxDs, AxBCs, and AIF   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### BOMs without BOM versions

When the **BOM versions** configuration key was disabled, bill of materials (BOM) versions were hidden in all forms, and the system forced a 1:1 relationship between released products and BOMs. In the current version of Dynamics AX, the **BOM versions** configuration key can't be disabled.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Using a configuration key to control BOM versions doesn't scale in a cloud environment. |
| **Replaced by another feature?**   | No                                                                                      |
| **Product areas affected**         | Product information management, Inventory management                                    |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                          |

### Brazilian Bordero

Specific method of payment for Brazilian companies

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Support for the Brazilian Bordero method of payment has been discontinued from Brazilian localization |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Accounts payable   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Brazilian Sintegra statement

Federal tax statement for ICMS tax

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This statement is not longer applicable in some Brazilian states. |
| **Replaced by another feature?**   | No. Users can use Generic Electronic reporting tool to configure the statement if required under specific situations. |
| **Product areas affected**         | Fiscal books    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### Brazilian SCAN contingency mode for NF-e

(SCAN) contingency environment is used to generate, export, and import the status of a Nota Fiscal eletrônica (NF-e) when the environment of Secretaria da Fazenda (SEFAZ) is not available.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This method of contingency is not longer applicable in all Brazilian states |
| **Replaced by another feature?**   | No                                                                          |
| **Product areas affected**         | Accounts receivable                                                         |
| **Status**                         | Deprecated: A removal date has not been set for this feature.              |

### Business Analyzer

This mobile application let users review key business metrics.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature.   |
| **Replaced by another feature?**   | The Monitor financial performance content pack for Microsoft Power BI will include key financial metrics that were previously available in Business Analyzer. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Deprecated: The use of Business Analyzer has been deprecated.    |

### Business statistics

The setup of business statistics inquiries that can help you analyze the performance of the organization

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Legacy approach to business intelligence (BI), low customer usage, and a limited feature set |
| **Replaced by another feature?**   | New BI solutions for the current version of Dynamics AX                                      |
| **Product areas affected**         | Procurement and sourcing, Accounts payable, Sales and marketing, Accounts receivable         |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                               |

### Change document date function in Invoice approval journal

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage                                                               |
| **Replaced by another feature?**   | Yes. The document date on the posted vendor transaction can be changed. |
| **Product areas affected**         | Accounts payable                                                        |
| **Status**                         | Removed as of Dynamics AX 7.0.                                          |

### ClieOp03 payment format for the Netherlands

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in the Netherlands, because it has been replaced by SEPA functionality. |
| **Replaced by another feature?**   | SEPA payments export  |
| **Product areas affected**         | All modules     |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### Compliance Center

The Compliance Center was an Enterprise Portal site for managing the documentation requirements for compliance initiatives that are related to the Sarbanes-Oxley law.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Lack of customer usage. Microsoft SharePoint includes the same capability that was available in the Compliance Center. |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | Compliance and internal controls  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Connector for Microsoft Dynamics

This tool was used to integrate key data from Microsoft Dynamics CRM to Microsoft Dynamics ERP applications.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature. |
| **Replaced by another feature?**   | Common data service                                      |
| **Product areas affected**         | Connector for Microsoft Dynamics                         |
| **Status**                         | Removed as of Dynamics AX 7.0.                           |

### Container unit and multi dimension on-hand

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality |
| **Replaced by another feature?**   | Yes. Since AX 2012, this functionality has been replaced by the consolidated batch orders feature set. This feature set includes the consolidated on-hand view. |
| **Product areas affected**         | Product information management, Production control, Inventory management, Sales and marketing  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Cue group metadata

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Cue groups were used to display one or more Cues in the FactBox area. There was limited uptake, and there were also performance concerns, because a record change in a parent form caused one query per Cue in the Cue group. |
| **Replaced by another feature?**   | No      |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Cue metadata

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Cue metadata was limited to count or sum information.    |
| **Replaced by another feature?**   | Tile metadata was introduced to provide more flexibility for modeling. For example, you can model current counts, navigation, and key performance indicators (KPIs). Count tile metadata is the direct replacement of the Cue metadata. |
| **Product areas affected**         | All modules           |
| **Status**                         | Removed as of Dynamics AX 7.0      |

### Danish check format

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Support for the Danish check format layout has been discontinued, and the report has been removed from DK localization. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | All modules    |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Data partitions

Data partitions provide a logical separation of data in the Microsoft Dynamics AX database.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Data partitions were introduced in Microsoft Dynamics AX 2012 R2 to enable data isolation. In a common scenario, a company has subsidiaries, and the data from one subsidiary should not be visible to another subsidiary, even though both subsidiaries are managed by the same IT department. However, extra scripts and management overhead throughout the program were required in order to create new partitions and populate them with data, and to back up partition data. In the cloud, where we have access to platform as a service (PaaS) database services (Microsoft Azure SQL Database), it's much more efficient to use a database as the isolation container than to do isolation in the program. Regardless of whether data partitioning is required for subsidiaries, for multiple tenants, or just for scale, we believe that the scenarios can be handled better through multiple instances of Finance and Operations. |
| **Replaced by another feature?**   | Customers using data partitions must use multiple instances of Finance and Operations if database level separation is a critical issue.    |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.  |


### Database and file share storage for attachments

Microsoft Dynamics AX 2012 allowed storage of attachments in the database and in file shares. Both of those options are no longer supported.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Files share storage is no longer supported because cloud-hosted environments cannot communicate with local file shares. Database storage has been deprecated in favor of Azure Blob storage. Azure Blob storage is equivalent to storage in the database, as documents can only be accessed through Dynamics 365 for Finance and Operations client forms. This provides the added benefit of providing storage that doesn't negatively affect the performance of the database. Blob storage is the default storage mechanism for Document Management and works immediately. |
| **Replaced by another feature?**   | Database storage has been deprecated in favor of Azure Blob storage.   |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Delimitation

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Time and attendance                    |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Desktop client

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The Dynamics AX client experience has been redesigned to improve usability across multiple platforms and devices.                      |
| **Replaced by another feature?**   | The new web client is based on the desktop Form metadata and programming model that have been modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Direct database connection

In Dynamics AX 2012 R3, Retail Modern POS could connect directly to the Channel DB in similar fashion to Enterprise POS. This was in addition to the standard communication method of Retail Modern POS communicating through Retail Server.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Direct database connectivity required lower security protocols and was primarily used to achieve the highest levels of performance. Due to the performance and security enhancements that have occurred in Finance and Operations, this functionality now causes more issues than it solves. |
| **Replaced by another feature?**   | No. Only standard Retail Server communication is now supported.  |
| **Product areas affected**         | Channel DB/Retail Modern POS   |
| **Status**                         | Removed as of Dynamics AX 7.0.  |

### Dutch SWIFT MT940

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Generic functionality is now used instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### eBilanz (XBRL for Germany)

This functionality provided eXtensible Business Reporting Language (XBRL) output that is intended specifically for the German eBilanz taxonomy.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Lack of customer usage  |
| **Replaced by another feature?**   | This feature hasn't been replaced by another feature, but multiple specialized XBRL packages that provide rich XBRL functionality are available for the German market. |
| **Product areas affected**         | Management Reporter      |
| **Status**                         | Deprecated: A removal date has not been set for this feature.  |

### Enterprise Portal client

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | A single client platform has been provided.  |
| **Replaced by another feature?**   | The new web client is based on the desktop form metadata and programming model that have been modified to provide a rich web platform. |
| **Product areas affected**         | All modules  |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### Environmental sustainability

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set  |
| **Replaced by another feature?**   | No              |
| **Product areas affected**         | Compliance and internal controls, Accounts payable  |
| **Status**                         | [Deprecated – Target timeframe for the functionality to be removed is \<month/year\> or \<quarter/year\> or \<release name\>. -OR- Removed as of \<release name\>.] |

### Form ActiveX and Managed Host controls

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The ActiveX and Managed Host controls are based on the deprecated desktop client. |
| **Replaced by another feature?**   | The extensible control framework supports building new controls that are based on HTML, CSS, and JavaScript, and is a first-class control in the Microsoft Visual Studio Tooling environment. |
| **Product areas affected**         | All modules     |
| **Status**                         | Removed as of Dynamics AX 7.0.       |

### Generate prenotes by using a batch

Prenote generation can't be done by using a batch, but it can still be done by a user.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | No form exists to persist and display the resulting prenote file when it's generated by using a batch. |
| **Replaced by another feature?**   | Prenotes can still be generated, and the user has control over the location where the file is saved.   |
| **Product areas affected**         | Accounts payable, Accounts receivable, Cash and bank management  |
| **Status**                         | Removed as of AX 7.0.    |

### German DTAUS payment export and account statement import (totals and transactions)

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in Germany, because it has been replaced by Single Euro Payments Area (SEPA) functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by SEPA payment export and advanced bank reconciliation functionality for importing account statements. |
| **Product areas affected**         | All modules  |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### German DTAZV payment format

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The format is no longer applicable in Germany, because it has been replaced by SEPA functionality. |
| **Replaced by another feature?**   | SEPA payments export    |
| **Product areas affected**         | All modules   |
| **Status**                         | Deprecated: A removal date has not been set for this feature.    |

### German MT940 import

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Generic functionality is now used instead of localized functionality.                    |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by Advanced bank reconciliation functionality. |
| **Product areas affected**         | All modules                                                                              |
| **Status**                         | Deprecated: A removal date has not been set for this feature.                           |

### German XML EU Sales list

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The XML format for German EU Sales List reporting is no longer supported. Only the ELMA5 text file format can be used to submit the EU Sales List report to the German Tax Office. |
| **Replaced by another feature?**   | No         |
| **Product areas affected**         | Tax        |
| **Status**                         | Deprecated: A removal date has not been set for this feature.   |

### GL SSRS reports

Reports that include the following menu items have been removed: **Summary trial balance**, **Detailed trial balance**, **Chart of accounts**, **Audit trail**, **Balances**, and **Balance list**.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Financial Microsoft SQL Server Reporting Services (SSRS) reports have been replaced by Management Reporter capabilities and default reports. |
| **Replaced by another feature?**   | Management Reporter (labeled **Financial reporting** in the current version of Dynamics AX)    |
| **Product areas affected**         | General ledger   |
| **Status**                         | Removed as of Dynamics AX 7.0.   |

### InfoPart and FormPart metadata

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | InfoPart and FormPart metadata enabled the creation of FactBoxes for two different clients. |
| **Replaced by another feature?**   | InfoPart metadata, which was a simplified form definition, is converted into a Form by upgrade tooling. FormPart metadata, which referenced a Form, is replaced by a more direct reference that is created by upgrade tooling. |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0.        |

### Main account list page

A list of accounts for the legal entity and related balance information

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Balance information is available on the **Trial balance** list page by account and dimension.  |
| **Replaced by another feature?**   | **Main accounts** contains the same list of accounts that the **Main account** list page contained. The grid view in **Main accounts** also shows an even smaller, grid-like view. |
| **Product areas affected**         | General ledger      |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Malaysia and Singapore bank cash flow report

This feature let the user print a cash flow report that shows transactions and details of the cash inflows and outflows for a specific date range for selected bank accounts.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The same information can be obtained from the Inquiry bank transaction. |
| **Replaced by another feature?**   | The Inquiry bank transaction                                            |
| **Product areas affected**         | Cash and bank management                                                |
| **Status**                         | Deprecated: A removal date has not been set for this feature.          |

### Mexican CFD electronic invoice

This feature enabled the generation of Mexican electronic invoices by using the Comprobante Fiscal Digital (CFD) method, where the company signs the invoice by requesting the related authorization from the government. This feature also provides a monthly report that includes all electronics invoices that were issued in the period.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The method is no longer applicable. The generation of electronic invoices by using the CFD method was deprecated by the tax authorities and replaced by the Comprobante Fiscal Digital a través de Internet (CFDI) method, where the signing is delegated to the third-party provider (PAC). The monthly report has been removed, and an inquiry option lets users inquire about historical transactions. |
| **Replaced by another feature?**   | No    |
| **Product areas affected**         | Account receivables, Project   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Mexico realized and unrealized VAT

Microsoft Dynamics AX 2012 managed unrealized value-added tax (VAT) by using Mexico-specific functionality for “unrealized tax.”

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality  |
| **Replaced by another feature?**   | Yes, this functionality has been replaced by standard conditional sales tax functionality that is provided by Core. |
| **Product areas affected**         | Tax   |
| **Status**                         | Deprecated: A removal date has not been set for this feature. |

### Microsoft Outlook integration


|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by Microsoft Exchange Server integration. |
| **Replaced by another feature?**   | Yes                                                                            |
| **Product areas affected**         | Sales and marketing                                                            |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                 |

### Payroll information in Human Resources

Human Resources Payroll information

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by core Payroll and Human Resources pages.  |
| **Replaced by another feature?**   | **Benefits**, **Earnings**, and other related pages that were previously in US Payroll have been reconfigured, and are now part of the core Human Resources configuration to help support external payroll processing. This functionality is accessed by using the **Human Resources 1** \> **Payroll**configuration key. |
| **Product areas affected**         | Human Resources, Payroll   |
| **Status**                         | Deprecated – Removed as of Dynamics 365 for Operations version 1611    |

### Private blocking of inventory and warehouse management journals

The inventory and warehouse journals no longer support the ability to mark a journal as private for a selected user. Only the process of blocking journals as private for user groups and blocking during editing is supported.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | No use of the functionality was found. |
| **Replaced by another feature?**   | No                                     |
| **Product areas affected**         | Inventory management                   |
| **Status**                         | Removed as of Dynamics AX 7.0.         |

### Product builder

Product builder was used to dynamically configure items from a sales order, purchase order, production order, sales quotation, project quotation, or item requirement. Based on a product model that had modeling variables, the user could select values to meet the customer requirements and get a unique product variant that had a BOM and route.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Product builder exposed X++ code to end users and isn't supported in the current version of Dynamics AX. It has been removed to avoid duplicate maintenance efforts on overlapping, sizeable codebases.  |
| **Replaced by another feature?**   | Yes. The constraint-based configuration was introduced in Dynamics AX 2012 where the depreciation of Product builder in future versions was already announced. The constraint-based configuration technology is selected on the product masters to enable the configuration. To learn more, see the Constraint-based configuration technology (https://docs.microsoft.com/en-us/dynamics365/unified-operations/supply-chain/pim/build-product-configuration-model). |
| **Product areas affected**         | Product information management, Sales and marketing  |
| **Status**                         | Removed as of Dynamics AX 7.0.      |

### Rename product dimension

This feature let you change the name of one of the three standard product dimensions (size, color, or style) to a name that better suited your business requirements. Renaming included all the labels where the product dimension name was used.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The current version of Dynamics AX doesn't support label changes at run time. |
| **Replaced by another feature?**   | No                                                                            |
| **Product areas affected**         | Product information management                                                |
| **Status**                         | Removed as of Dynamics AX 7.0.                                                |

### Retail Server connectivity using HTTP

In Dynamics AX 2012 R3, the Retail Server could function using HTTP communication (non-secured). This was in addition to the standard communication using HTTPS.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Due to new security requirements, only secured communication using TLS 1.2 (or above, as available) is now supported. The self-service installer will automatically configure the computer for this communication. |
| **Replaced by another feature?**   | No. Only standard HTTPS communication is now supported. |
| **Product areas affected**         | Retail Server  |
| **Status**                         | Removed as of Dynamics AX 7.0. |

### Role Center pages

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Role Center pages were built on the deprecated Enterprise Portal platform, which has been replaced by the new web client platform in the current version of Dynamics AX. |
| **Replaced by another feature?**   | The new Workspace form pattern provides users with a process-centered design that provides easy access to commonly used tasks within that process.                       |
| **Product areas affected**         | All modules    |
| **Status**                         | Removed as of Dynamics AX 7.0   |

### Sales tax jurisdictions

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low customer usage and a limited feature set |
| **Replaced by another feature?**   | No                                           |
| **Product areas affected**         | US sales tax                                 |
| **Status**                         | Removed as of Dynamics AX 7.0.               |

### Shipping carrier interface

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Duplicate functionality   |
| **Replaced by another feature?**   | Partially replaced by Transportation management |
| **Product areas affected**         | Sales and marketing, Inventory management  |
| **Status**                         | Removed as of Dynamics 365 for Operations version 1611.  |

### Sites Services

Sites Services let you build websites that extend your business processes to the Internet without IT support.

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The Microsoft Azure infrastructure that is used by Dynamics AX has new capabilities that can be used instead (for example, Azure sites). |
| **Replaced by another feature?**   | No   |
| **Product areas affected**         | HR recruiting, Case management, Request for quotes, Vendor registration  |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### SSAS demand forecasting strategy

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The design of the feature cannot be supported in the new cloud architecture. |
| **Replaced by another feature?**   | Azure Machine Learning demand forecasting strategy                           |
| **Product areas affected**         | Master planning                                                              |
| **Status**                         | Removed as of Dynamics AX 7.0.                                               |

### Vendor invoice pool excluding posting details

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage. This functionality has been replaced by the Invoice journal that has workflow functionality. |
| **Replaced by another feature?**   | Workflow capabilities of the Invoice journal.     |
| **Product areas affected**         | Accounts payable |
| **Status**                         | Removed as of Dynamics AX 7.0.    |

### Virtual company accounts

The virtual companies feature is no longer supported in Dynamics AX. The virtual companies feature let users set up tables that could be shared by a set of companies. For a description of the feature, see [Company accounts and Virtual company accounts](https://msdn.microsoft.com/en-us/library/aa834382(v=ax.10).aspx). The feature works by grouping tables into collections that are assigned to virtual companies, which are groups of existing “real” companies. Queries are created so that all the companies in the virtual company can access the data in the tables of the associated table collections.

|   |  | 
|------------|--------------------|
| **Reason for deprecation/removal** | - Virtual companies must be set up before data is stored in the tables. Retrofitting virtual companies onto an existing implementation is very difficult.<br><br>- Because there has been so much data normalization in the current version of Dynamics AX, it has become difficult to know what to add to the table collections. For example, it's difficult to know which tables to share. All the tables referenced from tables that are in a virtual company must also added. Because of table normalization, even simple master data that is spread across multiple tables must be part of the virtual company. Any mistake that is made here will cause functional issues.<br><br>- When a table is part of a virtual company, it loses information about the origin of the data, and only the virtual company is recorded.   |
| **Replaced by another feature?** | Global tables can be used to make tables accessible from all companies. Currently, there is no replacement. |   
| **Product areas affected**       | All modules |   
| **Status**                       | Removed as of Dynamics AX 7.0.   |   

### Warehouse management II

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | The Warehouse management II solution (WMS II) that was available in the **Inventory management** module duplicates functionality that is in the **Warehouse management** module that was released in Microsoft Dynamics AX 2012 R3.                                                                         |
| **Replaced by another feature?**   | The **Warehouse management** module that was released in AX 2012 R3, Microsoft Dynamics AX 2012 R3 CU8, and Dynamics AX 2012 R3 CU9 replaces the Warehouse management II features. The new module has more advanced features and more flexible warehouse management processes than Warehouse management II. |
| **Product areas affected**         | Inventory management, Sales and marketing, Procurement and sourcing   |
| **Status**                         | Removed as of 7.1     |

### Worker reminders in Human Resources

Human Resources Payroll information

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage                                                           |
| **Replaced by another feature?**   | No                                                                  |
| **Product areas affected**         | Human resources                                                     |
| **Status**                         | Deprecated – Removed as of Dynamics 365 for Operations version 1611 |

### Workplanner

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | Low usage |
| **Replaced by another feature?**   | No, but the **Profile relation** page, which is opened from the **Profile groups** page, supports the same business scenario as the deprecated **Workplanner** page. |
| **Product areas affected**         | Time and attendance     |
| **Status**                         | The code has not been removed. However, the form, JmgWorkPlanner, was not migrated.    |

### X++ financial statements

|   |  |
|------------|--------------------|
| **Reason for deprecation/removal** | This functionality has been replaced by another feature.                                    |
| **Replaced by another feature?**   | Management Reporter (labeled **Financial reporting** in the current version of Dynamics AX) |
| **Product areas affected**         | General ledger                                                                              |
| **Status**                         | Removed as of Dynamics AX 2012                                                              |
