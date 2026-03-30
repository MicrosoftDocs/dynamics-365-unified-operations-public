---
title: Global address book overview
description: The global address book can help you understand the relationships among people and organizations that are associated with your organization.
author: msftbrking
ms.author: anisagrawal
ms.topic: overview
ms.date: 03/17/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: IT Pro
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: DirPartyTable, DirPartyTableRoles
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: bb6c02fa-cd91-4ca8-a58c-020502b19074
---

# Global address book overview

[!include [banner](../../../finance/includes/banner.md)]

The global address book is a centralized repository for master data that you must store for all internal and external persons and organizations that your company interacts with. The data associated with party records includes the party's name, address, and contact information. Other details vary, depending on whether the party is a person or an organization. You assign each party record to a party, and each party can be associated with one or more party roles in a company. Party roles include customer, prospect, worker, user, vendor, competitor, applicant, and contact. For example, the organization party First Up Consultants, can be associated with customer, business relation, and vendor roles in the CEE company, and can also be associated with the vendor role in the CEU company. Here are some of the benefits of this shared data:

- The data shows the relationships that people and organizations have with other areas of the company. The relationship between two organizations changes when one organization has multiple roles, such as vendor and customer. Communication between the two organizations also changes. There might be special agreements that you can negotiate to encourage a closer partnership with the other organization.
- Setup and maintenance are easier. For example, when an address changes, you need to update the address in only one place. All the other associated records are updated automatically.

You can't delete any party in the global address book that's a legal entity. The **Delete** button is unavailable for these parties. 

## How the global address book works

The following illustration shows how party records, party roles, locations, and transactions interact and relate to an address book. As the illustration shows, a party record can belong to one or more address books. Each party record can store one or more locations, or addresses, and is assigned a party role. The role that is assigned to the party record can have specific transactions types associated with it. The following sections provide more information about party roles, locations, and transaction types. The following image is a graphical representation of the ways that parties, party roles, locations, and transactions interact in relation to the global address book.

:::image type="content" source="../../fin-ops/organization-administration/media/address-book-structure.png" alt-text="Global address book interaction with AX entities and transactions." lightbox="../../fin-ops/organization-administration/media/address-book-structure.png":::

### Party roles

You refer to roles that are associated with party records as party roles. You can assign several party roles to both party types, person and organization. Here are the definitions for each party role:

- **Customer** – Individuals, companies, or other entities who purchase goods and services that are produced by other individuals, companies, or entities.
- **Prospect** – A party that might provide a service or benefit to a legal entity.
- **Worker** – A person who assumes the role of an employee or a contractor, and who is paid in exchange for services.
- **User** – A person who is a user of the system.
- **Vendor** – A party that supplies products to one or more legal entities in exchange for payment.
- **Competitor** – A person or organization that provides goods or services that are similar to the goods or services that your business provides.
- **Applicant** – A person who makes a formal written or electronic request to work for or fill an open position in an organization.
- **Contact** – A person, either inside or outside your organization, that you create an entry for. In this entry, you can save information such as the person's street and email addresses, telephone and fax numbers, and webpage URLs.

### Creating new party records

Enter party records in the global address book in two ways:

- **Create a party record when you don't know the role** – Create a party record in the global address book when you don't know the role type (for example, you don't know whether the party is a customer or an opportunity). You can select the role type later.
- **Create a party record when you know the role** – If you know the role type for the party, create a record on the appropriate page for that type. For example, if the party is a customer, create a record on the **Customer** page. When you create and save a record by using the page for the party's role type, you automatically create the record in the global address book.

### Party roles and transactions

For transactions that are a part of the business processes, multiple parties might be associated with each transaction. An example is a customer that you need to reference on project quotations.

### Parties locations, addresses, and contact information

Each party record's addresses, locations, and contact information are shared across all the party roles that are associated with that party. Therefore, when you change any of this information, all other associated records are updated accordingly.

### Locations and transactions

When you include a party role in a transaction, you can access the location, address, or contact information of the party when you enter transaction details.


[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
