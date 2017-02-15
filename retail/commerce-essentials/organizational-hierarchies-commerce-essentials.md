---
# required metadata

title: Organizations and organizational hierarchies (Commerce essentials)
description: Commerce essentials has three types of internal organizations that you can define to help an organization carry out a business process or achieve a goal. 
author: josaw1
manager: AnnBe
ms.date: 2015-12-09 14 - 53 - 48
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Application User
# ms.devlang: 
# ms.reviewer: josaw1
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 21251
ms.assetid: c24cd11a-655a-4e83-9052-a95d215d53ac
ms.search.region: global
ms.search.industry: Retail
ms.author: rubendel
ms.dyn365.intro: Feb-16
ms.dyn365.version: AX 7.0.0

---

# Organizations and organizational hierarchies (Commerce essentials)

Commerce essentials has three types of internal organizations that you can define to help an organization carry out a business process or achieve a goal. 

An organization is a group of people who work together to carry out a business process or achieve a goal. An organizational hierarchy represents the relationships between the business units that make up your organization.

## Organizations
In Commerce essentials, you can define three types of internal organizations: legal entities, operating units, and teams. In Microsoft Dynamics AX, all internal organizations are types of the Party entity. Therefore, these organizations use an address book to store addresses and other contact information. A party can be either a person or an organization, and it can belong to one or more address books.
### Legal entities

A legal entity is an organization that has a registered or legislated legal structure. Legal entities can enter into legal contracts and are required to prepare statements that report on their performance. A company is a type of legal entity in Microsoft Dynamics AX, and every legal entity is associated with a company ID. This association exists because a company ID, or DataAreaId, is used in some data models where companies are used as a boundary for data security. Users can access data only for the company that they are currently logged on to.

### Operating units

An operating unit is an organization that is used to divide the control of economic resources and operational processes in a business. People in an operating unit have a duty to maximize the use of scarce resources, improve processes, and account for their performance. In Commerce essentials, the types of operating units include cost centers, business units, value streams, departments, and retail channels. The following table provides more information about each type of operating unit.
|                         |                                                                                         |                                                                                                                                             |
|-------------------------|-----------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------|
| **Operating unit type** | **Description**                                                                         | **Purpose**                                                                                                                                 |
| Business unit           | A semi-autonomous operating unit that is created to meet strategic business objectives. | Use business units for financial reporting that is based on industries or product lines that the organization serves across legal entities. |
| Retail channel          | An operating unit that represents a brick-and-mortar store.                             | Use to manage and control one or more stores within or across legal entities.                                                               |

## Organizational hierarchies
In Commerce essentials, each hierarchy is assigned a purpose. The purpose of a hierarchy determines the types of organizations that can be included in the hierarchy. The purpose also determines which application scenarios a hierarchy can be used in. For example, a retail hierarchy can be used to buy and sell products in a retail store. Organizations in a hierarchy can share parameters, policies, and transactions. An organization can inherit or override the parameters of its parent organization. However, shared master data, such as products and address books, applies to the whole organization and can’t be overridden for individual organizations.
### Best practices for setting up an organization in a hierarchy

Consider the following best practices when you implement an organization hierarchy:
-   Create a department to specify the intersection between a legal entity and a business unit. You can then roll up data from a department to a legal entity for statutory reporting, and from a department to a business unit for internal reporting.
-   In a single legal entity, don’t set up multiple hierarchies for the same hierarchy purpose.
-   Don’t create a hierarchy for every purpose. Usually, you can use one hierarchy for multiple purposes. For example, one hierarchy of operating units can be assigned to all policy-related purposes.
-   Create balanced hierarchies. In a hierarchy, all nodes that are the same distance from the root node are defined as a level. In a balanced hierarchy, only one type of operating unit can occur at each level, and the distance from the root node to each level is consistent. If there are intermediate levels between a department and a legal entity or a business unit, placeholder organizations may be required to create a balanced hierarchy.
-   Don’t set up a separate hierarchy of operating units if the structure for legal entities is also your operating structure. A mixed hierarchy of legal entities and operating units may serve both purposes.
-   Before you set up major restructuring scenarios, use the hierarchy's effective dates to perform an impact analysis and a validation test.
-   Save a hierarchy as a draft if you might change a hierarchy before you publish it.
-   Limit the number of people who have permissions to add or remove organizations from a hierarchy in a production environment. A smaller number reduces the chance that costly mistakes can occur and corrections must be made.

## Retail store management
The following table describes the Commerce essentials scenarios where organization hierarchies can be used.
| Task                                                                           | Description                                                                                                                                                                                                                                                                                                | Hierarchy purpose    |
|--------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------|
| Manage retail assortments                                                      | Identify the products that are available in each retail store.                                                                                                                                                                                                                                             | Retail assortment    |
| Manage retail replenishment                                                    | Group stores to replenish inventory based on replenishment rules.                                                                                                                                                                                                                                          | Retail replenishment |
| Report data for stores                                                         | Group stores for reporting.                                                                                                                                                                                                                                                                                | Retail reporting     |
| Post inventory, calculate statements, or post statements for a group of stores | Create a group of stores that can be assigned to a batch job. When you define a batch job to post inventory, calculate statements, or post statements, you can specify which hierarchy the job applies to. When stores are added to or removed from the hierarchy, you don’t have to modify the batch job. | Retail POS posting   |



