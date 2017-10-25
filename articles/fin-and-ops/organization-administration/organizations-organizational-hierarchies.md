---
# required metadata

title: Organizations and organizational hierarchies
description: An organization is a group of people who are working together to carry out a business process or achieve a goal. Organizational hierarchies represent the relationships between the organizations that make up your business.
author: sericks007
manager: AnnBe
ms.date: 08/18/2017
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-applications
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
ms.reviewer: sericks
ms.search.scope: Core, AX 7.0.0, Operations, UnifiedOperations
# ms.tgt_pltfrm: 
ms.custom: 17291
ms.assetid: 76b7ca45-93d4-45cc-b191-66ee63afa1fd
ms.search.region: Global
# ms.search.industry: 
ms.author: sericks
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Organizations and organizational hierarchies

[!include[banner](../includes/banner.md)]


An organization is a group of people who are working together to carry out a business process or achieve a goal. Organizational hierarchies represent the relationships between the organizations that make up your business.

Organizations
-------------

In Microsoft Dynamics 365 for Finance and Operations, you can define the following types of internal organizations: legal entities, operating units, and teams.

All internal organizations are types of the **Party** entity. Therefore, these organizations use the address book to store address and contact information. A party, which can be either a person or an organization, can belong to one or more address books.
### Legal entities

A legal entity is an organization that has a registered or legislated legal structure. Legal entities can enter into legal contracts and are required to prepare statements that report on their performance. 

A company is a type of legal entity. In this release of Microsoft Dynamics 365 for Finance and Operations, companies are the only kind of legal entity that you can create, and every legal entity is associated with a company ID. This association exists because some functional areas in the program use a company ID, or DataAreaId, in their data models. In these functional areas, companies are used as a boundary for data security. Users can access data only for the company that they are currently logged on to.

### Operating units

An operating unit is an organization that is used to divide the control of economic resources and operational processes in a business. People in an operating unit have a duty to maximize the use of scarce resources, improve processes, and account for their performance. 

In Microsoft Dynamics 365 for Finance and Operations, the types of operating units include cost centers, business units, value streams, departments, and retail channels. The following table provides more information about each type of operating unit.

| Operating unit type | Description         | Purpose      |
|---------------------|---------------------|--------------|
| Cost center         | An operating unit in which managers are accountable for budgeted and actual expenditures.                                                      | Used for the management and operational control of business processes that span legal entities.                                         |
| Business unit       | A semi-autonomous operating unit that is created to meet strategic business objectives.                                                        | Used for financial reporting that is based on industries or product lines that the organization serves independently of legal entities. |
| Value stream        | An operating unit that controls one or more production flows.                                                                                  | Commonly used in lean manufacturing to control the activities and flows that are required to supply a product or service to consumers.  |
| Department          | An operating unit that represents a category or functional part of an organization that performs a specific task, such as sales or accounting. | Used to report on functional areas. A department may have profit and loss responsibility, and may consist of a group of cost centers.   |
| Retail channel      | An operating unit that represents a brick and mortar store, an online store or an online marketplace.                                          | Used for the management and operational control of one or more stores within or across legal entities.                                  |

### Teams

A team is an organization in which the members share a common responsibility, interest, or objective. Teams cannot be used in organizational hierarchies.

Organizational hierarchies
--------------------------

Set up organizational hierarchies to view and report on your business from different perspectives. For example, you can set up a hierarchy of legal entities for tax, legal, or statutory reporting. Set up a hierarchy that is based on operating units to report financial information that is not legally required, but that is used for internal control. For example, you can create a purchasing hierarchy to control purchasing policies, rules, and business processes. 

Each hierarchy is assigned a purpose in Microsoft Dynamics 365 for Finance and Operations. The purpose of a hierarchy determines the types of organizations that can be included in the hierarchy. The purpose also determines which application scenarios a hierarchy can be used in. 

Organizations in a hierarchy can share parameters, policies, and transactions. An organization can inherit or override the parameters of its parent organization. However, shared master data, such as products and address books, applies to the whole organization and cannot be overridden for individual organizations. Creating organizations and hierarchies requires careful planning. For more information, see [Plan the organizational hierarchy](plan-organizational-hierarchy.md).





