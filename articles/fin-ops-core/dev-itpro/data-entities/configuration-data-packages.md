---
title: Configuration data packages
description: This article provides an overview of the configuration data packages for the July 2017 release of Microsoft Dynamics 365 Finance.
author: rcarlson
ms.date: 12/20/2017
ms.topic: article
ms.prod: 
ms.technology: 
audience: Developer, IT Pro
ms.reviewer: sericks
ms.search.region: Global
ms.author: rcarlson
ms.search.validFrom: 2017-06-26
ms.dyn365.ops.version: Platform update 8
ms.custom: 
---

# Configuration data packages

[!include [banner](../includes/banner.md)]


[!INCLUDE [PEAP](../../../includes/peap-3.md)]

> [!IMPORTANT]
> This article applies only to the July 2017 release of Microsoft Dynamics 365 Finance. If you are running a later release, refer to the article [Copy configuration data between companies or legal entities overview](copy-configuration.md). 

Configuration data packages are available as process data packages from Microsoft Dynamics Lifecycle Services (LCS). These data packages can help improve the repeatability of implementations and accelerate the configuration.

Data packages contain configuration entity spreadsheets. These entity spreadsheets contain best practice data that you can use to create an initial golden build. The data entities in the data packages are also sequenced appropriately to help guarantee a successful single-click import of the data. 

The entity spreadsheets include three types of data:

- **Business data** – The spreadsheet contains standard business data for a mid-sized trade or retail company. This data combines best practices and business standards that can be used as a starting point for your configuration.
- **Sample data** – The spreadsheet contains data that can be used as an example for business-specific data. This data can be imported and used as an example, but it must be changed for individual business practices.
- **No data** – The spreadsheet doesn't contain any data. Several areas of the product are unique to each business and its business practices. These areas must be configured specifically for the organization. These spreadsheets should be reviewed and updated for the organization as appropriate.

For more information about the type of data that is included in each entity spreadsheet in the data packages see the [Data packages](#data-packages-system) section of this article. You can modify individual spreadsheets before you import the data packages, or you can import the data packages as they have been supplied and then update your data in the system.

## Using configuration data packages
You can access configuration data packages from LCS. You can either apply them to an LCS environment, or download them so that you can manually import them.

1. Open your LCS project, and open the Asset library.
2. In the list of asset types, select **Process data package**.
3. Click **Import**.
4. Select the configuration data package.
5. Click **Pick**.

At this point, you can use the **Consume** function to apply the process data package to an LCS environment. 

You can also download the individual data package files from the **Data package** area. Use the **Data management** workspace to import the data packages from LCS. For more information about how to import and export configurations, see [Copy configuration data between companies or legal entities overview](copy-configuration.md).

## Special considerations
### System setup
The System data package must be imported before any other data package. By default, the System data package creates a new legal entity that is named **ST01**. The data packages for the module areas depend on this legal entity.

### General ledger
A generic chart of accounts is included in the configuration data packages. When this data is used as it's defined in the Main account entity spreadsheet, posting profiles across the system are filled with default posting data. If you change the main accounts that are used for the chart of accounts, you must also update the individual posting profiles and posting accounts for each area.

## Data packages: System

### 010 – System Setup

|                 &nbsp;                  | Spreadsheet content |    &nbsp;       |   &nbsp;    |
|-----------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                  | **Business data**   | **Sample data** | **No data** |
| Address and contact information purpose | X                   |                 |             |
| Address books                           |                     |                 | X           |
| Address format lines                    | X                   |                 |             |
| Address format                          | X                   |                 |             |
| Address parameters                      | X                   |                 |             |
| Calendar                                |                     |                 | X           |
| Cities                                  | X                   |                 |             |
| Counties                                | X                   |                 |             |
| CountryRegions                          | X                   |                 |             |
| Currencies                              | X                   |                 |             |
| Districts                               | X                   |                 |             |
| Exchange rates                          |                     | X               |             |
| Global address book parameters          | X                   |                 |             |
| Global address book                     |                     |                 | X           |
| Legal entities                          |                     | X               |             |
| Name affixes                            | X                   |                 |             |
| Name sequences                          | X                   |                 |             |
| Operating unit                          |                     | X               |             |
| Organization hierarchy purposes         |                     |                 | X           |
| Organization hierarchy type             |                     |                 | X           |
| Organization hierarchy                  |                     |                 | X           |
| Party contacts                          |                     |                 | X           |
| Party postal addresses                  |                     |                 | X           |
| Party relationships                     |                     |                 | X           |
| Postal codes                            | X                   |                 |             |
| Relationship types                      | X                   |                 |             |
| States                                  | X                   |                 |             |
| System parameters                       | X                   |                 |             |
| Team types                              |                     |                 | X           |
| Teams                                   |                     |                 | X           |
| Unit conversions                        | X                   |                 |             |
| Unit translations                       | X                   |                 |             |
| Units                                   | X                   |                 |             |
| User groups                             |                     |                 | X           |
| User information                        |                     |                 | X           |

## Data packages: Financials 

### 020 – GL Shared

|        &nbsp;                          | Spreadsheet content |    &nbsp;       |   &nbsp;    |
|----------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                 | **Business data**   | **Sample data** | **No data** |
| Account structure activation           |                     | X               |             |
| Account structure allowed values       |                     | X               |             |
| Account structures                     |                     | X               |             |
| Advanced rule criteria                 |                     | X               |             |
| Advanced rule structure activation     |                     | X               |             |
| Advanced rule structure allowed values |                     | X               |             |
| Advanced rule structures               |                     | X               |             |
| Advanced rules                         |                     | X               |             |
| Chart of accounts                      | X                   |                 |             |
| Consolidation groups and accounts      |                     | X               |             |
| Dimension attribute activation         |                     | X               |             |
| Financial dimension format             |                     | X               |             |
| Financial dimension sets               |                     | X               |             |
| Financial dimension translations       |                     |                 | X           |
| Financial dimension value translations |                     |                 | X           |
| Financial dimension values             |                     |                 | X           |
| Financial dimensions                   |                     | X               |             |
| Fiscal calendar period                 |                     | X               |             |
| Fiscal calendar                        |                     | X               |             |
| Main account categories                | X                   |                 |             |
| Main account                           | X                   |                 |             |
| Number sequence code                   |                     | X               |             |
| Number sequence group                  |                     |                 | X           |
| Number sequence references             |                     | X               |             |

### 025 – GL

|             &nbsp;                               | Spreadsheet content |       &nbsp;    |    &nbsp;   |
|--------------------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                           | **Business data**   | **Sample data** | **No data** |
| Accounts for automatic transactions              | X                   |                 |             |
| Balance control accounts                         |                     |                 | X           |
| Calendar                                         |                     |                 | X           |
| Date intervals                                   | X                   |                 |             |
| Default descriptions                             |                     | X               |             |
| Dimension parameters                             | X                   |                 |             |
| Document types                                   | X                   |                 |             |
| Financial dimension value legal entity overrides |                     |                 | X           |
| Financial reasons                                | X                   |                 |             |
| Journal descriptions                             | X                   |                 |             |
| Journal names                                    | X                   |                 |             |
| Ledger allocation basis source                   |                     |                 | X           |
| Ledger allocation basis                          |                     |                 | X           |
| Ledger allocation rule destination               |                     |                 | X           |
| Ledger allocation rule source                    |                     |                 | X           |
| Ledger allocation rule                           |                     |                 | X           |
| Ledger fiscal calendar period                    |                     | X               |             |
| Ledger fiscal calendar year                      |                     | X               |             |
| Ledger parameters                                | X                   |                 |             |
| Ledger                                           |                     | X               |             |
| Main account legal entity overrides              |                     |                 | X           |
| Organization email template message              |                     |                 | X           |
| Organization email template                      |                     |                 | X           |
| Subledger journal transfer rule                  | X                   |                 |             |
| Workflow organization parameters                 |                     |                 | X           |
| Working times                                    |                     |                 | X           |

### 100 – Bank

|            &nbsp;                                 | Spreadsheet content |    &nbsp;       |     &nbsp;  |
|---------------------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                            | **Business data**   | **Sample data** | **No data** |
| Bank accounts                                     |                     | X               |             |
| Bank facility groups                              |                     |                 | X           |
| Bank facility types                               |                     |                 | X           |
| Bank groups                                       |                     | X               |             |
| Bank parameters                                   | X                   |                 |             |
| Bank posting profiles                             |                     |                 | X           |
| Bank statement import methods for general journal |                     |                 | X           |
| Bank transaction groups                           | X                   |                 |             |
| Bank transaction type                             | X                   |                 |             |
| Check layout                                      |                     | X               |             |
| Customer charge groups                            |                     |                 | X           |
| Payment purpose codes                             |                     |                 | X           |
| Reconciliation matching rule sets                 |                     |                 | X           |
| Reconciliation matching rules                     |                     |                 | X           |
| Transaction code mapping                          |                     |                 | X           |

### 120 – AP

|             &nbsp;                          | Spreadsheet content |      &nbsp;     |    &nbsp;   |
|---------------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                      | **Business data**   | **Sample data** | **No data** |
| Aging period definitions                    |                     |                 | X           |
| Business segments                           |                     |                 | X           |
| Business subsegments                        |                     |                 | X           |
| Buyer groups                                |                     |                 | X           |
| Cash discount                               |                     |                 | X           |
| Delivery charges groups                     |                     |                 | X           |
| Destination code                            |                     |                 | X           |
| Expedite codes                              |                     |                 | X           |
| Item charge groups                          |                     |                 | X           |
| Line discount vendor groups                 |                     |                 | X           |
| Line of business                            |                     | X               |             |
| Modes of delivery                           |                     |                 | X           |
| Multiline discount vendor groups            |                     |                 | X           |
| Payment calendar rule                       |                     |                 | X           |
| Payment calendar                            |                     |                 | X           |
| Payment day lines                           |                     | X               |             |
| Payment schedule lines                      |                     | X               |             |
| Payment schedule                            |                     | X               |             |
| Price vendor groups                         |                     |                 | X           |
| Procurement charge codes                    |                     |                 | X           |
| Product categories                          |                     |                 | X           |
| Product category hierarchies                |                     |                 | X           |
| Product category hierarchy roles            |                     |                 | X           |
| Product category hierarchy translations     |                     |                 | X           |
| Purchase pools                              |                     |                 | X           |
| Sales tax groups                            |                     |                 | X           |
| Terms of delivery                           |                     |                 | X           |
| Terms of payment                            | X                   |                 |             |
| Total discount vendor groups                |                     |                 | X           |
| Vendor bank accounts                        |                     |                 | X           |
| Vendor charges group                        |                     |                 | X           |
| Vendor exception groups                     |                     |                 | X           |
| Vendor groups                               |                     |                 | X           |
| Vendor invoice form printing configurations |                     |                 | X           |
| Vendor invoice policy rule types            |                     |                 | X           |
| Vendor ledger accounts                      | X                   |                 |             |
| Vendor parameters                           | X                   |                 |             |
| Vendor payment fee                          |                     |                 | X           |
| Vendor payment format                       |                     |                 | X           |
| Vendor payment method specification         |                     |                 | X           |
| Vendor payment method                       |                     | X               |             |
| Vendor posting profile                      | X                   |                 |             |
| Vendor price tolerance groups               |                     |                 | X           |
| Vendor reasons                              | X                   |                 |             |
| Vendor, form parameters                     |                     |                 | X           |
| Vendors                                     |                     |                 | X           |

### 130 – Tax

|        &nbsp;                      | Spreadsheet content |    &nbsp;       |  &nbsp;     |
|------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**             | **Business data**   | **Sample data** | **No data** |
| Sales tax authorities              |                     | X               |             |
| Sales tax code limits              |                     |                 | X           |
| Sales tax code values              |                     | X               |             |
| Sales tax codes                    |                     | X               |             |
| Sales tax exempt code              | X                   |                 |             |
| Sales tax exempt numbers           |                     |                 | X           |
| Sales tax group details            |                     | X               |             |
| Sales tax groups                   |                     | X               |             |
| Sales tax item groups              |                     | X               |             |
| Sales tax ledger posting groups    | X                   |                 |             |
| Sales tax parameters preset entity |                     |                 | X           |
| Sales tax parameters               | X                   |                 |             |
| Sales tax period setup             |                     | X               |             |
| Sales tax reporting codes          |                     |                 | X           |
| Transaction codes                  |                     |                 | X           |
| Withholding tax code values        |                     | X               |             |
| Withholding tax codes              |                     | X               |             |
| Withholding tax group details      |                     |                 | X           |
| Withholding tax groups             |                     | X               |             |
| Withholding tax limits             |                     |                 | X           |

### 140 – AR

|                  &nbsp;                                 | Spreadsheet content |    &nbsp;       |    &nbsp;   |
|---------------------------------------------------------|---------------------|-----------------|-------------|
| **Entity spreadsheet**                                  | **Business data**   | **Sample data** | **No data** |
| Aging period definitions                                | X                   |                 |             |
| Business segments                                       |                     |                 | X           |
| Business subsegments                                    |                     |                 | X           |
| Cash discount                                           |                     |                 | X           |
| Collection letter form printing configurations          |                     |                 | X           |
| Collection letter setup                                 | X                   |                 |             |
| Commission calculation                                  |                     |                 | X           |
| Commission customer group                               |                     |                 | X           |
| Commission item group                                   |                     |                 | X           |
| Commission sales group                                  |                     |                 | X           |
| Customer account statement form printing configurations |                     |                 | X           |
| Customer bank accounts                                  |                     |                 | X           |
| Customer charge groups                                  |                     |                 | X           |
| Customer definitions                                    |                     |                 | X           |
| Customer details                                        |                     |                 | X           |
| Customer facing form printing configurations            |                     |                 | X           |
| Customer groups                                         |                     | X               |             |
| Customer ledger accounts                                | X                   |                 |             |
| Customer parameters                                     | X                   |                 |             |
| Customer payment fee                                    |                     |                 | X           |
| Customer payment method specification                   |                     |                 | X           |
| Customer payment method                                 |                     | X               |             |
| Customer posting profiles                               | X                   |                 |             |
| Customer reasons                                        |                     |                 | X           |
| Customer write-off reason codes                         | X                   |                 |             |
| Customers                                               |                     |                 | X           |
| Delivery charges groups                                 |                     |                 | X           |
| Expedite codes                                          |                     |                 | X           |
| Free text invoice form printing configurations          |                     |                 | X           |
| Interest codes with fees                                |                     |                 | X           |
| Interest codes with ranges                              |                     |                 | X           |
| Interest codes                                          | X                   |                 |             |
| Interest note form printing configurations              |                     |                 | X           |
| Item charge groups                                      |                     |                 | X           |
| Line discount customer groups                           |                     |                 | X           |
| Line of business                                        |                     |                 | X           |
| Modes of delivery                                       |                     |                 | X           |
| Payment calendar                                        |                     |                 | X           |
| Payment day lines                                       |                     |                 | X           |
| Payment schedule lines                                  |                     |                 | X           |
| Payment schedule                                        |                     |                 | X           |
| Price customer groups                                   |                     |                 | X           |
| Printed form notes                                      |                     |                 | X           |
| Sales charge codes                                      |                     |                 | X           |
| Sales districts                                         |                     |                 | X           |
| Sales order pools                                       |                     |                 | X           |
| Statistics group                                        |                     |                 | X           |
| Terms of delivery                                       |                     |                 | X           |
| Terms of payment                                        |                     |                 | X           |
| Total discount customer groups                          |                     |                 | X           |


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
