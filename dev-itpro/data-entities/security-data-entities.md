---
# required metadata

title: Security and data entities
description: Data entities support entry point security similar to menu items and forms. In order to provide flexibility in defining a security model, data entities allow separate security configuration for each integration mode.
author: RobinARH
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
ms.custom: 17852
ms.assetid: a9ede141-56fa-4310-997d-aeef184f7a52
ms.search.region: Global
# ms.search.industry: 
ms.author: kuntalme
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# Security and data entities

[!include[banner](../includes/banner.md)]


Data entities support entry point security similar to menu items and forms. In order to provide flexibility in defining a security model, data entities allow separate security configuration for each integration mode.

Role based security (with entry point)
--------------------------------------

Data entities support entry point security similar to menu items and forms. In order to provide flexibility in defining security model, data entities allow a separate security configuration for each integration mode. Currently there are two entry points/integration modes identified for a data entity.

## Entry points
|                 |                                                                                                                      |
|-----------------|----------------------------------------------------------------------------------------------------------------------|
| **Entry point** | **Description**                                                                                                      |
| Data services   | The ability to use OData services (API) for the entity.                                                              |
| Data management | The ability to use asynchronous integration options for the entity, such as import/export and connector integration. |

## Security modeling guidelines
In Data Management (DIXF/Connectors) and OData both provide read/write capabilities for a data entity. Thus, if a role can read/write the Data Entity via OData, then being able to export/import via Data Management (DIXF/Connectors) is permissible as well. The following tasks are required:

-   **Create two privileges per entity,** **one for view and the other for maintain**. On both privileges, leave IntegrationMode=All. The Maintain privilege is typically granted 'Delete' access and the View privilege is typically granted 'Read' access. Naming guidelines for these privileges are:
    -   EntityName + **'View'**
    -   EntityName + **'Maintain'**
-   **Add the Data Entity privileges to existing duties** (or roles). Determine the forms that relate to that Data Entity (expose similar data) and update the existing duties/roles that have privileges for that form by adding these new Data Entity privileges. **Roles that have permission to a form should also have permission to related Data Entities** via both OData and Data Management.

## Exceptional cases
In some cases, where users have limited access to modify a data entity (like only create or correct), or have access only through OData (no DIXF), instead of using privileges that are created automatically, developers should use existing form privileges and add data entity permissions to it. Set Access Level and Integration Mode to appropriate level. Consult with your product manager to determine the appropriate security for your entity in these cases.

## Scenario implications
### OData (Data Service)

If an entity is public (has its 'Public' property set to Yes), then this implies it is available via OData. Making a Data Entity available via OData enables other integration scenarios such as "Open in Excel" and "Export to Word", so a Data Entity should be left public unless there is a compelling reason to make it private.

### Data Management

Enabling data management allows users to do file based import/export. The capabilities of OData and Data management are similar thus, if users can access it via OData allowing import/export is also permissible.

Roles
=====

There will be roles and corresponding duties for data migration scenario.

## Modeling new entry point security in the Application Explorer
Security modeling follows a pattern similar to modeling security with privileges on entry point. The following steps outline how security is modeled.

1.  Create a new privilege.
2.  Create new data entity permissions.
3.  Set the **Name** to **Data Entity**.
4.  Select the **Access Level**.
5.  Select **Integration Mode** (All &gt; Data Services &gt; Data Management). This is specific to Object Type: Data Entity.
    -   **All** – Applies same security settings to be applied to both OData and data import/export.
    -   **Data Management** – Applies only to data import/export and connector integration.
    -   **Data Services** – Only applies to OData Services.

[![RolebasedSecurity](./media/rolebasedsecurity.png)](./media/rolebasedsecurity.png)

## Organization on Roles** **
Data entities support associating a company when assigned to a user to filter data based on that company.


