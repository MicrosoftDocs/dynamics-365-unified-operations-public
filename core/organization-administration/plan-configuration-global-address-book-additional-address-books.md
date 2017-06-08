---
# required metadata

title: Configure global address books
description: This article describes the considerations and decisions that you must make during the planning process, before you set up and configure the global address book and any additional address books in Microsoft Dynamics 365 for Operations. Some of the decisions will require that you confirm the decisions that have been made for other areas of the product, such as the organization hierarchy.
author: kfend
manager: AnnBe
ms.date: 04/04/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

ms.search.form: DirAddressBook, DirAddressBookTeam, DirParameters, DirPartyTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: kfend
ms.search.scope: AX 7.0.0, Operations, Core
# ms.tgt_pltfrm: 
ms.custom: 23341
ms.assetid: a41cd8de-9ee0-4275-aea5-131db5326e5b
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Configure global address books

[!include[banner](../includes/banner.md)]


This article describes the considerations and decisions that you must make during the planning process, before you set up and configure the global address book and any additional address books in Microsoft Dynamics 365 for Operations. Some of the decisions will require that you confirm the decisions that have been made for other areas of the product, such as the organization hierarchy.

Global address book
-------------------

Before you begin to work with the global address book, you must determine the default values for it. These default values are then used for any additional address books that you create. **Decisions:**

-   What sequence should names be displayed in for party records of the **Person** type? For example, one sequence is last name, middle name, first name.
-   Should party records be deleted from the address book when the role record is deleted? For example, if a customer record is deleted, should the party record also be deleted?
-   When a new record is created, should users be notified if a duplicate record is found in the global address book?
-   Should the Data Universal Numbering System (DUNS) number be included in a party record’s information?
-   If the DUNS number is included in a party record, should the uniqueness of the number be checked?
-   When a party record is created in the global address book, do you want a default party type, person, or organization?
-   Which user roles should have access to the private addresses and contact information of party records?

## Additional address books
After you create the global address book, you can create additional address books as you require, such as a separate address book for each company in your organization or for each line of business. For example, Fabrikam is an international organization that has multiple companies and multiple lines of business. Fabrikam plans to create an address book for each line of business. For lines of business that occur in more than one location, such as the pneumatic tools business, Fabrikam plans to create an address book for each location. Chris, the IT manager at Fabrikam, has created the following list of address books that are required. This list also also describes the party records that each address book must include.

-   **Public Sector Contracts (PubSC)** – Party records for all parties that are involved in the public sector contracts that Fabrikam holds.
-   **Private Sector Contracts (PriSC)** – Party records for all parties that are involved in the private sector contracts that Fabrikam holds.
-   **Electronic Tools (ET)** – Party records for all parties that are involved in the purchase or sale of electronic tools, or that otherwise interact with the electronic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
-   **Pneumatic Tools (PTJPN)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
-   **Pneumatic Tools (PTUSA)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-US company.

**Decision:**

-   How many additional address books will you create?

### Address book security

You can create address books at any time, and you can also set security parameters for the address books at any time. You aren't required to set security privileges for an address book, but if you don't, all workers in your organization can view all party records in that address book. You can set security privileges to party records through address books. Security privileges are based on teams. This approach guarantees that only workers who are assigned to a team that has access to an address book can view the party records in that address book. You must select the teams that have access to each address book. For each address book, you can set security privileges that allow or deny access to specific teams. If you grant a team privileges to an address book, all members of that team can view the records in the address book. If you don't grant a team access to an address book, the members of that team can't view the address book or its contents. **Decision:**

-   Which teams should have access to each new address book that you will create?




