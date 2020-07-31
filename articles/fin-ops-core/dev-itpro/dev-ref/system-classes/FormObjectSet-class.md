---
title: FormObjectSet class
description: This topic describes the FormObjectSet class.
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

# Class FormObjectSet

[!include [banner](../../includes/banner.md)]

```xpp
class FormObjectSet extends Object
```

The FormObjectSet class is a base class that provides basic functionality for working with the data sources for a form.

## Remarks

Most of the methods on the FormObjectSet class are empty. They are implemented in the FormDataSource derived class.

## Examples

## Methods

| Method                                                             | Description                                                                                                                                                                                                                 |
|--------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int active()                                                | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.active method, which retrieves data from joined data sources when a user navigates to a new record.                                 |
| public Common cursor()                                             | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.cursor method, which returns the currently active record in the table that is referenced by the data source.                        |
| public boolean findRecord(Common record)                           | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.findRecord method, which finds a specified record in the data source and makes it the current one.                                  |
| public boolean positionToRecord(Common record)                     |                                                                                                                                                                                                                             |
| public int first()                                                 | Moves focus to the first record in a data source.                                                                                                                                                                           |
| public xFormRun formRun()                                          |                                                                                                                                                                                                                             |
| public int getPosition()                                           |                                                                                                                                                                                                                             |
| public int id()                                                    |                                                                                                                                                                                                                             |
| public int last()                                                  | Moves focus to the last record in the data source.                                                                                                                                                                          |
| public boolean leaveRecord(\[boolean forceUpdate\])                | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.leaveRecord method, which provides a notification when the user moves to another record.                                            |
| public FormObjectSet masterObjectSet()                             | Retrieves the master object set for the current object set.                                                                                                                                                                 |
| public str name(\[str value\])                                     | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                                                                                     |
| public int next()                                                  | Moves focus to the next record in the data source.                                                                                                                                                                          |
| public int nextPage(int pageSize)                                  | Moves a specified number of records forward in the data source.                                                                                                                                                             |
| public FormDataObject object(int objectId)                         |                                                                                                                                                                                                                             |
| public int prev()                                                  | Moves focus to the previous record in the data source.                                                                                                                                                                      |
| public int prevPage(int pageSize)                                  | Moves a specified number of records back (a positional change) in the data source.                                                                                                                                          |
| public boolean setPosition(int position)                           |                                                                                                                                                                                                                             |
| public boolean validateDelete()                                    | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateDelete method, which prompts the user to confirm the deletion of a record from the data source.                             |
| public boolean validateWrite()                                     | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateWrite method, which determines whether data is valid and ready to be written.                                               |
| public void refresh()                                              | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refresh method, which updates the view of all records in the data source.                                                           |
| public void addNotifyHandler(FormObjectSetNotify notifyHandler)    |                                                                                                                                                                                                                             |
| public void reread()                                               | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.reread method, which rereads the current record from the database.                                                                  |
| public void init()                                                 | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.init method, which creates a data source query, based on the data source properties.                                                |
| public void deleteMarked()                                         | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.deleteMarked method, which deletes all marked records from a data source.                                                           |
| public void delete()                                               | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.delete method, which deletes the record that is currently selected from the data source.                                            |
| public void write()                                                | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.write method, which manages the database write operation.                                                                           |
| public void create(\[boolean append\])                             | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.create method, which creates a new record in the data source.                                                                       |
| public void removeNotifyHandler(FormObjectSetNotify notifyHandler) |                                                                                                                                                                                                                             |
| public void prompt()                                               | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.prompt method, which activates the SysQueryForm class that is used to limit a query range.                                          |
| public void research(\[boolean retainPosition\])                   | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.research method, which updates the database search that is defined by the filters and sorts that are currently applied to the form. |
| public void refreshEx(\[AnyType pos\])                             | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refreshEx method, which updates the view of the specified record.                                                                   |
| public void initValue()                                            | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.initValue method, which initializes field values in a new record.                                                                   |
| public void removeFilter()                                         | Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.removeFilter method, which resets the query for the data source.                                                                    |

## Method active

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.active method, which retrieves data from joined data sources when a user navigates to a new record.

```xpp
public int active()
```

### Return Value - active

Always returns 1.

## Method cursor

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.cursor method, which returns the currently active record in the table that is referenced by the data source.

```xpp
public Common cursor()
```

### Return Value - cursor

## Method findRecord

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.findRecord method, which finds a specified record in the data source and makes it the current one.

```xpp
public boolean findRecord(Common record)
```

### Parameters - findRecord

record  
A parameter that is not used in the FormObjectSet base class.

### Return Value - findRecord

true if the record was found; otherwise, false.

## Method positionToRecord

```xpp
public boolean positionToRecord(Common record)
```

### Parameters - positionToRecord

record  

### Return Value - positionToRecord

## Method first

Moves focus to the first record in a data source.

```xpp
public int first()
```

### Return Value - first

A non-zero integer if the operation succeeds.

### Remarks - first

This method is overridden by the method that is called when a user presses CTRL+HOME to select the first record in a form.

## Method formRun

```xpp
public xFormRun formRun()
```

### Return Value - formRun

## Method getPosition

```xpp
public int getPosition()
```

### Return Value - getPosition

## Method id

```xpp
public int id()
```

### Return Value - id

## Method last

Moves focus to the last record in the data source.

```xpp
public int last()
```

### Return Value - last

A non-zero integer if the operation succeeds.

### Remarks - last

This method is overridden by the method that is called when a user presses CTRL+END to select the last record in a form.

## Method leaveRecord

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.leaveRecord method, which provides a notification when the user moves to another record.

```xpp
public boolean leaveRecord([boolean forceUpdate])
```

### Parameters - leaveRecord

forceUpdate  

### Return Value - leaveRecord

## Method masterObjectSet

Retrieves the master object set for the current object set.

```xpp
public FormObjectSet masterObjectSet()
```

### Return Value - masterObjectSet

The master object set.

### Remarks - masterObjectSet

A form often has more than one object set (data source). These are joined together by using a tree hierarchy, where one data source is the master or parent data source. The masterObjectSet method returns the ID of the master data source for a specific data source.

### Examples - masterObjectSet

The following example returns the name of the master data source for a FormRun object.

```xpp
private static client Name formDataSourceName(FormRun _formRun) 
{ 
    return _formRun.objectSet().masterObjectSet().name(); 
}
```

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name to assign to the control.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

## Method next

Moves focus to the next record in the data source.

```xpp
public int next()
```

### Return Value - next

A non-zero integer if the operation succeeds.

### Remarks - next

This method is called when a user selects the next record in a form by pressing the DOWN ARROW key.

## Method nextPage

Moves a specified number of records forward in the data source.

```xpp
public int nextPage(int pageSize)
```

### Parameters - nextPage

pageSize  
The number of records to skip.

### Return Value - nextPage

A non-zero integer if the operation succeeds.

### Remarks - nextPage

This method is called when a user presses the PAGE DOWN key while he or she is in a form. The page size is then automatically calculated and used for the pageSize parameter. This method is overridden on the FormDataSource class.

## Method object

```xpp
public FormDataObject object(int objectId)
```

### Parameters - object

objectId  

### Return Value - object

## Method prev

Moves focus to the previous record in the data source.

```xpp
public int prev()
```

### Return Value - prev

A non-zero integer if the operation succeeds.

### Remarks - prev

This method is called when a user selects the previous record in the form.

## Method prevPage

Moves a specified number of records back (a positional change) in the data source.

```xpp
public int prevPage(int pageSize)
```

### Parameters - prevPage

pageSize  
The number of records to move back (a positional change).

### Return Value - prevPage

A non-zero integer if the operation succeeds.

### Remarks - prevPage

This method is called when a user presses the PAGE UP key while he or she is in a form. The page size is then calculated automatically and used for the pageSize parameter.

## Method setPosition

```xpp
public boolean setPosition(int position)
```

### Parameters - setPosition

position  

### Return Value - setPosition

## Method validateDelete

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateDelete method, which prompts the user to confirm the deletion of a record from the data source.

```xpp
public boolean validateDelete()
```

### Return Value - validateDelete

## Method validateWrite

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateWrite method, which determines whether data is valid and ready to be written.

```xpp
public boolean validateWrite()
```

### Return Value - validateWrite

## Method refresh

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refresh method, which updates the view of all records in the data source.

```xpp
public void refresh()
```

## Method addNotifyHandler

```xpp
public void addNotifyHandler(FormObjectSetNotify notifyHandler)
```

### Parameters - addNotifyHandler

notifyHandler  

## Method reread

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.reread method, which rereads the current record from the database.

```xpp
public void reread()
```

## Method init

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.init method, which creates a data source query, based on the data source properties.

```xpp
public void init()
```

## Method deleteMarked

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.deleteMarked method, which deletes all marked records from a data source.

```xpp
public void deleteMarked()
```

## Method delete

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.delete method, which deletes the record that is currently selected from the data source.

```xpp
public void delete()
```

## Method write

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.write method, which manages the database write operation.

```xpp
public void write()
```

## Method create

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.create method, which creates a new record in the data source.

```xpp
public void create([boolean append])
```

### Parameters - create

append  
A Boolean flag that indicates whether to insert the record after or before the current cursor position; optional. If the value is true, the new record is inserted after the current one.

## Method removeNotifyHandler

```xpp
public void removeNotifyHandler(FormObjectSetNotify notifyHandler)
```

### Parameters - removeNotifyHandler

notifyHandler  

## Method prompt

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.prompt method, which activates the SysQueryForm class that is used to limit a query range.

```xpp
public void prompt()
```

## Method research

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.research method, which updates the database search that is defined by the filters and sorts that are currently applied to the form.

```xpp
public void research([boolean retainPosition])
```

### Parameters - research

retainPosition  

## Method refreshEx

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refreshEx method, which updates the view of the specified record.

```xpp
public void refreshEx([AnyType pos])
```

### Parameters - refreshEx

pos  
A parameter that is not used in the FormObjectSet.refreshEx method; optional.

## Method initValue

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.initValue method, which initializes field values in a new record.

```xpp
public void initValue()
```

## Method removeFilter

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.removeFilter method, which resets the query for the data source.

```xpp
public void removeFilter()
```

