---
# required metadata

title: Create tables
description: 
author: kfend
manager: AnnBe
ms.date: 2015-12-04 23 - 17 - 02
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
# ms.reviewer: 51
ms.search.scope: AX 2012
# ms.tgt_pltfrm: 
ms.custom: 18161
ms.assetid: 96e1f184-d049-46c3-a4ef-12641361f356
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.dyn365.ops.intro: 
ms.dyn365.ops.version: 2012

---

# Create tables



Create tables to store data in by using the Application Object Tree (AOT).

| **Note**                                                                                                                                                                                                                                                                 |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Before creating new tables, review the tables that ship with Microsoft Dynamics AX to determine whether you can use existing tables. For more information, see [Application Tables](http://msdn.microsoft.com/library/a905f039-ef71-4c61-8f3f-71dadf27b09e(AX.60).aspx). |

Table fields are based on a primitive data type or an extended data type. For more information, see [Primitive Data Types](http://msdn.microsoft.com/library/29e7d464-b72d-4a86-a982-12f9e90e704e(AX.60).aspx) and [How to: Create an Extended Data Type](http://msdn.microsoft.com/library/6292481f-1d73-46e9-8b46-18ab7de9a71d(AX.60).aspx). The AutoReport and AutoLookup groups are automatically created when you create a table. For more information, see [Implementing Automatic Reports for Forms](http://msdn.microsoft.com/library/86ee1f62-8325-4bcb-a884-a5ae521355c8(AX.60).aspx) and [How to: Add a Control with a Lookup Form](http://msdn.microsoft.com/library/2e365e4b-842a-44eb-b0fa-6fa4c8c1e0fe(AX.60).aspx). To manage changes to AOT objects, a version control system is available. For more information, see [Version Control System](http://msdn.microsoft.com/library/522708f8-80a0-4bfd-9634-b7cb868d1874(AX.60).aspx).

## Create a Table
1.  In the AOT, expand the **Data Dictionary** node.
2.  Right-click the **Tables** node, and then select **New Table**.
3.  Right-click the table, and then click **Properties**.
4.  Rename the table by modifying the **Name** property.
5.  To specify the table as temporary, set the **Temporary** property to **Yes**. For more information, see [Table Properties](table-properties.md).
6.  Modify additional table properties, as needed. For more information, see [Table Properties](table-properties.md).
7.  To delete the table, right-click it, and then click **Delete**.

## Add Fields to a Table
| **Note**                                                                                                                               |
|----------------------------------------------------------------------------------------------------------------------------------------|
| You can delete only fields that do not contain data in any of the table records. You cannot modify the data type of an existing field. |

1.  Right-click the **Fields** node of your table.
2.  Click **New**, and then choose a primitive data type to base your field on. If you plan to base the field on a specific extended data type, you must choose a primitive data type that the extended data type is based on.
3.  To base the field on an extended data type, set the **ExtendedDataType** property.
4.  Modify additional field properties, as needed. For more information, see [Table Field Properties](http://ax.help.dynamics.com/en/wiki/table-field-properties/).
5.  To delete the field, right-click it, and then click **Delete**.

### Restart the AOS after Adding Fields to Tables

When you insert data in a table during development, the SQL statement you use to insert the data is cached in the AOS. Next you might add a new field to the table and persist the change to the database. This causes the SQL statement in the cache to become stale, because the statement is not updated to include the new field. If you reuse the stale statement, the new field is ignored, or an error might occur. To avoid this problem, restart the AOS after you persist table schema changes to the database. The cache is empty when the AOS restarts.

See also
--------

[Use the Table Browser to View, Add, Modify, or Delete Records](http://msdn.microsoft.com/library/89402b55-02ea-40bc-ad0e-0774b1655426(AX.60).aspx)

[How to: Add a Relation to a Table](http://msdn.microsoft.com/library/1b164b99-de08-4557-8da5-1931d9469ca1(AX.60).aspx)

[How to: Create a Field Group](href="http://msdn.microsoft.com/library/798cf898-d5a0-45f2-9e68-edd0aedc13a4(AX.60).aspx)

[How to: Create an Index](http://msdn.microsoft.com/library/5c412c46-724b-4498-ab42-51725f15c71a(AX.60).aspx)

[Tables, Views, and Maps](http://msdn.microsoft.com/library/9c62bde0-46a1-4b48-87b2-778a68627cd1(AX.60).aspx)

