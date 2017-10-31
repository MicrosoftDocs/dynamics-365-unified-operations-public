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

Demo data has been delivered as a database in prior releases. Starting in the Fall 2017 release, a subset of the demo data with changes will also be released in LCS as data packages in the shared asset library. These packages are designed to be loaded onto an empty environment and you can choose which packages that you need to load for your demonstration. 

Using data packages to deliver demo data provides some benefits over using the current database:
1. The download times are signficantly faster.
2. You can import only the data packages that you need.
3. You can edit the spreadsheets to customize the data for your customers. 
4. Updated demo data can be provided through LCS very quickly.

## How the packages are organized

The demo data packages are designed to be layered on top of each other as shown in this diagram:

![Demo data packages](./media/DemoData.png)

### System and shared
The base package, **System and Shared**, is the foundation for all other packages. This package creates the legal entities, loads the global address book, and adds additional shared information. It must be loaded first to support all of the remaining packages. The package is entitled "100 - System and Shared.zip"

Once the package is loaded, you will have the following legal entities:

| Legal entity | Description |  
|------|--------|
| HQUS | The US based headquarters for your demo company. This company was based on the original USMF data but changed to remove the manufacturing focus in the name. It includes setup information intended for US companies.|
| HQEU | The non-US based headquarters for your demo company. This company was based on the original DEMF data but changed to remove the manufacturing focus in the name. It includes setup information intended for non-US companies.|
| CONS | A small consolidations company. |
| PICH | A process industries company focused on chemicals. |
| PIFB | A process industries company focused on food and beverage. |

You can expect approximately 30 minutes to load this package. However, the time required to import this package will vary based on the speed of your instance.   

### Financials
The **Financial** data packages contain data for general ledger, bank, accounts payable, tax, accounts receivable, fixed assets, and budgeting for a single company. These data packages are entitled "200 - Financials" followed by the legal entity for which they were intended. For examples, the financial data packages for HQUS are entitled "200 - Financials - HQUS.zip".

At least two financials companies are required for cross company tasks such as centralized payments. All customers and vendors have been added to each legal entity to facilitate the cross company tasks. (CHECK THIS). (TEST THIS). The CONS company is required if you want to do consolidations. 

The financial data packages also have five inventory products to support the creation of invoices that will move through the accounts receivables and accounts payables processes. These items use a minimum of inventory and product functionality to support those process while eliminating complexity of setting up products when you want to demonstrate only financials functionality. More complete products will be added when you import the supply chain packages.  

You can expect approximately 15 minutes to load each package. However, the time required to import this package will vary based on the speed of your instance.

### Supply chain
There are several packages that contain the supply data for a company.

You can expect approximately 30 minutes to load each package. The time required to import this package will vary based on the speed of your instance.


## Steps to take before loading packages

There are some steps that you will need to do manually before you load the data. 
1) If you want to login as a specific user, you will need to change the user's email address to the login address that you want to use. You can make that change in the User information data entity spreadsheet or, after loading data, in the System administration, Users form.
2) You will need to start the Workflow jobs. Use System administration, Workflow infrastructure configuration and click on Ok. The workflow jobs will be started.
3) The ready to post scheduler must be started. This batch will post transactions automatically. Use Demo Data, ??? to open the form. Select Create scheduler and set up the batch to be recurring.

## Loading the packages

The data packages must be loaded in a specific order into a specific legal entity. The number preceding the name of the package provides guidance to the order that the data must be loaded. For example, to load the the HQUS financials, you must import "100 - System and shared.zip" first, followed by "200 - Financials - HQUS.zip". If you want to add supply chain data to the HQUS company, add "300 - Supply chain - HQUS.zip"

Follow these steps to load the packages:
1) Start with an empty instance where no data is loaded
2) Open the data management workspace
3) Click on the Import tile to create an import job
4) Add a title to the job. For example, "Import shared information"
5) Select "Add file" 
6) Select "Upload and add" and browse to the data package that you want to import. You will need to start with the System and Shared data package.
7) Select the data package and wait for the data to load
8) Once the data is loaded, close the dialogue and click on Import 
9) Repeat the process for additional packages. Be sure to change to the company for which the data package was intended. For example, switch to the HQUS company before importing the data package

### Loading package combinations
We recommend the following combinations:

| Description | ABC |  
|------|--------|

In some cases, there may be different data packages that have the same entities in them. If you load multiple packages in the same data project and those packages have data for the same entity, the data for entities that are loaded last will be the data that is used.

### Steps to take after loading packages




## Transactions and automatic posting


