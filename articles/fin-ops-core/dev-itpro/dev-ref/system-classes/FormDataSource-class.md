---
title: FormDataSource class
description: This topic describes the FormDataSource class.
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

# Class FormDataSource

[!include [banner](../../includes/banner.md)]

```xpp
class FormDataSource extends FormObjectSet
```

The FormDataSource class contains properties that define the behavior of data sources in forms.

## Remarks

By overriding the methods on the class, you can customize the behavior for the method actions, such as insertion or validation, for a specific form. The FormDataSource class is also used to determine how the data source table is related to other data sources (tables) that are displayed in the form. To override some of the methods in the FormDataSource class, right-click the Methods node for a form data source, and then click Override Method. When you create methods on a form, you should use a \_ds identifier to reference the FormDataSource object for a particular class. For example, CustTrans\_ds references the FormDataSource object for the CustTrans data source on the form, and CustTrans\_ds.executeQuery() executes the FormDataSource.executeQuery method on the CustTrans data source. Several FormDataSource methods return a FormObjectSet object. To use the methods that are defined on the FormDataSource method on this object, you must typecast it to a FormDataSource object.

## Examples

The following example supplies a custom query for a field instead of the automatically generated query. It overrides the performFormLookup method on the field.

```xpp
public void performFormLookup(FormRun _p1, FormControl _formControl)  
{ 
    FormDataSource formDataSource; 
    QueryRun queryRunGenerated; 
    // The FormDataSource object retrieved from the FormRun parameter. 
    formDataSource = _p1.dataSource(1); 
    // Get the generated query. 
    queryRunGenerated = formDataSource.queryRun(); 
    // Modify the query. 
    // ... 
    // Call the standard implementation of performFormLookup 
    // with the parameters supplied in this method. 
    super(_p1, _formControl); 
}
```

## Methods

| Method                                                                                                                         | Description                                                                                                                                              |
|--------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------|
| public int active()                                                                                                            | Retrieves data from joined data sources when a user navigates to a new record and then sets the new record as the current record.                        |
| public boolean allowCheck(\[boolean value\])                                                                                   |                                                                                                                                                          |
| public boolean allowCreate(\[boolean value\])                                                                                  |                                                                                                                                                          |
| public boolean allowDeferredLoad(\[boolean value\])                                                                            |                                                                                                                                                          |
| public boolean allowDelete(\[boolean value\])                                                                                  |                                                                                                                                                          |
| public boolean allowEdit(\[boolean value\])                                                                                    | Determines whether the user can change the contents of the control.                                                                                      |
| public boolean allRowsLoaded()                                                                                                 |                                                                                                                                                          |
| public boolean anyMarked()                                                                                                     | Checks whether any records in the underlying cache are marked.                                                                                           |
| public boolean autoNotify(\[boolean value\])                                                                                   |                                                                                                                                                          |
| public boolean autoQuery(\[boolean value\])                                                                                    |                                                                                                                                                          |
| public boolean autoSearch(\[boolean value\])                                                                                   |                                                                                                                                                          |
| public str bindField(FieldId fieldId)                                                                                          |                                                                                                                                                          |
| public str bindDataMethod(str dataMethodName)                                                                                  |                                                                                                                                                          |
| public boolean cacheAddMethod(str methodName, \[boolean updateOnWrite\])                                                       | Registers the specified display or edit method for caching.                                                                                              |
| public boolean cacheCalculateMethod(str methodName)                                                                            | Calls the specified cached method and updates the value in the cache for the current record.                                                             |
| public boolean cacheOnlyMode(\[boolean value\])                                                                                |                                                                                                                                                          |
| public boolean canCreate()                                                                                                     |                                                                                                                                                          |
| public boolean canDelete()                                                                                                     |                                                                                                                                                          |
| public boolean canEdit()                                                                                                       |                                                                                                                                                          |
| public int clientPageSize(\[int pageSize\])                                                                                    |                                                                                                                                                          |
| public str company(\[str value\])                                                                                              |                                                                                                                                                          |
| public FieldId counterField(\[FieldId value\])                                                                                 |                                                                                                                                                          |
| public boolean crossCompanyAutoQuery(\[boolean value\])                                                                        |                                                                                                                                                          |
| public Common cursor(\[int rowIndex\])                                                                                         | Has no functionality in the FormObjectSet class.                                                                                                         |
| public int defaultMark(\[int value\])                                                                                          | Sets the default mark value for records in a form, which determines whether records are marked when they have been selected in a grid.                   |
| public boolean delayActive(\[boolean value\])                                                                                  |                                                                                                                                                          |
| public int extends(\[AnyType value\])                                                                                          |                                                                                                                                                          |
| public boolean findRecord(Common record)                                                                                       | Finds the specified record in the data source and makes it the current record.                                                                           |
| public boolean findValue(FieldId field, str value)                                                                             | Finds the specified value in the data source and makes the record that has that value the current record that uses the FormDataSource.findRecord method. |
| public boolean positionToRecord(Common record)                                                                                 |                                                                                                                                                          |
| public boolean positionToRecordByValue(FieldId field, str value)                                                               |                                                                                                                                                          |
| public int first()                                                                                                             | Moves focus to the first record in the data source.                                                                                                      |
| public boolean forceWrite(\[boolean value\])                                                                                   |                                                                                                                                                          |
| public FormObject functionObject(str name)                                                                                     |                                                                                                                                                          |
| public FormDataRow getDataRow(\[int rowIndex\], \[boolean allowFetchAhead\])                                                   |                                                                                                                                                          |
| public Common getFirst(\[int mark\], \[boolean fetchAhead\])                                                                   | Retrieves the first record in a data set.                                                                                                                |
| public Common getNext()                                                                                                        | Returns the next record that meets the criteria that are set up in an earlier call to the FormDataSource.getFirst method.                                |
| public int id()                                                                                                                | Retrieves the ID of the data source.                                                                                                                     |
| public IndexId index(\[IndexId value\])                                                                                        |                                                                                                                                                          |
| public boolean insertAtEnd(\[boolean value\])                                                                                  |                                                                                                                                                          |
| public boolean insertIfEmpty(\[boolean value\])                                                                                |                                                                                                                                                          |
| public boolean isBaseDataSource()                                                                                              |                                                                                                                                                          |
| public boolean isInheritanceDataSource()                                                                                       |                                                                                                                                                          |
| private boolean isOptionalRecordCreated(\[boolean set\], Common record, \[boolean value\])                                     |                                                                                                                                                          |
| public boolean isReferenceDataSource()                                                                                         |                                                                                                                                                          |
| public str joinRelation(\[str value\])                                                                                         |                                                                                                                                                          |
| public DictRelation joinRelationAsDictRelation()                                                                               |                                                                                                                                                          |
| public int joinSource(\[AnyType value\])                                                                                       |                                                                                                                                                          |
| public FormDataSource joinSourceDataSource()                                                                                   |                                                                                                                                                          |
| public int last()                                                                                                              | Moves the mouse pointer to the last record in the data source.                                                                                           |
| public boolean leave()                                                                                                         | Provides notification when the mouse pointer is moved to the next record or to another data source.                                                      |
| public boolean leaveRecord(\[boolean forceUpdate\])                                                                            | Provides notification when the focus moves to another record or item in the form.                                                                        |
| public container resolvePartLinks(\[str relationName\], \[int partTableId\])                                                   |                                                                                                                                                          |
| public int linkType(\[int value\])                                                                                             |                                                                                                                                                          |
| public int mark(\[int value\])                                                                                                 |                                                                                                                                                          |
| public boolean markAllLoadedRecords(\[int value\])                                                                             |                                                                                                                                                          |
| public int markRecord(AnyType record, \[int mark\])                                                                            | Marks the specified record by using the specified mark value.                                                                                            |
| public boolean markRecords(Array markedRecordIds)                                                                              |                                                                                                                                                          |
| public FormDataSource masterInheritanceDataSource()                                                                            |                                                                                                                                                          |
| public int maxAccessRight(\[int value\])                                                                                       |                                                                                                                                                          |
| public int maxRecordsToLoad(\[int value\])                                                                                     |                                                                                                                                                          |
| public Int64 maxPagingRowCountValue(\[Int64 newValue\])                                                                        |                                                                                                                                                          |
| public str name(\[str value\])                                                                                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.                  |
| public int next()                                                                                                              | Moves the focus to the next record in the data source.                                                                                                   |
| public int nextPage(int pageSize)                                                                                              | Moves a specified number of records forward in the data source.                                                                                          |
| public int numberOfRowsLoaded(\[boolean redirectToMasterDS\])                                                                  |                                                                                                                                                          |
| public FormDataObject object(FieldId fieldId, \[int arrayIndex\])                                                              | Returns an instance of the FormDataObject class that has the specified ID.                                                                               |
| public boolean onlyFetchActive(\[boolean value\])                                                                              |                                                                                                                                                          |
| public int optionalRecordMode(\[int value\])                                                                                   |                                                                                                                                                          |
| public int pageSize()                                                                                                          |                                                                                                                                                          |
| public boolean pagingEnabled()                                                                                                 |                                                                                                                                                          |
| public TitleFields parentTitleFields(Common record)                                                                            |                                                                                                                                                          |
| public int prev()                                                                                                              | Moves the focus to the previous record in the data source.                                                                                               |
| public int prevPage(int pageSize)                                                                                              | Moves the focus back by a specified number of records in the data source.                                                                                |
| public Query query(\[Query value\])                                                                                            |                                                                                                                                                          |
| public QueryBuildDataSource queryBuildDataSource()                                                                             |                                                                                                                                                          |
| public QueryRun queryRun(\[QueryRun value\])                                                                                   |                                                                                                                                                          |
| public QueryBuildDataSource queryRunQueryBuildDataSource()                                                                     |                                                                                                                                                          |
| public Array recordsMarked()                                                                                                   |                                                                                                                                                          |
| public int startPosition(\[int value\])                                                                                        |                                                                                                                                                          |
| public int startRowIndex()                                                                                                     |                                                                                                                                                          |
| public TableId table(\[TableId value\])                                                                                        | Gets or sets the table ID associated with the object.                                                                                                    |
| public TitleFields titleFields(Common record)                                                                                  |                                                                                                                                                          |
| public int totalNumberOfRows()                                                                                                 |                                                                                                                                                          |
| public boolean validateDelete()                                                                                                | Requests that the user confirm the deletion of a record from the data source.                                                                            |
| public boolean validateWrite()                                                                                                 | Determines whether data is valid and ready to be written.                                                                                                |
| public int validTimeStateAutoQuery(\[int value\])                                                                              |                                                                                                                                                          |
| public int validTimeStateUpdate(\[int value\])                                                                                 |                                                                                                                                                          |
| public void delete()                                                                                                           | Deletes the current record from the data source.                                                                                                         |
| public void addFieldToSelectionList(FieldId fieldId)                                                                           |                                                                                                                                                          |
| public void cacheRemoveRecord(\[Common record\])                                                                               | Removes the specified record from the underlying cache of the data source.                                                                               |
| private void OnValidatedWrite(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                        |                                                                                                                                                          |
| public void reread()                                                                                                           | Rereads the current record from the database.                                                                                                            |
| public void rereadJoinHierarchy()                                                                                              |                                                                                                                                                          |
| private void OnRefreshed(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                             |                                                                                                                                                          |
| private void OnValidatedDelete(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                       |                                                                                                                                                          |
| public void markChanged()                                                                                                      |                                                                                                                                                          |
| public void setPagingParameters(boolean pagingEnabled, int startRowIndex, int pageSize)                                        |                                                                                                                                                          |
| public void deleted()                                                                                                          |                                                                                                                                                          |
| public void print(PrintMedium target)                                                                                          | Prints the current record.                                                                                                                               |
| private void OnReread(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                                |                                                                                                                                                          |
| public void research(\[boolean retainPosition\])                                                                               | Is overridden by the FormDataSource.research method.                                                                                                     |
| public void createTypes(Map concreteTypesToCreate, \[boolean append\], \[boolean implicitCreate\], \[boolean explicitCreate\]) |                                                                                                                                                          |
| private void OnCreated(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                               |                                                                                                                                                          |
| private void OnQueryExecuted(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                         |                                                                                                                                                          |
| public void written()                                                                                                          |                                                                                                                                                          |
| public void filter(FieldId field, str value)                                                                                   | Filters records in the data source.                                                                                                                      |
| public void refresh()                                                                                                          | Updates the form by updating the view of all the records in the data source.                                                                             |
| public void write()                                                                                                            | Calls the FormDataSource.validateWrite method and manages the database write operation.                                                                  |
| public void executeQuery()                                                                                                     | Executes the data source query and displays the records that are retrieved.                                                                              |
| public void setRecord(Common record)                                                                                           |                                                                                                                                                          |
| public void refreshEx(\[AnyType pos\])                                                                                         | Updates the view of the specified records.                                                                                                               |
| public void setCurrent()                                                                                                       |                                                                                                                                                          |
| private void OnValidatingDelete(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                      |                                                                                                                                                          |
| public void writing()                                                                                                          |                                                                                                                                                          |
| private void OnWritten(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                               |                                                                                                                                                          |
| public void clearDisplayOption(Common record)                                                                                  | Clears display options that were previously specified for a record and then redraws the record.                                                          |
| private void OnMarkChanged(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                           |                                                                                                                                                          |
| private void OnLeftRecord(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                            |                                                                                                                                                          |
| private void OnDeleted(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                               |                                                                                                                                                          |
| public void removeFilter()                                                                                                     | Resets the query for the data source.                                                                                                                    |
| private void OnInitialized(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                           |                                                                                                                                                          |
| private void OnPostLinkActive(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                        |                                                                                                                                                          |
| private void OnSelectionChanged(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                      |                                                                                                                                                          |
| public void deleting()                                                                                                         |                                                                                                                                                          |
| public void observe()                                                                                                          |                                                                                                                                                          |
| private void OnWriting(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                               |                                                                                                                                                          |
| private void OnActivated(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                             |                                                                                                                                                          |
| public void removeFieldFromSelectionList(FieldId fieldId)                                                                      |                                                                                                                                                          |
| private void OnCreating(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                              |                                                                                                                                                          |
| public void rereadReferenceDataSources()                                                                                       |                                                                                                                                                          |
| private void OnValidatingWrite(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                       |                                                                                                                                                          |
| public void prompt()                                                                                                           | Activates the standard form, SysQueryForm, that is used to limit a query range.                                                                          |
| private void OnQueryExecuting(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                        |                                                                                                                                                          |
| private void OnInitValue(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                             |                                                                                                                                                          |
| public void clearReferenceData(FieldId fieldId)                                                                                |                                                                                                                                                          |
| public void cursorNotify(int event)                                                                                            | Notifies the application about a cursor event.                                                                                                           |
| public void displayOption(Common record, FormRowDisplayOption options)                                                         | Sets the text color and the background color for a record in the data source.                                                                            |
| public void create(\[boolean append\])                                                                                         | Creates a new record in the data source.                                                                                                                 |
| public void init()                                                                                                             | Creates a data source query that is based on the data source properties.                                                                                 |
| public void linkActive()                                                                                                       | Calls the FormDataSource.exeuteQuery method on data sources that are linked to the current data source.                                                  |
| public void selectionChanged()                                                                                                 |                                                                                                                                                          |
| private void OnDeleting(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                              |                                                                                                                                                          |
| public void addReferenceFieldToSelectionList(FieldId fieldId, str referenceFieldGroupName)                                     |                                                                                                                                                          |
| public void initValue()                                                                                                        | Initializes field values in a new record.                                                                                                                |
| public void deleteMarked()                                                                                                     | Deletes all marked (selected) records from a data source.                                                                                                |
| private void OnLeavingRecord(\[FormDataSource sender\], \[FormDataSourceEventArgs e\])                                         |                                                                                                                                                          |

## Method active

Retrieves data from joined data sources when a user navigates to a new record and then sets the new record as the current record.

```xpp
public int active()
```

### Return Value - active

Always returns 1.

### Remarks - active

The active method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking active.

## Method allowCheck

```xpp
public boolean allowCheck([boolean value])
```

### Parameters - allowCheck

value  

### Return Value - allowCheck

## Method allowCreate

```xpp
public boolean allowCreate([boolean value])
```

### Parameters - allowCreate

value  

### Return Value - allowCreate

## Method allowDeferredLoad

```xpp
public boolean allowDeferredLoad([boolean value])
```

### Parameters - allowDeferredLoad

value  

### Return Value - allowDeferredLoad

## Method allowDelete

```xpp
public boolean allowDelete([boolean value])
```

### Parameters - allowDelete

value  

### Return Value - allowDelete

## Method allowEdit

Determines whether the user can change the contents of the control.

```xpp
public boolean allowEdit([boolean value])
```

### Parameters - allowEdit

value  

### Return Value - allowEdit

true if the control can be edited; otherwise, false.

### Remarks - allowEdit

When this property is set on a container control, modifications are disabled or enabled for all controls in the container.

## Method allRowsLoaded

```xpp
public boolean allRowsLoaded()
```

### Return Value - allRowsLoaded

## Method anyMarked

Checks whether any records in the underlying cache are marked.

```xpp
public boolean anyMarked()
```

### Return Value - anyMarked

true if any records are marked; otherwise, false.

### Remarks - anyMarked

Records in a data source can be marked (selected) for actions such as deletion or copying by using the FormDataSource.markedRecord method.

## Method autoNotify

```xpp
public boolean autoNotify([boolean value])
```

### Parameters - autoNotify

value  

### Return Value - autoNotify

## Method autoQuery

```xpp
public boolean autoQuery([boolean value])
```

### Parameters - autoQuery

value  

### Return Value - autoQuery

## Method autoSearch

```xpp
public boolean autoSearch([boolean value])
```

### Parameters - autoSearch

value  

### Return Value - autoSearch

## Method bindField

```xpp
public str bindField(FieldId fieldId)
```

### Parameters - bindField

fieldId  

### Return Value - bindField

## Method bindDataMethod

```xpp
public str bindDataMethod(str dataMethodName)
```

### Parameters - bindDataMethod

dataMethodName  

### Return Value - bindDataMethod

## Method cacheAddMethod

Registers the specified display or edit method for caching.

```xpp
public boolean cacheAddMethod(str methodName, [boolean updateOnWrite])
```

### Parameters - cacheAddMethod

methodName  
A Boolean value that determines whether the cached value is updated automatically when the record is written; optional.

<!-- -->

updateOnWrite  
A Boolean value that determines whether the cached value is updated automatically when the record is written; optional.

### Return Value - cacheAddMethod

true if the method was registered successfully; otherwise, false.

### Remarks - cacheAddMethod

Cached methods perform calculations on fetched data, and then the calculated values are passed to the client together with the data. The calculated values are updated on reread. By default, the values are also update on write and create. This method should be called after initialization of the data source, but before any data is fetched. Therefore, the call to this method should be put after the call to the super method in the init method. The updateOnWrite parameter also determines whether the display or edit method value should be calculated and cached when a new record is created. To manually update the cached value for the display or edit method, call the FormDataSource.cacheCalculateMethod method. Only table methods that have the display or edit keyword can be cached. Methods that are written on the form or the form data source cannot be cached. Do not register display or edit methods that are not used on the form. Those methods are calculated for each record, even though the values are never shown.

### Examples - cacheAddMethod

The following example registers two methods for caching on the VendTransOpen table.

```xpp
public void init() 
{ 
    super(); 
    this.cacheAddMethod(tablemethodstr(VendTransOpen, 
        nextCashDiscDate)); 
    this.cacheAddMethod(tablemethodstr(VendTransOpen, 
        nextCashDiscAmount)); 
}
```

## Method cacheCalculateMethod

Calls the specified cached method and updates the value in the cache for the current record.

```xpp
public boolean cacheCalculateMethod(str methodName)
```

### Parameters - cacheCalculateMethod

methodName  
The name of the table method to call.

### Return Value - cacheCalculateMethod

true if the value has been updated; otherwise, false.

### Remarks - cacheCalculateMethod

The cached value is updated only if the method name that was supplied was previously registered as a cached method by using the FormDataSource.cacheAddMethod method. The cacheCalculate method is particularly useful if you want to update cached values only when certain conditions are met. In this case, set the updateOnWrite parameter in the call to the FormDataSource.cacheAddMethod method to false, and then manually update the cache, such as by using the write method on the data source.

### Examples - cacheCalculateMethod

The following example recalculates cached values by using the nextCashDiscDate method and the nextCashDiscAmount method, both in the VendTransOpen table.

```xpp
public void write() 
{ 
    super(); 
    vendTransOpen_ds.cacheCalculateMethod(tablemethodstr( 
        VendTransOpen, nextCashDiscDate)); 
    vendTransOpen_ds.cacheCalculateMethod(tablemethodstr( 
        VendTransOpen, nextCashDiscAmount)); 
}
```

## Method cacheOnlyMode

```xpp
public boolean cacheOnlyMode([boolean value])
```

### Parameters - cacheOnlyMode

value  

### Return Value - cacheOnlyMode

## Method canCreate

```xpp
public boolean canCreate()
```

### Return Value - canCreate

## Method canDelete

```xpp
public boolean canDelete()
```

### Return Value - canDelete

## Method canEdit

```xpp
public boolean canEdit()
```

### Return Value - canEdit

## Method clientPageSize

```xpp
public int clientPageSize([int pageSize])
```

### Parameters - clientPageSize

pageSize  

### Return Value - clientPageSize

## Method company

```xpp
public str company([str value])
```

### Parameters - company

value  

### Return Value - company

## Method counterField

```xpp
public FieldId counterField([FieldId value])
```

### Parameters - counterField

value  

### Return Value - counterField

## Method crossCompanyAutoQuery

```xpp
public boolean crossCompanyAutoQuery([boolean value])
```

### Parameters - crossCompanyAutoQuery

value  

### Return Value - crossCompanyAutoQuery

## Method cursor

Has no functionality in the FormObjectSet class.

```xpp
public Common cursor([int rowIndex])
```

### Parameters - cursor

rowIndex  

### Return Value - cursor

### Remarks - cursor

This method is overridden by the FormDataSource.cursor method, which returns the currently active record in the table that is referenced by the data source.

## Method defaultMark

Sets the default mark value for records in a form, which determines whether records are marked when they have been selected in a grid.

```xpp
public int defaultMark([int value])
```

### Parameters - defaultMark

value  
The default mark value for records in the form. The standard default mark value for records is 1, but this value can be overridden by setting the value parameter. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form when they have been selected.

### Return Value - defaultMark

The default mark value for records in the form.

### Remarks - defaultMark

This method is executed when a user clicks the top-left corner in a grid control to select all the records in the grid. The defaultMark method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; defaultMark.

## Method delayActive

```xpp
public boolean delayActive([boolean value])
```

### Parameters - delayActive

value  

### Return Value - delayActive

## Method extends

```xpp
public int extends([AnyType value])
```

### Parameters - extends

value  

### Return Value - extends

## Method findRecord

Finds the specified record in the data source and makes it the current record.

```xpp
public boolean findRecord(Common record)
```

### Parameters - findRecord

record  
The record to find.

### Return Value - findRecord

true if the record was found; otherwise, false.

### Remarks - findRecord

This method is activated when the FormDataSource.findValue method is called. The findRecord method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking findRecord.

## Method findValue

Finds the specified value in the data source and makes the record that has that value the current record that uses the FormDataSource.findRecord method.

```xpp
public boolean findValue(FieldId field, str value)
```

### Parameters - findValue

field  
The value to find.

<!-- -->

value  
The value to find.

### Return Value - findValue

true if the value is found; otherwise, false.

### Remarks - findValue

This method is called when a user clicks FindValue in the shortcut menu on a form control. The findValue method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking findValue.

### Examples - findValue

The following example stores the ID of the current record before it tries to modify data. If the update fails, the data source is positioned on the original record.

```xpp
void clicked() 
{ 
    DocuTypeId  docuTypeId; 
    RecId       activeRecId; 
    ; 
     // Store current RecID 
    activeRecId = docuRef.RecId;  
    // Open the Document Type dialog. 
    docuTypeId = smmDocuments::getDocuTypeId(element.args().record()); 
    try 
    { 
        ttsbegin; 
        if (docuTypeId) 
        { 
            // Create a new document record 
            docuRef_ds.create(); 
            docuRef.RefTableId      = tableReference; 
            docuRef.RefRecId        = recReference; 
            docuRef_ds.write(); 
            super(); 
        } 
        ttscommit; 
    } 
    catch 
    { 
        // Focus moved back to original record if there is an error 
        docuRef_ds.executeQuery(); 
        docuRef_ds.findValue(fieldnum(DocuRef,RecId), 
            int642str(activeRecId)); 
    } 
}
```

## Method positionToRecord

```xpp
public boolean positionToRecord(Common record)
```

### Parameters - positionToRecord

record  

### Return Value - positionToRecord

## Method positionToRecordByValue

```xpp
public boolean positionToRecordByValue(FieldId field, str value)
```

### Parameters - positionToRecordByValue

field  

<!-- -->

value  

### Return Value - positionToRecordByValue

## Method first

Moves focus to the first record in the data source.

```xpp
public int first()
```

### Return Value - first

A non-zero value if focus is successfully moved to the first record.

### Remarks - first

This method is called when a user selects the first record in a form by pressing CTRL+HOME. The first method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click first.

### Examples - first

The following example overrides the first method for the InventTransPostingFinancial data source on the InventTrans form and returns the last record in another data source that is used on the form.

```xpp
int first() 
{ 
    return inventTrans_ds.first(); 
}
```

## Method forceWrite

```xpp
public boolean forceWrite([boolean value])
```

### Parameters - forceWrite

value  

### Return Value - forceWrite

## Method functionObject

```xpp
public FormObject functionObject(str name)
```

### Parameters - functionObject

name  

### Return Value - functionObject

## Method getDataRow

```xpp
public FormDataRow getDataRow([int rowIndex], [boolean allowFetchAhead])
```

### Parameters - getDataRow

rowIndex  

<!-- -->

allowFetchAhead  

### Return Value - getDataRow

## Method getFirst

Retrieves the first record in a data set.

```xpp
public Common getFirst([int mark], [boolean fetchAhead])
```

### Parameters - getFirst

mark  
A Boolean value; optional. The default value is true.

<!-- -->

fetchAhead  
A Boolean value; optional. The default value is true.

### Return Value - getFirst

The first record in the data set.

### Remarks - getFirst

If the mark parameter is not 0 (zero), the first record that is marked with the specified value is returned, and subsequent calls to the FormDataSource.getNext method return marked records. If the fetchAhead parameter is set to false, only cached records are returned. If it is set to true, additional records are found and added to the cache, but the operation can become very time-consuming when it is performed on a large record set. When records in a grid are multiselected, the records are marked with the value 1. The following examples illustrate how to retrieve a marked or unmarked record: // Get first recordformDataSource.getFirst();// Get first record marked with 2formDataSource.getFirst(2); // Get first cached record marked with 1formDataSource.getFirst(1, false);

### Examples - getFirst

The following example determines whether two records are selected in a form.

```xpp
boolean twoMarked() 
{ 
    SysVersionControlTmpItem tmpitem  = this.getFirst(1); 
    if (!tmpitem) 
    { 
        return false; 
    } 
    tmpitem = this.getNext(); 
    if (!tmpitem) 
    { 
        return false; 
    } 
    tmpitem = this.getNext(); 
    if (!tmpitem) 
    { 
        return true; 
    } 
    return false; 
}
```

## Method getNext

Returns the next record that meets the criteria that are set up in an earlier call to the FormDataSource.getFirst method.

```xpp
public Common getNext()
```

### Return Value - getNext

The next record in the dataset.

### Remarks - getNext

Depending on the initialization that is performed in the call to the FormDataSource.getFirst method, the getNext method might return only records that have a particular mark value, and it might return records from the cache.

### Examples - getNext

The following example determines whether two records are selected in a form.

```xpp
boolean twoMarked() 
{ 
    SysVersionControlTmpItem tmpitem  = this.getFirst(1); 
    if (!tmpitem) 
    { 
        return false; 
    } 
    tmpitem = this.getNext(); 
    if (!tmpitem) 
    { 
        return false; 
    } 
    tmpitem = this.getNext(); 
    if (!tmpitem) 
    { 
        return true; 
    } 
    return false; 
}
```

## Method id

Retrieves the ID of the data source.

```xpp
public int id()
```

### Return Value - id

The ID of the data source.

### Examples - id

The following example converts form data sources to their data source IDs.

```xpp
static client DataSourceNumber fds2fdsNo(FormDataSource _fds) 
{ 
    Form  form = _fds.formRun().form(); 
    int   i; 
    for (i=1;i<=form.dataSourceCount();i++) 
    { 
        if (_fds.formRun().dataSource(i).id() == _fds.id()) 
        { 
            return i; 
        } 
    } 
    return 0; 
}
```

## Method index

```xpp
public IndexId index([IndexId value])
```

### Parameters - index

value  

### Return Value - index

## Method insertAtEnd

```xpp
public boolean insertAtEnd([boolean value])
```

### Parameters - insertAtEnd

value  

### Return Value - insertAtEnd

## Method insertIfEmpty

```xpp
public boolean insertIfEmpty([boolean value])
```

### Parameters - insertIfEmpty

value  

### Return Value - insertIfEmpty

## Method isBaseDataSource

```xpp
public boolean isBaseDataSource()
```

### Return Value - isBaseDataSource

## Method isInheritanceDataSource

```xpp
public boolean isInheritanceDataSource()
```

### Return Value - isInheritanceDataSource

## Method isOptionalRecordCreated

```xpp
private boolean isOptionalRecordCreated([boolean set], Common record, [boolean value])
```

### Parameters - isOptionalRecordCreated

set  

<!-- -->

record  

<!-- -->

value  

### Return Value - isOptionalRecordCreated

## Method isReferenceDataSource

```xpp
public boolean isReferenceDataSource()
```

### Return Value - isReferenceDataSource

## Method joinRelation

```xpp
public str joinRelation([str value])
```

### Parameters - joinRelation

value  

### Return Value - joinRelation

## Method joinRelationAsDictRelation

```xpp
public DictRelation joinRelationAsDictRelation()
```

### Return Value - joinRelationAsDictRelation

## Method joinSource

```xpp
public int joinSource([AnyType value])
```

### Parameters - joinSource

value  

### Return Value - joinSource

## Method joinSourceDataSource

```xpp
public FormDataSource joinSourceDataSource()
```

### Return Value - joinSourceDataSource

## Method last

Moves the mouse pointer to the last record in the data source.

```xpp
public int last()
```

### Return Value - last

A non-zero value if the mouse pointer is successfully moved to the last record.

### Remarks - last

The last method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking last.

### Examples - last

The following example overrides the last method for the InventDim data source on the WMSOrderTransport form and returns the last record in the other data source that is used on the form.

```xpp
int last() 
{ 
    return WMSOrder_ds.last(); 
}
```

## Method leave

Provides notification when the mouse pointer is moved to the next record or to another data source.

```xpp
public boolean leave()
```

### Return Value - leave

Always returns true, unless the method is overridden.

### Remarks - leave

This method is often overridden to implement record-level input validation. The leave method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking leave.

### Examples - leave

The following example overrides the leave method to perform data validation before the current record is left. The method returns false if the data is invalid.

```xpp
public boolean leave() 
{ 
    boolean ret; 
    ret = super(); 
    if(! salesLine.PBAItemLine::checkMandatory()) 
    { 
        return false; 
    } 
    return ret; 
}
```

## Method leaveRecord

Provides notification when the focus moves to another record or item in the form.

```xpp
public boolean leaveRecord([boolean forceUpdate])
```

### Parameters - leaveRecord

forceUpdate  

### Return Value - leaveRecord

true if the operation succeeds; otherwise, false.

### Remarks - leaveRecord

The method might fail and return false if changes could not be validated or written. It is recommended that you not override this method. Instead, override the FormDataSource.leave method. If you do override the leaveRecord method, you must call the super method to make sure that the kernel implementation of the method is executed.

## Method resolvePartLinks

```xpp
public container resolvePartLinks([str relationName], [int partTableId])
```

### Parameters - resolvePartLinks

relationName  

<!-- -->

partTableId  

### Return Value - resolvePartLinks

## Method linkType

```xpp
public int linkType([int value])
```

### Parameters - linkType

value  

### Return Value - linkType

## Method mark

```xpp
public int mark([int value])
```

### Parameters - mark

value  

### Return Value - mark

## Method markAllLoadedRecords

```xpp
public boolean markAllLoadedRecords([int value])
```

### Parameters - markAllLoadedRecords

value  

### Return Value - markAllLoadedRecords

## Method markRecord

Marks the specified record by using the specified mark value.

```xpp
public int markRecord(AnyType record, [int mark])
```

### Parameters - markRecord

record  
The value that is associated with a marked record; optional. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form.

<!-- -->

mark  
The value that is associated with a marked record; optional. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form.

### Return Value - markRecord

A non-zero integer if the record has been marked.

### Remarks - markRecord

Use this method instead of the FormDataSource.mark method if the record has been found by using a select statement or a method call outside the form.

## Method markRecords

```xpp
public boolean markRecords(Array markedRecordIds)
```

### Parameters - markRecords

markedRecordIds  

### Return Value - markRecords

## Method masterInheritanceDataSource

```xpp
public FormDataSource masterInheritanceDataSource()
```

### Return Value - masterInheritanceDataSource

## Method maxAccessRight

```xpp
public int maxAccessRight([int value])
```

### Parameters - maxAccessRight

value  

### Return Value - maxAccessRight

## Method maxRecordsToLoad

```xpp
public int maxRecordsToLoad([int value])
```

### Parameters - maxRecordsToLoad

value  

### Return Value - maxRecordsToLoad

## Method maxPagingRowCountValue

```xpp
public Int64 maxPagingRowCountValue([Int64 newValue])
```

### Parameters - maxPagingRowCountValue

newValue  

### Return Value - maxPagingRowCountValue

## Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other application object.

```xpp
public str name([str value])
```

### Parameters - name

value  
The name for the data source; optional.

### Return Value - name

The name that is used in code to identify an application object.

### Remarks - name

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Examples - name

The following example creates a QueryBuildDataSource object for a form data source. The FormDataSource.name method is used to specify the name of the QueryBuildDataSource object.

```xpp
static client QueryBuildDataSource fds2Qbds(FormDataSource _fds) 
{ 
    Form     form = _fds.formRun().form(); 
    if (_fds.query()  
        && _fds.name()  
        && _fds.query().dataSourceName(_fds.name())) 
    { 
        return _fds.query().dataSourceName(_fds.name()); 
    } 
    // Use the first data source if not found by name. 
    if (_fds.query() && _fds.query().dataSourceNo(1)) 
    { 
        return _fds.query().dataSourceNo(1); 
    } 
    return null; 
}
```

## Method next

Moves the focus to the next record in the data source.

```xpp
public int next()
```

### Return Value - next

A non-zero integer if the operation succeeds.

### Remarks - next

The next method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click next.

### Examples - next

The following example overrides the next method on a data source to return the next record from a different data source.

```xpp
int next() 
{ 
    return inventTrans_ds.next(); 
}
```

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

## Method numberOfRowsLoaded

```xpp
public int numberOfRowsLoaded([boolean redirectToMasterDS])
```

### Parameters - numberOfRowsLoaded

redirectToMasterDS  

### Return Value - numberOfRowsLoaded

## Method object

Returns an instance of the FormDataObject class that has the specified ID.

```xpp
public FormDataObject object(FieldId fieldId, [int arrayIndex])
```

### Parameters - object

fieldId  

<!-- -->

arrayIndex  

### Return Value - object

An instance of the FormDataObject class that has the ID that is specified in the objectId parameter.

### Examples - object

The following example creates a FormDataObject object for the RepositoryFolder field in the SysVersionControlParameters table, and then sets the AllowEdit property for the field to true.

```xpp
public void initFormDatasource(FormDataSource _formDataSource) 
{ 
    FormDataObject dataObject = _formDataSource.object( 
        fieldnum(SysVersionControlParameters, RepositoryFolder)); 
    if (dataObject) 
    { 
        dataObject.allowEdit(true); 
    } 
}
```

## Method onlyFetchActive

```xpp
public boolean onlyFetchActive([boolean value])
```

### Parameters - onlyFetchActive

value  

### Return Value - onlyFetchActive

## Method optionalRecordMode

```xpp
public int optionalRecordMode([int value])
```

### Parameters - optionalRecordMode

value  

### Return Value - optionalRecordMode

## Method pageSize

```xpp
public int pageSize()
```

### Return Value - pageSize

## Method pagingEnabled

```xpp
public boolean pagingEnabled()
```

### Return Value - pagingEnabled

## Method parentTitleFields

```xpp
public TitleFields parentTitleFields(Common record)
```

### Parameters - parentTitleFields

record  

### Return Value - parentTitleFields

## Method prev

Moves the focus to the previous record in the data source.

```xpp
public int prev()
```

### Return Value - prev

A non-zero integer if the operation succeeds.

### Remarks - prev

This method can be used to iterate through the records of a data source in reverse order. The prev method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click prev.

### Examples - prev

The following example overrides the prev method on a data source to return the previous record from a different data source.

```xpp
int prev() 
{ 
    return inventTrans_ds.prev(); 
}
```

## Method prevPage

Moves the focus back by a specified number of records in the data source.

```xpp
public int prevPage(int pageSize)
```

### Parameters - prevPage

pageSize  
The number of records to move back by.

### Return Value - prevPage

A non-zero integer if the operation succeeds.

## Method query

```xpp
public Query query([Query value])
```

### Parameters - query

value  

### Return Value - query

## Method queryBuildDataSource

```xpp
public QueryBuildDataSource queryBuildDataSource()
```

### Return Value - queryBuildDataSource

## Method queryRun

```xpp
public QueryRun queryRun([QueryRun value])
```

### Parameters - queryRun

value  

### Return Value - queryRun

## Method queryRunQueryBuildDataSource

```xpp
public QueryBuildDataSource queryRunQueryBuildDataSource()
```

### Return Value - queryRunQueryBuildDataSource

## Method recordsMarked

```xpp
public Array recordsMarked()
```

### Return Value - recordsMarked

## Method startPosition

```xpp
public int startPosition([int value])
```

### Parameters - startPosition

value  

### Return Value - startPosition

## Method startRowIndex

```xpp
public int startRowIndex()
```

### Return Value - startRowIndex

## Method table

Gets or sets the table ID associated with the object.

```xpp
public TableId table([TableId value])
```

### Parameters - table

value  

### Return Value - table

The current value of the table ID associated with the object.

## Method titleFields

```xpp
public TitleFields titleFields(Common record)
```

### Parameters - titleFields

record  

### Return Value - titleFields

## Method totalNumberOfRows

```xpp
public int totalNumberOfRows()
```

### Return Value - totalNumberOfRows

## Method validateDelete

Requests that the user confirm the deletion of a record from the data source.

```xpp
public boolean validateDelete()
```

### Return Value - validateDelete

true if the deletion is performed successfully; otherwise, false.

### Remarks - validateDelete

This method calls the validateDelete method on the data source table. The FormDataSource.validateDelete method is called by the FormDataSource.delete method. Use this method to add custom data validation checks whenever they are required. The validateDelete method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking validateDelete.

### Examples - validateDelete

The following example does not call the super() method and returns true. This suppresses the display of the delete confirmation message box.

```xpp
public boolean validateDelete() 
{ 
    // Do not display warning dialog. 
    return true; 
}
```

## Method validateWrite

Determines whether data is valid and ready to be written.

```xpp
public boolean validateWrite()
```

### Return Value - validateWrite

Returns true if data is valid; otherwise, false.

### Remarks - validateWrite

This method is called from the FormDataSource.write method. If false is returned, the write operation is aborted and an error message is displayed. Override this method to add custom validation routines to your data source. The validateWrite method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking validateWrite. The call to the super() method in this method calls the validateWrite method on the table that is used as a data source. Therefore, the return value of the super() method should be examined. If you override the method, it should return true only if the super() method also returns true.

## Method validTimeStateAutoQuery

```xpp
public int validTimeStateAutoQuery([int value])
```

### Parameters - validTimeStateAutoQuery

value  

### Return Value - validTimeStateAutoQuery

## Method validTimeStateUpdate

```xpp
public int validTimeStateUpdate([int value])
```

### Parameters - validTimeStateUpdate

value  

### Return Value - validTimeStateUpdate

## Method delete

Deletes the current record from the data source.

```xpp
public void delete()
```

### Remarks - delete

This method is called when a user deletes a record in a form. The delete method calls the FormDataSource.validateDelete method. If the validateDelete method returns true, the record is deleted. After the deletion, the cursor is positioned on the next record (if there is one). The delete method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking delete.

### Examples - delete

The following example overrides the delete method on the Errors data source for the SysCompilerOutput form. The method updates the number of errors that are displayed in the Compiler output form after an error has been removed.

```xpp
public void delete() 
{ 
    super(); 
    sysCompilerOutput.updateCounters(); 
}
```

## Method addFieldToSelectionList

```xpp
public void addFieldToSelectionList(FieldId fieldId)
```

### Parameters - addFieldToSelectionList

fieldId  

## Method cacheRemoveRecord

Removes the specified record from the underlying cache of the data source.

```xpp
public void cacheRemoveRecord([Common record])
```

### Parameters - cacheRemoveRecord

record  
The record to remove from the cache; optional.

### Remarks - cacheRemoveRecord

You must enclose data modification statements in a ttsbegin/ttscommit block.

### Examples - cacheRemoveRecord

The following example deletes the inventTable record from the cache of the data source.

```xpp
void updateCache(container _conItemId) 
{ 
    SetIterator itSetItemId; 
    InventTable inventTable; 
    Set setItemId = new Set(Types::String); 
    setItemId = Set::create(_conItemId); 
    itSetItemId = new SetIterator(setItemId); 
    ttsBegin; 
    while (itSetItemId.more()) 
    { 
        inventTable = InventTable::find(itSetItemId.value()); 
        if(inventTableWithOutReqItem_ds. 
            findRecord(inventTable)) 
            inventTableWithOutReqItem_ds. 
                cacheRemoveRecord(inventTable); 
        itSetItemId.next(); 
    } 
    ttsCommit; 
}
```

## Method OnValidatedWrite

```xpp
private void OnValidatedWrite([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnValidatedWrite

sender  

<!-- -->

e  

## Method reread

Rereads the current record from the database.

```xpp
public void reread()
```

### Remarks - reread

Call this method to update the record with the latest changes from the database. The reread method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click reread.

### Examples - reread

The following example uses the reread method as part of a method that is used to update a table.

```xpp
void doRefresh() 
{ 
    salesTable_ds.reread(); 
    salesTable_ds.refresh(); 
    salesLine_ds.reread(); 
    salesLine_ds.refresh(); 
    interCompanyPurchSalesReference_ds.executeQuery(); 
}
```

## Method rereadJoinHierarchy

```xpp
public void rereadJoinHierarchy()
```

## Method OnRefreshed

```xpp
private void OnRefreshed([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnRefreshed

sender  

<!-- -->

e  

## Method OnValidatedDelete

```xpp
private void OnValidatedDelete([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnValidatedDelete

sender  

<!-- -->

e  

## Method markChanged

```xpp
public void markChanged()
```

## Method setPagingParameters

```xpp
public void setPagingParameters(boolean pagingEnabled, int startRowIndex, int pageSize)
```

### Parameters - setPagingParameters

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

## Method deleted

```xpp
public void deleted()
```

## Method print

Prints the current record.

```xpp
public void print(PrintMedium target)
```

### Parameters - print

target  
The print medium to use to print the record.

### Remarks - print

The current record is printed by using the system's auto report facilities (the SysTableReport report, which is located in the Reports node). The print method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click print.

## Method OnReread

```xpp
private void OnReread([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnReread

sender  

<!-- -->

e  

## Method research

Is overridden by the FormDataSource.research method.

```xpp
public void research([boolean retainPosition])
```

### Parameters - research

retainPosition  
A Boolean value that indicates whether to maintain the position in the grid after the method is completed.

### Remarks - research

This method has no functionality in the FormObjectSet class. It is overridden by the FormDataSource.research method, which updates the database search that is defined by the filters and sorts that are currently applied to the form.

## Method createTypes

```xpp
public void createTypes(Map concreteTypesToCreate, [boolean append], [boolean implicitCreate], [boolean explicitCreate])
```

### Parameters - createTypes

concreteTypesToCreate  

<!-- -->

append  

<!-- -->

implicitCreate  

<!-- -->

explicitCreate  

## Method OnCreated

```xpp
private void OnCreated([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnCreated

sender  

<!-- -->

e  

## Method OnQueryExecuted

```xpp
private void OnQueryExecuted([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnQueryExecuted

sender  

<!-- -->

e  

## Method written

```xpp
public void written()
```

## Method filter

Filters records in the data source.

```xpp
public void filter(FieldId field, str value)
```

### Parameters - filter

field  
The filtering condition.

<!-- -->

value  
The filtering condition.

### Remarks - filter

The filter method can be overridden on a form data source to extend the standard filtering functionality. Right-click the Methods node under the data source, point to Override Method, and then click filter.

## Method refresh

Updates the form by updating the view of all the records in the data source.

```xpp
public void refresh()
```

### Remarks - refresh

The contents of the records are redrawn without loading from disk. You can, for example, use refresh if you have to update while a lengthy operation is running. Use the FormDataSource.refreshEx method if you do not want to refresh all the records. The refresh method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click refresh.

### Examples - refresh

The following example overrides the write method on a data source so that it updates records in a different data source after a write operation.

```xpp
public void write() 
{ 
    super(); 
    EPParameters_ds.research(); 
    EPParameters_ds.refresh(); 
}
```

## Method write

Calls the FormDataSource.validateWrite method and manages the database write operation.

```xpp
public void write()
```

### Remarks - write

This method is invoked when a user inserts a new record or updates an existing one. The refreshEx method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click refreshEx.

## Method executeQuery

Executes the data source query and displays the records that are retrieved.

```xpp
public void executeQuery()
```

### Remarks - executeQuery

This method is executed when a form is opened for data display. The executeQuery method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking executeQuery.

### Examples - executeQuery

The following example executes a data source query in response to a tab page activation event.

```xpp
public void pageActivated() 
{ 
    monday_ds.executeQuery(); 
    super(); 
}
```

## Method setRecord

```xpp
public void setRecord(Common record)
```

### Parameters - setRecord

record  

## Method refreshEx

Updates the view of the specified records.

```xpp
public void refreshEx([AnyType pos])
```

### Parameters - refreshEx

pos  
The number of the record to refresh; optional. If a value of -1 is specified, all records are updated. If a value of -2 is specified, all marked records and all records that have display options specified are updated. The default value is -2.

### Remarks - refreshEx

The refreshEx method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking refreshEx.

## Method setCurrent

```xpp
public void setCurrent()
```

## Method OnValidatingDelete

```xpp
private void OnValidatingDelete([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnValidatingDelete

sender  

<!-- -->

e  

## Method writing

```xpp
public void writing()
```

## Method OnWritten

```xpp
private void OnWritten([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnWritten

sender  

<!-- -->

e  

## Method clearDisplayOption

Clears display options that were previously specified for a record and then redraws the record.

```xpp
public void clearDisplayOption(Common record)
```

### Parameters - clearDisplayOption

record  
The record to redraw.

### Remarks - clearDisplayOption

Display options are set by using the FormDataSource.displayOption method.

### Examples - clearDisplayOption

The following example redraws the first record in a data source.

```xpp
public void run() 
{ 
    super(); 
    sysRecordTmpTemplate_ds.clearDisplayOption( 
        sysRecordTmpTemplate_ds.getFirst()); 
}
```

## Method OnMarkChanged

```xpp
private void OnMarkChanged([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnMarkChanged

sender  

<!-- -->

e  

## Method OnLeftRecord

```xpp
private void OnLeftRecord([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnLeftRecord

sender  

<!-- -->

e  

## Method OnDeleted

```xpp
private void OnDeleted([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnDeleted

sender  

<!-- -->

e  

## Method removeFilter

Resets the query for the data source.

```xpp
public void removeFilter()
```

### Remarks - removeFilter

This method is called when a user clicks the Cancel Filter command in the shortcut menu on a form control. The removeFilter method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click removeFilter. For example, removeFilter removes all modifications to the original query that is generated by the FormDataSource.init method.

## Method OnInitialized

```xpp
private void OnInitialized([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnInitialized

sender  

<!-- -->

e  

## Method OnPostLinkActive

```xpp
private void OnPostLinkActive([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnPostLinkActive

sender  

<!-- -->

e  

## Method OnSelectionChanged

```xpp
private void OnSelectionChanged([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnSelectionChanged

sender  

<!-- -->

e  

## Method deleting

```xpp
public void deleting()
```

## Method observe

```xpp
public void observe()
```

## Method OnWriting

```xpp
private void OnWriting([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnWriting

sender  

<!-- -->

e  

## Method OnActivated

```xpp
private void OnActivated([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnActivated

sender  

<!-- -->

e  

## Method removeFieldFromSelectionList

```xpp
public void removeFieldFromSelectionList(FieldId fieldId)
```

### Parameters - removeFieldFromSelectionList

fieldId  

## Method OnCreating

```xpp
private void OnCreating([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnCreating

sender  

<!-- -->

e  

## Method rereadReferenceDataSources

```xpp
public void rereadReferenceDataSources()
```

## Method OnValidatingWrite

```xpp
private void OnValidatingWrite([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnValidatingWrite

sender  

<!-- -->

e  

## Method prompt

Activates the standard form, SysQueryForm, that is used to limit a query range.

```xpp
public void prompt()
```

### Remarks - prompt

This method is called when a user clicks the Filter records command on the Command menu or presses CTRL+F3. The prompt method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click prompt.

## Method OnQueryExecuting

```xpp
private void OnQueryExecuting([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnQueryExecuting

sender  

<!-- -->

e  

## Method OnInitValue

```xpp
private void OnInitValue([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnInitValue

sender  

<!-- -->

e  

## Method clearReferenceData

```xpp
public void clearReferenceData(FieldId fieldId)
```

### Parameters - clearReferenceData

fieldId  

## Method cursorNotify

Notifies the application about a cursor event.

```xpp
public void cursorNotify(int event)
```

### Parameters - cursorNotify

event  
The cursor event identifier. The following table shows the available cursor events.

### Remarks - cursorNotify

This method can be overridden to implement custom handling of cursor events. However, the super() method has to be called first to enable the kernel to handle the event as appropriate.

## Method displayOption

Sets the text color and the background color for a record in the data source.

```xpp
public void displayOption(Common record, FormRowDisplayOption options)
```

### Parameters - displayOption

record  
The FormRowDisplayOption object that encapsulates the desired record display properties.

<!-- -->

options  
The FormRowDisplayOption object that encapsulates the desired record display properties.

### Remarks - displayOption

This method is executed one time for each record before the record is displayed in a form. The displayOption method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click displayOption.

### Examples - displayOption

The following example overrides the displayOption method to set display options from a stored profile and to override the background color that is based on the settings for the particular record.

```xpp
public void displayOption(Common _record, FormRowDisplayOption 
    _options) 
{ 
    JmgProfileTable profile; 
    profile = _record; 
    _options.backColor(profile.Color); 
    super(_record, _options); 
}
```

## Method create

Creates a new record in the data source.

```xpp
public void create([boolean append])
```

### Parameters - create

append  
A Boolean value that indicates whether to insert the record after or before the current cursor position. If it is set to true, the new record is inserted after the current record.

### Remarks - create

This method is called when a user creates a new record in a data source, such as by using the default shortcut key for insertion (CTRL+N). The create method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; create.

## Method init

Creates a data source query that is based on the data source properties.

```xpp
public void init()
```

### Remarks - init

This method is called when the form is opened. The query that is generated by the method is used to the load data so that it can be displayed in the form. The init method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click init.

### Examples - init

The following example overrides the init method on a data source to specify the sorting order for the data source.

```xpp
public void init() 
{ 
    super(); 
    this.query().dataSourceTable( 
        tablenum(SysVersionControlTmpItem)).addSortField( 
            fieldnum(SysVersionControlTmpItem, VCSDate), 
        SortOrder::Descending); 
    this.query().dataSourceTable( 
        tablenum(SysVersionControlTmpItem)).addSortField( 
            fieldnum(SysVersionControlTmpItem, VCSTime), 
        SortOrder::Descending); 
    this.query().dataSourceTable( 
        tablenum(SysVersionControlTmpItem)).addSortField( 
            fieldnum(SysVersionControlTmpItem, ChangeNumber), 
        SortOrder::Ascending); 
}
```

## Method linkActive

Calls the FormDataSource.exeuteQuery method on data sources that are linked to the current data source.

```xpp
public void linkActive()
```

### Remarks - linkActive

This method is executed when a user moves to another record in the master data source. This causes an update to all linked data sources. The super() call in the FormDataSource.active method calls the FormDataSource.linkActive method on all linked child data sources if the LinkType property on the parent data source is set to Passive, Delayed, or Active. The linkActive method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click linkActive.

## Method selectionChanged

```xpp
public void selectionChanged()
```

## Method OnDeleting

```xpp
private void OnDeleting([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnDeleting

sender  

<!-- -->

e  

## Method addReferenceFieldToSelectionList

```xpp
public void addReferenceFieldToSelectionList(FieldId fieldId, str referenceFieldGroupName)
```

### Parameters - addReferenceFieldToSelectionList

fieldId  

<!-- -->

referenceFieldGroupName  

## Method initValue

Initializes field values in a new record.

```xpp
public void initValue()
```

### Remarks - initValue

This method is called when a new record is created. It populates the record with initial values for the fields. The initValue method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking initValue.

### Examples - initValue

The following example overrides FormDataSource.initValue so that the TaxLimitBase field is initialized with a particular value.

```xpp
public void initValue() 
{ 
    super(); 
    taxTable.TaxLimitBase = TaxLimitBase::InvoiceWithoutVAT; 
}
```

## Method deleteMarked

Deletes all marked (selected) records from a data source.

```xpp
public void deleteMarked()
```

### Remarks - deleteMarked

If no records have been selected, the FormDataSource.delete method is executed. The operation can be interrupted by pressing CTRL+BREAK. The deleteMarked method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; deleteMarked.

### Examples - deleteMarked

The following example overrides the deleteMarked method to let users confirm whether they want to delete the marked records.

```xpp
public void deleteMarked() 
{ 
    if (Box::yesNo("@SYS79428", DialogButton::Yes, "@SYS79319")) 
        super(); 
}
```

## Method OnLeavingRecord

```xpp
private void OnLeavingRecord([FormDataSource sender], [FormDataSourceEventArgs e])
```

### Parameters - OnLeavingRecord

sender  

<!-- -->

e  

