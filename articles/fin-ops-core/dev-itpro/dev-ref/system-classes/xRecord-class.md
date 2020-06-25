---
title: xRecord class
description: This topic describes the xRecord class.
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

# Class xRecord

[!include [banner](../../includes/banner.md)]

```xpp
class xRecord extends Object
```

## Remarks

## Examples

## Methods

| Method                                                                                                                     | Description                                                                                                                    |
|----------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| public boolean aosValidateDelete()                                                                                         | Validates on the server that the specified record can be deleted from a table.                                                 |
| public boolean aosValidateInsert()                                                                                         | Validates on the server that the specified record can be inserted.                                                             |
| public boolean aosValidateRead()                                                                                           | Validates on the server that the specified record can be read.                                                                 |
| public boolean aosValidateUpdate()                                                                                         | Validates on the server that the specified record can be updated.                                                              |
| public container buf2con(\[boolean packOrigBuffer\])                                                                       | Packs the table buffers of an xRecord instance into an X++ container.                                                          |
| public boolean canSubmitToWorkflow(\[str workflowType\])                                                                   | Indicates whether submission to workflow is possible.                                                                          |
| public str caption()                                                                                                       | Gets and sets the caption property of a table.                                                                                 |
| public boolean checkInvalidFieldAccess(\[boolean checkInvalidFieldAccess\])                                                | Gets and sets invalid field access.                                                                                            |
| public boolean checkRecord(\[boolean checkMandatoryFields\])                                                               | Gets and sets the property that indicates whether to check mandatory fields.                                                   |
| public boolean checkRestrictedDeleteActions(\[boolean checkRestrictedDeleteActions\])                                      | Gets and sets the property that indicates whether a record can be deleted.                                                     |
| public SelectableDataArea company(\[SelectableDataArea company\])                                                          | Gets and sets the property that indicates a legal entity for the record.                                                       |
| public Common con2buf(container container)                                                                                 | Unpacks a container into the table buffers.                                                                                    |
| public ConcurrencyModel concurrencyModel(\[ConcurrencyModel concurrencyModel\])                                            | Gets and sets the default concurrency model to use to update records.                                                          |
| public int context(\[int newValue\])                                                                                       | Gets and sets the context property.                                                                                            |
| public Common data(\[Common cursor\])                                                                                      | Retrieves a row from the table.                                                                                                |
| public FormObjectSet dataSource()                                                                                          | Retrieves the data source of the table.                                                                                        |
| public boolean disableCache(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether caching is disabled.                                                         |
| public boolean doValidateDelete()                                                                                          | Performs the action to validate that a record can be deleted.                                                                  |
| public boolean equal(Common cursor)                                                                                        | Determines whether the specified object is equal to the current one.                                                           |
| public AccessRight fieldAccessRight(FieldName fieldName)                                                                   | Returns the field access right.                                                                                                |
| public AccessRight fieldBufferAccessRight(FieldName fieldName)                                                             | Returns the field access right for the current record.                                                                         |
| public FieldState fieldState(FieldId fieldId, \[FieldState state\])                                                        | Sets or returns the state of a field in the table buffer.                                                                      |
| public container getAllowRedefault()                                                                                       | Returns the list of fields that are allowed to re-default.                                                                     |
| public container getDefaultingDependencies()                                                                               | Returns the container that holds defaulting dependencies.                                                                      |
| public TableExtension getExtension()                                                                                       | Returns the table extension.                                                                                                   |
| public AnyType getFieldValue(str fieldName, \[int arrayIndex\])                                                            | Gets the value of the specified field from a table buffer.                                                                     |
| public str getInstanceRelationType()                                                                                       | Returns the table name that corresponds to the InstanceRelationType ID.                                                        |
| public str getPhysicalTableName()                                                                                          | Return the physical table name, which, in the case of the SQL Temp DB table, is the table instance name.                       |
| public PresenceInfo getPresenceFieldData(FieldId fieldId, AnyType fieldValue)                                              | Retrieves the PresenceInfo value from the specified field.                                                                     |
| public str getSQLStatement()                                                                                               | Gets the SQL statement that is used to return records from the database.                                                       |
| public Common getTableInInstanceHierarchy(TableId tableId)                                                                 |                                                                                                                                |
| public TableType getTableType()                                                                                            | Indicates the type of the table.                                                                                               |
| public boolean hasRelatedTable(str relatedRoleName)                                                                        | Indicates whether a foreign key constraint buffer is linked with the table.                                                    |
| public str helpField(FieldId fieldId)                                                                                      | Retrieves a string that contains the Help text for the specified field.                                                        |
| public FieldState inputStatus(\[FieldState inputStatus\])                                                                  | Sets or returns the current input status of the table buffer.                                                                  |
| public boolean interactiveContext(\[boolean context\])                                                                     | Sets or returns the current interactive context of the table buffer.                                                           |
| public boolean isFieldDataRetrieved(str fieldName, \[int arrayIndex\])                                                     | Checks whether the data of the given field has been retrieved.                                                                 |
| public boolean isFieldSet(FieldId fieldId)                                                                                 | Checks whether a field has a Set or Defaulted state.                                                                           |
| public boolean isFormDataSource()                                                                                          | Indicates whether the data source is a form.                                                                                   |
| public boolean isNewRecord()                                                                                               | Returns true if the record is a new record that hasn't been persisted yet.                                                     |
| public boolean isPartOfUOWSaveChanges()                                                                                    |                                                                                                                                |
| public boolean isTempDb()                                                                                                  | Indicates whether the type of the table is SQL TempDB.                                                                         |
| public boolean isTmp()                                                                                                     | Indicates whether this is a temporary table.                                                                                   |
| public Common joinChild()                                                                                                  | Finds the join child of the current record.                                                                                    |
| public Common joinParent()                                                                                                 | Finds the join parent of the current record.                                                                                   |
| public boolean linkPhysicalTableInstance(\[Common record\])                                                                | Checks whether there is a link for the physical table instance for the record.                                                 |
| public Common orig()                                                                                                       | Retrieves the original values of the current record.                                                                           |
| public boolean overwriteSystemfields(\[boolean allowOverwrite\])                                                           | Gets and sets the property that indicates whether system fields can be overwritten.                                            |
| public boolean queryTimedOut()                                                                                             | Indicates whether the query exceeded the time limit for execution.                                                             |
| public int queryTimeout(\[int seconds\], \[boolean raiseException\])                                                       | Gets and sets the property that indicates the time limit for the execution of a query.                                         |
| public boolean readCommittedLock(\[boolean readCommittedLock\])                                                            |                                                                                                                                |
| public boolean readPast(\[boolean skipLockedRows\])                                                                        | Gets and sets the property that indicates whether to skip rows that are locked by other processes when a record is read.       |
| public boolean recordLevelSecurity(\[boolean newValue\])                                                                   | Gets and sets the property that indicates whether to apply security on a record level.                                         |
| public Common relatedTable(str name, \[Common buffer\])                                                                    | Sets or returns the related buffer of a link of a table buffer.                                                                |
| public Int64 RowCount()                                                                                                    | Retrieves the number of rows in the table.                                                                                     |
| public boolean selectForUpdate(\[boolean lockRecordsExclusive\])                                                           | Gets and sets the property that indicates whether to select records for update when they are read.                             |
| public boolean selectLocked(\[boolean lockRecordsShared\])                                                                 | Indicates whether to select locked records.                                                                                    |
| public Common selectRefRecord(FieldId referenceFieldId)                                                                    | Selects the record by referenced field ID.                                                                                     |
| public boolean selectWithRepeatableRead(\[boolean useRepeatableRead\])                                                     | Gets and sets the property that indicates whether repeatable read is enabled.                                                  |
| public boolean setTempDB()                                                                                                 |                                                                                                                                |
| public boolean setTmp()                                                                                                    | Sets the table so that it is not persisted to the database.                                                                    |
| public boolean skipAosValidation(\[boolean newValue\])                                                                     | Gets and sets the property that indicates whether to skip validation Application Object Server (AOS). |
| public boolean skipDatabaseLog(\[boolean newValue\])                                                                       | Gets and sets the property that indicates whether to skip database log requests.                                               |
| public boolean skipDataMethods(\[boolean newValue\])                                                                       | Gets and sets the property that indicates whether to discard overloaded methods.                                               |
| public boolean skipDeleteActions(\[boolean newValue\])                                                                     | Gets and sets the property that indicates whether to skip delete actions on the table.                                         |
| public boolean skipDeleteMethod(\[boolean newValue\])                                                                      | Gets and sets the property that indicates whether to discard overloaded methods.                                               |
| public boolean skipEvents(\[boolean newValue\])                                                                            | Provides an option to turn off calling the Application.event\* methods for the lifetime of an xRecord object.                  |
| public boolean skipPostLoad(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether to skip executing the xRecord.postLoad method on the table.                  |
| public boolean skipTTSCheck(\[boolean newValue\])                                                                          | Gets and sets the property that indicates whether to skip the check to determine whether the record is selected for update.    |
| public boolean suppressWarnings(\[boolean newValue\])                                                                      | Gets and sets the property that indicates whether to suppress warnings for this pointer.                                       |
| public AccessRight tableAccessRight()                                                                                      | Returns the table access right.                                                                                                |
| public AccessRight tableBufferAccessRight()                                                                                | Returns the table access right for the current record.                                                                         |
| public boolean takeOwnershipOfTempDBTable(boolean newValue)                                                                |                                                                                                                                |
| public str toolTipField(FieldId fieldId)                                                                                   | Retrieves the HelpText value for the specified field.                                                                          |
| public str toolTipRecord()                                                                                                 | Retrieves the ToolTip value for the current record.                                                                            |
| public int usageCount()                                                                                                    | Retrieves the current number of references (the value of the reference counter) that the object has.                           |
| public boolean useExistingTempDBTable(str physicalTempTableName)                                                           |                                                                                                                                |
| public boolean validateDelete()                                                                                            | Determines whether the current record is valid and ready to be deleted from the database.                                      |
| public boolean validateField(FieldId fieldIdToCheck)                                                                       | Determines whether the specified field is valid.                                                                               |
| public boolean validateFieldValue(FieldName fieldName, \[int arrayIndex\])                                                 |                                                                                                                                |
| private container validateRelations(\[boolean onlyValidateCompositeRelations\], \[boolean onlyValidateModifiedRelations\]) |                                                                                                                                |
| public boolean validateWrite()                                                                                             | Determines whether the current record is valid and ready to be written.                                                        |
| public ValidTimeStateUpdate validTimeStateUpdateMode(ValidTimeStateUpdate validTimeStateUpdateMode)                        | Sets a valid time state update mode on the cursor.                                                                             |
| public CachedHow wasCached()                                                                                               | Specifies the location from which the data was retrieved.                                                                      |
| public str xml(\[int indent\])                                                                                             | Retrieves an XML string that represents the current object.                                                                    |
| public void doDelete()                                                                                                     | Deletes the current record from the table and bypasses any additional logic in the delete method of the table.                 |
| public void update()                                                                                                       | Updates the current record.                                                                                                    |
| public void merge(Common mergeInto)                                                                                        | Merges the current table with the specified table.                                                                             |
| public void clear()                                                                                                        | Removes all rows from the table buffer.                                                                                        |
| public void setXDSContext(\[str contextString\])                                                                           | Sets new XDS context.                                                                                                          |
| public void renamePrimaryKey()                                                                                             | Renames the foreign keys in other tables according to the change of the corresponding primary key value in this table.         |
| public void dispose()                                                                                                      | Releases resources that are used by the xRecord object.                                                                        |
| public void setConnection(Connection connection)                                                                           | Sets the user connection for this table.                                                                                       |
| public void delete()                                                                                                       | Deletes the current record from the table.                                                                                     |
| public void defaultField(FieldId fieldId)                                                                                  | Populates default values in a field in the table.                                                                              |
| private void dbOpInTransaction(\[boolean isWriteOperation\])                                                               | Makes sure that database operations are correctly closed if they fail.                                                         |
| public void write()                                                                                                        | Updates a record if it exists; otherwise, inserts a record.                                                                    |
| public void preRemoting()                                                                                                  | Is executed before a cross-tier call is about to be executed for the table that would pack its state to the other tier.        |
| public void modifiedFieldValue(FieldName fieldName, \[int arrayIndex\])                                                    | Modifies the specified field to the original value.                                                                            |
| public void defaultRow()                                                                                                   | Populates default values in fields in the table in the non-interactive case.                                                   |
| public void reread()                                                                                                       | Rereads the record from the table.                                                                                             |
| public void modifiedField(FieldId fieldId)                                                                                 | Modifies the specified field to the original.                                                                                  |
| public void ttsabort()                                                                                                     | Aborts a transaction that was started by a call to the ttsbegin method.                                                        |
| public void insert()                                                                                                       | Inserts the record into the table.                                                                                             |
| public void doClear()                                                                                                      | Removes all rows from the table buffer and bypasses any additional logic in the clear method of the table.                     |
| public void initValue()                                                                                                    | Initializes a field to the default value.                                                                                      |
| public void doUpdate()                                                                                                     | Updates the current record and bypasses any additional logic in the update method of the table.                                |
| public void ttsbegin()                                                                                                     | Starts a transaction that can be either committed by the ttscommit method or aborted by the ttsabort method.                   |
| public void setCrossPartition(boolean newValue)                                                                            | Sets or resets cross-partitioning for the table.                                                                               |
| public void setTmpData(Common cursor)                                                                                      | Sets the contents of the temporary table to the specified data.                                                                |
| public void ttscommit()                                                                                                    | Commits a transaction that was started by a call to the ttsbegin method.                                                       |
| public void setFieldValue(str fieldName, AnyType value, \[int arrayIndex\])                                                | Sets the field value in the record buffer.                                                                                     |
| public void doInsert()                                                                                                     | Inserts the record into the table and bypasses any additional logic in the insert method of the table.                         |
| public void setSQLTracing(\[boolean tracingmode\])                                                                         | Enables or disables SQL tracing mode.                                                                                          |
| public void postLoad()                                                                                                     | Is executed after a record is read.                                                                                            |

## Method aosValidateDelete

Validates on the server that the specified record can be deleted from a table.

```xpp
public boolean aosValidateDelete()
```

### Return Value - aosValidateDelete

true if the record can be deleted; otherwise, false.

## Method aosValidateInsert

Validates on the server that the specified record can be inserted.

```xpp
public boolean aosValidateInsert()
```

### Return Value - aosValidateInsert

true if the record can be inserted; otherwise, false.

## Method aosValidateRead

Validates on the server that the specified record can be read.

```xpp
public boolean aosValidateRead()
```

### Return Value - aosValidateRead

true if the record can be read; otherwise, false.

## Method aosValidateUpdate

Validates on the server that the specified record can be updated.

```xpp
public boolean aosValidateUpdate()
```

### Return Value - aosValidateUpdate

true if the record can be updated; otherwise, false.

## Method buf2con

Packs the table buffers of an xRecord instance into an X++ container.

```xpp
public container buf2con([boolean packOrigBuffer])
```

### Parameters - buf2con

packOrigBuffer  

### Return Value - buf2con

A container that holds packed buffers.

## Method canSubmitToWorkflow

Indicates whether submission to workflow is possible.

```xpp
public boolean canSubmitToWorkflow([str workflowType])
```

### Parameters - canSubmitToWorkflow

workflowType  

### Return Value - canSubmitToWorkflow

true if submission is possible; otherwise, false.

## Method caption

Gets and sets the caption property of a table.

```xpp
public str caption()
```

### Return Value - caption

The caption of the table.

## Method checkInvalidFieldAccess

Gets and sets invalid field access.

```xpp
public boolean checkInvalidFieldAccess([boolean checkInvalidFieldAccess])
```

### Parameters - checkInvalidFieldAccess

checkInvalidFieldAccess  
The value to set; optional.

### Return Value - checkInvalidFieldAccess

true if invalid field access is set; otherwise, false.

## Method checkRecord

Gets and sets the property that indicates whether to check mandatory fields.

```xpp
public boolean checkRecord([boolean checkMandatoryFields])
```

### Parameters - checkRecord

checkMandatoryFields  
A Boolean value that indicates whether to check mandatory fields; optional.

### Return Value - checkRecord

true if mandatory fields are checked; otherwise, false.

## Method checkRestrictedDeleteActions

Gets and sets the property that indicates whether a record can be deleted.

```xpp
public boolean checkRestrictedDeleteActions([boolean checkRestrictedDeleteActions])
```

### Parameters - checkRestrictedDeleteActions

checkRestrictedDeleteActions  
A Boolean value that indicates whether a record can be deleted; optional.

### Return Value - checkRestrictedDeleteActions

true if the record can be deleted; otherwise, false.

### Remarks - checkRestrictedDeleteActions

The property is based on delete actions for a table, and whether the table allows for delete actions when corresponding records are in corresponding tables.

## Method company

Gets and sets the property that indicates a legal entity for the record.

```xpp
public SelectableDataArea company([SelectableDataArea company])
```

### Parameters - company

company  
A new legal entity for the record; optional.

### Return Value - company

The legal entity ID.

## Method con2buf

Unpacks a container into the table buffers.

```xpp
public Common con2buf(container container)
```

### Parameters - con2buf

container  

### Return Value - con2buf

## Method concurrencyModel

Gets and sets the default concurrency model to use to update records.

```xpp
public ConcurrencyModel concurrencyModel([ConcurrencyModel concurrencyModel])
```

### Parameters - concurrencyModel

concurrencyModel  
The new concurrency model, by default; optional.

### Return Value - concurrencyModel

The current value of the concurrency model property, by default.

## Method context

Gets and sets the context property.

```xpp
public int context([int newValue])
```

### Parameters - context

newValue  
The new value of the context property; optional.

### Return Value - context

The current value of the context property.

## Method data

Retrieves a row from the table.

```xpp
public Common data([Common cursor])
```

### Parameters - data

cursor  
The row to retrieve; optional.

### Return Value - data

The record buffer.

### Remarks - data

Partly because scenarios that involve table inheritance, we recommend that you instead use the following methods on the Global class: con2buf, buf2con, and buf2buf.

## Method dataSource

Retrieves the data source of the table.

```xpp
public FormObjectSet dataSource()
```

### Return Value - dataSource

The data source of the table.

## Method disableCache

Gets and sets the property that indicates whether caching is disabled.

```xpp
public boolean disableCache([boolean newValue])
```

### Parameters - disableCache

newValue  
A Boolean value that indicates whether caching is disabled.

### Return Value - disableCache

The new value of the disable cache property.

## Method doValidateDelete

Performs the action to validate that a record can be deleted.

```xpp
public boolean doValidateDelete()
```

### Return Value - doValidateDelete

## Method equal

Determines whether the specified object is equal to the current one.

```xpp
public boolean equal(Common cursor)
```

### Parameters - equal

cursor  
The object to check for equality.

### Return Value - equal

true if the objects are equal; otherwise, false.

### Remarks - equal

This method is overridden. The default implementation of the Object::equal method supports only reference equality. Derived classes can override the Object::equal method to support value equality.

## Method fieldAccessRight

Returns the field access right.

```xpp
public AccessRight fieldAccessRight(FieldName fieldName)
```

### Parameters - fieldAccessRight

fieldName  
The name of the field for which to obtain the field access right.

### Return Value - fieldAccessRight

The field access right for the field.

## Method fieldBufferAccessRight

Returns the field access right for the current record.

```xpp
public AccessRight fieldBufferAccessRight(FieldName fieldName)
```

### Parameters - fieldBufferAccessRight

fieldName  
The name of the field for which to obtain the field access right.

### Return Value - fieldBufferAccessRight

The field access right.

## Method fieldState

Sets or returns the state of a field in the table buffer.

```xpp
public FieldState fieldState(FieldId fieldId, [FieldState state])
```

### Parameters - fieldState

fieldId  

<!-- -->

state  

### Return Value - fieldState

The old state of the field.

## Method getAllowRedefault

Returns the list of fields that are allowed to re-default.

```xpp
public container getAllowRedefault()
```

### Return Value - getAllowRedefault

The container that holds the fields.

## Method getDefaultingDependencies

Returns the container that holds defaulting dependencies.

```xpp
public container getDefaultingDependencies()
```

### Return Value - getDefaultingDependencies

The container that holds defaulting dependencies.

## Method getExtension

Returns the table extension.

```xpp
public TableExtension getExtension()
```

### Return Value - getExtension

The table extension.

## Method getFieldValue

Gets the value of the specified field from a table buffer.

```xpp
public AnyType getFieldValue(str fieldName, [int arrayIndex])
```

### Parameters - getFieldValue

fieldName  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

### Return Value - getFieldValue

The value of a field.

### Remarks - getFieldValue

The arrayIndex parameter only applies to array fields. Either omit this parameter or specify 0 (zero) for fields that are not arrays. This method throws an ArgumentOutOfRange exception if the specified field is unknown.

## Method getInstanceRelationType

Returns the table name that corresponds to the InstanceRelationType ID.

```xpp
public str getInstanceRelationType()
```

### Return Value - getInstanceRelationType

The table name that corresponds to the InstanceRelationType ID.

## Method getPhysicalTableName

Return the physical table name, which, in the case of the SQL Temp DB table, is the table instance name.

```xpp
public str getPhysicalTableName()
```

### Return Value - getPhysicalTableName

The physical table name or the table instance name.

## Method getPresenceFieldData

Retrieves the PresenceInfo value from the specified field.

```xpp
public PresenceInfo getPresenceFieldData(FieldId fieldId, AnyType fieldValue)
```

### Parameters - getPresenceFieldData

fieldId  

<!-- -->

fieldValue  

### Return Value - getPresenceFieldData

## Method getSQLStatement

Gets the SQL statement that is used to return records from the database.

```xpp
public str getSQLStatement()
```

### Return Value - getSQLStatement

The string that contains the SQL statement.

## Method getTableInInstanceHierarchy

```xpp
public Common getTableInInstanceHierarchy(TableId tableId)
```

### Parameters - getTableInInstanceHierarchy

tableId  

### Return Value - getTableInInstanceHierarchy

## Method getTableType

Indicates the type of the table.

```xpp
public TableType getTableType()
```

### Return Value - getTableType

The type of the table (Regular, InMemory, or TempDB).

## Method hasRelatedTable

Indicates whether a foreign key constraint buffer is linked with the table.

```xpp
public boolean hasRelatedTable(str relatedRoleName)
```

### Parameters - hasRelatedTable

relatedRoleName  

### Return Value - hasRelatedTable

true if a foreign key constraint buffer is linked with the table; otherwise, false.

## Method helpField

Retrieves a string that contains the Help text for the specified field.

```xpp
public str helpField(FieldId fieldId)
```

### Parameters - helpField

fieldId  
The field for which to retrieve the Help text.

### Return Value - helpField

The Help text for the specified field.

## Method inputStatus

Sets or returns the current input status of the table buffer.

```xpp
public FieldState inputStatus([FieldState inputStatus])
```

### Parameters - inputStatus

inputStatus  

### Return Value - inputStatus

The old input status.

## Method interactiveContext

Sets or returns the current interactive context of the table buffer.

```xpp
public boolean interactiveContext([boolean context])
```

### Parameters - interactiveContext

context  

### Return Value - interactiveContext

The current interactive context of the table buffer.

## Method isFieldDataRetrieved

Checks whether the data of the given field has been retrieved.

```xpp
public boolean isFieldDataRetrieved(str fieldName, [int arrayIndex])
```

### Parameters - isFieldDataRetrieved

fieldName  

<!-- -->

arrayIndex  

### Return Value - isFieldDataRetrieved

true if the data has been retrieved; otherwise, false.

## Method isFieldSet

Checks whether a field has a Set or Defaulted state.

```xpp
public boolean isFieldSet(FieldId fieldId)
```

### Parameters - isFieldSet

fieldId  

### Return Value - isFieldSet

true if field has a Set or Defaulted state; otherwise, false.

## Method isFormDataSource

Indicates whether the data source is a form.

```xpp
public boolean isFormDataSource()
```

### Return Value - isFormDataSource

true if the data source is a form; otherwise, false.

## Method isNewRecord

Returns true if the record is a new record that hasn't been persisted yet.

```xpp
public boolean isNewRecord()
```

### Return Value - isNewRecord

true if the record is a new record that hasn't been persisted yet; otherwise, false.

## Method isPartOfUOWSaveChanges

```xpp
public boolean isPartOfUOWSaveChanges()
```

### Return Value - isPartOfUOWSaveChanges

## Method isTempDb

Indicates whether the type of the table is SQL TempDB.

```xpp
public boolean isTempDb()
```

### Return Value - isTempDb

true if the type of the table is SQL TempDB; otherwise, false.

## Method isTmp

Indicates whether this is a temporary table.

```xpp
public boolean isTmp()
```

### Return Value - isTmp

true if this is a temporary table; otherwise, false.

## Method joinChild

Finds the join child of the current record.

```xpp
public Common joinChild()
```

### Return Value - joinChild

The join child of the current record.

## Method joinParent

Finds the join parent of the current record.

```xpp
public Common joinParent()
```

### Return Value - joinParent

The join parent of the current record.

## Method linkPhysicalTableInstance

Checks whether there is a link for the physical table instance for the record.

```xpp
public boolean linkPhysicalTableInstance([Common record])
```

### Parameters - linkPhysicalTableInstance

record  

### Return Value - linkPhysicalTableInstance

A Boolean value that indicates whether a link is available.

## Method orig

Retrieves the original values of the current record.

```xpp
public Common orig()
```

### Return Value - orig

### Remarks - orig

Partly because of scenarios that involve table inheritance, we recommend that you instead use the following methods on the Global class: con2buf, buf2con, and buf2buf.

## Method overwriteSystemfields

Gets and sets the property that indicates whether system fields can be overwritten.

```xpp
public boolean overwriteSystemfields([boolean allowOverwrite])
```

### Parameters - overwriteSystemfields

allowOverwrite  
A Boolean value that indicates whether system fields can be overwritten; optional.

### Return Value - overwriteSystemfields

true if system fields can be overwritten; otherwise, false.

## Method queryTimedOut

Indicates whether the query exceeded the time limit for execution.

```xpp
public boolean queryTimedOut()
```

### Return Value - queryTimedOut

true if the query exceeded the time limit for execution; otherwise, false.

## Method queryTimeout

Gets and sets the property that indicates the time limit for the execution of a query.

```xpp
public int queryTimeout([int seconds], [boolean raiseException])
```

### Parameters - queryTimeout

seconds  

<!-- -->

raiseException  

### Return Value - queryTimeout

The current value of the query time-out property.

## Method readCommittedLock

```xpp
public boolean readCommittedLock([boolean readCommittedLock])
```

### Parameters - readCommittedLock

readCommittedLock  

### Return Value - readCommittedLock

## Method readPast

Gets and sets the property that indicates whether to skip rows that are locked by other processes when a record is read.

```xpp
public boolean readPast([boolean skipLockedRows])
```

### Parameters - readPast

skipLockedRows  
A Boolean value that indicates whether to skip rows that are locked; optional.

### Return Value - readPast

true if locked rows should be skipped; otherwise, false.

## Method recordLevelSecurity

Gets and sets the property that indicates whether to apply security on a record level.

```xpp
public boolean recordLevelSecurity([boolean newValue])
```

### Parameters - recordLevelSecurity

newValue  
A Boolean value that indicates whether to apply security on a record level; optional.

### Return Value - recordLevelSecurity

true if security should be applied on a record level; otherwise, false.

## Method relatedTable

Sets or returns the related buffer of a link of a table buffer.

```xpp
public Common relatedTable(str name, [Common buffer])
```

### Parameters - relatedTable

name  

<!-- -->

buffer  

### Return Value - relatedTable

The related buffer of a link of a table buffer.

## Method RowCount

Retrieves the number of rows in the table.

```xpp
public Int64 RowCount()
```

### Return Value - RowCount

The number of rows in the table.

## Method selectForUpdate

Gets and sets the property that indicates whether to select records for update when they are read.

```xpp
public boolean selectForUpdate([boolean lockRecordsExclusive])
```

### Parameters - selectForUpdate

lockRecordsExclusive  
A Boolean value that indicates whether to read records for update; optional.

### Return Value - selectForUpdate

true if records should be read for update; otherwise, false.

## Method selectLocked

Indicates whether to select locked records.

```xpp
public boolean selectLocked([boolean lockRecordsShared])
```

### Parameters - selectLocked

lockRecordsShared  
A Boolean value that indicates whether to select locked records.

### Return Value - selectLocked

true if locked records should be selected; otherwise, false.

## Method selectRefRecord

Selects the record by referenced field ID.

```xpp
public Common selectRefRecord(FieldId referenceFieldId)
```

### Parameters - selectRefRecord

referenceFieldId  
The referenced field ID.

### Return Value - selectRefRecord

The record buffer.

## Method selectWithRepeatableRead

Gets and sets the property that indicates whether repeatable read is enabled.

```xpp
public boolean selectWithRepeatableRead([boolean useRepeatableRead])
```

### Parameters - selectWithRepeatableRead

useRepeatableRead  
A Boolean value that indicates whether repeatable read is enabled; optional.

### Return Value - selectWithRepeatableRead

true if repeatable read is enabled; otherwise, false.

## Method setTempDB

```xpp
public boolean setTempDB()
```

### Return Value - setTempDB

## Method setTmp

Sets the table so that it is not persisted to the database.

```xpp
public boolean setTmp()
```

### Return Value - setTmp

true if the operation was successful; otherwise, false.

## Method skipAosValidation

Gets and sets the property that indicates whether to skip validation Application Object Server (AOS).

```xpp
public boolean skipAosValidation([boolean newValue])
```

### Parameters - skipAosValidation

newValue  
A Boolean value that indicates whether to skip AOS validation.

### Return Value - skipAosValidation

true if AOS validation should be skipped; otherwise, false.

### Remarks - skipAosValidation

If an attacker can control input to the skipAosValidation method, a security risk exists. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the SkipAOSValidationPermission class. Make sure that the user has development user rights by setting the security key to SysDevelopment on the control that calls this method.

## Method skipDatabaseLog

Gets and sets the property that indicates whether to skip database log requests.

```xpp
public boolean skipDatabaseLog([boolean newValue])
```

### Parameters - skipDatabaseLog

newValue  
A Boolean value that indicates whether to skip database log requests; optional.

### Return Value - skipDatabaseLog

true if database log requests should be skipped; otherwise, false.

## Method skipDataMethods

Gets and sets the property that indicates whether to discard overloaded methods.

```xpp
public boolean skipDataMethods([boolean newValue])
```

### Parameters - skipDataMethods

newValue  
A Boolean value that indicates whether to discard overloaded methods; optional.

### Return Value - skipDataMethods

true if overloaded methods should be discarded; otherwise, false.

## Method skipDeleteActions

Gets and sets the property that indicates whether to skip delete actions on the table.

```xpp
public boolean skipDeleteActions([boolean newValue])
```

### Parameters - skipDeleteActions

newValue  
A Boolean value that indicates whether to ignore requests to delete records; optional.

### Return Value - skipDeleteActions

true if requests to delete records should be ignored; otherwise, false.

### Remarks - skipDeleteActions

This method works only when you are using a set-based operation, such as the delete\_from statement. If you use it on a row-based operation, such as the xRecord.delete method, the property will not be respected, and the delete action will still be called.

## Method skipDeleteMethod

Gets and sets the property that indicates whether to discard overloaded methods.

```xpp
public boolean skipDeleteMethod([boolean newValue])
```

### Parameters - skipDeleteMethod

newValue  
A Boolean value that indicates whether to discard overloaded methods; optional.

### Return Value - skipDeleteMethod

true if overloaded methods should be discarded; otherwise, false.

## Method skipEvents

Provides an option to turn off calling the Application.event\* methods for the lifetime of an xRecord object.

```xpp
public boolean skipEvents([boolean newValue])
```

### Parameters - skipEvents

newValue  
A Boolean value that indicates whether to skip events; optional.

### Return Value - skipEvents

true if events are skipped; otherwise, false.

### Remarks - skipEvents

This method resembles the xRecord.skipDatabaseLog method. The skipEvents method is also used internally in the kernel to skip events that make no sense to generate; this is consistent with the current behavior of the xRecord.skipDatabaseLog method:

-   The Application.deleteCompany method: Event generation is turned off for the duration of a company delete operation. This is an admin operation, and it could cause performance issues to support events in this case.
-   The SqlDataDictionary.tableDelete method: Event generation is turned off for the duration of a table delete. This is an admin operation, and it could cause performance issues to support events in this case.
-   The RecordInsertList class, which implements array insert capabilities in the kernel, takes an optional argument, \_skipEvents = false, in the new method that will conditionally skip events as specified by a developer. Even if events are not skipped, this will not make the kernel rewrite the SQL.
-   When a primary key is renamed, event generation is turned off for the duration of the rename operation. This includes a primary key in one record and can include a foreign key in many records. After the rename operation, the eventRenameKey method is called.

## Method skipPostLoad

Gets and sets the property that indicates whether to skip executing the xRecord.postLoad method on the table.

```xpp
public boolean skipPostLoad([boolean newValue])
```

### Parameters - skipPostLoad

newValue  
A Boolean value that indicates whether to skip executing the postLoad method on the table; optional.

### Return Value - skipPostLoad

true to skip executing the postLoad method; otherwise, false.

## Method skipTTSCheck

Gets and sets the property that indicates whether to skip the check to determine whether the record is selected for update.

```xpp
public boolean skipTTSCheck([boolean newValue])
```

### Parameters - skipTTSCheck

newValue  
A Boolean value that indicates whether to skip the check; optional.

### Return Value - skipTTSCheck

true if the TTS check should be skipped; otherwise, false.

## Method suppressWarnings

Gets and sets the property that indicates whether to suppress warnings for this pointer.

```xpp
public boolean suppressWarnings([boolean newValue])
```

### Parameters - suppressWarnings

newValue  
A Boolean value that indicates whether to suppress warnings for this pointer; optional.

### Return Value - suppressWarnings

true if warnings for this pointer should be suppressed; otherwise, false.

## Method tableAccessRight

Returns the table access right.

```xpp
public AccessRight tableAccessRight()
```

### Return Value - tableAccessRight

The table access right value.

## Method tableBufferAccessRight

Returns the table access right for the current record.

```xpp
public AccessRight tableBufferAccessRight()
```

### Return Value - tableBufferAccessRight

The table access right for the current record.

## Method takeOwnershipOfTempDBTable

```xpp
public boolean takeOwnershipOfTempDBTable(boolean newValue)
```

### Parameters - takeOwnershipOfTempDBTable

newValue  

### Return Value - takeOwnershipOfTempDBTable

## Method toolTipField

Retrieves the HelpText value for the specified field.

```xpp
public str toolTipField(FieldId fieldId)
```

### Parameters - toolTipField

fieldId  
The field for which to retrieve the HelpText value.

### Return Value - toolTipField

The HelpText value of the specified field.

## Method toolTipRecord

Retrieves the ToolTip value for the current record.

```xpp
public str toolTipRecord()
```

### Return Value - toolTipRecord

The ToolTip value for the current record.

## Method usageCount

Retrieves the current number of references (the value of the reference counter) that the object has.

```xpp
public int usageCount()
```

### Return Value - usageCount

The current number of references that the object has.

### Remarks - usageCount

This method is overridden. When an object is created, its reference counter equals 1. When a new reference is created, its value increases. As a reference goes out of scope, its value decreases.

## Method useExistingTempDBTable

```xpp
public boolean useExistingTempDBTable(str physicalTempTableName)
```

### Parameters - useExistingTempDBTable

physicalTempTableName  

### Return Value - useExistingTempDBTable

## Method validateDelete

Determines whether the current record is valid and ready to be deleted from the database.

```xpp
public boolean validateDelete()
```

### Return Value - validateDelete

true if the current record can be deleted; otherwise, false.

## Method validateField

Determines whether the specified field is valid.

```xpp
public boolean validateField(FieldId fieldIdToCheck)
```

### Parameters - validateField

fieldIdToCheck  
The field ID of the field to validate.

### Return Value - validateField

true if the specified field is valid; otherwise, false.

## Method validateFieldValue

```xpp
public boolean validateFieldValue(FieldName fieldName, [int arrayIndex])
```

### Parameters - validateFieldValue

fieldName  

<!-- -->

arrayIndex  

### Return Value - validateFieldValue

## Method validateRelations

```xpp
private container validateRelations([boolean onlyValidateCompositeRelations], [boolean onlyValidateModifiedRelations])
```

### Parameters - validateRelations

onlyValidateCompositeRelations  

<!-- -->

onlyValidateModifiedRelations  

### Return Value - validateRelations

## Method validateWrite

Determines whether the current record is valid and ready to be written.

```xpp
public boolean validateWrite()
```

### Return Value - validateWrite

true if the current record can be written; otherwise, false.

## Method validTimeStateUpdateMode

Sets a valid time state update mode on the cursor.

```xpp
public ValidTimeStateUpdate validTimeStateUpdateMode(ValidTimeStateUpdate validTimeStateUpdateMode)
```

### Parameters - validTimeStateUpdateMode

validTimeStateUpdateMode  

### Return Value - validTimeStateUpdateMode

The old value of the valid time state update mode.

## Method wasCached

Specifies the location from which the data was retrieved.

```xpp
public CachedHow wasCached()
```

### Return Value - wasCached

A CachedHow enumeration value that indicates the location from which the data was retrieved.

## Method xml

Retrieves an XML string that represents the current object.

```xpp
public str xml([int indent])
```

### Parameters - xml

indent  
An integer that indicates the number of spaces to use for indentation in the XML string.

### Return Value - xml

An XML string that represents the current object.

### Remarks - xml

This method can be overridden to return values that are meaningful for that type.

## Method doDelete

Deletes the current record from the table and bypasses any additional logic in the delete method of the table.

```xpp
public void doDelete()
```

## Method update

Updates the current record.

```xpp
public void update()
```

## Method merge

Merges the current table with the specified table.

```xpp
public void merge(Common mergeInto)
```

### Parameters - merge

mergeInto  
The table to merge with.

## Method clear

Removes all rows from the table buffer.

```xpp
public void clear()
```

## Method setXDSContext

Sets new XDS context.

```xpp
public void setXDSContext([str contextString])
```

### Parameters - setXDSContext

contextString  

## Method renamePrimaryKey

Renames the foreign keys in other tables according to the change of the corresponding primary key value in this table.

```xpp
public void renamePrimaryKey()
```

## Method dispose

Releases resources that are used by the xRecord object.

```xpp
public void dispose()
```

## Method setConnection

Sets the user connection for this table.

```xpp
public void setConnection(Connection connection)
```

### Parameters - setConnection

connection  

## Method delete

Deletes the current record from the table.

```xpp
public void delete()
```

## Method defaultField

Populates default values in a field in the table.

```xpp
public void defaultField(FieldId fieldId)
```

### Parameters - defaultField

fieldId  

## Method dbOpInTransaction

Makes sure that database operations are correctly closed if they fail.

```xpp
private void dbOpInTransaction([boolean isWriteOperation])
```

### Parameters - dbOpInTransaction

isWriteOperation  
A Boolean value that indicates whether the operation is a write operation; optional.

## Method write

Updates a record if it exists; otherwise, inserts a record.

```xpp
public void write()
```

## Method preRemoting

Is executed before a cross-tier call is about to be executed for the table that would pack its state to the other tier.

```xpp
public void preRemoting()
```

## Method modifiedFieldValue

Modifies the specified field to the original value.

```xpp
public void modifiedFieldValue(FieldName fieldName, [int arrayIndex])
```

### Parameters - modifiedFieldValue

fieldName  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

## Method defaultRow

Populates default values in fields in the table in the non-interactive case.

```xpp
public void defaultRow()
```

## Method reread

Rereads the record from the table.

```xpp
public void reread()
```

## Method modifiedField

Modifies the specified field to the original.

```xpp
public void modifiedField(FieldId fieldId)
```

### Parameters - modifiedField

fieldId  
The field ID to modify.

## Method ttsabort

Aborts a transaction that was started by a call to the ttsbegin method.

```xpp
public void ttsabort()
```

## Method insert

Inserts the record into the table.

```xpp
public void insert()
```

## Method doClear

Removes all rows from the table buffer and bypasses any additional logic in the clear method of the table.

```xpp
public void doClear()
```

## Method initValue

Initializes a field to the default value.

```xpp
public void initValue()
```

## Method doUpdate

Updates the current record and bypasses any additional logic in the update method of the table.

```xpp
public void doUpdate()
```

## Method ttsbegin

Starts a transaction that can be either committed by the ttscommit method or aborted by the ttsabort method.

```xpp
public void ttsbegin()
```

## Method setCrossPartition

Sets or resets cross-partitioning for the table.

```xpp
public void setCrossPartition(boolean newValue)
```

### Parameters - setCrossPartition

newValue  
A new Boolean value to set or reset cross-partitioning.

## Method setTmpData

Sets the contents of the temporary table to the specified data.

```xpp
public void setTmpData(Common cursor)
```

### Parameters - setTmpData

cursor  
The new data for the temporary table.

## Method ttscommit

Commits a transaction that was started by a call to the ttsbegin method.

```xpp
public void ttscommit()
```

## Method setFieldValue

Sets the field value in the record buffer.

```xpp
public void setFieldValue(str fieldName, AnyType value, [int arrayIndex])
```

### Parameters - setFieldValue

fieldName  
The array index of the field; optional.

<!-- -->

value  
The array index of the field; optional.

<!-- -->

arrayIndex  
The array index of the field; optional.

### Remarks - setFieldValue

The arrayIndex parameter applies only to array fields. Either omit this parameter or specify0 (zero) for fields that are not arrays. This method throws an ArgumentOutOfRange exception if the specified field is unknown or a TypeMismatch exception if the value parameter is incompatible with the specified field..

## Method doInsert

Inserts the record into the table and bypasses any additional logic in the insert method of the table.

```xpp
public void doInsert()
```

## Method setSQLTracing

Enables or disables SQL tracing mode.

```xpp
public void setSQLTracing([boolean tracingmode])
```

### Parameters - setSQLTracing

tracingmode  

## Method postLoad

Is executed after a record is read.

```xpp
public void postLoad()
```

