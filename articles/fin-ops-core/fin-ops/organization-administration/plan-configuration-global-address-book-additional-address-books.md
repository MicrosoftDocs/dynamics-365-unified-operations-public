---
title: Plan for the global address book and other address books
description: Learn about the considerations and decisions for the global address book and other address books, including outlines on default values.
author: msftbrking
ms.author: anisagrawal
ms.topic: article
ms.date: 03/10/2026
ms.reviewer: johnmichalak
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DirAddressBook, DirAddressBookTeam, DirParameters, DirPartyTable
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: a41cd8de-9ee0-4275-aea5-131db5326e5b
---

# Plan for the global address book and other address books

[!include [banner](../includes/banner.md)]

This article describes the considerations and decisions that you must make during the planning process before you set up and configure the global address book and any additional address books. Some of the decisions require that you confirm the decisions made for other areas of the product, such as the organization hierarchy.

## Global address book

Before you begin to work with the global address book, determine the default values for it. Use these default values for any additional address books that you create.

**Decisions**

- What sequence should names be displayed in for party records of the **Person** type? For example, one sequence is last name, middle name, first name.
- Should the system delete party records from the address book when the system deletes the role record? For example, if the system deletes a customer record, should the system also delete the party record?
- When a user creates a new record, should the system notify the user if a duplicate record is found in the global address book?
- Should the Data Universal Numbering System (DUNS) number be included in a party record's information?
- If the system includes the DUNS number in a party record, should the system check the uniqueness of the number?
- When a user creates a party record in the global address book, do you want a default party type, person, or organization?
- Which user roles should have access to the private addresses and contact information of party records?

## Additional address books

After you create the global address book, you can create additional address books as you require, such as a separate address book for each company in your organization or for each line of business. For example, Fabrikam is an international organization that has multiple companies and multiple lines of business. Fabrikam plans to create an address book for each line of business. For lines of business that occur in more than one location, such as the pneumatic tools business, Fabrikam plans to create an address book for each location. Chris, the IT manager at Fabrikam, created the following list of address books that are required. This list also describes the party records that each address book must include.

- **Public Sector Contracts (PubSC)** – Party records for all parties that are involved in the public sector contracts that Fabrikam holds.
- **Private Sector Contracts (PriSC)** – Party records for all parties that are involved in the private sector contracts that Fabrikam holds.
- **Electronic Tools (ET)** – Party records for all parties that are involved in the purchase or sale of electronic tools, or that otherwise interact with the electronic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
- **Pneumatic Tools (PTJPN)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-Japan company.
- **Pneumatic Tools (PTUSA)** – Party records for all parties that are involved in the purchase or sale of pneumatic tools, or that otherwise interact with the pneumatic tools that are provided by or purchased for Fabrikam in the Fabrikam-US company.

**Decision:**

- How many additional address books will you create?


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
