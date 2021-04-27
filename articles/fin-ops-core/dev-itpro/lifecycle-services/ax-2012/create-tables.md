---
# required metadata

title: Create tables by using the Application Object Tree (AOT)
description: This topic provides information about how to use the Application Object Tree (AOT) to create tables in which to store data.
author: kfend
ms.date: 10/26/2017
ms.topic: article
ms.prod: dynamics-ax-2012 
ms.technology:

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer, IT Pro
# ms.devlang: 
ms.reviewer: sericks
# ms.tgt_pltfrm: 
ms.custom: 18161
ms.assetid: 96e1f184-d049-46c3-a4ef-12641361f356
ms.search.region: Global
# ms.search.industry: 
ms.author: kfend
ms.search.validFrom: 
ms.dyn365.ops.version: 2012

---

# Create tables by using the Application Object Tree (AOT)

[!include [banner](../../includes/banner.md)]

Create tables to store data in by using the Application Object Tree (AOT).

> [!NOTE]
> Before creating new tables, review the tables that ship with Microsoft Dynamics AX to determine whether you can use existing tables. For more information, see [Application Tables](/previous-versions/dynamics/ax-2012/reference/aa852568(v=ax.60)).

Table fields are based on a primitive data type or an extended data type. For more information, see [Primitive Data Types](/dynamicsax-2012/developer/primitive-data-types) and [How to: Create an Extended Data Type](/dynamicsax-2012/developer/how-to-create-an-extended-data-type). The AutoReport and AutoLookup groups are automatically created when you create a table. For more information, see [Implementing Automatic Reports for Forms](/dynamicsax-2012/developer/implementing-automatic-reports-for-forms) and [How to: Add a Control with a Lookup Form](/dynamicsax-2012/developer/how-to-add-a-control-with-a-lookup-form). To manage changes to AOT objects, a version control system is available. For more information, see [Version Control System](/dynamicsax-2012/developer/version-control-system).

## Create a Table
1.  In the AOT, expand the **Data Dictionary** node.
2.  Right-click the **Tables** node, and then select **New Table**.
3.  Right-click the table, and then click **Properties**.
4.  Rename the table by modifying the **Name** property.
5.  To specify the table as temporary, set the **Temporary** property to **Yes**. For more information, see [Table properties in the Application Object Tree (AOT)](table-properties.md).
6.  Modify additional table properties, as needed. For more information, see [Table properties in the Application Object Tree (AOT)](table-properties.md).
7.  To delete the table, right-click it, and then click **Delete**.

## Add Fields to a Table

> [!NOTE]
> You can delete only fields that do not contain data in any of the table records. You cannot modify the data type of an existing field.

1.  Right-click the **Fields** node of your table.
2.  Click **New**, and then choose a primitive data type to base your field on. If you plan to base the field on a specific extended data type, you must choose a primitive data type that the extended data type is based on.
3.  To base the field on an extended data type, set the **ExtendedDataType** property.
4.  Modify additional field properties, as needed. For more information, see [Table properties in the Application Object Tree (AOT)](table-properties.md).
5.  To delete the field, right-click it, and then click **Delete**.

### Restart the AOS after Adding Fields to Tables

When you insert data in a table during development, the SQL statement you use to insert the data is cached in the AOS. Next you might add a new field to the table and persist the change to the database. This causes the SQL statement in the cache to become stale, because the statement is not updated to include the new field. If you reuse the stale statement, the new field is ignored, or an error might occur. To avoid this problem, restart the AOS after you persist table schema changes to the database. The cache is empty when the AOS restarts.

Additional resources
--------

[Use the Table Browser to View, Add, Modify, or Delete Records](/dynamicsax-2012/developer/use-the-table-browser-to-view-add-modify-or-delete-records)

[How to: Add a Relation to a Table](/dynamicsax-2012/developer/how-to-add-a-relation-to-a-table)

[How to: Create an Index](/dynamicsax-2012/developer/how-to-create-an-index)

[Tables, Views, and Maps](/dynamicsax-2012/developer/tables-views-and-maps)





[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]