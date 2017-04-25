---
# required metadata

title: Data entities - Project accounting
description: This article provides a list of the data entities that are available for the Project management and accounting functionality in Microsoft Dynamics 365 for Operations.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96343
ms.assetid: d8a43ba6-f045-4318-85b0-3a6c14c418c7
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - Project accounting

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for the Project management and accounting functionality in Microsoft Dynamics 365 for Operations.

Available data entities
-----------------------

**Note:** The Project accounting and management parameters, Forecast models, Work breakdown structure, and other data entities aren't available in the Microsoft Dynamics 365 for Operations February 2016 release.

**26.1.001 PA - Projects setup**

| Suggested sequence | Entity name               | Area     | Entity type | Dependency | Comments                                                       |
|--------------------|---------------------------|----------|-------------|------------|----------------------------------------------------------------|
| 1                  | Project report sort field | Projects | Setup       | None       | Defined sorting criteria for projects                          |
| 2                  | Quotation template groups | Projects | Setup       | None       | Used to make the categorization of quotation templates easier. |

**26.1.002 PA - Journals setup**
Before you import Project journal approval details, verify that the User groups data entity has been imported.

| Suggested sequence | Entity name                      | Area     | Entity type | Dependency                        | Comments                                                                                                                                                        |
|--------------------|----------------------------------|----------|-------------|-----------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 3                  | Project journal approval         | Journals | Setup       | None                              | Specify the approval stages of a project journal approval procedure.                                                                                            |
| 4                  | Project journal names            | Journals | Setup       | Number sequence, Journal approval | Specifies how journal entries for projects are created. The options that were specified are inherited by the hour, fee, and beginning balance project journals. |
| 5                  | Project journal approval details | Journals | Setup       | Number sequence, User groups      | Additional information about project journal approval                                                                                                           |
| 6                  | Project journal description      | Journals | Setup       | None                              | Contains descriptions for project journals.                                                                                                                     |

**26.1.003 PA - Estimates setup**

| Suggested sequence | Entity name                 | Area      | Entity type | Dependency            | Comments                                                                                                                  |
|--------------------|-----------------------------|-----------|-------------|-----------------------|---------------------------------------------------------------------------------------------------------------------------|
| 7                  | Project cost template       | Estimates | Setup       | None                  | Calculations for revenue recognition for fixed-price projects                                                             |
| 8                  | Project cost template lines | Estimates | Setup       | Project cost template | Define the names of the cost lines, and assign all categories to the three system cost lines: items, hours, and expenses. |

**26.1.004 PA - Forms setup**

| Suggested sequence | Entity name        | Area  | Entity type | Dependency | Comments                                                                                                                                   |
|--------------------|--------------------|-------|-------------|------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| 9                  | Project form setup | Forms | Setup       | None       | Define form note parameters for invoices, project quotations, and packing slips that are issued from Dynamics 365 for Operations projects. |

**26.1.005 PA - Resourcing setup**

If you’re using demo data to import, some records that have Russian-specific information will fail, because Russian-specific features aren’t yet supported in the Dynamics 365 for Operations February 2016 release. You can ignore the error message that you receive. After you import the Project resource roles data entity, click **Project management and accounting** &gt; **Setup** &gt; **Resources** &gt; **Setup roles**. Personalize the page by right-clicking the grid columns for **Resources roles**, and insert the field for **Default resource category** as a column in the grid. If no records are set to **True**, select a record in the grid, and set it to **True**. At least one resource role should be set to **True**. Otherwise, you will receive an error message when you create a new project after you import data entities on Project accounting. The error occurs because the default resource category on the existing data entity isn’t exposed and isn’t part of the import.

| Suggested sequence | Entity name                 | Area       | Entity type | Dependency             | Comments |
|--------------------|-----------------------------|------------|-------------|------------------------|----------|
| 10                 | Project resource role       | Resourcing | Setup       | None                   |          |
| 11                 | Project scheduling resource | Resourcing | Setup       | Employee, Legal entity |          |

**26.1.006 PA - Project periods**

| Suggested sequence | Entity name                | Area       | Entity type | Dependency | Comments                                                                                                      |
|--------------------|----------------------------|------------|-------------|------------|---------------------------------------------------------------------------------------------------------------|
| 12                 | Project periods            | Timesheets | Setup       | None       | Used primarily with project timesheets, but also used when you work with estimates and invoice subscriptions. |
| 13                 | Project periods – employee |            | Setup       | None       | Workers are associated with a period, based on the pay and time reporting schedule that they follow.          |

**26.1.007 PA - Categories, Posting, and Line Property**

| Suggested sequence | Entity name                           | Area                                   | Entity type | Dependency                                                                                       | Comments                                                                                                                                                                                                                                        |
|--------------------|---------------------------------------|----------------------------------------|-------------|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 14                 | Shared category                       | Categories, Posting, and Line property | Setup       | None                                                                                             | Shared categories that can be used across all the legal entities in your organization. For example, if you create a shared expense category for meal expenses, the Meals category name and description will be used by all your legal entities. |
| 15                 | Project line property                 | Categories, Posting, and Line property | Setup       | None                                                                                             | Set up default information about hour, fee, expense, and item transaction lines.                                                                                                                                                                |
| 16                 | Category table                        | Categories, Posting, and Line property | Setup       | None                                                                                             | The types of costs or revenues that are defined for your organization.                                                                                                                                                                          |
| 17                 | Category group                        | Categories, Posting, and Line property | Setup       | Chart of accounts, Project line property                                                         | A grouping of similar cost categories, such as worker hours, materials, and travel expenses.                                                                                                                                                    |
| 18                 | Project category                      | Categories, Posting, and Line property | Setup       | Shared category, Item sales tax group, Project line property, Chart of accounts                  | Define a category that can be used for indirect costs for a project. A category defines how costs are posted to financial accounts.                                                                                                             |
| 19                 | Default offset accounts               | Categories, Posting, and Line property | Setup       | Chart of accounts, Project category                                                              | Set up default offset accounts for expense transactions that are entered on a project.                                                                                                                                                          |
| 20                 | Project groups                        | Categories, Posting, and Line property | Setup       | Project line property, Cost template, Period template/types, Chart of accounts, Project category | Specify the type of accounts that project transactions are posted to.                                                                                                                                                                           |
| 21                 | Line property setup                   | Categories, Posting, and Line property | Setup       | Project line property, Project categories, Project groups, Cost template                         | Set up default line properties at various levels. You can set up the default line property at the project or project group level, at the category or category group level, or in any combination of the two types.                              |
| 22                 | Category group                        | Categories, Posting, and Line property | Setup       | Chart of accounts, Project line property                                                         | Set up category groups for projects.                                                                                                                                                                                                            |
| 23                 | Ledger posting definition for project | Categories, Posting, and Line property | Setup       | Category groups, Chart of accounts, Sales Tax group, project groups                              | Ledger accounts to post each type of project transaction to.                                                                                                                                                                                    |

**26.1.008 PA - Forecasts setup**

| Suggested sequence | Entity name                    | Area      | Entity type | Dependency              | Comments                                                        |
|--------------------|--------------------------------|-----------|-------------|-------------------------|-----------------------------------------------------------------|
| 24                 | Project allocation keys        | Forecasts | Setup       | None                    | The allocation key for a project and used by forecast reduction |
| 25                 | Project allocation key details | Forecasts | Setup       | Project allocation keys | Lines for the project allocation keys                           |

**26.1.009 PA - Retention setup**

Before you proceed with additional data import, you must setup the Project management and accounting parameters manually, because the information is required in order to complete the next steps. As we mentioned earlier, the data entity isn’t yet part of the Dynamics 365 for Operations February 2016 release.

| Suggested sequence | Entity name                              | Area      | Entity type | Dependency                      | Comments                                               |
|--------------------|------------------------------------------|-----------|-------------|---------------------------------|--------------------------------------------------------|
| 26                 | Project customer retention term          | Retention | Setup       | None                            | Set up retention terms for customer invoices.          |
| 27                 | Project customer retention term schedule | Retention | Setup       | Project customer retention term | Specify the percentage of customer invoices to retain. |
| 28                 | Project vendor retention term            | Retention | Setup       | None                            | Set up payment retention terms for vendor invoices.    |
| 29                 | Project vendor retention term schedule   | Retention | Setup       | Project vendor retention term   | Specify the percentage of vendor invoices to retain.   |

**26.1.010 PA - Grants setup**

| Suggested sequence | Entity name            | Area   | Entity type | Dependency                        | Comments                                                         |
|--------------------|------------------------|--------|-------------|-----------------------------------|------------------------------------------------------------------|
| 30                 | Project grant matching | Grants | Setup       | None                              | Types that are created to identify categories of matching funds. |
| 31                 | Project grant type     | Grants | Setup       | Contacts/Workers, Operating units | Used to classify grants according to their source or purpose.    |
| 32                 | Project grantor type   | Grants | Setup       | None                              | An organization that awards a grant.                             |

**26.1.011 PA - Project contracts**

| Suggested sequence | Entity name            | Area              | Entity type | Dependency       | Comments                                                                                 |
|--------------------|------------------------|-------------------|-------------|------------------|------------------------------------------------------------------------------------------|
| 33                 | Project contract       | Project contracts | Setup       | None             | Base data for project contracts.                                                         |
| 34                 | Project funding source | Project contracts | Setup       | Project contract | Information about how parties will share funding responsibilities for the project costs. |
| 35                 | Project funding rules  | Project contracts | Setup       | Project contract | Definition on allocation charges for project contracts that have multiple funders.       |

**26.1.012 PA - Inventory project consumption setup**

| Suggested sequence | Entity name                                 | Area            | Entity type | Dependency | Comments |
|--------------------|---------------------------------------------|-----------------|-------------|------------|----------|
| 36                 | Inventory project consumption journal names | Inventory setup | Setup       | None       | a        |

**26.1.013 PA - Projects master**

Forecasts models aren’t part of the Dynamics 365 for Operations 7.0.0 release. During import, you can unmap the **EXTERNALREVISION mapping** field to import the Projects entity. If you’re using demo data to import, about 80 or more Project record will fail, because some of the inclusive projects dates are wrong.

| Suggested sequence | Entity name | Area     | Entity type | Dependency | Comments                                |
|--------------------|-------------|----------|-------------|------------|-----------------------------------------|
| 37                 | Projects    | Projects | Master      | None       | Base data for projects and subprojects. |

**26.1.014 PA - Validation setup**

**Note:** Some records on the Project validation group lines data entity might fail during import. The following error message will appear in the log after import: "Matching record for the read only data source 'ResourceView' does not exist."

| Suggested sequence | Entity name                        | Area       | Entity type | Dependency                        | Comments                                                   |
|--------------------|------------------------------------|------------|-------------|-----------------------------------|------------------------------------------------------------|
| 38                 | Worker/project validation group    | Validation | Setup       | Projects                          | Groups that combine workers and projects for validation    |
| 39                 | Employee/category validation group | Validation | Setup       | Projects                          | Groups that combine workers and categories for validation  |
| 40                 | Employee validation group lines    | Validation | Setup       | Worker/project validation group   |                                                            |
| 41                 | Project/category validation group  | Validation | Setup       | Projects                          | Groups that combine projects and categories for validation |
| 42                 | Project validation group lines     | Validation | Setup       | Project/category validation group |                                                            |

**26.1.015 PA - Pricing setup**

| Suggested sequence | Entity name                   | Area   | Entity type | Dependency                                                                                         | Comments                                                     |
|--------------------|-------------------------------|--------|-------------|----------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| 43                 | Project – expense cost price  | Prices | Setup       | Project category, Worker, Project ID, Customer account, Project contract ID, Price group           | Set up cost price expenses.                                  |
| 44                 | Project – expense sales price | Prices | Setup       | Project category, Worker, Project ID, Project contract ID, Customer account, Price group, Currency | Set up the sales prices per expense transaction.             |
| 45                 | Project – fee sales price     | Prices | Setup       | Project category, Worker, Project ID, Project contract ID, Customer account, Price group, Currency | Set up the sales prices for fee transactions.                |
| 46                 | Project – hour cost price     | Prices | Setup       | Worker, Customer account, Project contract, Project category, Project ID, Price/discount group     | Set up a cost price per hour transaction.                    |
| 47                 | Project – hour sales price    | Prices | Setup       | Project category, Worker, Project ID, Project contract ID, Customer account, Price group           | Set up hourly sales prices for your organization’s services. |
| 48                 | Project transfer price        | Prices | Setup       | Legal entity, Project category, Project, Worker, Sales currency                                    | Set up transfer prices for project hours and expenses.       |

**26.1.016 PA - Indirect costs setup**

| Suggested sequence | Entity name                                    | Area           | Entity type | Dependency                                                                                                  | Comments                                                                                   |
|--------------------|------------------------------------------------|----------------|-------------|-------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------|
| 49                 | Indirect cost component                        | Indirect costs | Setup       | Project category                                                                                            | Used to calculate and post indirect costs to a project.                                    |
| 50                 | Indirect cost component group assignment rules | Indirect costs | Setup       | Customer account, Project contract ID, Project category, Workers, Project ID, Indirect cost component group | Assign an indirect cost component group to a worker and a project for a specific customer. |

**26.8.001 - Project beginning balance**

| Suggested sequence | Entity name                          | Area     | Entity type  | Dependency | Comments                                                  |
|--------------------|--------------------------------------|----------|--------------|------------|-----------------------------------------------------------|
| 51                 | Journal lines for beginning balances | Journals | Transactions | None       | Beginning balances transactions for both header and lines |

**26.8.002 - Project hour and fee journal transactions**

| Suggested sequence | Entity name             | Area     | Entity type  | Dependency   | Comments                                       |
|--------------------|-------------------------|----------|--------------|--------------|------------------------------------------------|
| 52                 | Hour journal            | Journals | Transactions | None         | Transaction header for project hours and fees. |
| 53                 | Journal lines for hours | Journals | Transactions | Hour journal | Transaction lines for project hours and fees.  |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



