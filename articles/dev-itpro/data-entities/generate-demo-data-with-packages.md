---
# required metadata

title: Generate demo data by using data packages
description: This topic describes how to use demo data packages to generate data for your system. 
author: mikefalkner
manager: AnnBe
ms.date: 10/29/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: margoc
ms.search.scope: Operations, Platform, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 77523
ms.search.region: Global
# ms.search.industry: 
ms.author: mfalkner
ms.search.validFrom: 2017-10-31
ms.dyn365.ops.version: Platform update 11

---
# Generate demo data by using data packages

[!include[banner](../includes/banner.md)]

Demo data has been delivered as a database in prior releases. Starting in the Fall 2017 release, a variation of some of the demo data will also be released in LCS as data packages in the shared asset library. These packages are designed to be loaded onto an empty environment and you can choose which packages that you need to load for your demonstration. 

Using data packages to deliver demo data provides some benefits over using the current database:
1. The download times are signficantly smaller.
2. You can import only the data packages that you need.
3. You can edit the spreadsheets to customize the data for your customers. 
4. Updated demo data can be provided through LCS very quickly.

## How the packages are organized

The demo data packages are designed to be layered on top of each other as shown in this diagram:

![Demo data packages](./media/DemoData.png)

### System and shared
The base package, System and Shared, is the foundation for all other packages. This package creates the legal entities, loads the global address book, and adds additional shared information. It must be loaded first to support all of the remaining packages. The package is entitled "100 - System and Shared.zip"

Once the package is loaded, you will have the following legal entities:

| Legal entity | Description |  
|------|--------|
| HQUS | The US based headquarters for your demo company. This company was based on the original USMF data but changed to remove the manufacturing focus in the name. It includes setup information intended for US companies.|
| HQEU | The non-US based headquarters for your demo company. This company was based on the original DEMF data but changed to remove the manufacturing focus in the name. It includes setup information intended for non-US companies.|
| CONS | A small consolidations company. |
| PICH | A process industries company focused on chemicals. |
| PIFB | A process industries company focused on food and beverage. |

You can expect approximately 30 minutes to load this package. The time required to import this package will vary based on the speed of your instance.   

### Financials
There are several packages that contain the financials data for a company. These data packages are entitled "200 - Financials" followed by the legal entity for which they were intended. For examples, the financial data packages for HQUS are entitled "200 - Financials - HQUS.zip".

At least two financials companies are required for cross company tasks such as centralized payments. All customers and vendors have been added to each legal entity (CHECK THIS). (TEST THIS).

You can expect approximately 15 minutes to load each package. The time required to import this package will vary based on the speed of your instance.

### Supply chain
There are several packages that contain the supply data for a company.

You can expect approximately 30 minutes to load each package. The time required to import this package will vary based on the speed of your instance.


## Loading the packages

The data packages must be loaded in a specific order into a specific legal entity. The number preceding the name of the package provides guidance to the order t
