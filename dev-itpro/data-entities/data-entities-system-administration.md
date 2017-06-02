---
# required metadata

title: Data entities - System administration
description: This article provides a list of the data entities that are available for System administration.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 96433
ms.assetid: 8ee91948-bb1d-409d-80f4-75f32f0a7c5b
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Data entities - System administration

[!include[banner](../includes/banner.md)]


This article provides a list of the data entities that are available for System administration.


**01.1.001 SYS - Currencies**

| Suggested sequence | Entity name    | Area         | Entity type | Dependency | Comments                                                   |
|--------------------|----------------|--------------|-------------|------------|------------------------------------------------------------|
| 1                  | Currencies     | System setup | Setup       | None       | Define the currencies to use in the system.                |
| 2                  | Exchange rates | System setup | Setup       | Currencies, exchange rate types | Define currency exchange rates between any two currencies. Exchange rate types can be defined under General ledger > Currencies > Exchange rate types. |

**01.1.002 SYS – System parameters**

| Suggested sequence | Entity name       | Area         | Entity type | Dependency                      | Comments                                                     |
|--------------------|-------------------|--------------|-------------|---------------------------------|--------------------------------------------------------------|
| 3                  | System parameters | System setup | Setup       | Currencies, exchange rate types | Use to maintain parameters that apply to all legal entities. |

**1.1.003 SYS - Address basic setup for legal entities**

| Suggested sequence | Entity name                             | Area                        | Entity type | Dependency | Comments                                                                                                                                                                                                                                                                                                                                        |
|--------------------|-----------------------------------------|-----------------------------|-------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 4                  | Global address bok parameters           | Organization administration | Setup       | None       | Default values and security policies for address books, and privacy settings for address and contact information records.                                                                                                                                                                                                                       |
| 5                  | Address books                           | Organization administration | Setup       | None       | Stores address book values that are used as a groupign mechanism for different types fo parties. A party is a person or organization that is either internal or external ot your organization. Each party has its own record.                                                                                                                   |
| 6                  | Name affixes                            | Organization administration | Setup       | None       | The name titles and suffixes that are defined in the system.                                                                                                                                                                                                                                                                                    |
| 7                  | Name sequences                          | Organization administration | Setup       | Language   | Create name sequence patterns that can be used when you enter a perosn's party record information.                                                                                                                                                                                                                                              |
| 8                  | Relationship types                      | Organization administration | Setup       | None       | Define relationship types that can be used in the address book.                                                                                                                                                                                                                                                                                 |
| 9                  | Address and contact information purpose | Organization administration | Setup       | Language   | Assign one or more purposes to a postal address record or a contact information record. A purpose describes how a particular address record or contact information record is used. It shows the list of addresses for a customer and the purposes that are assigned to each postal address.                                                     |
| 10                 | Address parameters                      | Organization administration | Setup       | None       | Enables validation when you add address information. For example, if you enter the ZIP/postal code 12345 for a customer address, it is validated that the ZIP/postal code matches information that was previously entered for the country/region, county, and city that are included in the customer’s address. |
| 11                 | Address format                          | Organization administration | Setup       | None       | The setup of address component information and formatting.                                                                                                                                                                                                                                                                                      |

**01.1.004 SYS - Address prerequisites for legal entities**

Some records that are related to languages that aren't supported in the Dynamics 365 for Operations February 2016 release might fail during import. If you're using demo data, Russian addresses will fail during import for the same reason. Successful import will occur after Microsoft enables country/region-specific features.

| Suggested sequence | Entity name     | Area                        | Entity type | Dependency                | Comments                                             |
|--------------------|-----------------|-----------------------------|-------------|---------------------------|------------------------------------------------------|
| 12                 | Country/regions | Organization administration | Setup       | Address format, timezone  | Country/region information.                          |
| 13                 | States          | Organization administration | Setup       | Country/regions, timezone | The state/province information for a country/region. |

**01.1.005 SYS - Address setup**

There are five records that will fail during Cities import because of bad data.

| Suggested sequence | Entity name          | Area                        | Entity type | Dependency                                                     | Comments                                                                                                                                       |
|--------------------|----------------------|-----------------------------|-------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| 14                 | Address format lines | Organization administration | Setup       | Address format                                                 | The definition on the Address application object of the separators that are used, new lines, data entry, active/inactive, expand, and special. |
| 15                 | Counties             | Organization administration | Setup       | Country/regions, states                                        | County information                                                                                                                             |
| 16                 | Cities               | Organization administration | Setup       | Country/regions, states, counties                              | City information                                                                                                                               |
| 17                 | Districts            | Organization administration | Setup       | Country/regions, states, counties, cities                      | District information                                                                                                                           |
| 18                 | Postal codes         | Organization administration | Setup       | Country/regions, states, counties, cities, districts, timezone | ZIP/postal code information                                                                                                                    |


**01.1.006 SYS – Legal entities**

| Suggested sequence | Entity name    | Area         | Entity type | Dependency    | Comments                          |
|--------------------|----------------|--------------|-------------|---------------|-----------------------------------|
| 19                 | Legal entities | System setup | Setup       | Address setup | Use to create a new legal entity. |

**01.1.007 SYS - Operating units**

| Suggested sequence | Entity name    | Area         | Entity type | Dependency | Comments                                                                             |
|--------------------|----------------|--------------|-------------|------------|--------------------------------------------------------------------------------------|
| 20                 | Operating unit | System setup | Setup       | None       | An operating unit is an organization that represents a business process or function. |

**01.1.008 SYS – Organization hierarchies**
If you are building your own organization hierarchy, note that the entity for export is **Organization hierarchy – published** and the entity for import is **Organization hierarchy**.

| Suggested sequence | Entity name                     | Area         | Entity type | Dependency                                                    | Comments                                                                     |
|--------------------|---------------------------------|--------------|-------------|---------------------------------------------------------------|------------------------------------------------------------------------------|
| 21                 | Organization hierarchy type     | System setup | Setup       | None                                                          |                                                                              |
| 22                 | Organization hierarchy purposes | System setup | Setup       | Organization hierarchy types                                  | Determines the types of organizations that can be included in the hierarchy. |
| 23                 | Organization hierarchy          | System setup | Setup       | Organization hierarchy types, Organization hierarchy purposes | Can be used to view and report on your business from various perspectives.   |

**01.1.009 SYS – Units**

| Suggested sequence | Entity name      | Area         | Entity type | Dependency | Comments                                                                             |
|--------------------|------------------|--------------|-------------|------------|--------------------------------------------------------------------------------------|
| 24                 | Units            | System setup | Setup       | None       | Use to create units of measure.                                                      |
| 25                 | Unit conversions | System setup | Setup       | Units      | Use to set up conversion rules that control the conversion between units of measure. |

**01.1.010 SYS – Number sequences**

| Suggested sequence | Entity name                | Area         | Entity type | Dependency            | Comments                                                                                                                                                                                                                                                                                                           |
|--------------------|----------------------------|--------------|-------------|-----------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 26                 | Number sequence codes      | System setup | Setup       | None                  | Use to generate readable , unique identifiers for master data records and transaction records that require them.                                                                                                                                                                                                   |
| 27                 | Number sequence references | System setup | Setup       | Number sequence codes | Use to indicate which number sequences are used for specific tasks. Note: If any subsequent entity import fails because of a number sequence issue, reset the next number sequence number to a lower acceptable value, according to the data in the entity Microsoft Excel file, and then import the entity again. |

**01.1.011 SYS – Organizational calendar**

| Suggested sequence | Entity name   | Area         | Entity type | Dependency | Comments                                                                                                                                                                                                                                                                                                                      |
|--------------------|---------------|--------------|-------------|------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 28                 | Calendar      | System setup | Setup       | None       | The capacity that is available for an operations resource or resource group on specific days and at specific times. You can create an overall calendar for your production, several calendars for resources that operate at different times or shifts, or a separate calendar for each operations resource or resource group. |
| 29                 | Working items | System setup | Setup       | Calendar   | Working time calendars that can be used in Payroll and in Production control.                                                                                                                                                                                                                                                 |

**01.1.012 SYS – System users**

| Suggested sequence | Entity name                            | Area         | Entity type | Dependency        | Comments                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|--------------------|----------------------------------------|--------------|-------------|-------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 30                 | User information                       | System setup | Setup       | None              | Details that are related to the users. Note: Data import can’t contain a record for Guest or axrunner. These users are created at deployment and can’t be updated by the import. If these records are included, the whole entity will fail. If you create your own package with an export from another system, be sure to remove the administrator user from the import file. If you don’t, the information for the administrator user will be imported from the previous installation and may not allow you to log in to the current instance. |
| 31                 | Security user role association         | System setup | Setup       | User information  | The roles that are assigned to the individual user.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| 32                 | System security user role organization | Systems      | Setup       | None              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| 33                 | User group                             | System setup | Setup       | Users information | Groups of users that are used by other modules, such as Budgeting and Project.                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

**01.1.013 SYS – Document types**

| Suggested sequence | Entity name    | Area         | Entity type | Dependency | Comments                                                                                              |
|--------------------|----------------|--------------|-------------|------------|-------------------------------------------------------------------------------------------------------|
| 34                 | Document types | System setup | Setup       | None       | Describe the contents of unattached documents, such as purchase orders, invoices, or expense reports. |

See also
--------

[Data entities and packages framework](data-entities-data-packages.md)

[Data entities](data-entities.md)



