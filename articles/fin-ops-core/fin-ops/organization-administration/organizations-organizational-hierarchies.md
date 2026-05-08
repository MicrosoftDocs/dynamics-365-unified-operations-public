---
title: Organizations and organizational hierarchies overview
description: Organizational hierarchies represent the relationships between the organizations that make up your business, including overviews on operating unit types.
author: johnmichalak
ms.author: johnmichalak
ms.topic: overview
ms.date: 04/24/2026
ms.reviewer: johnmichalak
ms.collection: get-started
audience: Application User
ms.search.region: Global
ms.search.validFrom: 2016-02-28
ms.search.form: OMHierarchyManager, OMOperatingUnit,
ms.dyn365.ops.version: AX 7.0.0
ms.assetid: 76b7ca45-93d4-45cc-b191-66ee63afa1fd
---

# Organizations and organizational hierarchies overview

[!include [banner](../includes/banner.md)]

An organization is a group of people who work together to carry out a business process or achieve a goal. Organizational hierarchies show the relationships between the organizations that make up your business.

## Organizations

You can define the following types of internal organizations: legal entities, operating units, and teams.

All internal organizations are types of the **Party** entity. Therefore, these organizations use the address book to store address and contact information. A party, which can be either a person or an organization, can belong to one or more address books.

### Legal entities

A legal entity is an organization that has a registered or legislated legal structure. Legal entities can enter into legal contracts and must prepare statements that report on their performance.

A company is a type of legal entity. Currently, companies are the only kind of legal entity that you can create, and every legal entity is associated with a company ID. This association exists because some functional areas in the program use a company ID, or DataAreaId, in their data models. In these functional areas, companies are used as a boundary for data security. Users can access data only for the company that they're currently signed in to.

### Operating units

An operating unit is an organization that divides the control of economic resources and operational processes in a business. People in an operating unit have a duty to maximize the use of scarce resources, improve processes, and account for their performance.

The types of operating units include cost centers, business units, value streams, departments, and commerce channels. The following table provides more information about each type of operating unit.

| Operating unit type | Description | Purpose |
|---------------------|-------------|---------|
| Cost center         | An operating unit in which managers are accountable for budgeted and actual expenditures. | Used for the management and operational control of business processes that span legal entities. |
| Business unit       | A semi-autonomous operating unit that is created to meet strategic business objectives. | Used for financial reporting that is based on industries or product lines that the organization serves independently of legal entities. |
| Value stream        | An operating unit that controls one or more production flows. | Commonly used in lean manufacturing to control the activities and flows that are required to supply a product or service to consumers. |
| Department          | An operating unit that represents a category or functional part of an organization that performs a specific task, such as sales or accounting. | Used to report on functional areas. A department might have profit and loss responsibility, and might consist of a group of cost centers. |
| Retail channel      | An operating unit that represents a brick-and-mortar store, an online store, or call center. | Used for the management and operational control of one or more stores within or across legal entities. |

### <a id="establishments"></a>Establishments

> [!NOTE]
> **Availability**: Establishments support in Dynamics 365 Finance is available starting with version **10.0.48**.
> **Establishments** functionality in Finance is controlled by **Feature management**. To use **Establishments** in business documents and enable establishment‑level **Registration ID** validation and immutable storage on invoices, enable the **Establishment and Registration ID governance on invoices** feature. When the feature is turned off, establishment‑specific behavior (such as establishment selection, defaulting, and validation on invoices) isn't applied.

In Finance, an establishment represents an operational unit of a legal entity that carries out economic activity on a stable basis and might require its own regulatory identifiers, such as registration numbers used on invoices and regulatory reports.

You model establishments by using existing **Operating units**, combined with an **Organizational hierarchy** assigned with *Enterprise establishment structure* **Organizational hierarchy purpose**, to support invoicing and compliance scenarios.

A single legal entity can have one or multiple establishments, while remaining the sole legal and accounting entity. All establishments share the same legal identity of the company but might have distinct operational identities for invoicing and regulatory purposes.

Use **Operating units** to represent **Establishments** when a business requires:

- Identification of the issuing or receiving unit on invoices
- Separate regulatory identifiers per operational location
- Consistent establishment assignment across customer, vendor, project invoices

The system treats only **Operating units** that you explicitly include in a dedicated **Organizational hierarchy** assigned with **Enterprise establishment structure** purpose as **Establishments**. You can select these establishments in the **Establishment** field in the following documents where you can post an invoice:

- Free text invoices
- Sales orders
- Purchase orders
- Vendor invoices
- Pending vendor invoices
- Project invoice proposals
- Intercompany customer invoices
- General journals

Associate **Establishments** with inventory **Sites** (**Inventory management** > **Setup** > **Inventory breakdown** > **Sites**) to support transactional defaulting.

When you link an inventory **Site** to an **Establishment**, the system can derive the issuing or receiving establishment of the legal entity for customer, vendor, or project invoice that reference that site. This association ensures consistent establishment identification across business documents that result in invoice posting.

Associate **Establishments** with **Financial dimension values** to support transactional defaulting. When a **Financial dimension value** linked to an **Operating unit** included into an **Organizational hierarchy** assigned with **Enterprise establishment structure** purpose, is used on a business document, the system can derive and default the applicable **Establishments** for customer, vendor, or project invoices created from that document. This association complements site‑based defaulting and helps ensure consistent establishment identification across invoice‑generating processes.

### Teams

A team is an organization in which the members share a common responsibility, interest, or objective. Teams can't be used in organizational hierarchies.

## Organizational hierarchies

Set up organizational hierarchies to view and report on your business from different perspectives. For example, you can set up a hierarchy of legal entities for tax, legal, or statutory reporting. Set up a hierarchy that is based on operating units to report financial information that isn't legally required, but that is used for internal control. For example, you can create a purchasing hierarchy to control purchasing policies, rules, and business processes.

> [!NOTE]
> After an operating unit is added to a hierarchy, the operating unit can't be deleted.

Each hierarchy is assigned to a purpose. The purpose of a hierarchy determines the types of organizations that can be included in the hierarchy. The purpose also determines which application scenarios a hierarchy can be used in.

Organizations in a hierarchy can share parameters, policies, and transactions. An organization can inherit or override the parameters of its parent organization. However, shared master data, such as products and address books, applies to the whole organization and can't be overridden for individual organizations. Creating organizations and hierarchies requires careful planning. Learn more in [Plan your organizational hierarchy](plan-organizational-hierarchy.md).

### Establishment hierarchy

> [!NOTE]
> **Availability**: Establishments support in Finance is available starting with version **10.0.48**.
> **Establishments** functionality in Finance is controlled by **Feature management**. To use **Establishments** in business documents and enable establishment‑level **Registration ID** validation and immutable storage on invoices, enable the **Establishment and Registration ID governance on invoices** feature. When the feature is turned off, establishment‑specific behavior (such as establishment selection, defaulting, and validation on invoices) isn't applied.

**Organizational hierarchies** can be used to define which **Operating units** represent valid **Establishments** within a legal entity.

To support establishment scenarios, Finance introduces a dedicated organization hierarchy purpose: **Enterprise establishment structure**. This hierarchy purpose determines which operating units are considered establishments and participate in **Registration ID** validation and immutability on documents such as invoices.

## Using Organizational Hierarchies in Financial Reporting

Organizational Hierarchies can be selected as a **Tree type** option in Financial Reporting. Financial reporting selects the current effective hierarch as noted by hierarchy. <!-- Following link has been moved. For more information, see [Reporting tree definitions in Financial Reports](/dev-itpro/analytics/financial-reporting-tree-definitions.md). -->

## Additional resources

- [Plan your organizational hierarchy](plan-organizational-hierarchy.md)
- [Create an organization hierarchy](tasks/create-organization-hierarchy.md)
- [Create a legal entity](tasks/create-legal-entity.md)
- [Create an operating unit](tasks/create-operating-unit.md)

[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
