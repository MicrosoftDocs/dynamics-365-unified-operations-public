---
# required metadata

title: System tables | Microsoft Docs
description: This wiki describes the system tables.
author: RobinARH
manager: AnnBe
ms.date: 2016-07-27 16:39:02
ms.topic: reference
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: 61
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 104503
ms.assetid: 48c83eab-659c-447d-ab79-93a6447a124f
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# System tables

This wiki describes the system tables.

[]()Common
----------

The Common table is the base class for all tables. It does not contain any data. It is primarily used in X++ code to refer to any table in a polymorphic way.

### Methods

| Method                       | Description                                                                                                                 |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| aosValidateDelete            | Validates on the server that the specified record can be deleted from a table.                                              |
| aosValidateInsert            | Validates on the server that the specified record can be inserted.                                                          |
| aosValidateRead              | Validates on the server that the specified record can be read.                                                              |
| aosValidateUpdate            | Validates on the server that the specified record can be updated.                                                           |
| buf2con                      | Packs the table buffers of an xRecord instance into an X++ container.                                                       |
| canSubmitToWorkflow          | Indicates whether submission to workflow is possible.                                                                       |
| caption                      | Gets and sets the caption property of a table.                                                                              |
| checkInvalidFieldAccess      | Gets and sets invalid field access.                                                                                         |
| checkRecord                  | Gets and sets the property that indicates whether to check mandatory fields.                                                |
| checkRestrictedDeleteActions | Gets and sets the property that indicates whether a record can be deleted.                                                  |
| clear                        | Removes all rows from the table buffer.                                                                                     |
| company                      | Gets and sets the property that indicates a legal entity for the record.                                                    |
| con2buf                      | Unpacks a container into the table buffers.                                                                                 |
| concurrencyModel             | Gets and sets the default concurrency model to use to update records.                                                       |
| context                      | Gets and sets the context property.                                                                                         |
| data                         | Retrieves a row from the table.                                                                                             |
| dataSource                   | Retrieves the data source of the table.                                                                                     |
| dbOpInTransaction            | Makes sure that database operations are correctly closed if they fail.                                                      |
| defaultField                 | Populates default values in a field in the table.                                                                           |
| defaultRow                   | Populates default values in fields in the table in the non-interactive case.                                                |
| delete                       | Deletes the current record from the table.                                                                                  |
| disableCache                 | Gets and sets the property that indicates whether caching is disabled.                                                      |
| dispose                      | Releases resources that are used by the xRecord object.                                                                     |
| doClear                      | Removes all rows from the table buffer and bypasses any additional logic in the clear method of the table.                  |
| doDelete                     | Deletes the current record from the table and bypasses any additional logic in the delete method of the table.              |
| doInsert                     | Inserts the record into the table and bypasses any additional logic in the insert method of the table.                      |
| doUpdate                     | Updates the current record and bypasses any additional logic in the update method of the table.                             |
| doValidateDelete             | Performs the action to validate that a record can be deleted.                                                               |
| equal                        | Determines whether the specified object is equal to the current one.                                                        |
| fieldAccessRight             | Returns the field access right.                                                                                             |
| fieldBufferAccessRight       | Returns the field access right for the current record.                                                                      |
| fieldState                   | Sets or returns the state of a field in the table buffer.                                                                   |
| getAllowRedefault            | Returns the list of fields that are allowed to re-default.                                                                  |
| getDefaultingDependencies    | Returns the container that holds defaulting dependencies.                                                                   |
| getExtension                 | Returns the table extension.                                                                                                |
| getFieldValue                | Gets the value of the specified field from a table buffer.                                                                  |
| getInstanceRelationType      | Returns the table name that corresponds to the InstanceRelationType ID.                                                     |
| getPhysicalTableName         | Return the physical table name, which, in the case of the SQL Temp DB table, is the table instance name.                    |
| getPresenceFieldData         | Retrieves the PresenceInfo value from the specified field.                                                                  |
| getSQLStatement              | Gets the SQL statement that is used to return records from the database.                                                    |
| getTableInInstanceHierarchy  |                                                                                                                             |
| getTableType                 | Indicates the type of the table.                                                                                            |
| helpField                    | Retrieves a string that contains the Help text for the specified field.                                                     |
| initValue                    | Initializes a field to the default value.                                                                                   |
| inputStatus                  | Sets or returns the current input status of the table buffer.                                                               |
| insert                       | Inserts the record into the table.                                                                                          |
| interactiveContext           | Sets or returns the current interactive context of the table buffer.                                                        |
| isFieldDataRetrieved         | Checks whether the data of the given field has been retrieved.                                                              |
| isFieldSet                   | Checks whether a field has a Set or Defaulted state.                                                                        |
| isFormDataSource             | Indicates whether the data source is a form.                                                                                |
| isNewRecord                  | Returns true if the record is a new record that hasn’t been persisted yet.                                                  |
| isPartOfUOWSaveChanges       |                                                                                                                             |
| isTempDb                     | Indicates whether the type of the table is SQL TempDB.                                                                      |
| isTmp                        | Indicates whether this is a temporary table.                                                                                |
| joinChild                    | Finds the join child of the current record.                                                                                 |
| joinParent                   | Finds the join parent of the current record.                                                                                |
| linkPhysicalTableInstance    | Checks whether there is a link for the physical table instance for the record.                                              |
| merge                        | Merges the current table with the specified table.                                                                          |
| modifiedField                | Modifies the specified field to the original.                                                                               |
| modifiedFieldValue           | Modifies the specified field to the original value.                                                                         |
| orig                         | Retrieves the original values of the current record.                                                                        |
| overwriteSystemfields        | Gets and sets the property that indicates whether system fields can be overwritten.                                         |
| postLoad                     | Is executed after a record is read.                                                                                         |
| queryTimedOut                | Indicates whether the query exceeded the time limit for execution.                                                          |
| queryTimeout                 | Gets and sets the property that indicates the time limit for the execution of a query.                                      |
| readCommittedLock            |                                                                                                                             |
| readPast                     | Gets and sets the property that indicates whether to skip rows that are locked by other processes when a record is read.    |
| recordLevelSecurity          | Gets and sets the property that indicates whether to apply security on a record level.                                      |
| relatedTable                 | Sets or returns the related buffer of a link of a table buffer.                                                             |
| hasRelatedTable              | Indicates whether a foreign key constraint buffer is linked with the table.                                                 |
| renamePrimaryKey             | Renames the foreign keys in other tables according to the change of the corresponding primary key value in this table.      |
| reread                       | Rereads the record from the table.                                                                                          |
| RowCount                     | Retrieves the number of rows in the table.                                                                                  |
| selectForUpdate              | Gets and sets the property that indicates whether to select records for update when they are read.                          |
| selectLocked                 | Indicates whether to select locked records.                                                                                 |
| selectRefRecord              | Selects the record by referenced field ID.                                                                                  |
| selectWithRepeatableRead     | Gets and sets the property that indicates whether repeatable read is enabled.                                               |
| setConnection                | Sets the user connection for this table.                                                                                    |
| setCrossPartition            | Sets or resets cross-partitioning for the table.                                                                            |
| setFieldValue                | Sets the field value in the record buffer.                                                                                  |
| setSQLTracing                | Enables or disables SQL tracing mode.                                                                                       |
| setTempDB                    |                                                                                                                             |
| setTmp                       | Sets the table so that it is not persisted to the database.                                                                 |
| setTmpData                   | Sets the contents of the temporary table to the specified data.                                                             |
| setXDSContext                | Sets new XDS context.                                                                                                       |
| skipDatabaseLog              | Gets and sets the property that indicates whether to skip database log requests.                                            |
| skipDataMethods              | Gets and sets the property that indicates whether to discard overloaded methods.                                            |
| skipDeleteActions            | Gets and sets the property that indicates whether to skip delete actions on the table.                                      |
| skipDeleteMethod             | Gets and sets the property that indicates whether to discard overloaded methods.                                            |
| skipEvents                   | Provides an option to turn off calling the Application.event\* methods for the lifetime of an xRecord object.               |
| skipPostLoad                 | Gets and sets the property that indicates whether to skip executing the xRecord.postLoad method on the table.               |
| skipTTSCheck                 | Gets and sets the property that indicates whether to skip the check to determine whether the record is selected for update. |
| suppressWarnings             | Gets and sets the property that indicates whether to suppress warnings for this pointer.                                    |
| tableAccessRight             | Returns the table access right.                                                                                             |
| tableBufferAccessRight       | Returns the table access right for the current record.                                                                      |
| toolTipField                 | Retrieves the HelpText value for the specified field.                                                                       |
| toolTipRecord                | Retrieves the ToolTip value for the current record.                                                                         |
| ttsabort                     | Aborts a transaction that was started by a call to the ttsbegin method.                                                     |
| ttsbegin                     | Starts a transaction that can be either committed by the ttscommit method or aborted by the ttsabort method.                |
| ttscommit                    | Commits a transaction that was started by a call to the ttsbegin method.                                                    |
| update                       | Updates the current record.                                                                                                 |
| validateDelete               | Determines whether the current record is valid and ready to be deleted from the database.                                   |
| validateField                | Determines whether the specified field is valid.                                                                            |
| validateFieldValue           |                                                                                                                             |
| validateRelations            |                                                                                                                             |
| validateWrite                | Determines whether the current record is valid and ready to be written.                                                     |
| validTimeStateUpdateMode     | Sets a valid time state update mode on the cursor.                                                                          |
| wasCached                    | Specifies the location from which the data was retrieved.                                                                   |
| write                        | Updates a record if it exists; otherwise, inserts a record.                                                                 |
| xml                          | Retrieves an XML string that represents the current object.                                                                 |
| takeOwnershipOfTempDBTable   |                                                                                                                             |
| useExistingTempDBTable       |                                                                                                                             |

### Fields

| Field                 | Type        | Extended Type         | Enumeration Type | Description |
|-----------------------|-------------|-----------------------|------------------|-------------|
| CreatedBy             | String      | CreatedBy             |                  |             |
| CreatedDateTime       | UtcDateTime | CreatedDateTime       |                  |             |
| CreatedTransactionId  | Int64       | CreatedTransactionId  |                  |             |
| dataAreaId            | String      | DataAreaId            |                  |             |
| DEL\_CreatedTime      | Int         | DEL\_CreatedTime      |                  |             |
| DEL\_ModifiedTime     | Int         | DEL\_ModifiedTime     |                  |             |
| ModifiedBy            | String      | ModifiedBy            |                  |             |
| ModifiedDateTime      | UtcDateTime | ModifiedDateTime      |                  |             |
| ModifiedTransactionId | Int64       | ModifiedTransactionId |                  |             |
| Partition             | Int64       | Partition             |                  |             |
| RecId                 | Int64       | RecId                 |                  |             |
| recVersion            | Integer     | RecVersion            |                  |             |
| RelationType          | Int64       | RelationType          |                  |             |
| RowNumber             | Int         | RowNumber             |                  |             |
| SequenceNum           | Int64       | SequenceNum           |                  |             |
| TableId               | Int         | TableId               |                  |             |
| UnionAllBranchId      | Int         | UnionAllBranchId      |                  |             |

### Relations

| Relation   | Table    |
|------------|----------|
| dataAreaId | DataArea |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| RecId | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common)

## []()DataArea
The DataArea table contains a list of companies that have been created in the database.

### Fields

| Field        | Type    | Extended Type | Enumeration Type | Description                                                                                                               |
|--------------|---------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| alwaysNative | Enum    |               | boolean          |                                                                                                                           |
| id           | String  | DataAreaId    |                  | ID for an area of data                                                                                                    |
| isVirtual    | Enum    |               | boolean          |                                                                                                                           |
| name         | String  | UserIdStr     |                  | Name                                                                                                                      |
| Partition    | Int64   | Partition     |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId        | Int64   | RecId         |                  |                                                                                                                           |
| recVersion   | Integer | RecVersion    |                  |                                                                                                                           |
| timeZone     | Enum    |               | Timezone         |                                                                                                                           |

### Relations

| Relation  | Table      |
|-----------|------------|
| id        | DataArea   |
| Partition | Partitions |

### Indexes

| Index  | Allow Duplicates | Fields |
|--------|------------------|--------|
| Id     | No               |        |
| IdOnly | Yes              |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DataArea Table](#dataarea)

## []()DatabaseLog
The DatabaseLog table stores configuration information for the SysDatabaseLog table.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| domainId          | String      | DomainId          |                  | ID for the domain                                                                                                         |
| logField          | Integer     | FieldId           |                  | ID for the field                                                                                                          |
| logTable          | Integer     | TableId           |                  | ID for the table                                                                                                          |
| logType           | Enum        |                   | DatabaseLogType  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |

### Field Groups

| Field Group      | Fields |
|------------------|--------|
| logFieldRelation |        |

### Relations

| Relation              | Table           |
|-----------------------|-----------------|
| Relation\_DatabaseLog | DEL\_DomainInfo |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| Loglist | No               |        |
| RecId   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DatabaseLog Table](#databaselog)

## []()DEL\_AccessRightsList
Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| accessType        | Enum        |                   | AccessType       |                                                                                                                           |
| accessTypeFkeyUse | Enum        |                   | AccessType       |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| domainId          | String      | DomainId          |                  | ID for the domain                                                                                                         |
| elementName       | String      | UtilElementName   |                  | Name of the application element.                                                                                          |
| groupId           | String      | UserGroupId       |                  | ID for the user group                                                                                                     |
| id                | Int         |                   |                  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| parentId          | Int         |                   |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recordType        | Enum        |                   | AccessRecordType |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |

### Relations

| Relation                    | Table              |
|-----------------------------|--------------------|
| Relation\_AccessRightsList1 | UtilIdElements     |
| Relation\_AccessRightsList2 | UtilIdElements     |
| Relation\_AccessRightsList3 | DEL\_DomainInfo    |
| Relation\_AccessRightsList4 | DEL\_UserGroupInfo |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| Element | Yes              |        |
| Group   | No               |        |
| RecId   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DEL\_AccessRightsList Table](#del_accessrightslist)

## []()DEL\_CompanyDomainList
The CompanyDomainList table contains associations between the DomainInfo and DataArea tables. Security rights are granted per domain.

### Fields

| Field             | Type        | Extended Type      | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|--------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| companyId         | String      | SelectableDataArea |                  | ID for the company you can select                                                                                         |
| createdBy         | String      | CreatedBy          |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime    |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime   |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| domainId          | String      | DomainId           |                  | ID for the domain                                                                                                         |
| modifiedBy        | String      | ModifiedBy         |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime   |                  |                                                                                                                           |
| RecId             | Int64       | RecId              |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion         |                  |                                                                                                                           |

### Relations

| Relation  | Table           |
|-----------|-----------------|
| companyId | DataArea        |
| domainId  | DEL\_DomainInfo |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| Company | No               |        |
| Domain  | No               |        |
| RecId   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DEL\_CompanyDomainList Table](#del_companydomainlist)

## []()DEL\_DomainInfo
Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description       |
|------------|---------|---------------|------------------|-------------------|
| id         | String  | DomainId      |                  | ID for the domain |
| name       | String  | UserIdStr     |                  | Name              |
| RecId      | Int64   | RecId         |                  |                   |
| recVersion | Integer | RecVersion    |                  |                   |

### Relations

| Relation | Table           |
|----------|-----------------|
| id       | DEL\_DomainInfo |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DEL\_DomainInfo Table](#del_domaininfo)

## []()DEL\_UserGroupInfo
The UserGroupInfo table contains the list of available user groups.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description           |
|------------|---------|---------------|------------------|-----------------------|
| id         | String  | UserGroupId   |                  | ID for the user group |
| name       | String  | UserIdStr     |                  | Name                  |
| RecId      | Int64   | RecId         |                  |                       |
| recVersion | Integer | RecVersion    |                  |                       |

### Relations

| Relation | Table         |
|----------|---------------|
| id       | UserGroupInfo |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DEL\_UserGroupInfo Table](#del_usergroupinfo)

## []()DEL\_UserGroupList
The UserGroupList table contains the list of users associated with each user groups.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| groupId           | String      | UserGroupId       |                  | ID for the user group                                                                                                     |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| userId            | String      | UserId            |                  | ID for the user                                                                                                           |

### Relations

| Relation                 | Table              |
|--------------------------|--------------------|
| Relation\_UserGroupList1 | DEL\_UserGroupInfo |
| Relation\_UserGroupList2 | UserInfo           |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| GroupId | No               |        |
| RecId   | No               |        |
| UserId  | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [DEL\_UserGroupList Table](#del_usergrouplist)

## []()ModelSecPolRuntimeEx
The ModelSecPolRuntimeEx table stores the runtime metadata that is necessary to apply security policies.

### Fields

| Field                 | Type      | Extended Type | Enumeration Type | Description |
|-----------------------|-----------|---------------|------------------|-------------|
| ConstrainedTable      | String    |               |                  |             |
| ContextString         | String    |               |                  |             |
| ContextType           | Int       |               |                  |             |
| DEL\_ElementHandle    | Int       |               |                  |             |
| DEL\_IsEnabled        | Int       |               |                  |             |
| DEL\_LayerId          | Int       |               |                  |             |
| ElementHandle         | Int       |               |                  |             |
| IsDirty               | Int       |               |                  |             |
| IsEnabled             | Int       |               |                  |             |
| IsModeled             | Int       |               |                  |             |
| LayerId               | Int       |               |                  |             |
| ModeledQueryDebugInfo | String    |               |                  |             |
| ModeledQueryPackData  | Container |               |                  |             |
| Name                  | String    |               |                  |             |
| Operation             | Int       |               |                  |             |
| PrimaryTableAOTName   | String    |               |                  |             |
| QueryObjectAOTName    | String    |               |                  |             |
| RecId                 | Int64     | RecId         |                  |             |
| recVersion            | Integer   | RecVersion    |                  |             |

### Indexes

| Index               | Allow Duplicates | Fields           |
|---------------------|------------------|------------------|
| ConstrainedTableIdx | Yes              | ConstrainedTable |
| RecIDIdx            | No               | RecId            |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [ModelSecPolRuntimeEx Table](#modelsecpolruntimeex)

## []()ModelSecPolRuntimeView
The ModelSecPolRuntimeView view shows the runtime metadata for the currently active security policies.

### Fields

| Field                 | Type      | Extended Type | Enumeration Type | Description |
|-----------------------|-----------|---------------|------------------|-------------|
| ConstrainedTable      | String    |               |                  |             |
| ContextString         | String    |               |                  |             |
| ContextType           | Int       |               |                  |             |
| ElementHandle         | Int       |               |                  |             |
| IsDirty               | Int       |               |                  |             |
| IsModeled             | Int       |               |                  |             |
| LayerId               | Int       |               |                  |             |
| ModeledQueryDebugInfo | String    |               |                  |             |
| ModeledQueryPackData  | Container |               |                  |             |
| Name                  | String    |               |                  |             |
| Operation             | Int       |               |                  |             |
| PrimaryTableAOTName   | String    |               |                  |             |
| QueryObjectAOTName    | String    |               |                  |             |
| RecId                 | Int64     | RecId         |                  |             |
| recVersion            | Integer   | RecVersion    |                  |             |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [ModelSecPolRuntimeView Table](#modelsecpolruntimeview)

## []()Partitions
The Partitions table contains the list of data partitions in the system.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                                             |
|-------------------|-------------|-------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| createdBy         | String      | CreatedBy         |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| modifiedBy        | String      | ModifiedBy        |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| name              | String      | UserIdStr         |                  | Name (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))          |
| PartitionKey      | String      | PartitionKey      |                  | Partition Key (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId             | Int64       | RecId             |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |
| recVersion        | Integer     | RecVersion        |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS))               |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Relations

| Relation     | Table      |
|--------------|------------|
| PartitionKey | Partitions |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| PartitionIdx | No               |        |
| RecIDIdx     | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [Partitions Table](#partitions)

## []()PrintJobHeader
The PrintJobHeader table contains information regarding the current print job

### Fields

| Field               | Type        | Extended Type    | Enumeration Type | Description                                                                                                               |
|---------------------|-------------|------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdBy           | String      | CreatedBy        |                  |                                                                                                                           |
| createdDateTime     | UtcDateTime | CreatedDateTime  |                  |                                                                                                                           |
| dataAreaId          | String      | DataAreaId       |                  |                                                                                                                           |
| dEL\_CreatedTime    | Integer     | DEL\_CreatedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| deviceName          | String      |                  |                  |                                                                                                                           |
| format              | Enum        |                  | PrintFormat      |                                                                                                                           |
| jobDescription      | String      |                  |                  |                                                                                                                           |
| jobStatus           | Enum        |                  | PrintJobStatus   |                                                                                                                           |
| jobType             | String      |                  |                  |                                                                                                                           |
| numberOfPages       | Int         |                  |                  |                                                                                                                           |
| Partition           | Int64       | Partition        |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| printedBy           | String      | UserId           |                  | ID for the user                                                                                                           |
| printedDate         | date        |                  |                  |                                                                                                                           |
| printedTime         | Int         |                  |                  |                                                                                                                           |
| printerInfo         | Container   |                  |                  |                                                                                                                           |
| printFromPage       | Int         |                  |                  |                                                                                                                           |
| printNumcopies      | Int         |                  |                  |                                                                                                                           |
| printOnServer       | Enum        |                  | boolean          |                                                                                                                           |
| printToPage         | Int         |                  |                  |                                                                                                                           |
| RecId               | Int64       | RecId            |                  |                                                                                                                           |
| recVersion          | Integer     | RecVersion       |                  |                                                                                                                           |
| unlimitedPageHeight | Enum        |                  | boolean          |                                                                                                                           |

### Relations

| Relation   | Table      |
|------------|------------|
| dataAreaId | DataArea   |
| Partition  | Partitions |
| printedBy  | UserInfo   |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| CreatedBy   | Yes              |        |
| CreatedDate | Yes              |        |
| JobType     | Yes              |        |
| RecId       | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [PrintJobHeader Table](#printjobheader)

## []()PrintJobPages
The PrintJobPages table contains information regarding the currently printing page of a print job

### Fields

| Field            | Type      | Extended Type | Enumeration Type | Description                                                                                                               |
|------------------|-----------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| dataAreaId       | String    | DataAreaId    |                  |                                                                                                                           |
| numberOfLines    | Int       |               |                  |                                                                                                                           |
| pageContents     | Container |               |                  |                                                                                                                           |
| pageNo           | Int       |               |                  |                                                                                                                           |
| pagesHeaderRecId | Int64     | RecId         |                  | Unique ID for the record in the database                                                                                  |
| Partition        | Int64     | Partition     |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId            | Int64     | RecId         |                  |                                                                                                                           |
| recVersion       | Integer   | RecVersion    |                  |                                                                                                                           |

### Relations

| Relation                 | Table          |
|--------------------------|----------------|
| dataAreaId               | DataArea       |
| pagesHeaderRecId         | PrintJobHeader |
| Partition                | Partitions     |
| Relation\_PrintJobPages1 | PrintJobHeader |

### Indexes

| Index  | Allow Duplicates | Fields |
|--------|------------------|--------|
| PageNo | No               |        |
| RecId  | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [PrintJobPages Table](#printjobpages)

## []()SecurableObject
The SecurableObject table contains all security artifacts reference by the security framework.

### Fields

| Field      | Type    | Extended Type      | Enumeration Type | Description                             |
|------------|---------|--------------------|------------------|-----------------------------------------|
| ChildName  | String  | SecurableChildName |                  | The child name of the securable object. |
| Name       | String  | SecurableName      |                  | The name of the securable object.       |
| RecId      | Int64   | RecId              |                  |                                         |
| recVersion | Integer | RecVersion         |                  |                                         |
| Type       | Enum    |                    | SecurableType    |                                         |

### Field Groups

| Field Group | Fields |
|-------------|--------|
| AutoLookup  |        |

### Indexes

| Index            | Allow Duplicates | Fields |
|------------------|------------------|--------|
| NameChildTypeIdx | No               |        |
| RecIDIdx         | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurableObject Table](#securableobject)

## []()SecurityDuty
### Fields

| Field       | Type   | Extended Type           | Enumeration Type | Description |
|-------------|--------|-------------------------|------------------|-------------|
| Identifier  | String | SecurityDutyIdentifier  |                  |             |
| Name        | String | SecurityDutyName        |                  |             |
| Description | String | SecurityDutyDescription |                  |             |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification | Name   |

### Indexes

| Index         | Allow Duplicates | Fields     |
|---------------|------------------|------------|
| RecIDIdx      | No               | RecId      |
| IdentifierIdx | No               | Identifier |
| NameIdx       | Yes              | Name       |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityDuty Table](#securityduty)

## []()SecurityEntryPointInferredTables
### Fields

| Field                | Type   | Extended Type | Enumeration Type     | Description |
|----------------------|--------|---------------|----------------------|-------------|
| EntryPointName       | String | SecurableName |                      |             |
| Type                 | Enum   |               | SecurableType        |             |
| TableName            | String | SecurableName |                      |             |
| AllowEdit            | Enum   |               | boolean              |             |
| AllowCreate          | Enum   |               | boolean              |             |
| AllowDelete          | Enum   |               | boolean              |             |
| ValidTimeStateUpdate | Enum   |               | ValidTimeStateUpdate |             |

### Indexes

| Index              | Allow Duplicates | Fields                                                |
|--------------------|------------------|-------------------------------------------------------|
| RecIDIdx           | No               | RecId                                                 |
| EntryPointTableIdx | No               | EntryPointName, Type, TableName, ValidTimeStateUpdate |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityEntryPointInferredTables Table](#securityentrypointinferredtables)

## []()SecurityEntryPointLink
The SecurityEntryPointLink table contains the entry point to securable object mapping that has been specified on the AOT nodes of menu items and web menu items.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| EntryPoint      | Int64       | RecId         |                  | Unique ID for the record in the database |
| PermissionOwner | Int64       | RecId         |                  | Unique ID for the record in the database |
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                          | Table           |
|-----------------------------------|-----------------|
| Relation\_SecurityEntryPointLink1 | SecurableObject |
| Relation\_SecurityEntryPointLink2 | SecurableObject |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| EntryPointIdx | No               |        |
| RecIDIdx      | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityEntryPointLink Table](#securityentrypointlink)

## []()SecurityPermission
The SecurityPermission table contains the list of permissions that have been specified on the AOT nodes of forms, reports, security code permissions, and service operations.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| Access          | Enum        |               | AccessRight      |                                          |
| Group           | Enum        |               | AccessRight      |                                          |
| Owner           | Int64       | RecId         |                  | Unique ID for the record in the database |
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecurableObject | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                      | Table           |
|-------------------------------|-----------------|
| Relation\_SecurityPermission1 | SecurableObject |
| Relation\_SecurityPermission2 | SecurableObject |

### Indexes

| Index               | Allow Duplicates | Fields |
|---------------------|------------------|--------|
| OwnerGroupObjectIdx | No               |        |
| RecIDIdx            | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityPermission Table](#securitypermission)

## []()SecurityPrivilege
### Fields

| Field       | Type   | Extended Type                | Enumeration Type | Description |
|-------------|--------|------------------------------|------------------|-------------|
| Identifier  | String | SecurityPrivilegeIdentifier  |                  |             |
| Name        | String | SecurityPrivilegeName        |                  |             |
| Description | String | SecurityPrivilegeDescription |                  |             |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification | Name   |

### Indexes

| Index         | Allow Duplicates | Fields     |
|---------------|------------------|------------|
| RecIDIdx      | No               | RecId      |
| IdentifierIdx | No               | Identifier |
| NameIdx       | Yes              | Name       |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityPrivilege Table](#securityprivilege)

## []()SecurityRole
The SecurityRole table reflects the list of roles defined by the security AOT role node.

### Fields

| Field                    | Type    | Extended Type           | Enumeration Type | Description                       |
|--------------------------|---------|-------------------------|------------------|-----------------------------------|
| AllowCurrentRecords      | Enum    |                         | AccessRight      |                                   |
| AllowFutureRecords       | Enum    |                         | AccessRight      |                                   |
| AllowPastRecords         | Enum    |                         | AccessRight      |                                   |
| AotName                  | String  | SecurityRoleAotName     |                  | The name of the role in the AOT.  |
| ContextString            | String  |                         |                  |                                   |
| DEL\_AllowCurrentRecords | Enum    |                         | AccessRight      |                                   |
| DEL\_AllowFutureRecords  | Enum    |                         | AccessRight      |                                   |
| DEL\_AllowPastRecords    | Enum    |                         | AccessRight      |                                   |
| DEL\_IsEnabled           | Enum    |                         | boolean          |                                   |
| Description              | String  | SecurityRoleDescription |                  | Description of the security role. |
| IsEnabled                | Enum    |                         | boolean          |                                   |
| Name                     | String  | SecurityRoleName        |                  | The name of the security role.    |
| RecId                    | Int64   | RecId                   |                  |                                   |
| recVersion               | Integer | RecVersion              |                  |                                   |
| UserLicenseType          | Enum    |                         | UserLicenseType  |                                   |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Indexes

| Index      | Allow Duplicates | Fields |
|------------|------------------|--------|
| AotNameIdx | No               |        |
| NameIdx    | Yes              |        |
| RecIDIdx   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRole Table](#securityrole)

## []()SecurityRoleAssignmentRule
Rules for dynamically assigning users to role

### Fields

| Field                     | Type        | Extended Type             | Enumeration Type | Description                                                                                                               |
|---------------------------|-------------|---------------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| MembershipRuleDescription | String      | MembershipRuleDescription |                  | Description of the automatic role membership rule                                                                         |
| MembershipRuleName        | String      | MembershipRuleName        |                  | Name of the automatic role membership rule                                                                                |
| Partition                 | Int64       | Partition                 |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId                     | Int64       | RecId                     |                  |                                                                                                                           |
| recVersion                | Integer     | RecVersion                |                  |                                                                                                                           |
| RuleQuery                 | Container   |                           |                  |                                                                                                                           |
| SecurityRole              | Int64       | RecId                     |                  | Unique ID for the record in the database                                                                                  |
| ValidFrom                 | UtcDateTime |                           |                  |                                                                                                                           |
| ValidTo                   | UtcDateTime |                           |                  |                                                                                                                           |

### Relations

| Relation                 | Table        |
|--------------------------|--------------|
| Partition                | Partitions   |
| SecurityRole             | SecurityRole |
| SecurityRoleRelationShip | SecurityRole |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| AlternateKey | No               |        |
| RecIDIdx     | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRoleAssignmentRule Table](#securityroleassignmentrule)

## []()SecurityRoleDutyExplodedGraph
### Fields

| Field        | Type  | Extended Type | Enumeration Type | Description |
|--------------|-------|---------------|------------------|-------------|
| SecurityRole | Int64 | RecId         |                  |             |
| SecurityDuty | Int64 | RecId         |                  |             |

### Relations

| Relation     | Table        |
|--------------|--------------|
| SecurityRole | SecurityRole |
| SecurityDuty | SecurityDuty |

### Indexes

| Index       | Allow Duplicates | Fields                     |
|-------------|------------------|----------------------------|
| RecIDIdx    | No               | RecId                      |
| RoleDutyIdx | No               | SecurityRole, SecurityDuty |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRoleDutyExplodedGraph Table](#securityroledutyexplodedgraph)

## []()SecurityRoleExplodedGraph
The SecurityRoleExplodedGraph table contains all role relationships, direct or indirect, as defined by the AOT sub role nodes of the security role nodes.

### Fields

| Field           | Type    | Extended Type | Enumeration Type | Description                              |
|-----------------|---------|---------------|------------------|------------------------------------------|
| RecId           | Int64   | RecId         |                  |                                          |
| recVersion      | Integer | RecVersion    |                  |                                          |
| RefCount        | Int     |               |                  |                                          |
| SecurityRole    | Int64   | RecId         |                  | Unique ID for the record in the database |
| SecuritySubRole | Int64   | RecId         |                  | Unique ID for the record in the database |

### Relations

| Relation                | Table        |
|-------------------------|--------------|
| Relation\_SecurityRole1 | SecurityRole |
| Relation\_SecurityRole2 | SecurityRole |
| SecurityRole            | SecurityRole |
| SecuritySubRole         | SecurityRole |

### Indexes

| Index          | Allow Duplicates | Fields |
|----------------|------------------|--------|
| RecIDIdx       | No               |        |
| RoleSubRoleIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRoleExplodedGraph Table](#securityroleexplodedgraph)

## []()SecurityRolePermissionOverride
The SecurityRolePermissionOverride table contains the list of permissions that have been specified on the security role AOT nodes.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| Access          | Enum        |               | AccessRight      |                                          |
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecurableObject | Int64       | RecId         |                  | Unique ID for the record in the database |
| SecurityRole    | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                                  | Table           |
|-------------------------------------------|-----------------|
| Relation\_SecurityRolePermissionOverride1 | SecurityRole    |
| Relation\_SecurityRolePermissionOverride2 | SecurableObject |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| RecIDIdx      | No               |        |
| RoleObjectIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRolePermissionOverride Table](#securityrolepermissionoverride)

## []()SecurityRolePrivilegeExplodedGraph
### Fields

| Field             | Type  | Extended Type | Enumeration Type | Description |
|-------------------|-------|---------------|------------------|-------------|
| SecurityRole      | Int64 | RecId         |                  |             |
| SecurityPrivilege | Int64 | RecId         |                  |             |

### Relations

| Relation          | Table             |
|-------------------|-------------------|
| SecurityRole      | SecurityRole      |
| SecurityPrivilege | SecurityPrivilege |

### Indexes

| Index            | Allow Duplicates | Fields                          |
|------------------|------------------|---------------------------------|
| RecIDIdx         | No               | RecId                           |
| RolePrivilegeIdx | No               | SecurityRole, SecurityPrivilege |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRolePrivilegeExplodedGraph Table](#securityroleprivilegeexplodedgraph)

## []()SecurityRoleRuntime
### Fields

| Field                | Type   | Extended Type      | Enumeration Type | Description |
|----------------------|--------|--------------------|------------------|-------------|
| SecurityRole         | Int64  | RecId              |                  |             |
| Name                 | String | SecurableName      |                  |             |
| ChildName            | String | SecurableChildName |                  |             |
| Type                 | Enum   |                    | SecurableType    |             |
| CreateAccess         | Int    |                    |                  |             |
| ReadAccess           | Int    |                    |                  |             |
| UpdateAccess         | Int    |                    |                  |             |
| DeleteAccess         | Int    |                    |                  |             |
| CorrectAccess        | Int    |                    |                  |             |
| InvokeAccess         | Int    |                    |                  |             |
| PastCreateAccess     | Int    |                    |                  |             |
| PastReadAccess       | Int    |                    |                  |             |
| PastUpdateAccess     | Int    |                    |                  |             |
| PastDeleteAccess     | Int    |                    |                  |             |
| PastCorrectAccess    | Int    |                    |                  |             |
| PastInvokeAccess     | Int    |                    |                  |             |
| CurrentCreateAccess  | Int    |                    |                  |             |
| CurrentReadAccess    | Int    |                    |                  |             |
| CurrentUpdateAccess  | Int    |                    |                  |             |
| CurrentDeleteAccess  | Int    |                    |                  |             |
| CurrentCorrectAccess | Int    |                    |                  |             |
| CurrentInvoke        | Int    |                    |                  |             |
| FutureCreateAccess   | Int    |                    |                  |             |
| FutureReadAccess     | Int    |                    |                  |             |
| FutureUpdateAccess   | Int    |                    |                  |             |
| FutureDeleteAccess   | Int    |                    |                  |             |
| FutureCorrectAccess  | Int    |                    |                  |             |
| FutureInvokeAccess   | Int    |                    |                  |             |

### Field Groups

| Field Group        | Fields                |
|--------------------|-----------------------|
| AutoIdentification | Name, ChildName, Type |

### Indexes

| Index              | Allow Duplicates | Fields                |
|--------------------|------------------|-----------------------|
| RecIDIdx           | No               | RecId                 |
| RoleIDIdx          | Yes              | SecurityRole          |
| SecurableObjectIdx | Yes              | Type, Name, ChildName |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRoleRuntime Table](#securityroleruntime)

## []()SecurityRoleTaskGrant
The SecurityRoleTaskGrant table contains the list of role to duty mappings and role to privilege mappings as defined by the AOT security role node.

### Fields

| Field        | Type    | Extended Type | Enumeration Type | Description                              |
|--------------|---------|---------------|------------------|------------------------------------------|
| RecId        | Int64   | RecId         |                  |                                          |
| recVersion   | Integer | RecVersion    |                  |                                          |
| SecurityRole | Int64   | RecId         |                  | Unique ID for the record in the database |
| SecurityTask | Int64   | RecId         |                  | Unique ID for the record in the database |

### Relations

| Relation                         | Table        |
|----------------------------------|--------------|
| Relation\_SecurityRoleTaskGrant1 | SecurityRole |
| Relation\_SecurityRoleTaskGrant2 | SecurityTask |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| RecIDIdx    | No               |        |
| RoleTaskIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityRoleTaskGrant Table](#securityroletaskgrant)

## []()SecuritySegregationOfDutiesConflict
The SecuritySegregationOfDutiesConflict table stores information about segregation of duties conflicts that result from attempted assignments of users to roles, and resolutions to the conflicts provided by authorized users.

### Fields

| Field                   | Type        | Extended Type                      | Enumeration Type              | Description                                                                                                               |
|-------------------------|-------------|------------------------------------|-------------------------------|---------------------------------------------------------------------------------------------------------------------------|
| AssignmentMode          | Enum        |                                    | RoleAssignmentMode            |                                                                                                                           |
| createdBy               | String      | CreatedBy                          |                               |                                                                                                                           |
| createdDateTime         | UtcDateTime | CreatedDateTime                    |                               |                                                                                                                           |
| dEL\_CreatedTime        | Integer     | DEL\_CreatedTime                   |                               | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| DEL\_ExistingTask       | Int64       | RecId                              |                               |                                                                                                                           |
| dEL\_ModifiedTime       | Integer     | DEL\_ModifiedTime                  |                               | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| DEL\_NewTask            | Int64       | RecId                              |                               |                                                                                                                           |
| ExistingDuty            | Int64       | RecId                              |                               |                                                                                                                           |
| ExistingRole            | Int64       | RecId                              |                               | Unique ID for the record in the database                                                                                  |
| ExistingTask            | Int64       | RecId                              |                               | Unique ID for the record in the database                                                                                  |
| modifiedBy              | String      | ModifiedBy                         |                               |                                                                                                                           |
| modifiedDateTime        | UtcDateTime | ModifiedDateTime                   |                               |                                                                                                                           |
| NewDuty                 | Int64       | RecId                              |                               |                                                                                                                           |
| NewRole                 | Int64       | RecId                              |                               | Unique ID for the record in the database                                                                                  |
| NewTask                 | Int64       | RecId                              |                               | Unique ID for the record in the database                                                                                  |
| Partition               | Int64       | Partition                          |                               | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| ReasonForOverride       | VarString   | SegregationOfDutiesOverrideComment |                               | Comment explaining the reason for overriding the segregation of duties violation                                          |
| RecId                   | Int64       | RecId                              |                               |                                                                                                                           |
| recVersion              | Integer     | RecVersion                         |                               |                                                                                                                           |
| Resolution              | Enum        |                                    | SegregationOfDutiesResolution |                                                                                                                           |
| SegregationOfDutiesRule | Int64       | RecId                              |                               | Unique ID for the record in the database                                                                                  |
| User                    | String      | UserId                             |                               | ID for the user                                                                                                           |

### Relations

| Relation                       | Table                           |
|--------------------------------|---------------------------------|
| ExistingDuty                   | SecurityDuty                    |
| ExistingRole                   | SecurityRole                    |
| ExistingRoleRelationship       | SecurityRole                    |
| ExistingTaskRelationship       | SecurityTask                    |
| NewDuty                        | SecurityDuty                    |
| NewRole                        | SecurityRole                    |
| NewRoleRelationship            | SecurityRole                    |
| NewTaskRelationship            | SecurityTask                    |
| Partition                      | Partitions                      |
| Relation\_SecuritySegregation7 | UserInfo                        |
| SecuritySODRuleRelationship    | SecuritySegregationOfDutiesRule |
| SegregationOfDutiesRule        | SecuritySegregationOfDutiesRule |
| User                           | UserInfo                        |

### Indexes

| Index           | Allow Duplicates | Fields       |
|-----------------|------------------|--------------|
| AlternateKey    | No               |              |
| ExistingDutyIdx | Yes              | ExistingDuty |
| ExistingRoleIdx | Yes              |              |
| ExistingTaskIdx | Yes              |              |
| NewDutyIdx      | Yes              | NewDuty      |
| NewRoleIdx      | Yes              |              |
| NewTaskIdx      | Yes              |              |
| RecIDIdx        | No               |              |
| UserInfoIdx     | Yes              |              |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecuritySegregationOfDutiesConflict Table](#securitysegregationofdutiesconflict)

## []()SecuritySegregationOfDutiesRule
The SecuritySegregationOfDutiesRule table stores the rules governing segregation of duties.

### Fields

| Field                   | Type        | Extended Type               | Enumeration Type            | Description                                                                      |
|-------------------------|-------------|-----------------------------|-----------------------------|----------------------------------------------------------------------------------|
| DEL\_FirstSecurityTask  | Int64       | RecId                       |                             |                                                                                  |
| DEL\_SecondSecurityTask | Int64       | RecId                       |                             |                                                                                  |
| FirstDuty               | Int64       | RecId                       |                             |                                                                                  |
| FirstSecurityTask       | Int64       | RecId                       |                             | Unique ID for the record in the database                                         |
| Mitigation              | String      | SecurityMitigation          |                             | Mitigation for the risk associated with violating the segregation of duties rule |
| Name                    | String      | SegregationOfDutiesRuleName |                             | Name of the segregation of duties rule                                           |
| RecId                   | Int64       | RecId                       |                             |                                                                                  |
| recVersion              | Integer     | RecVersion                  |                             |                                                                                  |
| Risk                    | String      | SecurityRisk                |                             | Risk associated with violating the segregation of duties rule                    |
| SecondDuty              | Int64       | RecId                       |                             |                                                                                  |
| SecondSecurityTask      | Int64       | RecId                       |                             | Unique ID for the record in the database                                         |
| Severity                | Enum        |                             | SegregationOfDutiesSeverity |                                                                                  |
| ValidFrom               | UtcDateTime |                             |                             |                                                                                  |
| ValidTo                 | UtcDateTime |                             |                             |                                                                                  |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Relations

| Relation                       | Table        |
|--------------------------------|--------------|
| FirstDuty                      | SecurityDuty |
| FirstSecurityTaskRelationship  | SecurityTask |
| SecondDuty                     | SecurityDuty |
| SecondSecurityTaskRelationship | SecurityTask |

### Indexes

| Index              | Allow Duplicates | Fields     |
|--------------------|------------------|------------|
| AlternateKey       | No               |            |
| FirstSecurityDuty  | Yes              | FirstDuty  |
| NameIdx            | No               |            |
| RecIDIdx           | No               |            |
| SecondSecurityDuty | Yes              | SecondDuty |
| SecondSecurityTask | Yes              |            |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecuritySegregationOfDutiesRule Table](#securitysegregationofdutiesrule)

## []()SecuritySubRole
The SecuritySubRole table contains all sub roles that have been specified on the security role AOT nodes.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecurityRole    | Int64       | RecId         |                  | Unique ID for the record in the database |
| SecuritySubRole | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                          | Table        |
|-----------------------------------|--------------|
| Relation\_SecuritySubRole1        | SecurityRole |
| Relation\_SecurityTaskPermission2 | SecurityRole |
| SecurityRole                      | SecurityRole |
| SecuritySubRole                   | SecurityRole |

### Indexes

| Index          | Allow Duplicates | Fields |
|----------------|------------------|--------|
| RecIDIdx       | No               |        |
| RoleSubRoleIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecuritySubRole Table](#securitysubrole)

## []()SecuritySubTask
The SecuritySubTask table contains the duty to privilege mappings that have been specified on the security duty AOT nodes.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecuritySubTask | Int64       | RecId         |                  | Unique ID for the record in the database |
| SecurityTask    | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                   | Table        |
|----------------------------|--------------|
| Relation\_SecuritySubTask1 | SecurityTask |
| Relation\_SecuritySubTask2 | SecurityTask |

### Indexes

| Index          | Allow Duplicates | Fields |
|----------------|------------------|--------|
| RecIDIdx       | No               |        |
| TaskSubTaskIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecuritySubTask Table](#securitysubtask)

## []()SecurityTask
The SecurityTask table contains the list of duties and privileges that have been defined by the AOT security duty and security privilege nodes.

### Fields

| Field           | Type    | Extended Type           | Enumeration Type | Description                                           |
|-----------------|---------|-------------------------|------------------|-------------------------------------------------------|
| AotName         | String  | SecurityTaskAotName     |                  | The name of the task in the AOT.                      |
| Description     | String  | SecurityTaskDescription |                  | Description of the process cycle, duty, or privilege. |
| IsEnabled       | Enum    |                         | boolean          |                                                       |
| IsPermissionSet | Enum    |                         | boolean          |                                                       |
| Name            | String  | SecurityTaskName        |                  | The name of the process cycle, duty, or privilege.    |
| RecId           | Int64   | RecId                   |                  |                                                       |
| recVersion      | Integer | RecVersion              |                  |                                                       |
| Type            | Enum    |                         | SecurityTaskType |                                                       |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Indexes

| Index      | Allow Duplicates | Fields |
|------------|------------------|--------|
| AotNameIdx | No               |        |
| NameIdx    | Yes              |        |
| RecIDIdx   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityTask Table](#securitytask)

## []()SecurityTaskEntryPoint
The SecurityTaskEntryPoint table contains the list of privilege to entry point mappings that have been specified on the AOT security privilege node.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| EntryPoint      | Int64       | RecId         |                  | Unique ID for the record in the database |
| PermissionGroup | Enum        |               | AccessRight      |                                          |
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecurityTask    | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                          | Table           |
|-----------------------------------|-----------------|
| Relation\_SecurityTaskEntryPoint1 | SecurityTask    |
| Relation\_SecurityTaskEntryPoint2 | SecurableObject |

### Indexes

| Index             | Allow Duplicates | Fields |
|-------------------|------------------|--------|
| RecIDIdx          | No               |        |
| TaskEntryPointIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityTaskEntryPoint Table](#securitytaskentrypoint)

## []()SecurityTaskExplodedGraph
The SecurityTaskExplodedGraph table contains the duty to privilege mappings that have been specified on the security duty AOT nodes.

### Fields

| Field           | Type    | Extended Type | Enumeration Type | Description                              |
|-----------------|---------|---------------|------------------|------------------------------------------|
| RecId           | Int64   | RecId         |                  |                                          |
| recVersion      | Integer | RecVersion    |                  |                                          |
| RefCount        | Int     |               |                  |                                          |
| SecuritySubTask | Int64   | RecId         |                  | Unique ID for the record in the database |
| SecurityTask    | Int64   | RecId         |                  | Unique ID for the record in the database |

### Relations

| Relation                             | Table        |
|--------------------------------------|--------------|
| Relation\_SecurityTaskExplodedGraph1 | SecurityTask |
| Relation\_SecurityTaskExplodedGraph2 | SecurityTask |

### Indexes

| Index          | Allow Duplicates | Fields |
|----------------|------------------|--------|
| RecIDIdx       | No               |        |
| SubTaskIdx     | Yes              |        |
| TaskSubTaskIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityTaskExplodedGraph Table](#securitytaskexplodedgraph)

## []()SecurityTaskPermission
The SecurityTaskPermission table is obsolete.

### Fields

| Field           | Type    | Extended Type | Enumeration Type | Description                              |
|-----------------|---------|---------------|------------------|------------------------------------------|
| Access          | Int     |               |                  |                                          |
| Level           | Int     |               |                  |                                          |
| RecId           | Int64   | RecId         |                  |                                          |
| recVersion      | Integer | RecVersion    |                  |                                          |
| SecurableObject | Int64   | RecId         |                  | Unique ID for the record in the database |
| SecurityTask    | Int64   | RecId         |                  | Unique ID for the record in the database |

### Relations

| Relation                          | Table           |
|-----------------------------------|-----------------|
| Relation\_SecurityTaskPermission1 | SecurityTask    |
| Relation\_SecurityTaskPermission2 | SecurableObject |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| RecIDIdx      | No               |        |
| TaskObjectIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityTaskPermission Table](#securitytaskpermission)

## []()SecurityTaskPermissionOverride
The SecurityTaskPermissionOverride table contains the list of permissions that have been specified on the security privilege AOT nodes.

### Fields

| Field           | Type        | Extended Type | Enumeration Type | Description                              |
|-----------------|-------------|---------------|------------------|------------------------------------------|
| Access          | Enum        |               | AccessRight      |                                          |
| RecId           | Int64       | RecId         |                  |                                          |
| recVersion      | Integer     | RecVersion    |                  |                                          |
| SecurableObject | Int64       | RecId         |                  | Unique ID for the record in the database |
| SecurityTask    | Int64       | RecId         |                  | Unique ID for the record in the database |
| ValidFrom       | UtcDateTime |               |                  |                                          |
| ValidTo         | UtcDateTime |               |                  |                                          |

### Relations

| Relation                                  | Table           |
|-------------------------------------------|-----------------|
| Relation\_SecurityTaskPermissionOverride1 | SecurityTask    |
| Relation\_SecurityTaskPermissionOverride2 | SecurableObject |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| RecIDIdx      | No               |        |
| TaskObjectIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityTaskPermissionOverride Table](#securitytaskpermissionoverride)

## []()SecurityUserRole
The SecurityUserRole table contains the user to role mappings.

### Fields

| Field            | Type        | Extended Type | Enumeration Type     | Description                                                                                                               |
|------------------|-------------|---------------|----------------------|---------------------------------------------------------------------------------------------------------------------------|
| AssignmentMode   | Enum        |               | RoleAssignmentMode   |                                                                                                                           |
| AssignmentStatus | Enum        |               | RoleAssignmentStatus |                                                                                                                           |
| Partition        | Int64       | Partition     |                      | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId            | Int64       | RecId         |                      |                                                                                                                           |
| recVersion       | Integer     | RecVersion    |                      |                                                                                                                           |
| SecurityRole     | Int64       | RecId         |                      | Unique ID for the record in the database                                                                                  |
| User             | String      | UserId        |                      | ID for the user                                                                                                           |
| ValidFrom        | UtcDateTime |               |                      |                                                                                                                           |
| ValidTo          | UtcDateTime |               |                      |                                                                                                                           |

### Relations

| Relation                    | Table        |
|-----------------------------|--------------|
| Partition                   | Partitions   |
| Relation\_SecurityRole      | SecurityRole |
| Relation\_SecurityUserRole3 | UserInfo     |
| SecurityRole                | SecurityRole |
| User                        | UserInfo     |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| RecIDIdx    | No               |        |
| UserRoleIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityUserRole Table](#securityuserrole)

## []()SecurityUserRoleCondition
The SecurityUserRoleCondition table contains the list of companies that constrain a user to role mappings.?If there are no entries for a particular user to role mapping then the user is granted the permissions of that role for all companies.

### Fields

| Field            | Type    | Extended Type | Enumeration Type | Description                                                                                                               |
|------------------|---------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| ControllingKey   | int64   |               |                  |                                                                                                                           |
| DataArea         | String  | DataAreaId    |                  | ID for an area of data                                                                                                    |
| Partition        | Int64   | Partition     |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId            | Int64   | RecId         |                  |                                                                                                                           |
| recVersion       | Integer | RecVersion    |                  |                                                                                                                           |
| SecurityUserRole | Int64   | RecId         |                  | Unique ID for the record in the database                                                                                  |

### Relations

| Relation                             | Table            |
|--------------------------------------|------------------|
| DataArea                             | DataArea         |
| Partition                            | Partitions       |
| Relation\_SecurityUserRoleCondition1 | SecurityUserRole |
| Relation\_SecurityUserRoleCondition2 | DataArea         |
| SecurityUserRole                     | SecurityUserRole |

### Indexes

| Index               | Allow Duplicates | Fields |
|---------------------|------------------|--------|
| RecIDIdx            | No               |        |
| UserRoleDataAreaIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SecurityUserRoleCondition Table](#securityuserrolecondition)

## []()SqlDescribe
The SqlDescribe table is used to store the table and field metadata. The SqlDataDictionary::tablemetadata method populates this table by using a back end database query.

### Fields

| Field            | Type    | Extended Type   | Enumeration Type | Description                      |
|------------------|---------|-----------------|------------------|----------------------------------|
| array            | Int     |                 |                  |                                  |
| fieldId          | Integer | FieldId         |                  | ID for the field                 |
| fieldType        | Enum    |                 | Types            |                                  |
| flags            | Int     |                 |                  |                                  |
| name             | String  | UtilElementName |                  | Name of the application element. |
| nullable         | Enum    |                 | boolean          |                                  |
| numericPrecision | Int     |                 |                  |                                  |
| numericScale     | Int     |                 |                  |                                  |
| RecId            | Int64   | RecId           |                  |                                  |
| recVersion       | Integer | RecVersion      |                  |                                  |
| rightJustify     | Enum    |                 | boolean          |                                  |
| shadow           | Enum    |                 | boolean          |                                  |
| sqlName          | String  | UtilElementName |                  | Name of the application element. |
| strSize          | Int     |                 |                  |                                  |
| tabId            | Integer | TableId         |                  | ID for the table                 |

### Field Groups

| Field Group     | Fields |
|-----------------|--------|
| fieldIdRelation |        |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| Field   | No               |        |
| RecId   | No               |        |
| SqlName | Yes              |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlDescribe Table](#sqldescribe)

## []()SqlDictionary
The SqlDictionary table describes the current state of the database with respect to the table and field metadata. The table also contains view and table dependency information. The database synchronization engine uses the SqlDictionary table to determine the actions that are required to synchronize the AOT with the database.

### Fields

| Field        | Type    | Extended Type   | Enumeration Type | Description                      |
|--------------|---------|-----------------|------------------|----------------------------------|
| array        | Int     |                 |                  |                                  |
| fieldId      | Integer | FieldId         |                  | ID for the field                 |
| fieldType    | Enum    |                 | Types            |                                  |
| flags        | Int     |                 |                  |                                  |
| name         | String  | UtilElementName |                  | Name of the application element. |
| nullable     | Enum    |                 | boolean          |                                  |
| RecId        | Int64   | RecId           |                  |                                  |
| recVersion   | Integer | RecVersion      |                  |                                  |
| rightJustify | Enum    |                 | boolean          |                                  |
| shadow       | Enum    |                 | boolean          |                                  |
| sqlName      | String  | UtilElementName |                  | Name of the application element. |
| strSize      | Int     |                 |                  |                                  |
| tabId        | Integer | TableId         |                  | ID for the table                 |

### Field Groups

| Field Group     | Fields |
|-----------------|--------|
| fieldIdRelation |        |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Field | No               |        |
| RecId | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlDictionary Table](#sqldictionary)

## []()SqlParameters
The SqlParameters table stores database related information in the form of parameter and value pairs. This table is not used in Microsoft Dynamics Ax 2009.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description |
|------------|---------|---------------|------------------|-------------|
| id         | Int     |               |                  |             |
| iParm      | Int     |               |                  |             |
| iValue     | Int     |               |                  |             |
| parm       | String  |               |                  |             |
| RecId      | Int64   | RecId         |                  |             |
| recVersion | Integer | RecVersion    |                  |             |
| value      | String  |               |                  |             |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Parm  | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlParameters Table](#sqlparameters)

## []()SqlStatistics
The SqlStatistics table stores related database statistics for the user. This table is not used in Microsoft Dynamics Ax 2009.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| indexId           | Integer     | IndexId           |                  | ID for the index                                                                                                          |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| objectType        | Enum        |                   | SqlStatType      |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| tabId             | Integer     | TableId           |                  | ID for the table                                                                                                          |
| userId            | String      | UserId            |                  | ID for the user                                                                                                           |
| value1            | Int         |                   |                  |                                                                                                                           |
| value10           | Int         |                   |                  |                                                                                                                           |
| value11           | Int         |                   |                  |                                                                                                                           |
| value12           | Int         |                   |                  |                                                                                                                           |
| value2            | Int         |                   |                  |                                                                                                                           |
| value3            | Int         |                   |                  |                                                                                                                           |
| value4            | Int         |                   |                  |                                                                                                                           |
| value5            | Int         |                   |                  |                                                                                                                           |
| value6            | Int         |                   |                  |                                                                                                                           |
| value7            | Int         |                   |                  |                                                                                                                           |
| value8            | Int         |                   |                  |                                                                                                                           |
| value9            | Int         |                   |                  |                                                                                                                           |

### Field Groups

| Field Group     | Fields |
|-----------------|--------|
| indexIdRelation |        |

### Relations

| Relation            | Table         |
|---------------------|---------------|
| Relation\_SqlStats1 | SqlStatistics |
| Relation\_SqlStats2 | UserInfo      |
| tabId               | SqlStatistics |
| userId              | UserInfo      |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |
| RecId | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlStatistics Table](#sqlstatistics)

## []()SqlStorage
The SqlStorage table contains information about table space and its Oracle attributes.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description      |
|------------|---------|---------------|------------------|------------------|
| id         | Int     |               |                  |                  |
| indexId    | Integer | IndexId       |                  | ID for the index |
| objectType | Int     |               |                  |                  |
| override   | Enum    |               | boolean          |                  |
| parm       | String  |               |                  |                  |
| RecId      | Int64   | RecId         |                  |                  |
| recVersion | Integer | RecVersion    |                  |                  |
| tabId      | Integer | TableId       |                  | ID for the table |
| value      | String  |               |                  |                  |

### Field Groups

| Field Group     | Fields |
|-----------------|--------|
| indexIdRelation |        |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlStorage Table](#sqlstorage)

## []()SqlSyncInfo
The SqlSyncInfo table captures messages and DDL statements during the database synchronization process. Once the synchronization process is complete the information in the table is deleted.

### Fields

| Field       | Type    | Extended Type | Enumeration Type   | Description |
|-------------|---------|---------------|--------------------|-------------|
| ID          | Int     |               |                    |             |
| LogType     | Enum    |               | SqlSyncLogType     |             |
| MessageType | Enum    |               | SqlSyncMessageType |             |
| ParentID    | Int     |               |                    |             |
| RecId       | Int64   | RecId         |                    |             |
| recVersion  | Integer | RecVersion    |                    |             |
| Sequence    | Int     |               |                    |             |
| SyncTable   | Enum    |               | boolean            |             |
| TableName   | String  |               |                    |             |
| Text        | String  |               |                    |             |
| WarningOk   | Enum    |               | boolean            |             |

### Indexes

| Index     | Allow Duplicates | Fields |
|-----------|------------------|--------|
| TableName | Yes              |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateReadUpdateDelete. The Application Object Server authorizes each create, read, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SqlSyncInfo Table](#sqlsyncinfo)

## []()Subquery
The Subquery table is used by position based paging functionality.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description |
|------------|---------|---------------|------------------|-------------|
| dataAreaId | String  | DataAreaId    |                  |             |
| RecId      | Int64   | RecId         |                  |             |
| recVersion | Integer | RecVersion    |                  |             |

### Relations

| Relation   | Table    |
|------------|----------|
| dataAreaId | DataArea |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| RecId | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [Subquery Table](#subquery)

## []()SysActiveTempTable
The SysActiveTempTable table provides data about the temporary database tables that are currently created. The table is used by the framework to manage the lifetime of these tables.

### Fields

| Field            | Type        | Extended Type    | Enumeration Type | Description                                                                                                               |
|------------------|-------------|------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdDateTime  | UtcDateTime | CreatedDateTime  |                  |                                                                                                                           |
| dEL\_CreatedTime | Integer     | DEL\_CreatedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| InstanceId       | String      | UtilElementName  |                  | Name of the application element.                                                                                          |
| RecId            | Int64       | RecId            |                  |                                                                                                                           |
| recVersion       | Integer     | RecVersion       |                  |                                                                                                                           |
| RelationTypeId   | Int64       | RecId            |                  | Unique ID for the record in the database                                                                                  |
| ServerId         | Int64       | RecId            |                  | Unique ID for the record in the database                                                                                  |
| SessionId        | Int64       | RecId            |                  | Unique ID for the record in the database                                                                                  |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| InstanceIdIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysActiveTempTable Table](#sysactivetemptable)

## []()SysBCProxyUserAccount
The SysBCProxyUserAccount table stores the business connector proxy information that is entered through the SysBcAliasForm security form. This table always contains one record.

### Fields

| Field         | Type    | Extended Type | Enumeration Type | Description |
|---------------|---------|---------------|------------------|-------------|
| networkAlias  | String  | NetworkAlias  |                  |             |
| networkDomain | String  | NetworkDomain |                  |             |
| RecId         | Int64   | RecId         |                  |             |
| recVersion    | Integer | RecVersion    |                  |             |
| sid           | String  | Sid           |                  |             |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| RecID | No               |        |
| Sid   | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysBCProxyUserAccount Table](#sysbcproxyuseraccount)

## []()SysBreakpointList
The SysBreakpointList table contains a list of developers that have breakpoints in MorphX.

### Fields

| Field            | Type        | Extended Type    | Enumeration Type | Description                                                                                                               |
|------------------|-------------|------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdBy        | String      | CreatedBy        |                  |                                                                                                                           |
| createdDateTime  | UtcDateTime | CreatedDateTime  |                  |                                                                                                                           |
| dEL\_CreatedTime | Integer     | DEL\_CreatedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| machineName      | String      | NetworkDomain    |                  |                                                                                                                           |
| RecId            | Int64       | RecId            |                  |                                                                                                                           |
| recVersion       | Integer     | RecVersion       |                  |                                                                                                                           |
| userId           | String      | UserId           |                  | ID for the user                                                                                                           |
| version          | Int         |                  |                  |                                                                                                                           |

### Relations

| Relation | Table    |
|----------|----------|
| userId   | UserInfo |

### Indexes

| Index  | Allow Duplicates | Fields |
|--------|------------------|--------|
| RecId  | No               |        |
| UserId | Yes              |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysBreakpointList Table](#sysbreakpointlist)

## []()SysBreakpoints
The SysBreakpoints table contains a list of all the breakpoints in MorphX.

### Fields

| Field      | Type      | Extended Type | Enumeration Type | Description                              |
|------------|-----------|---------------|------------------|------------------------------------------|
| codePath   | Container |               |                  |                                          |
| lineNo     | Int       |               |                  |                                          |
| listRecId  | Int64     | RecId         |                  | Unique ID for the record in the database |
| RecId      | Int64     | RecId         |                  |                                          |
| recVersion | Integer   | RecVersion    |                  |                                          |
| status     | Int       |               |                  |                                          |
| version    | Int       |               |                  |                                          |

### Relations

| Relation                  | Table             |
|---------------------------|-------------------|
| listRecId                 | SysBreakpointList |
| Relation\_SysBreakpoints1 | SysBreakpointList |

### Indexes

| Index     | Allow Duplicates | Fields |
|-----------|------------------|--------|
| ListRecId | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysBreakpoints Table](#sysbreakpoints)

## []()SysCacheFlush
The SysCacheFlush table contains data that is used for synchronization of caches across multiple AOS servers.

### Fields

| Field            | Type        | Extended Type          | Enumeration Type | Description                                     |
|------------------|-------------|------------------------|------------------|-------------------------------------------------|
| ClearData        | Container   |                        |                  |                                                 |
| FlushData        | Container   |                        |                  |                                                 |
| FlushVersion     | Int         |                        |                  |                                                 |
| modifiedDateTime | UtcDateTime | ModifiedDateTime       |                  |                                                 |
| RecId            | Int64       | RecId                  |                  |                                                 |
| recVersion       | Integer     | RecVersion             |                  |                                                 |
| Scope            | String      | GlobalObjectCacheScope |                  | Name of an instance in the global object cache. |

### Indexes

| Index         | Allow Duplicates | Fields |
|---------------|------------------|--------|
| CacheScopeIdx | No               |        |
| RecIDIdx      | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysCacheFlush Table](#syscacheflush)

## []()SysClientAccessLog
### Fields

| Field           | Type        | Extended Type   | Enumeration Type | Description                                                                                                               |
|-----------------|-------------|-----------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| ClientComputer  | String      | UserIdStr       |                  | Name                                                                                                                      |
| createdBy       | String      | CreatedBy       |                  |                                                                                                                           |
| createdDateTime | UtcDateTime | CreatedDateTime |                  |                                                                                                                           |
| EventsContainer | Container   |                 |                  |                                                                                                                           |
| Partition       | Int64       | Partition       |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId           | Int64       | RecId           |                  |                                                                                                                           |
| recVersion      | Integer     | RecVersion      |                  |                                                                                                                           |
| SessionId       | Int         |                 |                  |                                                                                                                           |

### Relations

| Relation  | Table      |
|-----------|------------|
| Partition | Partitions |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| CreatedByIdx | Yes              |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateDelete. The Application Object Server authorizes each create and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysClientAccessLog Table](#sysclientaccesslog)

## []()SysClientSessions
The SysClientSessions contains the data for the client sessions that are currently active in the system.

### Fields

| Field            | Type        | Extended Type       | Enumeration Type | Description                                                                                                                             |
|------------------|-------------|---------------------|------------------|-----------------------------------------------------------------------------------------------------------------------------------------|
| clientComputer   | String      | UserIdStr           |                  | Name                                                                                                                                    |
| clientType       | Int         |                     |                  |                                                                                                                                         |
| DataPartition    | String      | PartitionKey        |                  | Partition Key (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| DEL\_company     | String      |                     |                  |                                                                                                                                         |
| DEL\_Login\_time | Int         |                     |                  |                                                                                                                                         |
| helpLanguage     | String      | InstalledLanguageId |                  |                                                                                                                                         |
| LoginDateTime    | UtcDateTime |                     |                  |                                                                                                                                         |
| RecId            | Int64       | RecId               |                  |                                                                                                                                         |
| recVersion       | Integer     | RecVersion          |                  |                                                                                                                                         |
| ServerId         | Int         |                     |                  |                                                                                                                                         |
| SessionId        | Int         |                     |                  |                                                                                                                                         |
| sessionType      | Int         |                     |                  |                                                                                                                                         |
| sid              | String      | Sid                 |                  |                                                                                                                                         |
| Status           | Int         |                     |                  |                                                                                                                                         |
| userId           | String      | UserId              |                  | ID for the user                                                                                                                         |
| userLanguage     | String      | InstalledLanguageId |                  |                                                                                                                                         |
| Version          | Int         |                     |                  |                                                                                                                                         |

### Relations

| Relation                     | Table             |
|------------------------------|-------------------|
| DataPartition                | Partitions        |
| Relation\_SysClientSessions1 | SysServerSessions |
| Relation\_SysClientSessions2 | UserInfo          |
| ServerId                     | SysServerSessions |
| userId                       | UserInfo          |

### Indexes

| Index                      | Allow Duplicates | Fields |
|----------------------------|------------------|--------|
| ServerId                   | Yes              |        |
| SessionId                  | No               |        |
| Status                     | Yes              | Status |
| Status\_ClientType\_UserId | Yes              |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysClientSessions Table](#sysclientsessions)

## []()SysConfig
The SysConfig table contains license and configuration information.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| configType        | Enum        |                   | ConfigType       |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| expiration        | String      |                   |                  |                                                                                                                           |
| id                | Int         |                   |                  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| shadowValue       | String      |                   |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| timestamp         | String      |                   |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| userCount         | Int         |                   |                  |                                                                                                                           |
| value             | String      |                   |                  |                                                                                                                           |

### Indexes

| Index      | Allow Duplicates | Fields |
|------------|------------------|--------|
| ConfigType | No               |        |
| RecId      | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysConfig Table](#sysconfig)

## []()SysEncryptionKey
The SysEncryptionKey table stores the encryption key that is used to encrypt the EP query string and post the data parameters.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| Key               | Container   |                   |                  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| RecID | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysEncryptionKey Table](#sysencryptionkey)

## []()SysGlobalConfiguration
The SysGlobalConfiguration table stores system level global setting that can be used to configure specific components.

### Fields

| Field        | Type    | Extended Type | Enumeration Type | Description |
|--------------|---------|---------------|------------------|-------------|
| Name         | String  |               |                  |             |
| RecId        | Int64   | RecId         |                  |             |
| recVersion   | Integer | RecVersion    |                  |             |
| ServerId     | String  |               |                  |             |
| SettingLevel | Int     |               |                  |             |
| Value        | String  |               |                  |             |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| NameIdx  | No               |        |
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysGlobalConfiguration Table](#sysglobalconfiguration)

## []()SysInheritanceRelations
The SysInheritanceRelations framework helper table for table inheritance. The table stores table inheritance hierarchy related information.

### Fields

| Field          | Type    | Extended Type | Enumeration Type | Description |
|----------------|---------|---------------|------------------|-------------|
| MainTableId    | Int     |               |                  |             |
| RecId          | Int64   | RecId         |                  |             |
| recVersion     | Integer | RecVersion    |                  |             |
| RelatedTableId | Int     |               |                  |             |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| Main        | No               |        |
| RelatedMain | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysInheritanceRelations Table](#sysinheritancerelations)

## []()SysLastValue
The SysLastValue table is storage for the usage data that is recorded as users navigate the system.

### Fields

| Field       | Type      | Extended Type      | Enumeration Type | Description                                                                                                               |
|-------------|-----------|--------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| company     | String    | SelectableDataArea |                  | ID for the company you can select                                                                                         |
| designName  | String    | UtilElementName    |                  | Name of the application element.                                                                                          |
| elementName | String    | UtilElementName    |                  | Name of the application element.                                                                                          |
| isKernel    | Enum      |                    | boolean          |                                                                                                                           |
| Partition   | Int64     | Partition          |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId       | Int64     | RecId              |                  |                                                                                                                           |
| recordType  | Enum      |                    | UtilElementType  |                                                                                                                           |
| recVersion  | Integer   | RecVersion         |                  |                                                                                                                           |
| userId      | String    | UserId             |                  | ID for the user                                                                                                           |
| value       | Container |                    |                  |                                                                                                                           |

### Relations

| Relation                | Table      |
|-------------------------|------------|
| isVirtual\_Extern       | DataArea   |
| Partition               | Partitions |
| Relation\_SysLastValue1 | UserInfo   |
| Relation\_SysLastValue2 | DataArea   |
| userId                  | UserInfo   |

### Indexes

| Index      | Allow Duplicates | Fields |
|------------|------------------|--------|
| RecordType | Yes              |        |
| UserId     | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysLastValue Table](#syslastvalue)

## []()SysModel
The SysModel table contains information about installed models on the system.

### Fields

| Field            | Type        | Extended Type    | Enumeration Type | Description          |
|------------------|-------------|------------------|------------------|----------------------|
| createdBy        | String      | CreatedBy        |                  |                      |
| createdDateTime  | UtcDateTime | CreatedDateTime  |                  |                      |
| Layer            | Int64       | LayerRecid       |                  | The ID of the layer. |
| modifiedBy       | String      | ModifiedBy       |                  |                      |
| modifiedDateTime | UtcDateTime | ModifiedDateTime |                  |                      |
| RecId            | Int64       | RecId            |                  |                      |
| recVersion       | Integer     | RecVersion       |                  |                      |
| State            | String      |                  |                  |                      |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModel Table](#sysmodel)

## []()SysModelElement
The SysModelElement table lists the ModelElements that the installation holds.

### Fields

| Field              | Type    | Extended Type           | Enumeration Type | Description                                                              |
|--------------------|---------|-------------------------|------------------|--------------------------------------------------------------------------|
| AxId               | Integer | UtilElementId           |                  | Unique internal identification number of the application object.         |
| ElementType        | Int64   | ModelElementType        |                  | The ID of an ElementType                                                 |
| Name               | String  |                         |                  |                                                                          |
| Origin             |         |                         |                  |                                                                          |
| ParentId           | Integer | UtilElementParentId     |                  | The unique internal identification number of a parent application object |
| ParentModelElement | Int64   | ParentModelElementRecid |                  | The ID of a parent model element                                         |
| PartOfInheritance  | Int     |                         |                  |                                                                          |
| RecId              | Int64   | RecId                   |                  |                                                                          |
| recVersion         | Integer | RecVersion              |                  |                                                                          |
| RootModelElement   | Int64   | RootModelElementRecid   |                  | The ID of a root model element                                           |

### Relations

| Relation                      | Table               |
|-------------------------------|---------------------|
| ElementType                   | SysModelElementType |
| Relation\_SysModelElementType | SysModelElementType |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElement Table](#sysmodelelement)

## []()SysModelElementData
The SysModelElementData table provides the Layer specific data for any SysModelElement.

### Fields

| Field            | Type        | Extended Type     | Enumeration Type | Description              |
|------------------|-------------|-------------------|------------------|--------------------------|
| createdBy        | String      | CreatedBy         |                  |                          |
| createdDateTime  | UtcDateTime | CreatedDateTime   |                  |                          |
| Layer            | Int64       | LayerRecid        |                  | The ID of the layer.     |
| LegacyId         | Int         |                   |                  |                          |
| ModelElement     | Int64       | ModelElementRecid |                  | The ID of a ModelElement |
| ModelId          | Integer     | ModelId           |                  | The ID of the model.     |
| modifiedBy       | String      | ModifiedBy        |                  |                          |
| modifiedDateTime | UtcDateTime | ModifiedDateTime  |                  |                          |
| RecId            | Int64       | RecId             |                  |                          |
| recVersion       | Integer     | RecVersion        |                  |                          |
| SaveCount        | Int         |                   |                  |                          |

### Relations

| Relation                  | Table           |
|---------------------------|-----------------|
| Layer                     | SysModelLayer   |
| ModelElement              | SysModelElement |
| ModelId                   | SysModel        |
| Relation\_SysModel        | SysModel        |
| Relation\_SysModelElement | SysModelElement |
| Relation\_SysModelLayer   | SysModelLayer   |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementData Table](#sysmodelelementdata)

## []()SysModelElementDataOld
The SysModelElementDataOld table provides the Layer specific data for any SysModelElementOld.

### Fields

| Field            | Type        | Extended Type     | Enumeration Type | Description              |
|------------------|-------------|-------------------|------------------|--------------------------|
| createdBy        | String      | CreatedBy         |                  |                          |
| createdDateTime  | UtcDateTime | CreatedDateTime   |                  |                          |
| Layer            | Int64       | LayerRecid        |                  | The ID of the layer.     |
| LegacyId         | Int         |                   |                  |                          |
| ModelElement     | Int64       | ModelElementRecid |                  | The ID of a ModelElement |
| ModelId          | Integer     | ModelId           |                  | The ID of the model.     |
| modifiedBy       | String      | ModifiedBy        |                  |                          |
| modifiedDateTime | UtcDateTime | ModifiedDateTime  |                  |                          |
| RecId            | Int64       | RecId             |                  |                          |
| recVersion       | Integer     | RecVersion        |                  |                          |
| SaveCount        | Int         |                   |                  |                          |

### Relations

| Relation                     | Table              |
|------------------------------|--------------------|
| Layer                        | SysModelLayerOld   |
| ModelElement                 | SysModelElementOld |
| ModelId                      | SysModelOld        |
| Relation\_SysModelElementOld | SysModelElementOld |
| Relation\_SysModelLayerOld   | SysModelLayerOld   |
| Relation\_SysModelOld        | SysModelOld        |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementDataOld Table](#sysmodelelementdataold)

## []()SysModelElementLabel
The SysModelElementLabel table contains the label text for a given language.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description |
|------------|---------|---------------|------------------|-------------|
| Comment    | String  |               |                  |             |
| Id         | Int     |               |                  |             |
| LabelId    | String  |               |                  |             |
| Language   | String  |               |                  |             |
| Module     | String  |               |                  |             |
| RecId      | Int64   | RecId         |                  |             |
| recVersion | Integer | RecVersion    |                  |             |
| Text       | String  |               |                  |             |

### Indexes

| Index           | Allow Duplicates | Fields |
|-----------------|------------------|--------|
| ModuleLangIDIdx | No               |        |
| RecIDIdx        | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementLabel Table](#sysmodelelementlabel)

## []()SysModelElementLabelOld
The SysModelElementLabelOld table contains the label text for a given language.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description |
|------------|---------|---------------|------------------|-------------|
| Comment    | String  |               |                  |             |
| Id         | Int     |               |                  |             |
| LabelId    | String  |               |                  |             |
| Language   | String  |               |                  |             |
| Module     | String  |               |                  |             |
| RecId      | Int64   | RecId         |                  |             |
| recVersion | Integer | RecVersion    |                  |             |
| Text       | String  |               |                  |             |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementLabelOld Table](#sysmodelelementlabelold)

## []()SysModelElementOld
The SysModelElementOld table lists the ModelElements that the installation holds.

### Fields

| Field              | Type    | Extended Type           | Enumeration Type | Description                                                              |
|--------------------|---------|-------------------------|------------------|--------------------------------------------------------------------------|
| AxId               | Integer | UtilElementId           |                  | Unique internal identification number of the application object.         |
| ElementType        | Int64   | ModelElementType        |                  | The ID of an ElementType                                                 |
| Name               | String  |                         |                  |                                                                          |
| Origin             |         |                         |                  |                                                                          |
| ParentId           | Integer | UtilElementParentId     |                  | The unique internal identification number of a parent application object |
| ParentModelElement | Int64   | ParentModelElementRecid |                  | The ID of a parent model element                                         |
| PartOfInheritance  | Int     |                         |                  |                                                                          |
| RecId              | Int64   | RecId                   |                  |                                                                          |
| recVersion         | Integer | RecVersion              |                  |                                                                          |
| RootModelElement   | Int64   | RootModelElementRecid   |                  | The ID of a root model element                                           |

### Relations

| Relation                         | Table                  |
|----------------------------------|------------------------|
| ElementType                      | SysModelElementTypeOld |
| Relation\_SysModelElementTypeOld | SysModelElementTypeOld |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementOld Table](#sysmodelelementold)

## []()SysModelElementSource
The SysModelElementSource table contains the Source Text for all SysModelElements that have source.

### Fields

| Field        | Type      | Extended Type     | Enumeration Type | Description              |
|--------------|-----------|-------------------|------------------|--------------------------|
| Layer        | Int64     | LayerRecid        |                  | The ID of the layer.     |
| ModelElement | Int64     | ModelElementRecid |                  | The ID of a ModelElement |
| RecId        | Int64     | RecId             |                  |                          |
| recVersion   | Integer   | RecVersion        |                  |                          |
| Source       | Container |                   |                  |                          |

### Relations

| Relation                      | Table               |
|-------------------------------|---------------------|
| Layer                         | SysModelElementData |
| Relation\_SysModelElementData | SysModelElementData |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementSource Table](#sysmodelelementsource)

## []()SysModelElementSourceOld
The SysModelElementSourceOld table contains the Source Text for all SysModelElementsOld that have source.

### Fields

| Field        | Type      | Extended Type     | Enumeration Type | Description              |
|--------------|-----------|-------------------|------------------|--------------------------|
| Layer        | Int64     | LayerRecid        |                  | The ID of the layer.     |
| ModelElement | Int64     | ModelElementRecid |                  | The ID of a ModelElement |
| RecId        | Int64     | RecId             |                  |                          |
| recVersion   | Integer   | RecVersion        |                  |                          |
| Source       | Container |                   |                  |                          |

### Relations

| Relation                         | Table                  |
|----------------------------------|------------------------|
| Layer                            | SysModelElementDataOld |
| Relation\_SysModelElementDataOld | SysModelElementDataOld |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementSourceOld Table](#sysmodelelementsourceold)

## []()SysModelElementType
The SysModelElementType table specifies the possible SysModelElement types. Its Recid is backwards compatible with the UtilRecordType enum for the ‘old’ element types.

### Fields

| Field        | Type    | Extended Type        | Enumeration Type | Description                   |
|--------------|---------|----------------------|------------------|-------------------------------|
| Name         | String  | ModelElementTypeName |                  | The name of the element type. |
| ParentType   | Int64   | ModelElementType     |                  | The ID of an ElementType      |
| RecId        | Int64   | RecId                |                  |                               |
| recVersion   | Integer | RecVersion           |                  |                               |
| TreeNodeName | String  |                      |                  |                               |

### Relations

| Relation | Table               |
|----------|---------------------|
| Name     | SysModelElementType |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| RecIDIdx    | No               |        |
| TypeNameIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementType Table](#sysmodelelementtype)

## []()SysModelElementTypeOld
The SysModelElementTypeOld table specifies the possible SysModelElementOld types. Its Recid is backwards compatible with the UtilRecordType enum for the ‘old’ element types.

### Fields

| Field        | Type    | Extended Type        | Enumeration Type | Description                   |
|--------------|---------|----------------------|------------------|-------------------------------|
| Name         | String  | ModelElementTypeName |                  | The name of the element type. |
| ParentType   | Int64   | ModelElementType     |                  | The ID of an ElementType      |
| RecId        | Int64   | RecId                |                  |                               |
| recVersion   | Integer | RecVersion           |                  |                               |
| TreeNodeName | String  |                      |                  |                               |

### Relations

| Relation | Table               |
|----------|---------------------|
| Name     | SysModelElementType |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelElementTypeOld Table](#sysmodelelementtypeold)

## []()SysModelLayer
The SysModelLayer table lists the possible LayerId and Name. If Model data exists in a layer it reports the aggregated version number for that layer.

### Fields

| Field         | Type    | Extended Type | Enumeration Type | Description |
|---------------|---------|---------------|------------------|-------------|
| IsDirty       | Int     |               |                  |             |
| Layer         | Enum    |               | UtilEntryLevel   |             |
| RecId         | Int64   | RecId         |                  |             |
| recVersion    | Integer | RecVersion    |                  |             |
| VersionNumber | Int     |               |                  |             |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelLayer Table](#sysmodellayer)

## []()SysModelLayerOld
The SysModelLayerOld table lists the possible LayerId and Name. If Model data exists in a layer it reports the aggregated version number for that layer.

### Fields

| Field         | Type    | Extended Type | Enumeration Type | Description |
|---------------|---------|---------------|------------------|-------------|
| Layer         | Enum    |               | UtilEntryLevel   |             |
| RecId         | Int64   | RecId         |                  |             |
| recVersion    | Integer | RecVersion    |                  |             |
| VersionNumber | Int     |               |                  |             |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelLayerOld Table](#sysmodellayerold)

## []()SysModelManifest
The SysModelManifest table contains the manifest information about deployed models, such as Description, Publisher and Version of a model

### Fields

| Field           | Type    | Extended Type              | Enumeration Type | Description                               |
|-----------------|---------|----------------------------|------------------|-------------------------------------------|
| Category        | Integer | ModelManifestCategoryRecId |                  | The ID of the model category              |
| Description     | String  | ModelDescription           |                  | The description of the model.             |
| DisplayName     | String  | ModelDisplayName           |                  | The display name of the model.            |
| Model           | Int64   | ModelRecid                 |                  | The ID of the model.                      |
| Name            | String  | ModelName                  |                  | The name of the model in the model store. |
| Publisher       | String  | ModelPublisher             |                  | The publisher of the model.               |
| RecId           | Int64   | RecId                      |                  |                                           |
| recVersion      | Integer | RecVersion                 |                  |                                           |
| Signed          | Int     |                            |                  |                                           |
| VersionBuildNo  | Int     |                            |                  |                                           |
| VersionMajor    | Int     |                            |                  |                                           |
| VersionMinor    | Int     |                            |                  |                                           |
| VersionRevision | Int     |                            |                  |                                           |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Relations

| Relation                           | Table                    |
|------------------------------------|--------------------------|
| Category                           | SysModelManifestCategory |
| Model                              | SysModel                 |
| Relation\_SysModel                 | SysModel                 |
| Relation\_SysModelManifestCategory | SysModelManifestCategory |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| ModelNameIdx | No               |        |
| RecIDIdx     | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelManifest Table](#sysmodelmanifest)

## []()SysModelManifestCategory
The SysModelManifestCategory table contains the category aspect of the manifest information for deployed models.

### Fields

| Field      | Type    | Extended Type             | Enumeration Type | Description                     |
|------------|---------|---------------------------|------------------|---------------------------------|
| Name       | String  | ModelManifestCategoryName |                  | The name of the model category. |
| RecId      | Int64   | RecId                     |                  |                                 |
| recVersion | Integer | RecVersion                |                  |                                 |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| NameIdx  | No               |        |
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelManifestCategory Table](#sysmodelmanifestcategory)

## []()SysModelManifestCategoryOld
The SysModelManifestCategoryOld table contains the category aspect of the manifest information for deployed models.

### Fields

| Field      | Type    | Extended Type             | Enumeration Type | Description                     |
|------------|---------|---------------------------|------------------|---------------------------------|
| Name       | String  | ModelManifestCategoryName |                  | The name of the model category. |
| RecId      | Int64   | RecId                     |                  |                                 |
| recVersion | Integer | RecVersion                |                  |                                 |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelManifestCategoryOld Table](#sysmodelmanifestcategoryold)

## []()SysModelManifestOld
The SysModelManifestOld table contains the manifest information about deployed models, such as Description, Publisher and Version of a model.

### Fields

| Field           | Type    | Extended Type              | Enumeration Type | Description                               |
|-----------------|---------|----------------------------|------------------|-------------------------------------------|
| Category        | Integer | ModelManifestCategoryRecId |                  | The ID of the model category              |
| Description     | String  | ModelDescription           |                  | The description of the model.             |
| DisplayName     | String  | ModelDisplayName           |                  | The display name of the model.            |
| Model           | Int64   | ModelRecidOld              |                  | The ID of the model (old).                |
| Name            | String  | ModelName                  |                  | The name of the model in the model store. |
| Publisher       | String  | ModelPublisher             |                  | The publisher of the model.               |
| RecId           | Int64   | RecId                      |                  |                                           |
| recVersion      | Integer | RecVersion                 |                  |                                           |
| Signed          | Int     |                            |                  |                                           |
| VersionBuildNo  | Int     |                            |                  |                                           |
| VersionMajor    | Int     |                            |                  |                                           |
| VersionMinor    | Int     |                            |                  |                                           |
| VersionRevision | Int     |                            |                  |                                           |

### Field Groups

| Field Group        | Fields |
|--------------------|--------|
| AutoIdentification |        |

### Relations

| Relation                              | Table                       |
|---------------------------------------|-----------------------------|
| Category                              | SysModelManifestCategoryOld |
| Model                                 | SysModelOld                 |
| Relation\_SysModelManifestCategoryOld | SysModelManifestCategoryOld |
| Relation\_SysModelOld                 | SysModelOld                 |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| ModelNameIdx | No               |        |
| RecIDIdx     | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelManifestOld Table](#sysmodelmanifestold)

## []()SysModelOld
The SysModelOld table contains information about installed models on the system.

### Fields

| Field            | Type        | Extended Type    | Enumeration Type | Description          |
|------------------|-------------|------------------|------------------|----------------------|
| createdBy        | String      | CreatedBy        |                  |                      |
| createdDateTime  | UtcDateTime | CreatedDateTime  |                  |                      |
| Layer            | Int64       | LayerRecid       |                  | The ID of the layer. |
| modifiedBy       | String      | ModifiedBy       |                  |                      |
| modifiedDateTime | UtcDateTime | ModifiedDateTime |                  |                      |
| RecId            | Int64       | RecId            |                  |                      |
| recVersion       | Integer     | RecVersion       |                  |                      |
| State            | String      |                  |                  |                      |

### Indexes

| Index    | Allow Duplicates | Fields |
|----------|------------------|--------|
| RecIDIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysModelOld Table](#sysmodelold)

## []()SysOccConfiguration
The SysOccConfiguration table stores the global concurrency model setting and updates the conflict exception login policy.

### Fields

| Field                     | Type    | Extended Type | Enumeration Type | Description |
|---------------------------|---------|---------------|------------------|-------------|
| AutoUpdateRecVersion      | Enum    |               | boolean          |             |
| GlobalOccMode             | Enum    |               | GlobalOccMode    |             |
| LogHandledUpdateConflicts | Enum    |               | boolean          |             |
| RecId                     | Int64   | RecId         |                  |             |
| recVersion                | Integer | RecVersion    |                  |             |
| UniqueIndex               | Int     |               |                  |             |
| UseReadUncommitedForAll   | Enum    |               | boolean          |             |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| UniqueIndex | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysOccConfiguration Table](#sysoccconfiguration)

## []()SysRecordLevelSecurity
The SysRecordLevelSecurity table contains all the record level security restrictions that are configured by the system administrator. The restrictions are persisted on a per company, per group basis.

### Fields

| Field             | Type        | Extended Type      | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|--------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| \_unused          | Enum        |                    | boolean          |                                                                                                                           |
| companyId         | String      | SelectableDataArea |                  | ID for the company you can select                                                                                         |
| createdBy         | String      | CreatedBy          |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime    |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime   |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| DEL\_groupId      | String      | UserGroupId        |                  | ID for the user group                                                                                                     |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| modifiedBy        | String      | ModifiedBy         |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime   |                  |                                                                                                                           |
| Partition         | Int64       | Partition          |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId             | Int64       | RecId              |                  |                                                                                                                           |
| recVersion        | Integer     | RecVersion         |                  |                                                                                                                           |
| restriction       | Container   |                    |                  |                                                                                                                           |
| SecurityRole      | Int64       | RecId              |                  | Name of the security role                                                                                                 |
| tabId             | Integer     | TableId            |                  | ID for the table                                                                                                          |

### Relations

| Relation               | Table         |
|------------------------|---------------|
| companyId              | DataArea      |
| DEL\_groupId           | UserGroupInfo |
| Partition              | Partitions    |
| Relation\_SecurityRole | SecurityRole  |
| SecurityRole           | SecurityRole  |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| RecId | No               |        |
| Role  | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysRecordLevelSecurity Table](#sysrecordlevelsecurity)

## []()SysServerSessions
The SysServerSessions table is used to store information about the active AOS Servers in the system.

### Fields

| Field               | Type        | Extended Type | Enumeration Type | Description |
|---------------------|-------------|---------------|------------------|-------------|
| AOSAccount          | String      |               |                  |             |
| AOSId               | String      |               |                  |             |
| DEL\_LastUpdateTime | Int         |               |                  |             |
| DEL\_Login\_time    | Int         |               |                  |             |
| Instance\_Name      | String      |               |                  |             |
| LastUpdateDateTime  | UtcDateTime |               |                  |             |
| LoadBalance         | Int         |               |                  |             |
| LoginDateTime       | UtcDateTime |               |                  |             |
| RecId               | Int64       | RecId         |                  |             |
| recVersion          | Integer     | RecVersion    |                  |             |
| ServerId            | Int         |               |                  |             |
| Status              | Int         |               |                  |             |
| Version             | Int         |               |                  |             |
| Workload            | Int         |               |                  |             |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| LoadBalance | Yes              |        |
| ServerId    | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysServerSessions Table](#sysserversessions)

## []()SysSetbasedHelper
The SysSetbasedHelper framework helper table for table inheritance set-based operations.

### Fields

| Field          | Type    | Extended Type | Enumeration Type | Description                              |
|----------------|---------|---------------|------------------|------------------------------------------|
| CandidateRecId | Int64   | RecId         |                  | Unique ID for the record in the database |
| RecId          | Int64   | RecId         |                  |                                          |
| recVersion     | Integer | RecVersion    |                  |                                          |

### Indexes

| Index             | Allow Duplicates | Fields |
|-------------------|------------------|--------|
| CandidateRecIDIdx | No               |        |
| RecIDIdx          | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SysSetbasedHelper Table](#syssetbasedhelper)

## []()SystemSequences
The SystemSequences table holds the next available record ID block for each table.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description                              |
|------------|---------|---------------|------------------|------------------------------------------|
| cycle      | Enum    |               | boolean          |                                          |
| dataAreaId | String  | DataAreaId    |                  |                                          |
| id         | Int     |               |                  |                                          |
| maxVal     | Int64   | RecId         |                  | Unique ID for the record in the database |
| minVal     | Int64   | RecId         |                  | Unique ID for the record in the database |
| name       | String  |               |                  |                                          |
| nextVal    | Int64   | RecId         |                  | Unique ID for the record in the database |
| RecId      | Int64   | RecId         |                  |                                          |
| recVersion | Integer | RecVersion    |                  |                                          |
| tabId      | Integer | TableId       |                  | ID for the table                         |

### Relations

| Relation   | Table    |
|------------|----------|
| dataAreaId | DataArea |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [SystemSequences Table](#systemsequences)

## []()TableCollectionList
The TableCollectionList table stores the mapping between table collections and virtual companies.

### Fields

| Field           | Type    | Extended Type   | Enumeration Type | Description                                                                                                               |
|-----------------|---------|-----------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| Partition       | Int64   | Partition       |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId           | Int64   | RecId           |                  |                                                                                                                           |
| recVersion      | Integer | RecVersion      |                  |                                                                                                                           |
| tableCollection | String  | UtilElementName |                  | Name of the application element.                                                                                          |
| virtualDataArea | String  | VirtualDataArea |                  | ID for a virtual company                                                                                                  |

### Relations

| Relation                  | Table        |
|---------------------------|--------------|
| isVirtual\_Extern         | DataArea     |
| parentId\_Extern          | UtilElements |
| Partition                 | Partitions   |
| Relation\_CollectionList1 | UtilElements |
| Relation\_CollectionList2 | DataArea     |

### Indexes

| Index           | Allow Duplicates | Fields |
|-----------------|------------------|--------|
| VirtualDataArea | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [TableCollectionList Table](#tablecollectionlist)

## []()TimeZonesList
The TimeZonesList table contains the list of the time zones that are supported.

### Fields

| Field           | Type    | Extended Type | Enumeration Type | Description |
|-----------------|---------|---------------|------------------|-------------|
| EnumName        | String  |               |                  |             |
| EnumPosition    | Int     |               |                  |             |
| RecId           | Int64   | RecId         |                  |             |
| recVersion      | Integer | RecVersion    |                  |             |
| TimeZoneKeyName | String  |               |                  |             |
| TzEnum          | Enum    |               | Timezone         |             |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| EnumPosition | No               |        |
| TzEnum       | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [TimeZonesList Table](#timezoneslist)

## []()TimeZonesRulesData
The TimeZonesRulesData table contains the GMT offsets and daylight saving time information for all time zones that are supported.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description |
|------------|---------|---------------|------------------|-------------|
| Bias       | Int     |               |                  |             |
| DBias      | Int     |               |                  |             |
| DDay       | Int     |               |                  |             |
| DDayOfWeek | Int     |               |                  |             |
| DHour      | Int     |               |                  |             |
| DMinute    | Int     |               |                  |             |
| DMonth     | Int     |               |                  |             |
| DSecond    | Int     |               |                  |             |
| DYear      | Int     |               |                  |             |
| RecId      | Int64   | RecId         |                  |             |
| recVersion | Integer | RecVersion    |                  |             |
| RuleId     | Int     |               |                  |             |
| SBias      | Int     |               |                  |             |
| SDay       | Int     |               |                  |             |
| SDayOfWeek | Int     |               |                  |             |
| SHour      | Int     |               |                  |             |
| SMinute    | Int     |               |                  |             |
| SMonth     | Int     |               |                  |             |
| SSecond    | Int     |               |                  |             |
| SYear      | Int     |               |                  |             |
| TzEnum     | Enum    |               | Timezone         |             |
| Year       | Int     |               |                  |             |

### Relations

| Relation                      | Table         |
|-------------------------------|---------------|
| Relation\_TimeZonesRulesData1 | TimeZonesList |
| TzEnum                        | TimeZonesList |

### Indexes

| Index  | Allow Duplicates | Fields |
|--------|------------------|--------|
| RuleId | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [TimeZonesRulesData Table](#timezonesrulesdata)

## []()UserDataAreaFilter
The UserDataAreaFilter table contains a list of selectable companies for a user. It is populated by invoking the populateSelectableCompanies method on the SecurityRights class.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description                                                                                                               |
|------------|---------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| DataArea   | String  | DataAreaId    |                  | ID for an area of data                                                                                                    |
| Partition  | Int64   | Partition     |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId      | Int64   | RecId         |                  |                                                                                                                           |
| recVersion | Integer | RecVersion    |                  |                                                                                                                           |
| User       | String  | UserId        |                  | ID for the user                                                                                                           |

### Relations

| Relation           | Table      |
|--------------------|------------|
| DataArea           | DataArea   |
| Partition          | Partitions |
| Relation\_DataArea | DataArea   |
| Relation\_User     | UserInfo   |
| User               | UserInfo   |

### Indexes

| Index       | Allow Duplicates | Fields |
|-------------|------------------|--------|
| DataAreaIdx | No               |        |
| RecIdIdx    | No               |        |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UserDataAreaFilter Table](#userdataareafilter)

## []()UserInfo
The UserInfo table contains a list of users and their active directory and default information.

### Fields

| Field                     | Type    | Extended Type       | Enumeration Type     | Description                                                                                                               |
|---------------------------|---------|---------------------|----------------------|---------------------------------------------------------------------------------------------------------------------------|
| accountType               | Enum    |                     | UserAccountType      |                                                                                                                           |
| autoInfo                  | Int     |                     |                      |                                                                                                                           |
| autoLogOff                | Int     |                     |                      |                                                                                                                           |
| autoUpdate                | Int     |                     |                      |                                                                                                                           |
| clientAccessLogLevel      | Int     |                     |                      |                                                                                                                           |
| company                   | String  | SelectableDataArea  |                      | ID for the company you can select                                                                                         |
| compilerWarningLevel      | Enum    |                     | CompilerWarningLevel |                                                                                                                           |
| confirmDelete             | Int     |                     |                      |                                                                                                                           |
| confirmUpdate             | Int     |                     |                      |                                                                                                                           |
| credentialRecId           | int64   |                     |                      |                                                                                                                           |
| debuggerPopup             | Int     |                     |                      |                                                                                                                           |
| debugInfo                 | Int     |                     |                      |                                                                                                                           |
| defaultPartition          | Enum    |                     | boolean              | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| DEL\_\_unused1            | String  |                     |                      |                                                                                                                           |
| DEL\_\_unused2            | String  |                     |                      |                                                                                                                           |
| DEL\_defaultModelId       | Int     |                     |                      |                                                                                                                           |
| DEL\_osAccountName        | String  |                     |                      |                                                                                                                           |
| DEL\_password             | String  |                     |                      |                                                                                                                           |
| DEL\_startupMenu          | String  | UtilElementName     |                      | Name of the application element.                                                                                          |
| enable                    | Enum    |                     | boolean              |                                                                                                                           |
| enabledOnce               | Enum    |                     | boolean              |                                                                                                                           |
| externalId                | String  |                     |                      |                                                                                                                           |
| externalIdType            | Enum    |                     | ExternalIdType       |                                                                                                                           |
| externalUser              | Enum    |                     | boolean              |                                                                                                                           |
| filterByGridOnByDefault   | Enum    |                     | boolean              |                                                                                                                           |
| formFontName              | String  |                     |                      |                                                                                                                           |
| formFontSize              | Int     |                     |                      |                                                                                                                           |
| garbagecollectlimit       | Int     |                     |                      |                                                                                                                           |
| generalInfo               | Int     |                     |                      |                                                                                                                           |
| globalExcelExportFilePath | String  |                     |                      | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| globalExcelExportLocation | Int     |                     |                      |                                                                                                                           |
| globalExcelExportMode     | Int     |                     |                      |                                                                                                                           |
| globalFormOpenMode        | Int     |                     |                      |                                                                                                                           |
| globalListPageLinkMode    | Int     |                     |                      |                                                                                                                           |
| helplanguage              | String  | InstalledLanguageId |                      |                                                                                                                           |
| historyLimit              | Int     |                     |                      |                                                                                                                           |
| homePageRefreshDuration   | Int     |                     |                      |                                                                                                                           |
| id                        | String  | UserId              |                      | ID for the user                                                                                                           |
| IdentityProvider          | String  | NetworkDomain       |                      |                                                                                                                           |
| infologLevel              | Int     |                     |                      |                                                                                                                           |
| issuerRecId               | int64   |                     |                      |                                                                                                                           |
| language                  | String  | InstalledLanguageId |                      |                                                                                                                           |
| messageLimit              | Int     |                     |                      |                                                                                                                           |
| name                      | String  | UserIdStr           |                      | Name                                                                                                                      |
| networkAlias              | String  | NetworkAlias        |                      |                                                                                                                           |
| networkDomain             | String  | NetworkDomain       |                      |                                                                                                                           |
| notifyTimeZoneMismatch    | Enum    |                     | boolean              |                                                                                                                           |
| Partition                 | Int64   | Partition           |                      | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| preferredCalendar         | Enum    |                     | PreferredCalendar    |                                                                                                                           |
| PreferredLocale           | String  | PreferredLocale     |                      |                                                                                                                           |
| preferredTimeZone         | Enum    |                     | Timezone             |                                                                                                                           |
| propertyFontName          | String  |                     |                      |                                                                                                                           |
| propertyFontSize          | Int     |                     |                      |                                                                                                                           |
| querytimeLimit            | Int     |                     |                      |                                                                                                                           |
| RecId                     | Int64   | RecId               |                      |                                                                                                                           |
| recVersion                | Integer | RecVersion          |                      |                                                                                                                           |
| reportBottomMargin        | String  |                     |                      |                                                                                                                           |
| reportFontName            | String  |                     |                      |                                                                                                                           |
| reportFontSize            | Int     |                     |                      |                                                                                                                           |
| reportLeftMargin          | String  |                     |                      |                                                                                                                           |
| reportRightMargin         | String  |                     |                      |                                                                                                                           |
| reportTopMargin           | String  |                     |                      |                                                                                                                           |
| showAOTLayer              | Int     |                     |                      |                                                                                                                           |
| showModelNameInAOT        | Int     |                     |                      |                                                                                                                           |
| showStatusLine            | Int     |                     |                      |                                                                                                                           |
| showToolbar               | Int     |                     |                      |                                                                                                                           |
| sid                       | String  | Sid                 |                      |                                                                                                                           |
| startupProject            | String  | UtilElementName     |                      | Name of the application element.                                                                                          |
| statuslineInfo            | Int     |                     |                      |                                                                                                                           |
| toolbarInfo               | Int     |                     |                      |                                                                                                                           |
| traceInfo                 | Int     |                     |                      |                                                                                                                           |

### Field Groups

| Field Group | Fields                                                     |
|-------------|------------------------------------------------------------|
| AutoLookup  | id, accountType, name, networkAlias, networkDomain, enable |
| AutoReport  |                                                            |

### Relations

| Relation           | Table      |
|--------------------|------------|
| id                 | UserInfo   |
| isVirtual\_Extern  | DataArea   |
| Partition          | Partitions |
| Relation\_UserInfo | DataArea   |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| Id      | No               |        |
| IdOnly  | Yes              |        |
| Sid     | Yes              |        |
| SidOnly | Yes              |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateDelete. The Application Object Server authorizes each create and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UserInfo Table](#userinfo)

## []()UserInfoStartupModel
The UserInfoStartupModel table holds the preferred startup model for each layer for each user.

### Fields

| Field      | Type    | Extended Type | Enumeration Type | Description                                                                                                               |
|------------|---------|---------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| Layer      | Enum    |               | UtilEntryLevel   |                                                                                                                           |
| ModelId    | Int64   | ModelRecid    |                  | The ID of the model.                                                                                                      |
| Partition  | Int64   | Partition     |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId      | Int64   | RecId         |                  |                                                                                                                           |
| recVersion | Integer | RecVersion    |                  |                                                                                                                           |
| UserId     | String  | UserGroupId   |                  | ID for the user group                                                                                                     |

### Relations

| Relation                        | Table              |
|---------------------------------|--------------------|
| ModelId                         | SysModelManifest   |
| Partition                       | Partitions         |
| Relation\_SysModelManifest      | SysModelManifest   |
| Relation\_UserInfo              | UserInfo           |
| Relation\_UserInfoStartupModel3 | DEL\_UserGroupInfo |
| UserId                          | UserInfo           |

### Indexes

| Index              | Allow Duplicates | Fields |
|--------------------|------------------|--------|
| RecIDIdx           | No               |        |
| UserID\_Layer\_Idx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UserInfoStartupModel Table](#userinfostartupmodel)

## []()UtilElements
The UtilElements table contains the application that is shown in the AOT.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| baseVersion       | Int         |                   |                  |                                                                                                                           |
| code              | Container   |                   |                  |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| name              | String      | UtilElementName   |                  | Name of the application element.                                                                                          |
| parentId          | Int         |                   |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recordType        | Enum        |                   | UtilElementType  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| saveCount         | Int         |                   |                  |                                                                                                                           |
| source            | Container   |                   |                  |                                                                                                                           |
| utilLevel         | Enum        |                   | UtilEntryLevel   |                                                                                                                           |
| version           | Int         |                   |                  |                                                                                                                           |

### Indexes

| Index | Allow Duplicates | Fields                                |
|-------|------------------|---------------------------------------|
| name  | No               | recordType, parentId, name, utilLevel |
| RecId | No               |                                       |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UtilElements Table](#utilelements)

## []()UtilElementsOld
The UtilElementsOld table contains the application model stored in the application folder. It is used during the upgrade process.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| baseVersion       | Int         |                   |                  |                                                                                                                           |
| code              | Container   |                   |                  |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| name              | String      | UtilElementName   |                  | Name of the application element.                                                                                          |
| parentId          | Int         |                   |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recordType        | Enum        |                   | UtilElementType  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| saveCount         | Int         |                   |                  |                                                                                                                           |
| source            | Container   |                   |                  |                                                                                                                           |
| utilLevel         | Enum        |                   | UtilEntryLevel   |                                                                                                                           |
| version           | Int         |                   |                  |                                                                                                                           |

### Indexes

| Index | Allow Duplicates | Fields                                |
|-------|------------------|---------------------------------------|
| name  | No               | recordType, parentId, name, utilLevel |
| RecId | No               |                                       |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UtilElementsOld Table](#utilelementsold)

## []()UtilIdElements
The UtilIdElements table contains the application model shown in the AOT.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| baseVersion       | Int         |                   |                  |                                                                                                                           |
| code              | Container   |                   |                  |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| id                | Int         |                   |                  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| name              | String      | UtilElementName   |                  | Name of the application element.                                                                                          |
| parentId          | Int         |                   |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recordType        | Enum        |                   | UtilElementType  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| saveCount         | Int         |                   |                  |                                                                                                                           |
| utilLevel         | Enum        |                   | UtilEntryLevel   |                                                                                                                           |
| version           | Int         |                   |                  |                                                                                                                           |

### Indexes

| Index | Allow Duplicates | Fields                                |
|-------|------------------|---------------------------------------|
| Id    | No               |                                       |
| name  | No               | recordType, parentId, name, utilLevel |
| RecId | No               |                                       |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UtilIdElements Table](#utilidelements)

## []()UtilIdElementsOld
The UtilIdElementsOld table contains the application model stored in the application folder. It is used during the upgrade process.

### Fields

| Field             | Type        | Extended Type     | Enumeration Type | Description                                                                                                               |
|-------------------|-------------|-------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| baseVersion       | Int         |                   |                  |                                                                                                                           |
| code              | Container   |                   |                  |                                                                                                                           |
| createdBy         | String      | CreatedBy         |                  |                                                                                                                           |
| createdDateTime   | UtcDateTime | CreatedDateTime   |                  |                                                                                                                           |
| dEL\_CreatedTime  | Integer     | DEL\_CreatedTime  |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| dEL\_ModifiedTime | Integer     | DEL\_ModifiedTime |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| id                | Int         |                   |                  |                                                                                                                           |
| modifiedBy        | String      | ModifiedBy        |                  |                                                                                                                           |
| modifiedDateTime  | UtcDateTime | ModifiedDateTime  |                  |                                                                                                                           |
| name              | String      | UtilElementName   |                  | Name of the application element.                                                                                          |
| parentId          | Int         |                   |                  |                                                                                                                           |
| RecId             | Int64       | RecId             |                  |                                                                                                                           |
| recordType        | Enum        |                   | UtilElementType  |                                                                                                                           |
| recVersion        | Integer     | RecVersion        |                  |                                                                                                                           |
| saveCount         | Int         |                   |                  |                                                                                                                           |
| utilLevel         | Enum        |                   | UtilEntryLevel   |                                                                                                                           |
| version           | Int         |                   |                  |                                                                                                                           |

### Indexes

| Index | Allow Duplicates | Fields                                |
|-------|------------------|---------------------------------------|
| Id    | No               |                                       |
| name  | No               | recordType, parentId, name, utilLevel |
| RecId | No               |                                       |

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UtilIdElementsOld Table](#utilidelementsold)

## []()UtilModels
The UtilModels table contains information about models that are installed on the system.

### Fields

| Field            | Type    | Extended Type    | Enumeration Type | Description                               |
|------------------|---------|------------------|------------------|-------------------------------------------|
| CategoryId       | Int     |                  |                  |                                           |
| Description      | String  | ModelDescription |                  | The description of the model.             |
| DisplayName      | String  | ModelDisplayName |                  | The display name of the model.            |
| Id               | Int     |                  |                  |                                           |
| InstallMode      | Int     |                  |                  |                                           |
| Layer            | Enum    |                  | UtilEntryLevel   |                                           |
| MarkedForRemoval | Int     |                  |                  |                                           |
| ModelGroupId     | Int     |                  |                  |                                           |
| Name             | String  | ModelName        |                  | The name of the model in the model store. |
| Publisher        | String  | ModelPublisher   |                  | The publisher of the model.               |
| RecId            | Int64   | RecId            |                  |                                           |
| recVersion       | Integer | RecVersion       |                  |                                           |
| Signed           | Int     |                  |                  |                                           |
| State            | String  |                  |                  |                                           |
| VersionBuildNo   | Int     |                  |                  |                                           |
| VersionMajor     | Int     |                  |                  |                                           |
| VersionMinor     | Int     |                  |                  |                                           |
| VersionRevision  | Int     |                  |                  |                                           |

### Indexes

| Index        | Allow Duplicates | Fields |
|--------------|------------------|--------|
| ModelIDIdx   | No               |        |
| ModelNameIdx | No               |        |
| RecIDIdx     | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [UtilModels Table](#utilmodels)

## []()VirtualDataAreaList
The VirtualDataAreaList table stores the mapping between real companies and virtual companies.

### Fields

| Field           | Type    | Extended Type      | Enumeration Type | Description                                                                                                               |
|-----------------|---------|--------------------|------------------|---------------------------------------------------------------------------------------------------------------------------|
| id              | String  | SelectableDataArea |                  | ID for the company you can select                                                                                         |
| Partition       | Int64   | Partition          |                  | (This field applies only to the following version(s): Microsoft Dynamics AX 2012 R3, Microsoft Dynamics AX 2012 R2 (SYS)) |
| RecId           | Int64   | RecId              |                  |                                                                                                                           |
| recVersion      | Integer | RecVersion         |                  |                                                                                                                           |
| virtualDataArea | String  | VirtualDataArea    |                  | ID for a virtual company                                                                                                  |

### Field Groups

| Field Group             | Fields |
|-------------------------|--------|
| virtualDataAreaRelation |        |

### Relations

| Relation                | Table      |
|-------------------------|------------|
| isVirtual\_Extern       | DataArea   |
| Partition               | Partitions |
| Relation\_DataAreaList1 | DataArea   |
| Relation\_DataAreaList2 | DataArea   |

### Indexes

| Index | Allow Duplicates | Fields |
|-------|------------------|--------|
| Id    | No               |        |
| RecId | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [VirtualDataAreaList Table](#virtualdataarealist)

## []()VSAssembly
The VSAssembly table contains synchronization information that describes the last time an assembly that is stored under the Visual Studio Projects node in the AOT was deployed..

### Fields

| Field       | Type        | Extended Type | Enumeration Type | Description |
|-------------|-------------|---------------|------------------|-------------|
| DeployTo    | Enum        |               | DeployTo         |             |
| Name        | String      | AssemblyName  |                  |             |
| ProjectName | String      | ProjectName   |                  |             |
| ProjectType | String      | ProjectType   |                  |             |
| RecId       | Int64       | RecId         |                  |             |
| recVersion  | Integer     | RecVersion    |                  |             |
| ServerId    | Int         |               |                  |             |
| UpdatedDate | UtcDateTime |               |                  |             |

### Indexes

| Index   | Allow Duplicates | Fields |
|---------|------------------|--------|
| NameIdx | No               |        |

### Security Note

Use of this table could lead to an Elevation of Privileges attack or a Denial of Service attack. Therefore, the AOSAuthorization property is set to an enumeration value of CreateUpdateDelete. The Application Object Server authorizes each create, update, and delete action on the table by confirming that the current user has permission to perform the requested operation on that table. If the user who initiates the operation is not authorized to perform the operation, an exception occurs.

### Inheritance Hierarchy

[xRecord Class](https://docs.microsoft.com/en-us/dynamics365/operations/dev-itpro/dev-reference/x-classes#class-xrecord) [Common Table](#common) [VSAssembly Table](#vsassembly)

