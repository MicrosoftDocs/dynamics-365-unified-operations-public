---
title: SqlDataDictionary class
description: This topic describes the SqlDataDictionary class.
author: robinarh
manager: tonyafehr
ms.date: 06/25/2020
ms.topic: article
ms.prod: 
ms.service: dynamics-ax-platform
ms.technology: 

audience: Developer
ms.reviewer: rhaertle
ms.search.scope: Operations
ms.search.region: Global
ms.author: rhaertle
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0
---

# Class SqlDataDictionary

[!include [banner](../../includes/banner.md)]

```xpp
class SqlDataDictionary extends Object
```

The SqlDataDictionary class provides a collection of methods for data dictionary maintenance.

## Remarks

This API has a built-in authorization check that is invoked at run time. Calls to members of the SQLDataDictionary class by users without access to the development security key (SysDevelopment) results in an exception.

## Examples

The following example checks whether the UserInfo table exists in the database.

```xpp
server static public void Main(Args _args) 
{ 
    SqlDataDictionary sqlDict; 
    boolean b; 
    sqlDict = new SqlDataDictionary(); 
    if (sqlDict) 
    { 
        b = sqlDict.tableExist("USERINFO"); 
        print b; 
        pause; 
    } 
}
```

## Methods

| Method                                                                                                               | Description                                                                                                                   |
|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| public int indexCreate(\[TableId tableId\], \[IndexId indexId\])                                                     | Creates the indexes of a table in the SQL database. You can also use this method to re-create indexes. |
| public str indexCreateDDL(TableId tableId)                                                                           | Generates and returns the SQL statements needed to create the indexes of a table.                      |
| public int indexDrop(\[TableId tableId\], \[IndexId indexId\], \[boolean onlyNonUnique\])                            | Drops the indexes of a table in the SQL database.                                                      |
| public str name(str bmsname, \[FieldId fieldId\], \[int arrayindex\])                                                | Translates any object name into a valid SQL database object-name; that is, valid for the database currently connected.        |
| public int tableCreate(\[boolean indexes\], \[TableId tableId\])                                                     | Creates one or more  tables in the SQL database. Also, provides an option to create for index.           |
| public str tableCreateDDL(TableId tableId)                                                                           | Generates and returns the SQL statement to create a table.                                             |
| public int tableDrop(TableId tableId, \[boolean prompt\_before\_drop\])                                              | Drops the  table in the SQL database.                                                                    |
| public str tableDropDDL(TableId tableId)                                                                             | Generates and returns the SQL statement to drop a table.                                               |
| public boolean tableEmpty(TableId tableId, \[str company\], \[boolean not\_this\_company\])                          | Returns true if table is not empty; otherwise false.                                                                          |
| public boolean tableExist(str sqltablename, \[boolean use\_within\_transaction\])                                    | Returns true if table exists; otherwise false.                                                                                |
| public int tableMetaData(TableId tableId)                                                                            | Fills the SqlDescribe table with data dictionary meta data.                                                                   |
| public int tableReindex(\[TableId tableId\], \[IndexId indexId\])                                                    | Updates index for the table.                                                                                                  |
| public int tableSynchronize(TableId tableId, \[boolean update\_dict\_info\_only\], \[boolean check\_indexes\])       | Synchronizes the  table and the table of the SQL database.                                               |
| public int tableTruncate(TableId tableId, \[boolean prompt\_before\_truncate\], \[boolean truncate\_system\_table\]) | Truncates the  table.                                                                                    |
| public str tableTruncateDDL(TableId tableId)                                                                         | Generates and returns a SQL statement to truncate a table.                                             |
| ::public static int synchronize(\[boolean synchronize\_all\])                                                        | Synchronizes the  data dictionary and the data dictionary of the SQL database.                           |
| public void new()                                                                                                    | Initializes a new instance of the SqlDataDictionary class.                                                                    |
| public void tableDelete(TableId tableId)                                                                             | Deletes the  table in the SQL database.                                                                  |

## Method indexCreate

Creates the indexes of a table in the SQL database. You can also use this method to re-create indexes.

```xpp
public int indexCreate([TableId tableId], [IndexId indexId])
```

### Parameters - indexCreate

tableId  
The index handle (0 for all); optional.

<!-- -->

indexId  
The index handle (0 for all); optional.

### Return Value - indexCreate

0 if the method succeeds.

### Remarks - indexCreate

This method can be used to re-create indexes. Use 0 for the parameters to indicate all tables or indexes.

### Examples - indexCreate

```xpp
{ 
    SqlDataDictionary DD = new SqlDataDictionary(); 
    DD.indexCreate(TableName2Id("Address")); 
}
```

## Method indexCreateDDL

Generates and returns the SQL statements needed to create the indexes of a table.

```xpp
public str indexCreateDDL(TableId tableId)
```

### Parameters - indexCreateDDL

tableId  
The table handle that the index should be created for.

### Return Value - indexCreateDDL

Returns SQL statements to create the indexes of the  table.

## Method indexDrop

Drops the indexes of a table in the SQL database.

```xpp
public int indexDrop([TableId tableId], [IndexId indexId], [boolean onlyNonUnique])
```

### Parameters - indexDrop

tableId  

<!-- -->

indexId  

<!-- -->

onlyNonUnique  

### Return Value - indexDrop

Zero if the method succeeds.

### Remarks - indexDrop

Use 0 for the parameters to indicate all tables or indexes.

### Examples - indexDrop

```xpp
{ 
    SqlDataDictionary DD = new SqlDataDictionary(); 
    DD.indexDrop(TableName2Id("Address")); 
}
```

## Method name

Translates any object name into a valid SQL database object-name; that is, valid for the database currently connected.

```xpp
public str name(str bmsname, [FieldId fieldId], [int arrayindex])
```

### Parameters - name

bmsname  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

<!-- -->

fieldId  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

<!-- -->

arrayindex  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

### Return Value - name

The valid object name.

### Remarks - name

Because names may be truncated, a unique object identifier may be supplied. Also, a third parameter enables the method to return discrete SQL field names for  array fields.

## Method tableCreate

Creates one or more  tables in the SQL database. Also, provides an option to create for index.

```xpp
public int tableCreate([boolean indexes], [TableId tableId])
```

### Parameters - tableCreate

indexes  
The table handle (0 for all); optional.

<!-- -->

tableId  
The table handle (0 for all); optional.

### Return Value - tableCreate

Zero if the method succeeds.

### Remarks - tableCreate

Used for low-level maintenance only.

### Examples - tableCreate

```xpp
{ 
    SqlDataDictionary DD = new SqlDataDictionary(); 
    DD.tableCreate(TableName2Id("Address")); 
}
```

## Method tableCreateDDL

Generates and returns the SQL statement to create a table.

```xpp
public str tableCreateDDL(TableId tableId)
```

### Parameters - tableCreateDDL

tableId  
The table handle of the table to be created.

### Return Value - tableCreateDDL

The SQL statement to create a table.

## Method tableDrop

Drops the  table in the SQL database.

```xpp
public int tableDrop(TableId tableId, [boolean prompt_before_drop])
```

### Parameters - tableDrop

tableId  
A boolean flag that determines whether to ask user before dropping the table; optional. By default, true.

<!-- -->

prompt\_before\_drop  
A boolean flag that determines whether to ask user before dropping the table; optional. By default, true.

### Return Value - tableDrop

Zero if the method succeeds.

## Method tableDropDDL

Generates and returns the SQL statement to drop a table.

```xpp
public str tableDropDDL(TableId tableId)
```

### Parameters - tableDropDDL

tableId  
The table to be dropped.

### Return Value - tableDropDDL

The SQL statement that drops the specified  table.

## Method tableEmpty

Returns true if table is not empty; otherwise false.

```xpp
public boolean tableEmpty(TableId tableId, [str company], [boolean not_this_company])
```

### Parameters - tableEmpty

tableId  
If true excludes records that belongs to the company from the query; optional. By default, false.

<!-- -->

company  
If true excludes records that belongs to the company from the query; optional. By default, false.

<!-- -->

not\_this\_company  
If true excludes records that belongs to the company from the query; optional. By default, false.

### Return Value - tableEmpty

true if the table empty; otherwise, false.

## Method tableExist

Returns true if table exists; otherwise false.

```xpp
public boolean tableExist(str sqltablename, [boolean use_within_transaction])
```

### Parameters - tableExist

sqltablename  
A boolean flag that determines whether transactions are to be used; optional. By default, false.

<!-- -->

use\_within\_transaction  
A boolean flag that determines whether transactions are to be used; optional. By default, false.

### Return Value - tableExist

true if the table exists; otherwise, false.

## Method tableMetaData

Fills the SqlDescribe table with data dictionary meta data.

```xpp
public int tableMetaData(TableId tableId)
```

### Parameters - tableMetaData

tableId  
The table handle.

### Return Value - tableMetaData

true if the method succeeds.

## Method tableReindex

Updates index for the table.

```xpp
public int tableReindex([TableId tableId], [IndexId indexId])
```

### Parameters - tableReindex

tableId  
The index handle (0 for all); optional. By default, 0.

<!-- -->

indexId  
The index handle (0 for all); optional. By default, 0.

### Return Value - tableReindex

Zero if the method succeeds.

## Method tableSynchronize

Synchronizes the  table and the table of the SQL database.

```xpp
public int tableSynchronize(TableId tableId, [boolean update_dict_info_only], [boolean check_indexes])
```

### Parameters - tableSynchronize

tableId  
When set forces reindex of the table indexes; optional. By default, true.

<!-- -->

update\_dict\_info\_only  
When set forces reindex of the table indexes; optional. By default, true.

<!-- -->

check\_indexes  
When set forces reindex of the table indexes; optional. By default, true.

### Return Value - tableSynchronize

true if the method succeeds.

## Method tableTruncate

Truncates the  table.

```xpp
public int tableTruncate(TableId tableId, [boolean prompt_before_truncate], [boolean truncate_system_table])
```

### Parameters - tableTruncate

tableId  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

<!-- -->

prompt\_before\_truncate  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

<!-- -->

truncate\_system\_table  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

### Return Value - tableTruncate

Zero if the method succeeds.

## Method tableTruncateDDL

Generates and returns a SQL statement to truncate a table.

```xpp
public str tableTruncateDDL(TableId tableId)
```

### Parameters - tableTruncateDDL

tableId  
The table handle of the table to be truncated.

### Return Value - tableTruncateDDL

The SQL statement to truncate the table.

## Method synchronize

Synchronizes the  data dictionary and the data dictionary of the SQL database.

```xpp
public static int synchronize([boolean synchronize_all])
```

### Parameters - synchronize

synchronize\_all  
A boolean flag that determines whether to synchronize all tables; optional. If true, this method synchronizes all tables (instead of only those marked dirty by the  kernel). By default, false.

### Return Value - synchronize

true if synchronization was successful; otherwise false.

## Method new

Initializes a new instance of the SqlDataDictionary class.

```xpp
public void new()
```

## Method tableDelete

Deletes the  table in the SQL database.

```xpp
public void tableDelete(TableId tableId)
```

### Parameters - tableDelete

tableId  

