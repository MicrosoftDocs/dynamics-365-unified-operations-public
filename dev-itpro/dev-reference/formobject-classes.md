---
# required metadata

title: F Classes - FormObject to FormRealControl
description: API reference for classes from FormObject to FormRealControl.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 23 - 03 - 53
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# ms.search.form: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.search.scope: AX 7.0.0, Operations
# ms.tgt_pltfrm: 
ms.custom: 63603
ms.assetid: 170eb939-154e-488e-84a8-f67dd9d9a8f6
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FormObject to FormRealControl

API reference for classes from FormObject to FormRealControl.

Class FormObject
----------------

    class FormObject extends Object

### Remarks

### Examples

### Methods

| Method                                        | Description                             |
|-----------------------------------------------|-----------------------------------------|
| public boolean getAllowEdit(\[int rowIndex\]) |                                         |
| public AnyType getValue(\[int rowIndex\])     |                                         |
| public boolean getVisible()                   |                                         |
| public str helpField()                        | Returns the Help text for the control.  |
| public str labelText()                        | Returns the label text for the control. |
| public boolean setValue(AnyType value)        |                                         |
| public str toolTip()                          |                                         |
| public boolean validate()                     |                                         |
| public void jumpRef()                         |                                         |
| public void modified()                        |                                         |
| public void restore()                         |                                         |
| public void find()                            |                                         |
| public void context()                         |                                         |

### Method getAllowEdit

    public boolean getAllowEdit([int rowIndex])

#### Parameters

rowIndex  

#### Return Value

### Method getValue

    public AnyType getValue([int rowIndex])

#### Parameters

rowIndex  

#### Return Value

### Method getVisible

    public boolean getVisible()

#### Return Value

### Method helpField

Returns the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text.

#### Examples

The following example shows how to use the helpField method.

    str strHelp;
    strHelp = this.helpField();

### Method labelText

Returns the label text for the control.

    public str labelText()

#### Return Value

The label text for the control; an empty string if there is no label text for the control.

### Method setValue

    public boolean setValue(AnyType value)

#### Parameters

value  

#### Return Value

### Method toolTip

    public str toolTip()

#### Return Value

### Method validate

    public boolean validate()

#### Return Value

### Method jumpRef

    public void jumpRef()

### Method modified

    public void modified()

### Method restore

    public void restore()

### Method find

    public void find()

### Method context

    public void context()

## Class FormObjectSet
    class FormObjectSet extends Object

The FormObjectSet class is a base class that provides basic functionality for working with the data sources for a form.

### Remarks

Most of the methods on the FormObjectSet class are empty. They are implemented in the FormDataSource derived class.

### Examples

### Methods

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
| public str name(\[str value\])                                     | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                                                                     |
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

### Method active

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.active method, which retrieves data from joined data sources when a user navigates to a new record.

    public int active()

#### Return Value

Always returns 1.

### Method cursor

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.cursor method, which returns the currently active record in the table that is referenced by the data source.

    public Common cursor()

#### Return Value

### Method findRecord

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.findRecord method, which finds a specified record in the data source and makes it the current one.

    public boolean findRecord(Common record)

#### Parameters

record  
A parameter that is not used in the FormObjectSet base class.

#### Return Value

true if the record was found; otherwise, false.

### Method positionToRecord

    public boolean positionToRecord(Common record)

#### Parameters

record  

#### Return Value

### Method first

Moves focus to the first record in a data source.

    public int first()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is overridden by the method that is called when a user presses CTRL+HOME to select the first record in a form.

### Method formRun

    public xFormRun formRun()

#### Return Value

### Method getPosition

    public int getPosition()

#### Return Value

### Method id

    public int id()

#### Return Value

### Method last

Moves focus to the last record in the data source.

    public int last()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is overridden by the method that is called when a user presses CTRL+END to select the last record in a form.

### Method leaveRecord

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.leaveRecord method, which provides a notification when the user moves to another record.

    public boolean leaveRecord([boolean forceUpdate])

#### Parameters

forceUpdate  

#### Return Value

### Method masterObjectSet

Retrieves the master object set for the current object set.

    public FormObjectSet masterObjectSet()

#### Return Value

The master object set.

#### Remarks

A form often has more than one object set (data source). These are joined together by using a tree hierarchy, where one data source is the master or parent data source. The masterObjectSet method returns the ID of the master data source for a specific data source.

#### Examples

The following example returns the name of the master data source for a FormRun object.

    private static client Name formDataSourceName(FormRun _formRun) 
    { 
        return _formRun.objectSet().masterObjectSet().name(); 
    }

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method next

Moves focus to the next record in the data source.

    public int next()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is called when a user selects the next record in a form by pressing the DOWN ARROW key.

### Method nextPage

Moves a specified number of records forward in the data source.

    public int nextPage(int pageSize)

#### Parameters

pageSize  
The number of records to skip.

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is called when a user presses the PAGE DOWN key while he or she is in a form. The page size is then automatically calculated and used for the pageSize parameter. This method is overridden on the FormDataSource class.

### Method object

    public FormDataObject object(int objectId)

#### Parameters

objectId  

#### Return Value

### Method prev

Moves focus to the previous record in the data source.

    public int prev()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is called when a user selects the previous record in the form.

### Method prevPage

Moves a specified number of records back (a positional change) in the data source.

    public int prevPage(int pageSize)

#### Parameters

pageSize  
The number of records to move back (a positional change).

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method is called when a user presses the PAGE UP key while he or she is in a form. The page size is then calculated automatically and used for the pageSize parameter.

### Method setPosition

    public boolean setPosition(int position)

#### Parameters

position  

#### Return Value

### Method validateDelete

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateDelete method, which prompts the user to confirm the deletion of a record from the data source.

    public boolean validateDelete()

#### Return Value

### Method validateWrite

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.validateWrite method, which determines whether data is valid and ready to be written.

    public boolean validateWrite()

#### Return Value

### Method refresh

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refresh method, which updates the view of all records in the data source.

    public void refresh()

### Method addNotifyHandler

    public void addNotifyHandler(FormObjectSetNotify notifyHandler)

#### Parameters

notifyHandler  

### Method reread

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.reread method, which rereads the current record from the database.

    public void reread()

### Method init

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.init method, which creates a data source query, based on the data source properties.

    public void init()

### Method deleteMarked

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.deleteMarked method, which deletes all marked records from a data source.

    public void deleteMarked()

### Method delete

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.delete method, which deletes the record that is currently selected from the data source.

    public void delete()

### Method write

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.write method, which manages the database write operation.

    public void write()

### Method create

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.create method, which creates a new record in the data source.

    public void create([boolean append])

#### Parameters

append  
A Boolean flag that indicates whether to insert the record after or before the current cursor position; optional. If the value is true, the new record is inserted after the current one.

### Method removeNotifyHandler

    public void removeNotifyHandler(FormObjectSetNotify notifyHandler)

#### Parameters

notifyHandler  

### Method prompt

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.prompt method, which activates the SysQueryForm class that is used to limit a query range.

    public void prompt()

### Method research

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.research method, which updates the database search that is defined by the filters and sorts that are currently applied to the form.

    public void research([boolean retainPosition])

#### Parameters

retainPosition  

### Method refreshEx

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.refreshEx method, which updates the view of the specified record.

    public void refreshEx([AnyType pos])

#### Parameters

pos  
A parameter that is not used in the FormObjectSet.refreshEx method; optional.

### Method initValue

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.initValue method, which initializes field values in a new record.

    public void initValue()

### Method removeFilter

Has no functionality in the FormObjectSet class but is overridden by the FormDataSource.removeFilter method, which resets the query for the data source.

    public void removeFilter()

## Class FormObjectSetCacheChangedEventArgs
    class FormObjectSetCacheChangedEventArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                                                 | Description                                               |
|--------------------------------------------------------|-----------------------------------------------------------|
| public NotifyCacheChangeType cacheChangeType()         |                                                           |
| public void finalize()                                 |                                                           |
| public void new(NotifyCacheChangeType cacheChangeType) | Initializes a new instance of the ManagedEventArgs class. |

### Method cacheChangeType

    public NotifyCacheChangeType cacheChangeType()

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new(NotifyCacheChangeType cacheChangeType)

#### Parameters

cacheChangeType  

## Class FormObjectSetCurrentChangedEventArgs
    class FormObjectSetCurrentChangedEventArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                        | Description                                               |
|-------------------------------|-----------------------------------------------------------|
| public int position()         |                                                           |
| public void new(int position) | Initializes a new instance of the ManagedEventArgs class. |
| public void finalize()        |                                                           |

### Method position

    public int position()

#### Return Value

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new(int position)

#### Parameters

position  

### Method finalize

    public void finalize()

## Class FormObjectSetLeaveEventArgs
    class FormObjectSetLeaveEventArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                    | Description                                                          |
|---------------------------|----------------------------------------------------------------------|
| public void finalize()    |                                                                      |
| public void new()         | Initializes a new instance of the FormObjectSetLeaveEventArgs class. |
| public void cancelLeave() |                                                                      |

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the FormObjectSetLeaveEventArgs class.

    public void new()

### Method cancelLeave

    public void cancelLeave()

## Class FormObjectSetMarkingChangedEventArgs
    class FormObjectSetMarkingChangedEventArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                     | Description                                               |
|----------------------------|-----------------------------------------------------------|
| public Array ids()         |                                                           |
| public void finalize()     |                                                           |
| public void new(Array ids) | Initializes a new instance of the ManagedEventArgs class. |

### Method ids

    public Array ids()

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new(Array ids)

#### Parameters

ids  

## Class FormObjectSetNotify
    class FormObjectSetNotify extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                               | Description                                                  |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------|
| public boolean onLeave(FormObjectSet sender)                                                                                                                                         |                                                              |
| public int onRequestCacheSize(FormObjectSet sender)                                                                                                                                  |                                                              |
| public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)                                                                                              |                                                              |
| public void new()                                                                                                                                                                    | Initializes a new instance of the FormObjectSetNotify class. |
| public void onCurrentChanged(FormObjectSet sender, int position)                                                                                                                     |                                                              |
| public void onActive(FormObjectSet sender)                                                                                                                                           |                                                              |
| public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)                                                                  |                                                              |
| public void finalize()                                                                                                                                                               |                                                              |
| public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType) |                                                              |
| public void onRefresh(FormObjectSet sender)                                                                                                                                          |                                                              |
| public void onMarkingChanged(FormObjectSet sender, Array ids)                                                                                                                        |                                                              |

### Method onLeave

    public boolean onLeave(FormObjectSet sender)

#### Parameters

sender  

#### Return Value

### Method onRequestCacheSize

    public int onRequestCacheSize(FormObjectSet sender)

#### Parameters

sender  

#### Return Value

### Method onCacheChanged

    public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)

#### Parameters

sender  

<!-- -->

cacheChangeType  

### Method new

Initializes a new instance of the FormObjectSetNotify class.

    public void new()

### Method onCurrentChanged

    public void onCurrentChanged(FormObjectSet sender, int position)

#### Parameters

sender  

<!-- -->

position  

### Method onActive

    public void onActive(FormObjectSet sender)

#### Parameters

sender  

### Method onPagingParametersChanged

    public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)

#### Parameters

sender  

<!-- -->

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

### Method finalize

    public void finalize()

### Method onRuntimeMetadataChanged

    public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType)

#### Parameters

sender  

<!-- -->

changedDatasourceName  

<!-- -->

referencedDatasourceName  

<!-- -->

changedFieldId  

<!-- -->

changeType  

### Method onRefresh

    public void onRefresh(FormObjectSet sender)

#### Parameters

sender  

### Method onMarkingChanged

    public void onMarkingChanged(FormObjectSet sender, Array ids)

#### Parameters

sender  

<!-- -->

ids  

## Class FormObjectSetNotifyEvents
    class FormObjectSetNotifyEvents extends FormObjectSetNotify

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                               | Description                                                        |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------|
| public boolean onLeave(FormObjectSet sender)                                                                                                                                         |                                                                    |
| public int onRequestCacheSize(FormObjectSet sender)                                                                                                                                  |                                                                    |
| public void new()                                                                                                                                                                    | Initializes a new instance of the FormObjectSetNotifyEvents class. |
| public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType) |                                                                    |
| public void onRefresh(FormObjectSet sender)                                                                                                                                          |                                                                    |
| public void finalize()                                                                                                                                                               |                                                                    |
| public void addEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)                                                                                   |                                                                    |
| public void onCurrentChanged(FormObjectSet sender, int position)                                                                                                                     |                                                                    |
| public void removeEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)                                                                                |                                                                    |
| public void onMarkingChanged(FormObjectSet sender, Array ids)                                                                                                                        |                                                                    |
| public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)                                                                  |                                                                    |
| public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)                                                                                              |                                                                    |
| public void onActive(FormObjectSet sender)                                                                                                                                           |                                                                    |

### Method onLeave

    public boolean onLeave(FormObjectSet sender)

#### Parameters

sender  

#### Return Value

### Method onRequestCacheSize

    public int onRequestCacheSize(FormObjectSet sender)

#### Parameters

sender  

#### Return Value

### Method new

Initializes a new instance of the FormObjectSetNotifyEvents class.

    public void new()

### Method onRuntimeMetadataChanged

    public void onRuntimeMetadataChanged(FormObjectSet sender, str changedDatasourceName, str referencedDatasourceName, FieldId changedFieldId, DataSourceMetadataChangeType changeType)

#### Parameters

sender  

<!-- -->

changedDatasourceName  

<!-- -->

referencedDatasourceName  

<!-- -->

changedFieldId  

<!-- -->

changeType  

### Method onRefresh

    public void onRefresh(FormObjectSet sender)

#### Parameters

sender  

### Method finalize

    public void finalize()

### Method addEventDelegate

    public void addEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)

#### Parameters

eventType  

<!-- -->

eventDelegate  

### Method onCurrentChanged

    public void onCurrentChanged(FormObjectSet sender, int position)

#### Parameters

sender  

<!-- -->

position  

### Method removeEventDelegate

    public void removeEventDelegate(FormObjectSetEventType eventType, ManagedEventDelegate eventDelegate)

#### Parameters

eventType  

<!-- -->

eventDelegate  

### Method onMarkingChanged

    public void onMarkingChanged(FormObjectSet sender, Array ids)

#### Parameters

sender  

<!-- -->

ids  

### Method onPagingParametersChanged

    public void onPagingParametersChanged(FormObjectSet sender, boolean pagingEnabled, int startRowIndex, int pageSize)

#### Parameters

sender  

<!-- -->

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

### Method onCacheChanged

    public void onCacheChanged(FormObjectSet sender, NotifyCacheChangeType cacheChangeType)

#### Parameters

sender  

<!-- -->

cacheChangeType  

### Method onActive

    public void onActive(FormObjectSet sender)

#### Parameters

sender  

## Class FormObjectSetPagingParamsChangedEvtArgs
    class FormObjectSetPagingParamsChangedEvtArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                                                                  | Description                                               |
|-------------------------------------------------------------------------|-----------------------------------------------------------|
| public int pageSize()                                                   |                                                           |
| public boolean pagingEnabled()                                          |                                                           |
| public int startRowIndex()                                              |                                                           |
| public void finalize()                                                  |                                                           |
| public void new(boolean pagingEnabled, int startRowIndex, int pageSize) | Initializes a new instance of the ManagedEventArgs class. |

### Method pageSize

    public int pageSize()

#### Return Value

### Method pagingEnabled

    public boolean pagingEnabled()

#### Return Value

### Method startRowIndex

    public int startRowIndex()

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the ManagedEventArgs class.

    public void new(boolean pagingEnabled, int startRowIndex, int pageSize)

#### Parameters

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

## Class FormObjectSetRequestCacheSizeEventArgs
    class FormObjectSetRequestCacheSizeEventArgs extends ManagedEventArgs

### Remarks

### Examples

### Methods

| Method                                  | Description                                                                     |
|-----------------------------------------|---------------------------------------------------------------------------------|
| public void setCacheSize(int cacheSize) |                                                                                 |
| public void finalize()                  |                                                                                 |
| public void new()                       | Initializes a new instance of the FormObjectSetRequestCacheSizeEventArgs class. |

### Method setCacheSize

    public void setCacheSize(int cacheSize)

#### Parameters

cacheSize  

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the FormObjectSetRequestCacheSizeEventArgs class.

    public void new()

## Class FormPart
    class FormPart extends TreeNode

### Remarks

### Examples

### Methods

| Method                                       | Description                                                                                                                               |
|----------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------|
| public str caption(\[str value\])            | Gets or set the caption of the control.                                                                                                   |
| public str form(\[str value\])               |                                                                                                                                           |
| public str managedContentItem(\[str value\]) |                                                                                                                                           |
| public str name(\[str value\])               | Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object. |
| public Guid origin(\[Guid value\])           |                                                                                                                                           |
| public void new()                            | Initializes a new instance of the FormPart class.                                                                                         |

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method form

    public str form([str value])

#### Parameters

value  

#### Return Value

### Method managedContentItem

    public str managedContentItem([str value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or another Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   Begins with a letter.
-   Doesn't exceed 250 characters.
-   Can include numbers and underscore characters.
-   Cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, classes, and so on.

### Method origin

    public Guid origin([Guid value])

#### Parameters

value  

#### Return Value

### Method new

Initializes a new instance of the FormPart class.

    public void new()

## Class FormProgressControl
    class FormProgressControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public int pos(\[int value\])                                                                               |                                                                                                                                                                         |
| public int progressType(\[int value\])                                                                      |                                                                                                                                                                         |
| public int rangeHi(\[int value\])                                                                           |                                                                                                                                                                         |
| public int rangeLo(\[int value\])                                                                           |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int step(\[int value\])                                                                              |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void stepIt()                                                                                        |                                                                                                                                                                         |
| public void deltaPos(int inc)                                                                               |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The new value for the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key to assign to the control; optional.

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method direction

    public int direction([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave, the dragOver, and dragOverEx methods to specify the behavior.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  
An integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer value that indicates how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An integer that specifies the height in pixels; optional.

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to assign as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

This method sets the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Retrieves the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false. For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

### Method leave

    public boolean leave()

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method pos

    public int pos([int value])

#### Parameters

value  

#### Return Value

### Method progressType

    public int progressType([int value])

#### Parameters

value  

#### Return Value

### Method rangeHi

    public int rangeHi([int value])

#### Parameters

value  

#### Return Value

### Method rangeLo

    public int rangeLo([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise false.

### Method step

    public int step([int value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  
An integer that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table:

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method enter

    public void enter()

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method displayControl

Displays the control.

    public void displayControl()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method stepIt

    public void stepIt()

### Method deltaPos

    public void deltaPos(int inc)

#### Parameters

inc  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

## Class FormQueryMiner
    class FormQueryMiner extends Object

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class FormRadioControl
    class FormRadioControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the font weight that is used to display text in the control.                                                                                               |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                                                         |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                         |                                                                                                                                                                         |
| public int bottomMarginValue(\[int value\])                                                                 |                                                                                                                                                                         |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                                                 |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public int columns(\[int value\])                                                                           |                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public int count()                                                                                          |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                                                |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether the object is enabled or disabled.                                                                                                                   |
| public EnumId enumType(\[EnumId value\])                                                                    |                                                                                                                                                                         |
| public EnumId enumTypeValue()                                                                               |                                                                                                                                                                         |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int find(str string)                                                                                 |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font that is used for the control.                                                                                                         |
| public int fontSize(\[int value\])                                                                          | Gets or sets the font size that is used for the control.                                                                                                                |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public int framePosition(\[int value\])                                                                     |                                                                                                                                                                         |
| public int frameType(\[int value\])                                                                         |                                                                                                                                                                         |
| public str getText(int index)                                                                               |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.                                                         |
| public boolean hideFirstEntry(\[boolean value\])                                                            |                                                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Returns the handle to the window that is associated with the control.                                                                                                   |
| public boolean isContainer()                                                                                | Gets a value that indicates whether the control is a container.                                                                                                         |
| public boolean isDisplayed()                                                                                | Returns a value that indicates whether the control is displayed.                                                                                                        |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                    | Sets or returns a value that indicates whether the text in the control is italic.                                                                                       |
| public int item(\[int value\])                                                                              |                                                                                                                                                                         |
| public int items(\[int value\])                                                                             |                                                                                                                                                                         |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                     |                                                                                                                                                                         |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                           |                                                                                                                                                                         |
| public int leftMarginValue(\[int value\])                                                                   |                                                                                                                                                                         |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                    |                                                                                                                                                                         |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                          |                                                                                                                                                                         |
| public int rightMarginValue(\[int value\])                                                                  |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the security key that is associated with the control.                                                                                                   |
| public int selection(\[int value\])                                                                         |                                                                                                                                                                         |
| public int selectionChange()                                                                                |                                                                                                                                                                         |
| public int selectText(str string)                                                                           |                                                                                                                                                                         |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public str text(\[str value\])                                                                              | Sets or returns the text for the control.                                                                                                                               |
| public str toolTip()                                                                                        | Sets or returns the tooltip text for the control.                                                                                                                       |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                                                         |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                            |                                                                                                                                                                         |
| public int topMarginValue(\[int value\])                                                                    |                                                                                                                                                                         |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the value of the underline property for the text in the control.                                                                                        |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void insert(str string, int index)                                                                   |                                                                                                                                                                         |
| private void OnSelectionChanged(\[FormControl sender\], \[FormControlEventArgs e\])                         |                                                                                                                                                                         |
| public void delete(str string)                                                                              |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void endUpdate()                                                                                     |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void add(str string)                                                                                 |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| private void OnSelectionChanging(\[FormControl sender\], \[FormControlEventArgs e\])                        |                                                                                                                                                                         |
| public void beginUpdate()                                                                                   |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void clear()                                                                                         |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The Boolean value to assign as the allowEdit property of the control; optional.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  
The value to assign for the background color of the control; optional.

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  
The value to assign for the background style of the control; optional.

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method bold

Gets or sets the font weight that is used to display text in the control.

    public int bold([int value])

#### Parameters

value  
The value to assign to the bold setting of the control; optional.

#### Return Value

An integer value between 0 (zero) and 9, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 – Use the default font weight.
-   1 – Thin.
-   2 – Extra-light.
-   3 – Light.
-   4 – Normal.
-   5 – Medium.
-   6 – Semibold.
-   7 – Bold.
-   8 – Extra-bold.
-   9 – Heavy.

### Method bottomMargin

    public int bottomMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method bottomMarginMode

    public AutoMode bottomMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method bottomMarginValue

    public int bottomMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method caption

Gets or set the caption of the control.

    public str caption([str value])

#### Parameters

value  

#### Return Value

The string that is used as the caption of the control.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table.

| Value | Description          |
|-------|----------------------|
| 0     | ANSI\_CHARSET        |
| 1     | DEFAULT\_CHARSET     |
| 2     | SYMBOL\_CHARSET      |
| 77    | MAC\_CHARSET         |
| 128   | SHIFTJIS\_CHARSET    |
| 129   | HANGUL\_CHARSET      |
| 134   | GB2312\_CHARSET      |
| 136   | CHINESEBIG5\_CHARSET |
| 161   | GREEK\_CHARSET       |
| 162   | TURKISH\_CHARSET     |
| 163   | VIETNAMESE\_CHARSET  |
| 186   | BALTIC\_CHARSET      |
| 204   | RUSSIAN\_CHARSET     |
| 238   | EASTEUROPE\_CHARSET  |
| 255   | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value | Description    |
|-------|----------------|
| 130   | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value | Description     |
|-------|-----------------|
| 177   | HEBREW\_CHARSET |
| 178   | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value | Description   |
|-------|---------------|
| 222   | THAI\_CHARSET |

The default character set is set to a value that is based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

### Method columns

    public int columns([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Method count

    public int count()

#### Return Value

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method displayLength

    public int displayLength([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayLengthMode

    public AutoMode displayLengthMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayLengthValue

    public int displayLengthValue([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether the object is enabled or disabled.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that determines whether the control is enabled; optional.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property lets you enable or disable controls at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

### Method enumType

    public EnumId enumType([EnumId value])

#### Parameters

value  

#### Return Value

### Method enumTypeValue

    public EnumId enumTypeValue()

#### Return Value

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method find

    public int find(str string)

#### Parameters

string  

#### Return Value

### Method font

Gets or sets the name of the font that is used for the control.

    public str font([str value])

#### Parameters

value  
The value to assign as the font for the control; optional.

#### Return Value

The name of the font, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the font size that is used for the control.

    public int fontSize([int value])

#### Parameters

value  
The value to assign as the font size for the control; optional.

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be 0 (zero).
-   The maximum value for a single byte is 255.

### Method framePosition

    public int framePosition([int value])

#### Parameters

value  

#### Return Value

### Method frameType

    public int frameType([int value])

#### Parameters

value  

#### Return Value

### Method getText

    public str getText(int index)

#### Parameters

index  

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table.

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table.

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text that is displayed at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value to assign as the Help text for the control; optional.

#### Return Value

The string that should be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hideFirstEntry

    public boolean hideFirstEntry([boolean value])

#### Parameters

value  

#### Return Value

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Returns the handle to the window that is associated with the control.

    public int hWnd()

#### Return Value

The handle to the window that is associated with the control.

#### Remarks

The handle to the window can be used with Windows API functions.

### Method isContainer

Gets a value that indicates whether the control is a container.

    public boolean isContainer()

#### Return Value

true if the control is a container; otherwise, false.

### Method isDisplayed

Returns a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter. The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

### Method isValid

    public boolean isValid()

#### Return Value

### Method italic

Sets or returns a value that indicates whether the text in the control is italic.

    public boolean italic([boolean value])

#### Parameters

value  
The value for the control's italic setting; optional.

#### Return Value

true if the text in the control is italic; otherwise, false.

### Method item

    public int item([int value])

#### Parameters

value  

#### Return Value

### Method items

    public int items([int value])

#### Parameters

value  

#### Return Value

### Method leave

    public boolean leave()

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMargin

    public int leftMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method leftMarginMode

    public AutoMode leftMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method leftMarginValue

    public int leftMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method modified

    public boolean modified()

#### Return Value

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method previewPartRef

    public str previewPartRef([str value])

#### Parameters

value  

#### Return Value

### Method rightMargin

    public int rightMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method rightMarginMode

    public AutoMode rightMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method rightMarginValue

    public int rightMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the security key that is associated with the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The security key that is associated with the control; optional.

#### Return Value

The security key that is associated with the control.

### Method selection

    public int selection([int value])

#### Parameters

value  

#### Return Value

### Method selectionChange

    public int selectionChange()

#### Return Value

### Method selectText

    public int selectText(str string)

#### Parameters

string  

#### Return Value

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

#### Return Value

### Method text

Sets or returns the text for the control.

    public str text([str value])

#### Parameters

value  
The text to assign to the control; optional.

#### Return Value

The text for the control; an empty string if there is no text for the control.

### Method toolTip

Sets or returns the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if there is no tooltip text for the control.

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMargin

    public int topMargin([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method topMarginMode

    public AutoMode topMarginMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method topMarginValue

    public int topMarginValue([int value])

#### Parameters

value  

#### Return Value

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

Sets or returns the value of the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value of the underline property for the control; optional.

#### Return Value

true if the text in the control is underlined; otherwise, false.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method validate

    public boolean validate()

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method insert

    public void insert(str string, int index)

#### Parameters

string  

<!-- -->

index  

### Method OnSelectionChanged

    private void OnSelectionChanged([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method delete

    public void delete(str string)

#### Parameters

string  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method jumpRef

    public void jumpRef()

### Method endUpdate

    public void endUpdate()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method displayControl

Displays the control.

    public void displayControl()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method add

    public void add(str string)

#### Parameters

string  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method OnSelectionChanging

    private void OnSelectionChanging([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method beginUpdate

    public void beginUpdate()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method enter

    public void enter()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method clear

    public void clear()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method lookup

    public void lookup()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method undo

    public void undo()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

## Class FormRealControl
    class FormRealControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public int allowNegative(\[int value\])                                                                     |                                                                                                                                                                         |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int autoInsSeparator(\[int value\])                                                                  |                                                                                                                                                                         |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font that is used to output text in the control.                                                                                             |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int charFromPos(int x, int y)                                                                        |                                                                                                                                                                         |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public int dataFieldArrayIndex()                                                                            |                                                                                                                                                                         |
| public FieldName dataFieldName()                                                                            |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source that will be used by the control or the form.                                                                                                |
| public int decimalSeparator(\[int value\])                                                                  |                                                                                                                                                                         |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displaceNegative(\[int value\], \[AutoMode mode\])                                               |                                                                                                                                                                         |
| public AutoMode displaceNegativeMode(\[AutoMode mode\])                                                     |                                                                                                                                                                         |
| public int displaceNegativeValue(\[int value\])                                                             |                                                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both. |
| public int dragDrop(\[int value\])                                                                          | Indicates whether to enable or disable drag-and-drop operations for the control.                                                                                        |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public int formatMST(\[int value\])                                                                         |                                                                                                                                                                         |
| public container getCursorPos()                                                                             |                                                                                                                                                                         |
| public int getFirstVisibleLine()                                                                            |                                                                                                                                                                         |
| public str getLine(int lineNo)                                                                              |                                                                                                                                                                         |
| public int getLineCount()                                                                                   |                                                                                                                                                                         |
| public container getSelection()                                                                             |                                                                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
| public int iMEMode(\[int value\])                                                                           |                                                                                                                                                                         |
| public boolean isContainer()                                                                                |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Returns a value that indicates whether the control allows for the specified level of customization.                                                                     |
| public boolean isValid()                                                                                    |                                                                                                                                                                         |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                         |
| public str label(\[str value\])                                                                             | Gets or sets the label for a control.                                                                                                                                   |
| public int labelAlignment(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelBold(\[int value\])                                                                         |                                                                                                                                                                         |
| public int labelCharacterSet(\[int value\])                                                                 |                                                                                                                                                                         |
| public str labelFont(\[str value\])                                                                         |                                                                                                                                                                         |
| public int labelFontSize(\[int value\])                                                                     |                                                                                                                                                                         |
| public int labelForegroundColor(\[int value\])                                                              |                                                                                                                                                                         |
| public int labelGuide(\[int value\])                                                                        |                                                                                                                                                                         |
| public int labelHeight(int value, \[int mode\])                                                             |                                                                                                                                                                         |
| public int labelHeightMode(\[int value\])                                                                   |                                                                                                                                                                         |
| public int labelHeightValue(\[int value\])                                                                  |                                                                                                                                                                         |
| public boolean labelItalic(\[boolean value\])                                                               |                                                                                                                                                                         |
| public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                        |                                                                                                                                                                         |
| public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                            |                                                                                                                                                                         |
| public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                              |                                                                                                                                                                         |
| public int labelPosition(\[int value\])                                                                     |                                                                                                                                                                         |
| public boolean labelUnderline(\[boolean value\])                                                            |                                                                                                                                                                         |
| public int labelWidth(int value, \[int mode\])                                                              |                                                                                                                                                                         |
| public int labelWidthMode(\[int value\])                                                                    |                                                                                                                                                                         |
| public int labelWidthValue(\[int value\])                                                                   |                                                                                                                                                                         |
| public boolean leave()                                                                                      |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int limitText(\[int value\], \[AutoMode mode\])                                                      |                                                                                                                                                                         |
| public AutoMode limitTextMode(\[AutoMode mode\])                                                            |                                                                                                                                                                         |
| public int limitTextValue(\[int value\])                                                                    |                                                                                                                                                                         |
| public int lineFromChar(int charIndex)                                                                      |                                                                                                                                                                         |
| public int lineIndex(int lineNo)                                                                            |                                                                                                                                                                         |
| public int lineLength(int lineNo)                                                                           |                                                                                                                                                                         |
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int minNoOfDecimals(\[int value\], \[AutoMode mode\])                                                |                                                                                                                                                                         |
| public AutoMode minNoOfDecimalsMode(\[AutoMode mode\])                                                      |                                                                                                                                                                         |
| public int minNoOfDecimalsValue(\[int value\])                                                              |                                                                                                                                                                         |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public int noOfDecimals(\[int value\], \[AutoMode mode\])                                                   |                                                                                                                                                                         |
| public AutoMode noOfDecimalsMode(\[AutoMode mode\])                                                         |                                                                                                                                                                         |
| public int noOfDecimalsValue(\[int value\])                                                                 |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public Real realValue(\[Real value\])                                                                       |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int rotateSign(\[int value\])                                                                        |                                                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public int showZero(\[int value\])                                                                          |                                                                                                                                                                         |
| public int signDisplay(\[int value\])                                                                       |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public int thousandSeparator(\[int value\])                                                                 |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userFastTabSummary(\[int value\])                                                                |                                                                                                                                                                         |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels, as specified by the user.                                                                                           |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |

### Method alignControl

Determines whether to align the control.

    public boolean alignControl([boolean value])

#### Parameters

value  

#### Return Value

true if the control should be aligned; otherwise, false.

#### Remarks

The upper-left corner of the control is aligned according to the longest label.

### Method alignment

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

### Method allowNegative

    public int allowNegative([int value])

#### Parameters

value  

#### Return Value

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method arrayIndex

    public int arrayIndex([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoInsSeparator

    public int autoInsSeparator([int value])

#### Parameters

value  

#### Return Value

### Method backgroundColor

Gets or sets the background color of the control.

    public int backgroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method backStyle

Determiness whether the control background can be transparent.

    public int backStyle([int value])

#### Parameters

value  

#### Return Value

1 if the control background can be transparent; otherwise, 0.

### Method beginDrag

Is called when the user starts to drag a form control.

    public int beginDrag(int x, int y)

#### Parameters

x  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer. The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method bold

Gets or sets the weight of font that is used to output text in the control.

    public int bold([int value])

#### Parameters

value  

#### Return Value

An integer value between zero and nine, inclusive.

#### Remarks

The integer that is returned contains the weight of the font as follows:

-   0 Use the default font weight.
-   1 Thin.
-   2 Extra-light.
-   3 Light.
-   4 Normal.
-   5 Medium.
-   6 Semibold.
-   7 Bold.
-   8 Extra-bold.
-   9 Heavy.

### Method border

Gets or sets the style of the borderline of the control.

    public int border([int value])

#### Parameters

value  

#### Return Value

An integer between zero and four, inclusive.

#### Remarks

The integer that is returned contains the style of the borderline of the control as follows.

| Value | Description |
|-------|-------------|
| 0     | Auto        |
| 1     | 3D          |
| 2     | Single line |
| 3     | Flat        |
| 4     | None        |

### Method cacheDataMethod

    public int cacheDataMethod([int value])

#### Parameters

value  

#### Return Value

### Method calcControlSize

Retrieves the size of the control.

    public container calcControlSize(int chars, int lines)

#### Parameters

chars  
The number of lines to use to determine the height.

<!-- -->

lines  
The number of lines to use to determine the height.

#### Return Value

The container that holds the width and height.

### Method characterSet

Gets or sets the character set of the font.

    public int characterSet([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the character set of the font.

#### Remarks

The values for the integer that is returned indicate the character set according to the following table:

| Value | Description          |
|-------|----------------------|
| 0     | ANSI\_CHARSET        |
| 1     | DEFAULT\_CHARSET     |
| 2     | SYMBOL\_CHARSET      |
| 77    | MAC\_CHARSET         |
| 128   | SHIFTJIS\_CHARSET    |
| 129   | HANGUL\_CHARSET      |
| 134   | GB2312\_CHARSET      |
| 136   | CHINESEBIG5\_CHARSET |
| 161   | GREEK\_CHARSET       |
| 162   | TURKISH\_CHARSET     |
| 163   | VIETNAMESE\_CHARSET  |
| 186   | BALTIC\_CHARSET      |
| 204   | RUSSIAN\_CHARSET     |
| 238   | EASTEUROPE\_CHARSET  |
| 255   | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value | Description    |
|-------|----------------|
| 130   | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value | Description     |
|-------|-----------------|
| 177   | HEBREW\_CHARSET |
| 178   | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value | Description   |
|-------|---------------|
| 222   | THAI\_CHARSET |

The default character set is set to a values that are based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method charFromPos

    public int charFromPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

#### Return Value

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table.

| Value | Style                 |
|-------|-----------------------|
| 0     | Default               |
| 1     | The Windows palette   |
| 2     | The true-color scheme |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

The identifier of the configuration key that is assigned to the control.

#### Remarks

The configuration key is used to determine whether this control can be displayed. If the configuration key is disabled in the system, the control is not displayed in the form.

### Method configurationKeyEx

Retrieves a list that contains the IDs of configuration keys that are in effect for the control.

    public List configurationKeyEx()

#### Return Value

A list that contains the IDs of configuration keys that are in effect for the control.

#### Remarks

The returned list does not contain duplicate IDs. If the control is bound to a data source, the returned list of configuration key IDs also includes the configuration key ID for the table and field. The returned list also contains any configuration key IDs that are applied to the properties, extended data type, or enumType methods.

### Method countryRegionCodes

Gets or sets the comma-separated list of country/region codes for the control.

    public str countryRegionCodes([str value])

#### Parameters

value  
The string that contains the country/region codes to set; optional.

#### Return Value

The comma-separated list of country/region codes for the control.

### Method countryRegionContextField

    public FieldId countryRegionContextField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method dataFieldArrayIndex

    public int dataFieldArrayIndex()

#### Return Value

### Method dataFieldName

    public FieldName dataFieldName()

#### Return Value

### Method dataMethod

    public str dataMethod([str value])

#### Parameters

value  

#### Return Value

### Method dataRelationPath

Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.

    public str dataRelationPath([str value])

#### Parameters

value  
The string that contains the period-delimited list of relations; optional.

#### Return Value

The period-delimited list of relations that links the field binding of the DataField object to a relative table.

#### Remarks

This method is used by the reference group control to track exactly which relations produce the replacement field that is used. It enables the reference group control to bind consistently to the controls that it contains.

### Method dataSource

Gets or sets a data source that will be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source that will be used.

### Method decimalSeparator

    public int decimalSeparator([int value])

#### Parameters

value  

#### Return Value

### Method direction

    public int direction([int value])

#### Parameters

value  

#### Return Value

### Method displaceNegative

    public int displaceNegative([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displaceNegativeMode

    public AutoMode displaceNegativeMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displaceNegativeValue

    public int displaceNegativeValue([int value])

#### Parameters

value  

#### Return Value

### Method displayHeight

    public int displayHeight([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayHeightMode

    public AutoMode displayHeightMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayHeightValue

    public int displayHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method displayLength

    public int displayLength([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method displayLengthMode

    public AutoMode displayLengthMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method displayLengthValue

    public int displayLengthValue([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal for Microsoft Dynamics AX, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics AX client, in Enterprise Portal, or in both.

### Method dragDrop

Indicates whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, 0.

### Method dragOver

Raises the dragOver event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragOverEx

Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.

    public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

#### Return Value

A FormDrag enumeration value that indicates the mode of dragging.

### Method dragText

Retrieves the text that is displayed when the form control is dragged.

    public str dragText()

#### Return Value

The text that is displayed when the control is dragged; an empty string if there is no text to display when the control is dragged.

### Method enabled

Determines whether to enable or disable the object.

    public boolean enabled([boolean value])

#### Parameters

value  

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property allows for controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

### Method extendedDataType

    public ExtendedTypeId extendedDataType([ExtendedTypeId value])

#### Parameters

value  

#### Return Value

### Method fastTabSummary

    public int fastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method font

Gets or sets the name of the font for the control to use.

    public str font([str value])

#### Parameters

value  

#### Return Value

The name of the font to use, such as Tahoma or Verdana.

### Method fontSize

Gets or sets the size of the font for the control to use.

    public int fontSize([int value])

#### Parameters

value  

#### Return Value

The height of the font in points.

### Method foregroundColor

Gets or sets the text color for the control to use.

    public int foregroundColor([int value])

#### Parameters

value  

#### Return Value

An integer that contains a packed RGB color.

#### Remarks

The integer that is returned contains a packed RGB color as follows:

-   The low-order byte contains a value for the relative intensity of red.
-   The second byte contains a value for green.
-   The third byte contains a value for blue.
-   The high-order byte must be zero.
-   The maximum value for a single byte is 255.

### Method formatMST

    public int formatMST([int value])

#### Parameters

value  

#### Return Value

### Method getCursorPos

    public container getCursorPos()

#### Return Value

### Method getFirstVisibleLine

    public int getFirstVisibleLine()

#### Return Value

### Method getLine

    public str getLine(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method getLineCount

    public int getLineCount()

#### Return Value

### Method getSelection

    public container getSelection()

#### Return Value

### Method hasChanged

Sets or returns a value that indicates whether the contents of the control have changed.

    public boolean hasChanged([boolean val])

#### Parameters

val  
The value to assign as the hasChanged value for the control; optional.

#### Return Value

true if the contents of the control have changed; otherwise, false.

### Method hasUserSetting

Indicates whether the control has custom user settings.

    public boolean hasUserSetting()

#### Return Value

true if the control has custom user settings; otherwise, false.

### Method height

Gets or sets the height of the control.

    public int height(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the height according to the following table:

| Mode            | Height calculation                                                                        |
|-----------------|-------------------------------------------------------------------------------------------|
| -1 Exact        | The exact height in pixels of the controls is used.                                       |
| 0 Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode          | Height calculation                                                                        |
|---------------|-------------------------------------------------------------------------------------------|
| Exact         | The exact height in pixels of the controls is used.                                       |
| Auto          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  

#### Return Value

The height in pixels.

#### Remarks

The height of the control is not changed unless the exact height calculation mode is used.

### Method helpField

Retrieves the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Remarks

The helpField method cannot be used to set the value of the Help text. Use the helpText method to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property dialog box. The Help text must not exceed 250 characters.

### Method hierarchyParent

Gets or sets the HierarchyParent property value of the control.

    public str hierarchyParent([str value])

#### Parameters

value  
The value to assign to the HierarchyParent property of the control.

#### Return Value

The HierarchyParent property value of the control.

### Method hWnd

Retrieves the Windows handle for the control.

    public int hWnd()

#### Return Value

The handle for the control.

#### Remarks

The handle can be used with the Windows API.

### Method iMEMode

    public int iMEMode([int value])

#### Parameters

value  

#### Return Value

### Method isContainer

    public boolean isContainer()

#### Return Value

### Method isDisplayed

Retrieves a value that indicates whether the control is displayed.

    public boolean isDisplayed()

#### Return Value

true if the control is displayed; otherwise, false.

#### Remarks

To modify the visible state of the control, call the visible method.

### Method isRestricted

Retrieves a value that indicates whether the control is restricted.

    public boolean isRestricted()

#### Return Value

true if the control is restricted; otherwise, false.

### Method isUserSetupEnabled

Returns a value that indicates whether the control allows for the specified level of customization.

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that is specified by the neededSetupRights parameter; otherwise, false.

#### Remarks

The following table describes the values for the neededSetupRights parameter.

|                                  |                                                                                                                                  |
|----------------------------------|----------------------------------------------------------------------------------------------------------------------------------|
| FormAllowUserSetup::No 0         | No changes can be made to the control. If this value is set for the neededSetupRights parameter, the method always returns true. |
| FormAllowUserSetup::Restricted 1 | The user can change the editable, visible, skip, label, and width properties of the control. The user cannot move the control.   |
| FormAllowUserSetup::Yes 2        | The user can change the editable, visible, skip, label, and width properties of the control. The user can also move the control. |

For this method to return true, the AllowUserSetup property for the design and all parent containers must allow for the level of access that is specified by the neededSetupRights parameter.

### Method isValid

    public boolean isValid()

#### Return Value

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method label

Gets or sets the label for a control.

    public str label([str value])

#### Parameters

value  

#### Return Value

The current value of the label string.

#### Remarks

The label determines which text is displayed in the control or adjacent to it. The label property value cannot exceed 250 characters.

### Method labelAlignment

    public int labelAlignment([int value])

#### Parameters

value  

#### Return Value

### Method labelBold

    public int labelBold([int value])

#### Parameters

value  

#### Return Value

### Method labelCharacterSet

    public int labelCharacterSet([int value])

#### Parameters

value  

#### Return Value

### Method labelFont

    public str labelFont([str value])

#### Parameters

value  

#### Return Value

### Method labelFontSize

    public int labelFontSize([int value])

#### Parameters

value  

#### Return Value

### Method labelForegroundColor

    public int labelForegroundColor([int value])

#### Parameters

value  

#### Return Value

### Method labelGuide

    public int labelGuide([int value])

#### Parameters

value  

#### Return Value

### Method labelHeight

    public int labelHeight(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelHeightMode

    public int labelHeightMode([int value])

#### Parameters

value  

#### Return Value

### Method labelHeightValue

    public int labelHeightValue([int value])

#### Parameters

value  

#### Return Value

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelMouseDblClick

    public int labelMouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelMouseDown

    public int labelMouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelMouseUp

    public int labelMouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  

<!-- -->

y  

<!-- -->

button  

<!-- -->

Ctrl  

<!-- -->

Shift  

#### Return Value

### Method labelPosition

    public int labelPosition([int value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method labelWidth

    public int labelWidth(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method labelWidthMode

    public int labelWidthMode([int value])

#### Parameters

value  

#### Return Value

### Method labelWidthValue

    public int labelWidthValue([int value])

#### Parameters

value  

#### Return Value

### Method leave

    public boolean leave()

#### Return Value

### Method left

Gets or sets the horizontal position of the control in the form.

    public int left(int value, [int mode])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method leftMode

Sets the horizontal arrange mode for the control in the form.

    public int leftMode([int value])

#### Parameters

value  
An integer value that indicates the horizontal arrange mode for the control; optional.

#### Return Value

The horizontal arrange mode for the control in the form.

### Method leftValue

Gets or sets the horizontal position of the control in the form.

    public int leftValue([int value])

#### Parameters

value  
An integer value that indicates the horizontal position of the control; optional.

#### Return Value

The horizontal position of the control in the form.

### Method limitText

    public int limitText([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method limitTextMode

    public AutoMode limitTextMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method limitTextValue

    public int limitTextValue([int value])

#### Parameters

value  

#### Return Value

### Method lineFromChar

    public int lineFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

### Method lineIndex

    public int lineIndex(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lineLength

    public int lineLength(int lineNo)

#### Parameters

lineNo  

#### Return Value

### Method lookupButton

    public int lookupButton([int value])

#### Parameters

value  

#### Return Value

### Method mandatory

    public boolean mandatory([boolean value])

#### Parameters

value  

#### Return Value

### Method markAsUserAdd

Marks or unmarks the control as a user-added control.

    public boolean markAsUserAdd([boolean value])

#### Parameters

value  
The Boolean value that indicates whether the control should be marked as a user-added control.

#### Return Value

true if the control was marked as a user-added control; otherwise, false.

### Method minNoOfDecimals

    public int minNoOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method minNoOfDecimalsMode

    public AutoMode minNoOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method minNoOfDecimalsValue

    public int minNoOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method modified

    public boolean modified()

#### Return Value

### Method mouseDblClick

Is called when the control is double-clicked by the user.

    public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseDown

Is called when the user clicks the mouse button over the control.

    public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method mouseMove

Is called when the user moves the mouse pointer over the control.

    public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned.

### Method mouseUp

Is called when the user releases the mouse button over the control area.

    public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

Typically, when this method is overridden, the return value from a call to the super method is returned. This event is called only if a value is specified for the label of the control and the ShowLabel property of the control is set to Yes.

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics AX application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

### Method noOfDecimals

    public int noOfDecimals([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method noOfDecimalsMode

    public AutoMode noOfDecimalsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method noOfDecimalsValue

    public int noOfDecimalsValue([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method posFromChar

    public container posFromChar(int charIndex)

#### Parameters

charIndex  

#### Return Value

### Method previewPartRef

    public str previewPartRef([str value])

#### Parameters

value  

#### Return Value

### Method promptrect

    public int promptrect([int value])

#### Parameters

value  

#### Return Value

### Method realValue

    public Real realValue([Real value])

#### Parameters

value  

#### Return Value

### Method replaceOnLookup

    public boolean replaceOnLookup([boolean value])

#### Parameters

value  

#### Return Value

### Method rotateSign

    public int rotateSign([int value])

#### Parameters

value  

#### Return Value

### Method searchAfterInput

    public int searchAfterInput([int value])

#### Parameters

value  

#### Return Value

### Method searchMode

    public int searchMode([int value])

#### Parameters

value  

#### Return Value

### Method securityKey

Sets or returns the ID of the security key for the control.

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  
The ID of the security key to assign to the control; optional.

#### Return Value

The ID of the security key for the control; 0 (zero) if no security key is assigned to the control.

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method showLabel

    public boolean showLabel([boolean value])

#### Parameters

value  

#### Return Value

### Method showZero

    public int showZero([int value])

#### Parameters

value  

#### Return Value

### Method signDisplay

    public int signDisplay([int value])

#### Parameters

value  

#### Return Value

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method thousandSeparator

    public int thousandSeparator([int value])

#### Parameters

value  

#### Return Value

### Method toolTip

Retrieves the tooltip text for the control.

    public str toolTip()

#### Return Value

The tooltip text for the control; an empty string if no tooltip text has been defined for the control.

#### Remarks

The method might be overridden to provide a value to the toolTip method.

### Method top

Gets or sets the vertical position of the control in the form.

    public int top(int value, [int mode])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

<!-- -->

mode  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method topMode

Sets the vertical arrange mode for the control in the form.

    public int topMode([int value])

#### Parameters

value  
An integer value that indicates the vertical arrange mode for the control; optional.

#### Return Value

The vertical arrange mode for the control in the form.

### Method topValue

Gets or sets the vertical position of the control in the form.

    public int topValue([int value])

#### Parameters

value  
An integer value that indicates the vertical position of the control; optional.

#### Return Value

The vertical position of the control in the form.

### Method type

    public int type([int value])

#### Parameters

value  

#### Return Value

### Method underline

    public boolean underline([boolean value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(container data)

#### Parameters

data  

#### Return Value

### Method userData

Gets or sets the user data for the control.

    public int userData([int value])

#### Parameters

value  
An integer value that indicates the user data for the control; optional.

#### Return Value

The user data for the control.

### Method userDataItem

Gets or sets the user data item for the control.

    public int userDataItem([int value])

#### Parameters

value  
An integer value that indicates the user data item for the control; optional.

#### Return Value

The user data item for the control.

### Method userDataItems

Gets or sets the number of user data items for the control.

    public int userDataItems([int value])

#### Parameters

value  
An integer value that indicates the number of user data items for the control; optional.

#### Return Value

The number of user data items for the control.

### Method userDisable

Gets or sets the value that indicates whether the control is disabled for the user.

    public int userDisable([int value])

#### Parameters

value  
The value that indicates whether the control is disabled for the user; optional.

#### Return Value

1 if the control is disabled for the user; otherwise, 0.

### Method userFastTabSummary

    public int userFastTabSummary([int value])

#### Parameters

value  

#### Return Value

### Method userHeight

Gets or sets the custom user height for the control.

    public int userHeight([int value])

#### Parameters

value  
The user height for the control; optional.

#### Return Value

The custom user height for the control.

### Method userHide

Gets or sets the value that indicates whether the control is hidden from the user.

    public int userHide([int value])

#### Parameters

value  
The value that indicates whether the control is hidden from the user; optional.

#### Return Value

1 if the control is hidden from the user; otherwise, 0.

#### Remarks

The user specifies whether a control is hidden by right-clicking the control when it is viewable or by right-clicking another control when the original control is hidden. A right-click opens a menu that can be used to hide or display the control. This method lets you programmatically determine and set the value.

### Method userOrgContainer

Gets or sets the organization container for the control.

    public int userOrgContainer([int value])

#### Parameters

value  
The organization container to set for the control; optional.

#### Return Value

The organization container for the control.

### Method userOrgSibling

Gets or sets the organization sibling for the control.

    public int userOrgSibling([int value])

#### Parameters

value  
The organization sibling to set for the control; optional.

#### Return Value

The organization sibling for the control.

### Method userPromptText

Gets or sets the user label text for the control.

    public str userPromptText([str value])

#### Parameters

value  
The user label text to set for the control; optional.

#### Return Value

The user label text for the control.

### Method userSecurityLevel

Gets or sets the user security level for the control.

    public int userSecurityLevel([int value])

#### Parameters

value  
The user security level to set for the control; optional.

#### Return Value

The user security level for the control.

### Method userSkip

Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.

    public int userSkip([int value])

#### Parameters

value  
The value to assign to the userSkip property; optional. The value is 1 if the user setting to skip the control is in effect; otherwise, the value is 0.

#### Return Value

1 if the user setting to skip the control is in effect; otherwise, 0.

### Method userWidth

Sets or returns the width of the control in pixels, as specified by the user.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method validate

    public boolean validate()

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode value for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode value for the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method verticalSpacingMode

Sets the vertical spacing mode for the control in the form.

    public AutoMode verticalSpacingMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

The vertical spacing mode for the control in the form.

### Method verticalSpacingValue

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacingValue([int value])

#### Parameters

value  
An integer value that indicates the vertical spacing of the control; optional.

#### Return Value

The vertical spacing of the control in the form.

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value to assign to the visibility setting for the control; optional.

#### Return Value

true if the control is visible; otherwise, false.

### Method width

Gets or sets the width of the control.

    public int width(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted. Calculate the width according to the following table.

| Mode           | Width calculation                                                                        |
|----------------|------------------------------------------------------------------------------------------|
| -1 Exact       | The exact width in pixels of the controls is used.                                       |
| 0 Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table.

| Mode         | Width calculation                                                                        |
|--------------|------------------------------------------------------------------------------------------|
| Exact        | The exact width in pixels of the controls is used.                                       |
| Auto         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method displayControl

Displays the control.

    public void displayControl()

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method pasteText

    public void pasteText(str pasteStr, [boolean InsertSel])

#### Parameters

pasteStr  

<!-- -->

InsertSel  

### Method lookup

    public void lookup()

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

### Method undo

    public void undo()

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method textChange

    public void textChange()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method drop

Raises the drop event to indicate that a drop operation is being performed on the current control.

    public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method scrollCursor

    public void scrollCursor()

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setSelection

    public void setSelection(int charIndexFrom, int charIndexTo)

#### Parameters

charIndexFrom  

<!-- -->

charIndexTo  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method jumpRef

    public void jumpRef()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method mouseEnter

Is called when the user moves the mouse pointer into the control area.

    public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)

#### Parameters

x  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

y  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

button  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Ctrl  
A Boolean value that indicates whether the SHIFT key is down.

<!-- -->

Shift  
A Boolean value that indicates whether the SHIFT key is down.

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method enter

    public void enter()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method dropEx

Raises the dropEx event to indicate that a drop operation is being performed on the current control.

    public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)

#### Parameters

dragSource  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

dragMode  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

x  
An integer value that indicates the vertical client coordinate of the mouse position.

<!-- -->

y  
An integer value that indicates the vertical client coordinate of the mouse position.

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  



