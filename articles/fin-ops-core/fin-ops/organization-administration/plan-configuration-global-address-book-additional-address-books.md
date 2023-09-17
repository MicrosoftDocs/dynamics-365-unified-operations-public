---
# required metadata

title: Plan for the global address book and other address books
description: This article describes the considerations and decisions that you must make during the planning process.
author: msftbrking 
ms.date: 01/13/2020
ms.topic: article
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: DirAddressBook, DirAddressBookTeam, DirParameters, DirPartyTable
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.assetid: a41cd8de-9ee0-4275-aea5-131db5326e5b
ms.search.region: Global
# ms.search.industry: 
ms.author: brking
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Plan for the global address book and other address books

[!include [banner](../includes/banner.md)]

This article describes the considerations and decisions that you must make during the planning process, before you set up and configure the global address book and any additional address books. Some of the decisions will require that you confirm the decisions that have been made for other areas of the product, such as the organization hierarchy.

## Global address book

Before you begin to work with the global address book, you must determine the default values for it. These default values are then used for any additional address books that you create.

**Decisions**

- What sequence should names be displayed in for party records of the **Person** type? For example, one sequence is last name, middle name, first name.
- Should party records be deleted from the address book when the role record is deleted? For example, if a customer record is deleted, should the party record also be deleted?
- When a new record is created, should users be notified if a duplicate record is found in the global address book?
- Should the Data Universal Numbering System (DUNS) number be included in a party record's information?
- If the DUNS number is included in a party record, should the uniqueness of the number be checked?
- When a party record is created in the global address book, do you want a default party type, person, or organization?
- Which user roles should have access to the private addresses and contact information of party records?

## Additional address books

After you create the global address book, you can create additional address books as you require, such as a separate address book for each company in your organization or for each line of business. For example, Fabrikam is an international organization that has multiple companies and multiple lines of business. Fabrikam plans to create an address book for each line of business. For lines of business that occur in more than one location, such as the pneumatic tools business, Fabrikam plans to create an address book for each location. Chris, the IT manager at Fabrikam, has created the following list of address books that are required. This list also describes the party records that each address book must include.

- **Public Sector Contracts (PubSC)** – Party records for all parties that are involved in the public sector contracts that Fabrikam holds.
- **Private Sector Contracts (PriSC)** – Party records for all parties that are involved in the private sector contracts that Fabrikam holds.
- **Electronic Tools (ET)** – Party records for all parties that are involved in the purchase or sale of electronic tools, or that otherwise interact with the electronic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
- **Pneumatic Tools (PTJPN)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
- **Pneumatic Tools (PTUSA)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-US company.

**Decision:**

- How many additional address books will you create?


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]