---
# required metadata

title: Configuration in the Intelligent Data Management Framework (AX 2012) | Microsoft Docs
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 20:04:07
ms.topic: article
ms.prod: 
ms.service: Lifecycle Services
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: 51
ms.suite: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 17661
ms.assetid: b9a74ace-218f-466d-b05f-1dad603bebd7
ms.region: Global
# ms.industry: 
ms.author: kfend

---

# Configuration in the Intelligent Data Management Framework (AX 2012)



Purge and archive functionality
-------------------------------

The Microsoft Dynamics AX application provides real-time updates for a transaction. For example, when users enter, modify, or delete orders, Microsoft Dynamics AX updates a main table and some of its related tables. Over time, the volume of data in the database grows. IDMF lets you analyze the database and maintain an optimal database size. To maintain the database size, IDMF provides the purge and archive functions. The purge function removes or deletes data from a set of related entities, or tables, from the production database. The archive function moves data from a set of related tables from the production database to a standby database called the archive database. Users can use the archive database for reporting, but we recommend that they not be allowed to update it. IDMF and this document use the term offlining interchangeably with the term archiving, and recycling interchangeably with purge or delete operation. Both the purge and archive operations depend on a carefully determined hierarchical relationship tree of related tables based on the Microsoft Dynamics AX metadata. For example, when a user creates, updates, or deletes a sales order, the **SalesTable** table and other tables that are related to **SalesTable** are updated. When you archive or purge data from a main table, such as SalesTable, you must archive or purge data from all the tables that are related to that main table. The archive and purge operations always work on a set of related tables. This set of related tables forms a hierarchical relationship. Each hierarchical relationship starts with the main table, called a driver table, at the root level, level 0, of the hierarchical tree. All the child tables that are related to the driver table are at the next level, level 1. All the child tables of tables in level 1 are at the next level, level 2. The nested hierarchy of parent-child relationships continues until there are no more child tables for the lowest level of tables. To help you understand the hierarchical relationships, IDMF includes some templates that show sample hierarchical relationships. Templates for the archive function are called archive templates. Templates for the purge function are called purge templates. Each template provides a sample hierarchy based on a standard installation without any customizations. You cannot use these templates directly. You must open these templates, review them to verify applicability in your environment, and then save them before you can use them for the archive or purge function. When you open a template, verify that the relationship hierarchy contains all the relevant tables from your implementation of Microsoft Dynamics AX. The hierarchical tree in the template may not match your implementation for several reasons. The following list provides some of the reasons for a difference between a template and the relationships in your implementation of Microsoft Dynamics AX:

-   Your implementation may not have certain tables that are in the template, depending on the customization, configuration, and licensing of your implementation.
-   Certain fields in the tables in the template might not be available in your implementation.
-   You may have created custom tables that are not contained in the templates.

It is very important that your hierarchical relationship include all relevant tables in your implementation. A purge or archive operation that is based on an incorrect hierarchy causes data corruption. Therefore, you must create a relationship tree that is complete and accurate for your implementation. Because of the uniqueness of each implementation, you cannot use a template in the archive or purge function. Instead, you must create a Purge Object or an Archive Object that encompasses all relevant relationships for your implementation. There are two ways you can create a Purge Object or an Archive Object:

-   Work with a template. Open a template that is included with IDMF. Review the template, and then add or remove tables and rules to match your implementation. Verify that the relationship tree is complete for your implementation. Save the template. An archive template is saved as an Archive Object. A purge template is saved as a Purge Object.
-   Create an object on your own instead of using the template that is included with IDMF. Depending on the licensing, configuration, and customization, the hierarchical relationship in your implementation may significantly differ from the templates that are included with IDMF. In this case, you must use the discovery process, which lets you select a driver table that is the parent table that forms the root of the relationship tree. Based on the driver table that you select, and the Microsoft Dynamics AX metadata, IDMF generates the hierarchical relationship tree. IDMF checks an exception list and ignores tables that are contained in the exception list.

We recommend that you create a Purge Object or an Archive Object through the discovery process instead of opening and saving a template. Compare your object with the template, if a similar template exists, to see whether your object is missing any tables that the template contains. Depending on the comparison and verification, add tables to or remove tables from your object, as appropriate. Each Archive Object or Purge Object contains certain rules that govern the archiving or purging of data. Rules let you specify the selection criteria that are used to select the data that is qualified for purging or archiving. You can add, remove, or modify these rules to match your archive and purge guidelines. You must save an Archive Object or a Purge Object before you can use it in a purge or archive task. IDMF provides a graphical view of your Purge Object or Archive Object that resembles the sample that is shown in the following diagram. Familiarize yourself with the legend, so that you can easily understand and validate your Archive Objects and Purge Objects. ![IDMF archive object](./media/idmfarchiveobject.png) The following table explains the legend that is shown in a relationship tree of an object or a template.

| Text                                                                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
|-----------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Table removed                                                         | This table has been removed from the object you are working with. The Purge Object or Archive Object does not purge or archive data from this table.                                                                                                                                                                                                                                                                                                                                                                                                                                               |
| Table is missing from the production database                         | This table exists in the template or object you are working with, but is not found in your production database. You must remove this table from the relationship before you can save this object.                                                                                                                                                                                                                                                                                                                                                                                                  |
| Fields with disabled configuration keys                               | In Microsoft Dynamics AX, each field is governed by the security key and a configuration key. Depending on the licensing, security keys, and configuration you use, each field can be an enabled or a disabled field. For the purpose of this document, a disabled field refers to a field that is disabled via the configuration key. A driver table with any rules that use a disabled field, or a child table with any relationships that use a disabled field, appears with a yellow border. You must resolve the rules and relationships with disabled fields before you can save the object. |
| Selected table                                                        | You have selected this table. You can select multiple tables, and then perform actions such as remove all occurrences of the selected tables or add selected tables to the data replication feature.                                                                                                                                                                                                                                                                                                                                                                                               |
| Table group property is worksheet header                              | This table has a **TableGroup** value of **WorksheetHeader**. You can right-click such tables and rediscover related child tables.                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| Related Archive Object                                                | This is a Related Archive Object. To avoid complexity, you can add a Related Archive Object to your Archive Object, instead of adding a child table with many levels of nested relationships.                                                                                                                                                                                                                                                                                                                                                                                                      |
| Related Archive Object: Table is missing from the production database | This Related Archive Object does not exist in the production database. You must remove this table from the Related Archive Object and save it before you can save your current object.                                                                                                                                                                                                                                                                                                                                                                                                             |
| Related Archive Object: Fields with disabled configuration keys       | This Related Archive Object contains relationships or rules with disabled configuration keys. You must enable the configuration keys, or remove the relationships and rules based on disabled fields, and then save the Related Archive Object before you can use it in this object.                                                                                                                                                                                                                                                                                                               |
| Driver table of the parent Archive Object                             | This is the driver table of the Archive Object that is the parent object of this Related Archive Object.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |

 

## Introduction to the discovery process
The discovery process creates a hierarchical relationship tree for a Purge Object or an Archive Object. When you create a new Purge Object or Archive Object, you select a parent table, called the driver table. IDMF uses a process called discovery to create a hierarchical relationship tree based on the driver table you select. The following steps provide a high-level walkthrough of the discovery process, assuming that you selected the WMSOrder table as the driver table:
1.  The discovery process starts when you select a table as the driver table that is the root parent in a parent-child hierarchy. However, IDMF does not display tables in the driver table list that are part of an exception list. The **WMSOrder** table appears in the list, because it is not in the exception parameters list.
2.  The **xRefTableRelation** table in Microsoft Dynamics AX contains relationships between two tables, and the fields that are used by the relationship. IDMF queries the **xRefTableRelation** table to retrieve the names of the tables that are child tables of the parent, **WMSOrder**. Explanation of the **xRefTableRelation** field is beyond the scope of this topic. For more information, see [xRefTableRelation table](https://msdn.microsoft.com/en-us/library/aa860828.aspx).
3.  Continue the previous step for every table, until there are no child tables left. In certain cases, a child table is excluded from the relationship tree in these conditions:
    -   The child table has a **TableGroup** value of **Main**, **Parameter**, or **Group**.
    -   The child table is in the exception parameters list, with the **Purge discovery** field selected. In this case, the child table is excluded from the relationship tree of the Purge Object.
    -   The child table is in the exception parameters list, with the **Archive discovery** field selected. In this case, the child table is excluded from the relationship tree of the Archive Object.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><strong>Note</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Tables with a <strong><span class="ui">Table Group</span></strong> value of <strong><span class="ui">WorksheetHeader</span></strong> are ideal candidates for driver tables, and appear with a black border in the relationship tree when they are discovered as child tables. The discovery process shows these tables as child tables, but does not show their child tables in the tree. Determine which option in the following list is the best way to incorporate these tables in your purge and archive strategy:
<ul>
<li>Keep these tables in the relationship tree, but do not add their child tables.</li>
<li>Keep these tables in the relationship tree, and add their child tables. Right-click a table, and then select <strong><span class="ui">Discover</span></strong> to discover, or add, the child tables that form the parent-child hierarchy for the table.</li>
<li>In the case of an Archive Object, remove these tables from the relationship tree, and either add them as Related Archive Objects or create independent Archive Objects.</li>
<li>In the case of a Purge Object, remove these tables, and create new Purge Objects by using these tables as the driver tables.</li>
</ul></td>
</tr>
</tbody>
</table>

| **Caution**                                                                                                                                                                                                                                                                              |
|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| You must understand the Microsoft Dynamics AX metadata and application before you start working with the exception parameters list, Archive Objects, or Purge Objects. You must functionally validate the Purge Object or Archive Object to maintain database and application integrity. |



