---
# required metadata

title: Configuration data packages
description: This topic provides an overview of the configuration data packages available on LCS.
author: saraschi
manager: 
ms.date: 06/26/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 
ms.search.scope: Operations, Platform
# ms.tgt_pltfrm: 
ms.custom: 
ms.search.region: Global
# ms.search.industry: 
ms.author: saraschi
ms.search.validFrom: 2017-06-26
ms.dyn365.ops.version: Platform update 8
---

# Configuration data packages

## Overview

Configuration data packages are available as process data packages from LCS to
help you improve implementation repeatability and accelerate configuration of
Dynamics 365 for Finance and Operations. The data packages are comprised of
configuration entity spreadsheets populated with best practice data to create an
initial golden build. The data entities are also sequenced appropriately within
the data packages for a successful single-click import of the data. There are
three different types of data included in the entity spreadsheets.

-   Business data: The spreadsheet contains standard business data for a
    mid-sized trade or retail company. This data combines best practices and
    business standards to be used as a starting point for your configuration.

-   Sample data: The spreadsheet contains data to be used as an example for
    business-specific data. This data can be imported and used as an example but
    will need to be changed for individual business practices.

-   No data: The spreadsheet does not contain any data. There are several areas
    of the product that are unique to each business and their business
    practices, and must be configured specifically for the organization. These
    spreadsheets should be reviewed and updated for the organization as
    appropriate.

See the Data packages sections for the type of data included in each entity
spreadsheet in the data packages. You can either modify individual spreadsheets
before importing the data packages, or import the data packages as they have
been supplied and update data in the system.

## Usage of configuration data packages

Configuration data packages can be accessed from LCS, and either applied to an
LCS environment or downloaded to be manually imported into Dynamics 365 for
Finance and Operations.

1.  Navigate to the Asset library within your LCS project

2.  In the Asset type list, select Process data packages

3.  Click Import

4.  Select the Configuration data package

5.  Click Pick

At this point you have the option to use the Consume function to apply the
process data package to an LCS environment.

You can also download the individual data package files from the Data packages
area. Use the Data management workspace within Dynamics 365 for Finance and
Operations to import the data packages from LCS. Reference the Copy
configuration data from one company to another wiki for additional information
on importing and exporting configurations.

## Special considerations

System setup: The System data package is required to be imported before any
other data packages. By default, the system data package will create a new legal
entity, ST01, and the module area data packages are dependent upon this legal
entity.

General ledger: A generic chart of accounts is included in the configuration
data package. When this data is used as defined in the Main account entity
spreadsheet, posting profiles across the system will also populate with default
posting data. If you change the main accounts used for the chart of accounts,
then you will also need to update the individual posting profiles and posting
accounts for each area.

## Data packages: System

### 010 – System Setup

|                                         | **Spreadsheet content:** |                 |             |
|-----------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                  | **Business data**        | **Sample data** | **No data** |
| Address and contact information purpose | X                        |                 |             |
| Address books                           |                          |                 | X           |
| Address format lines                    | X                        |                 |             |
| Address format                          | X                        |                 |             |
| Address parameters                      | X                        |                 |             |
| Calendar                                |                          |                 | X           |
| Cities                                  | X                        |                 |             |
| Counties                                | X                        |                 |             |
| CountryRegions                          | X                        |                 |             |
| Currencies                              | X                        |                 |             |
| Districts                               | X                        |                 |             |
| Exchange rates                          |                          | X               |             |
| Global address book parameters          | X                        |                 |             |
| Global address book                     |                          |                 | X           |
| Legal entities                          |                          | X               |             |
| Name affixes                            | X                        |                 |             |
| Name sequences                          | X                        |                 |             |
| Operating unit                          |                          | X               |             |
| Organization hierarchy purposes         |                          |                 | X           |
| Organization hierarchy type             |                          |                 | X           |
| Organization hierarchy                  |                          |                 | X           |
| Party contacts                          |                          |                 | X           |
| Party postal addresses                  |                          |                 | X           |
| Party relationships                     |                          |                 | X           |
| Postal codes                            | X                        |                 |             |
| Relationship types                      | X                        |                 |             |
| States                                  | X                        |                 |             |
| System parameters                       | X                        |                 |             |
| Team types                              |                          |                 | X           |
| Teams                                   |                          |                 | X           |
| Unit conversions                        | X                        |                 |             |
| Unit translations                       | X                        |                 |             |
| Units                                   | X                        |                 |             |
| User groups                             |                          |                 | X           |
| User information                        |                          |                 | X           |

## Data packages: Financials 

### 020 – GL Shared

|                                        | **Spreadsheet content:** |                 |             |
|----------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                 | **Business data**        | **Sample data** | **No data** |
| Account structure activation           |                          | X               |             |
| Account structure allowed values       |                          | X               |             |
| Account structures                     |                          | X               |             |
| Advanced rule criteria                 |                          | X               |             |
| Advanced rule structure activation     |                          | X               |             |
| Advanced rule structure allowed values |                          | X               |             |
| Advanced rule structures               |                          | X               |             |
| Advanced rules                         |                          | X               |             |
| Chart of accounts                      | X                        |                 |             |
| Consolidation groups and accounts      |                          | X               |             |
| Dimension attribute activation         |                          | X               |             |
| Financial dimension format             |                          | X               |             |
| Financial dimension sets               |                          | X               |             |
| Financial dimension translations       |                          |                 | X           |
| Financial dimension value translations |                          |                 | X           |
| Financial dimension values             |                          |                 | X           |
| Financial dimensions                   |                          | X               |             |
| Fiscal calendar period                 |                          | X               |             |
| Fiscal calendar                        |                          | X               |             |
| Main account categories                | X                        |                 |             |
| Main account                           | X                        |                 |             |
| Number sequence code                   |                          | X               |             |
| Number sequence group                  |                          |                 | X           |
| Number sequence references             |                          | X               |             |

### 025 – GL

|                                                  | **Spreadsheet content:** |                 |             |
|--------------------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                           | **Business data**        | **Sample data** | **No data** |
| Accounts for automatic transactions              | X                        |                 |             |
| Balance control accounts                         |                          |                 | X           |
| Calendar                                         |                          |                 | X           |
| Date intervals                                   | X                        |                 |             |
| Default descriptions                             |                          | X               |             |
| Dimension parameters                             | X                        |                 |             |
| Document types                                   | X                        |                 |             |
| Financial dimension value legal entity overrides |                          |                 | X           |
| Financial reasons                                | X                        |                 |             |
| Journal descriptions                             | X                        |                 |             |
| Journal names                                    | X                        |                 |             |
| Ledger allocation basis source                   |                          |                 | X           |
| Ledger allocation basis                          |                          |                 | X           |
| Ledger allocation rule destination               |                          |                 | X           |
| Ledger allocation rule source                    |                          |                 | X           |
| Ledger allocation rule                           |                          |                 | X           |
| Ledger fiscal calendar period                    |                          | X               |             |
| Ledger fiscal calendar year                      |                          | X               |             |
| Ledger parameters                                | X                        |                 |             |
| Ledger                                           |                          | X               |             |
| Main account legal entity overrides              |                          |                 | X           |
| Organization email template message              |                          |                 | X           |
| Organization email template                      |                          |                 | X           |
| Subledger journal transfer rule                  | X                        |                 |             |
| Workflow organization parameters                 |                          |                 | X           |
| Working times                                    |                          |                 | X           |

### 100 – Bank

|                                                   | **Spreadsheet content:** |                 |             |
|---------------------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                            | **Business data**        | **Sample data** | **No data** |
| Bank accounts                                     |                          | X               |             |
| Bank facility groups                              |                          |                 | X           |
| Bank facility types                               |                          |                 | X           |
| Bank groups                                       |                          | X               |             |
| Bank parameters                                   | X                        |                 |             |
| Bank posting profiles                             |                          |                 | X           |
| Bank statement import methods for general journal |                          |                 | X           |
| Bank transaction groups                           | X                        |                 |             |
| Bank transaction type                             | X                        |                 |             |
| Check layout                                      |                          | X               |             |
| Customer charge groups                            |                          |                 | X           |
| Payment purpose codes                             |                          |                 | X           |
| Reconciliation matching rule sets                 |                          |                 | X           |
| Reconciliation matching rules                     |                          |                 | X           |
| Transaction code mapping                          |                          |                 | X           |

### 120 – AP

|                                             | **Spreadsheet content:** |                 |             |
|---------------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                      | **Business data**        | **Sample data** | **No data** |
| Aging period definitions                    |                          |                 | X           |
| Business segments                           |                          |                 | X           |
| Business subsegments                        |                          |                 | X           |
| Buyer groups                                |                          |                 | X           |
| Cash discount                               |                          |                 | X           |
| Delivery charges groups                     |                          |                 | X           |
| Destination code                            |                          |                 | X           |
| Expedite codes                              |                          |                 | X           |
| Item charge groups                          |                          |                 | X           |
| Line discount vendor groups                 |                          |                 | X           |
| Line of business                            |                          | X               |             |
| Modes of delivery                           |                          |                 | X           |
| Multiline discount vendor groups            |                          |                 | X           |
| Payment calendar rule                       |                          |                 | X           |
| Payment calendar                            |                          |                 | X           |
| Payment day lines                           |                          | X               |             |
| Payment schedule lines                      |                          | X               |             |
| Payment schedule                            |                          | X               |             |
| Price vendor groups                         |                          |                 | X           |
| Procurement charge codes                    |                          |                 | X           |
| Product categories                          |                          |                 | X           |
| Product category hierarchies                |                          |                 | X           |
| Product category hierarchy roles            |                          |                 | X           |
| Product category hierarchy translations     |                          |                 | X           |
| Purchase pools                              |                          |                 | X           |
| Sales tax groups                            |                          |                 | X           |
| Terms of delivery                           |                          |                 | X           |
| Terms of payment                            | X                        |                 |             |
| Total discount vendor groups                |                          |                 | X           |
| Vendor bank accounts                        |                          |                 | X           |
| Vendor charges group                        |                          |                 | X           |
| Vendor exception groups                     |                          |                 | X           |
| Vendor groups                               |                          |                 | X           |
| Vendor invoice form printing configurations |                          |                 | X           |
| Vendor invoice policy rule types            |                          |                 | X           |
| Vendor ledger accounts                      | X                        |                 |             |
| Vendor parameters                           | X                        |                 |             |
| Vendor payment fee                          |                          |                 | X           |
| Vendor payment format                       |                          |                 | X           |
| Vendor payment method specification         |                          |                 | X           |
| Vendor payment method                       |                          | X               |             |
| Vendor posting profile                      | X                        |                 |             |
| Vendor price tolerance groups               |                          |                 | X           |
| Vendor reasons                              | X                        |                 |             |
| Vendor, form parameters                     |                          |                 | X           |
| Vendors                                     |                          |                 | X           |

### 130 – Tax

|                                    | **Spreadsheet content:** |                 |             |
|------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**             | **Business data**        | **Sample data** | **No data** |
| Sales tax authorities              |                          | X               |             |
| Sales tax code limits              |                          |                 | X           |
| Sales tax code values              |                          | X               |             |
| Sales tax codes                    |                          | X               |             |
| Sales tax exempt code              | X                        |                 |             |
| Sales tax exempt numbers           |                          |                 | X           |
| Sales tax group details            |                          | X               |             |
| Sales tax groups                   |                          | X               |             |
| Sales tax item groups              |                          | X               |             |
| Sales tax ledger posting groups    | X                        |                 |             |
| Sales tax parameters preset entity |                          |                 | X           |
| Sales tax parameters               | X                        |                 |             |
| Sales tax period setup             |                          | X               |             |
| Sales tax reporting codes          |                          |                 | X           |
| Transaction codes                  |                          |                 | X           |
| Withholding tax code values        |                          | X               |             |
| Withholding tax codes              |                          | X               |             |
| Withholding tax group details      |                          |                 | X           |
| Withholding tax groups             |                          | X               |             |
| Withholding tax limits             |                          |                 | X           |

### 140 – AR

|                                                         | **Spreadsheet content:** |                 |             |
|---------------------------------------------------------|--------------------------|-----------------|-------------|
| **Entity spreadsheet**                                  | **Business data**        | **Sample data** | **No data** |
| Aging period definitions                                | X                        |                 |             |
| Business segments                                       |                          |                 | X           |
| Business subsegments                                    |                          |                 | X           |
| Cash discount                                           |                          |                 | X           |
| Collection letter form printing configurations          |                          |                 | X           |
| Collection letter setup                                 | X                        |                 |             |
| Commission calculation                                  |                          |                 | X           |
| Commission customer group                               |                          |                 | X           |
| Commission item group                                   |                          |                 | X           |
| Commission sales group                                  |                          |                 | X           |
| Customer account statement form printing configurations |                          |                 | X           |
| Customer bank accounts                                  |                          |                 | X           |
| Customer charge groups                                  |                          |                 | X           |
| Customer definitions                                    |                          |                 | X           |
| Customer details                                        |                          |                 | X           |
| Customer facing form printing configurations            |                          |                 | X           |
| Customer groups                                         |                          | X               |             |
| Customer ledger accounts                                | X                        |                 |             |
| Customer parameters                                     | X                        |                 |             |
| Customer payment fee                                    |                          |                 | X           |
| Customer payment method specification                   |                          |                 | X           |
| Customer payment method                                 |                          | X               |             |
| Customer posting profiles                               | X                        |                 |             |
| Customer reasons                                        |                          |                 | X           |
| Customer write-off reason codes                         | X                        |                 |             |
| Customers                                               |                          |                 | X           |
| Delivery charges groups                                 |                          |                 | X           |
| Expedite codes                                          |                          |                 | X           |
| Free text invoice form printing configurations          |                          |                 | X           |
| Interest codes with fees                                |                          |                 | X           |
| Interest codes with ranges                              |                          |                 | X           |
| Interest codes                                          | X                        |                 |             |
| Interest note form printing configurations              |                          |                 | X           |
| Item charge groups                                      |                          |                 | X           |
| Line discount customer groups                           |                          |                 | X           |
| Line of business                                        |                          |                 | X           |
| Modes of delivery                                       |                          |                 | X           |
| Payment calendar                                        |                          |                 | X           |
| Payment day lines                                       |                          |                 | X           |
| Payment schedule lines                                  |                          |                 | X           |
| Payment schedule                                        |                          |                 | X           |
| Price customer groups                                   |                          |                 | X           |
| Printed form notes                                      |                          |                 | X           |
| Sales charge codes                                      |                          |                 | X           |
| Sales districts                                         |                          |                 | X           |
| Sales order pools                                       |                          |                 | X           |
| Statistics group                                        |                          |                 | X           |
| Terms of delivery                                       |                          |                 | X           |
| Terms of payment                                        |                          |                 | X           |
| Total discount customer groups                          |                          |                 | X           |
