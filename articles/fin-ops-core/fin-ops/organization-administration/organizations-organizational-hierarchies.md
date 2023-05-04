---
# required metadata

title: Organizations and organizational hierarchies overview
description: Organizational hierarchies represent the relationships between the organizations that make up your business.
author: sericks007
ms.date: 01/03/2022
ms.topic: overview
ms.prod: 
ms.technology: 

# optional metadata

ms.search.form: OMHierarchyManager, OMOperatingUnit,
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: ["17291", "intro-internal"]
ms.assetid: 76b7ca45-93d4-45cc-b191-66ee63afa1fd
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Organizations and organizational hierarchies overview

[!include [banner](../includes/banner.md)]

An organization is a group of people who are working together to carry out a business process or achieve a goal. Organizational hierarchies represent the relationships between the organizations that make up your business.

## Organizations

You can define the following types of internal organizations: legal entities, operating units, and teams.

All internal organizations are types of the **Party** entity. Therefore, these organizations use the address book to store address and contact information. A party, which can be either a person or an organization, can belong to one or more address books.

### Legal entities

A legal entity is an organization that has a registered or legislated legal structure. Legal entities can enter into legal contracts and are required to prepare statements that report on their performance.

A company is a type of legal entity. Currently, companies are the only kind of legal entity that you can create, and every legal entity is associated with a company ID. This association exists because some functional areas in the program use a company ID, or DataAreaId, in their data models. In these functional areas, companies are used as a boundary for data security. Users can access data only for the company that they are currently logged on to.

### Operating units

An operating unit is an organization that is used to divide the control of economic resources and operational processes in a business. People in an operating unit have a duty to maximize the use of scarce resources, improve processes, and account for their performance.

The types of operating units include cost centers, business units, value streams, departments, and commerce channels. The following table provides more information about each type of operating unit.

| Operating unit type | Description | Purpose |
|---------------------|-------------|---------|
| Cost center         | An operating unit in which managers are accountable for budgeted and actual expenditures. | Used for the management and operational control of business processes that span legal entities. |
| Business unit       | A semi-autonomous operating unit that is created to meet strategic business objectives. | Used for financial reporting that is based on industries or product lines that the organization serves independently of legal entities. |
| Value stream        | An operating unit that controls one or more production flows. | Commonly used in lean manufacturing to control the activities and flows that are required to supply a product or service to consumers. |
| Department          | An operating unit that represents a category or functional part of an organization that performs a specific task, such as sales or accounting. | Used to report on functional areas. A department may have profit and loss responsibility, and may consist of a group of cost centers. |
| Retail channel      | An operating unit that represents a brick and mortar store, an online store, or call center. | Used for the management and operational control of one or more stores within or across legal entities. |

### Teams

A team is an organization in which the members share a common responsibility, interest, or objective. Teams cannot be used in organizational hierarchies.

## Organizational hierarchies

Set up organizational hierarchies to view and report on your business from different perspectives. For example, you can set up a hierarchy of legal entities for tax, legal, or statutory reporting. Set up a hierarchy that is based on operating units to report financial information that is not legally required, but that is used for internal control. For example, you can create a purchasing hierarchy to control purchasing policies, rules, and business processes.

> [!NOTE]
> After an operating unit has been added to a hierarchy, the operating unit cannot be deleted. 

Each hierarchy is assigned a purpose. The purpose of a hierarchy determines the types of organizations that can be included in the hierarchy. The purpose also determines which application scenarios a hierarchy can be used in.

Organizations in a hierarchy can share parameters, policies, and transactions. An organization can inherit or override the parameters of its parent organization. However, shared master data, such as products and address books, applies to the whole organization and cannot be overridden for individual organizations. Creating organizations and hierarchies requires careful planning. For more information, see [Plan your organizational hierarchy](plan-organizational-hierarchy.md).

## Using Organizational Hierarchies in Financial Reporting

Organizational Hierarchies can be selected as a **Tree type** option in Financial Reporting. Financial reporting will select the current effective hierarch as noted by hierarchy. For more information, see [Reporting tree definitions in Financial Reports](/dev-itpro/analytics/financial-reporting-tree-definitions.md).

## Additional resources
- [Plan your organizational hierarchy](plan-organizational-hierarchy.md)
- [Create an organization hierarchy](tasks/create-organization-hierarchy.md)
- [Create a legal entity](tasks/create-legal-entity.md)
- [Create an operating unit](tasks/create-operating-unit.md)



[!INCLUDE[footer-include](../../../includes/footer-banner.md)]
