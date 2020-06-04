---
# required metadata

title: Delete data
description: This topic describes the delete method and doDelete method in the X++ language.
author: RobinARH
manager: AnnBe
ms.date: 11/07/2019
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: rhaertle
ms.search.scope: Operations
# ms.tgt_pltfrm: 
ms.custom: 150273
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.dyn365.ops.version: AX 7.0.0
ms.search.validFrom: 2016-02-28

---

# Delete data

[!include [banner](../../includes/banner.md)]

This topic describes the delete method and doDelete method in the X++ language.

## delete method
The **delete** table method deletes the current record from the database. To use this method, use a **where** clause to specify the rows to delete. One record at a time is then removed from the specified table. The **delete\_from** operator is a record set–based operator that removes multiple records at the same time. The **delete** method can be overridden. For example, you might want to add extra validation before records are deleted. If you override the **delete** method, you can run the original (base) version of the **delete** method by calling the **doDelete** method. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method. In the following example, all records in the MyTable table that satisfy the criterion in the **where** clause (that is, all records where the value of the **AccountNum** field is equal to **1000**) are deleted from the database. One record is deleted at a time.

```xpp
ttsBegin;
while select forUpdate myTable
    where myTable.AccountNum == '1000'
{
    myTable.delete();
}
ttsCommit;
```

## doDelete method
Like the **delete** table method, the **doDelete** table method deletes the current record from the database. Use the **doDelete** method if the **delete** table method has been overridden, and you want to run the original (base) version of the **delete** method instead of the overridden version. Therefore, a call to the **doDelete** method is equivalent to a call to **super()** in the **delete** method. The following example deletes all records in the myTable table that have an account number that is more than or equal to **200**.

```xpp
ttsBegin;
while select forUpdate myTable
    where myTable.AccountNum >='200';
{
    myTable.doDelete();
}
ttsCommit;
```


### Deleting a set of records

You can use a **while select** statement to loop over a set of records that meet some criteria, and perform an action on each record. In the following example, the statement is used to delete a set of records.

```xpp
TableName myXrec;
while select myXrec where conditions // conditions is a Boolean variable defined elsewhere.
{
    myXrec.delete();
}
```

You can achieve the same effect by using the **delete\_from** keyword.

```xpp
TableName myXrec;
delete_from myXrec where conditions; // conditions is a Boolean variable defined elsewhere.
```