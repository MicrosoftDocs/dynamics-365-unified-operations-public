---
# required metadata

title: F Classes - FormDataObject to FormFastTabHeaderControl
description: API reference for classes from FormDataObject to FormFastTabHeaderControl.
author: RobinARH
manager: AnnBe
ms.date: 2016-03-08 23 - 39 - 56
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
ms.custom: 63703
ms.assetid: 7c23d29c-9408-49ca-82e7-ddb940dc8526
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# F Classes - FormDataObject to FormFastTabHeaderControl

API reference for classes from FormDataObject to FormFastTabHeaderControl.

Class FormDataObject
--------------------

    class FormDataObject extends FormObject

The FormDataObject class represents the fields, affects how controls that refer to a field are displayed on form data sources, and modifies lookup and validation behavior.

### Remarks

By changing the properties, you affect how controls that refer to the field are displayed. Furthermore, if you override the methods on this class, the behavior on lookup and validation can be modified. By using the properties on the FormDataObject class instead of properties on the individual controls, you make sure that the various representations of the same field are handled consistently. This also makes upgrades easier.

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public Common lookupReference(\[FormReferenceControl formReferenceControl\])                                |                                                                                                                                                                         |
| public Common resolveReference(\[FormReferenceControl formReferenceControl\])                               |                                                                                                                                                                         |
| public str resolveAmbiguousReference(\[FormControl formControl\])                                           |                                                                                                                                                                         |
| public int allowAdd(\[int value\])                                                                          | Sets or returns the value of the allowAdd property for the form data object.                                                                                            |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can modify the contents of the control.                                                                                                     |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public FormDataSource datasource()                                                                          |                                                                                                                                                                         |
| public boolean editAutoPostback(\[boolean value\])                                                          |                                                                                                                                                                         |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether the object is enabled or disabled.                                                                                                                   |
| public FieldId fieldId()                                                                                    |                                                                                                                                                                         |
| public str helpField()                                                                                      | Returns the Help text for the control.                                                                                                                                  |
| public str labelText()                                                                                      | Returns the label text for the control.                                                                                                                                 |
| public boolean mandatory(\[boolean value\])                                                                 | Sets or returns a value that indicates whether the data field is mandatory.                                                                                             |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source. |
| public str toolTip()                                                                                        |                                                                                                                                                                         |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| private void OnModified(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                            |                                                                                                                                                                         |
| private void OnValidated(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                           |                                                                                                                                                                         |
| public void modified()                                                                                      | Indicates that the field has been successfully validated and modified in the current record.                                                                            |
| private void OnValidating(\[FormDataObject sender\], \[FormDataFieldEventArgs e\])                          |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void restore()                                                                                       |                                                                                                                                                                         |
| public void lookup(FormControl formControl, str filterStr)                                                  |                                                                                                                                                                         |
| public void dataChanged()                                                                                   |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| public void context()                                                                                       |                                                                                                                                                                         |
| public void find()                                                                                          |                                                                                                                                                                         |
| public void filter(\[str filterStr\], \[NoYes clearPrev\])                                                  |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form, FormControl formControl)                                       |                                                                                                                                                                         |

### Method lookupReference

    public Common lookupReference([FormReferenceControl formReferenceControl])

#### Parameters

formReferenceControl  

#### Return Value

### Method resolveReference

    public Common resolveReference([FormReferenceControl formReferenceControl])

#### Parameters

formReferenceControl  

#### Return Value

### Method resolveAmbiguousReference

    public str resolveAmbiguousReference([FormControl formControl])

#### Parameters

formControl  

#### Return Value

### Method allowAdd

Sets or returns the value of the allowAdd property for the form data object.

    public int allowAdd([int value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

A FormAllowAdd enumeration value that indicates whether the allowAdd property is set to No, Restricted, or Yes.

#### Examples

The following example shows how to retrieve and set the allowAdd property.

    // fdo previously assigned to a FormDataObject object. 
    // Retrieve the allowAdd property. 
    nAllowAdd = fdo.allowAdd(); 
    // Set the allowAdd property. 
    fdo.allowAdd(FormAllowAdd::Restricted);

### Method allowEdit

Determines whether the user can modify the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be modified; otherwise, false.

#### Remarks

If this property is set on a container control, modifications are disabled or enabled for all controls in the container.

#### Examples

The following example shows how to retrieve and set the value of the allowEdit property.

    // Return the value. 
    info (strfmt("allowEdit: %1", this.allowEdit())); 
    // Set the value. 
    this.allowEdit(false);

### Method dataField

    public FieldId dataField([FieldId value])

#### Parameters

value  

#### Return Value

### Method datasource

    public FormDataSource datasource()

#### Return Value

### Method editAutoPostback

    public boolean editAutoPostback([boolean value])

#### Parameters

value  

#### Return Value

### Method enabled

Determines whether the object is enabled or disabled.

    public boolean enabled([boolean value])

#### Parameters

value  
A Boolean value that specifies whether the control is enabled.

#### Return Value

true if the object is enabled; otherwise, false.

#### Remarks

The enabled property lets you enable or disable a control at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message that provides read-only information.

#### Examples

The following example shows how to retrieve and set the enabled property for a control.

    // Return the value of the enabled property. 
    info(strfmt("enabled: %1", this.enabled())); 
    // Set the enabled property. 
    this.enabled(false);

### Method fieldId

    public FieldId fieldId()

#### Return Value

### Method helpField

Returns the Help text for the control.

    public str helpField()

#### Return Value

The Help text for the control; an empty string if there is no Help text for the control.

#### Examples

The following example shows how to use the helpField method.

    str strHelp; 
    strHelp = this.helpField();

### Method labelText

Returns the label text for the control.

    public str labelText()

#### Return Value

The label text for the control; an empty string if there is no label text for the control.

### Method mandatory

Sets or returns a value that indicates whether the data field is mandatory.

    public boolean mandatory([boolean value])

#### Parameters

value  
The value to assign to the mandatory property of the field.

#### Return Value

true if the field is mandatory; otherwise, false.

#### Examples

The following example shows how to retrieve and set the mandatory property for the field.

    // Return the value of the mandatory property. 
    info (strfmt("mandatory: %1", fdo.mandatory())); 
    // Set the value of the mandatory property. 
    fdo.mandatory(false);

### Method skip

Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control that is associated with the data source.

    public boolean skip([boolean value])

#### Parameters

value  
The value to assign to the skip property of the data source that is associated with the control; optional.

#### Return Value

true if the control is skipped when the user presses the TAB key to move to the control that is associated with the data source; otherwise, false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control. Controls are skipped if either the control's skip value is true or the data source's skip value is true.

#### Examples

The following shows how to retrieve and set the skip property of a data source for a control.

    // Return the value of the skip property. 
    info(strfmt("skip: %1", this.skip())); 
    // Set the value of the skip property. 
    this.skip(true);

### Method toolTip

    public str toolTip()

#### Return Value

### Method validate

    public boolean validate()

#### Return Value

### Method visible

Sets or returns a value that indicates whether the control is visible.

    public boolean visible([boolean value])

#### Parameters

value  
The value that is assigned to the visibility setting for the control.

#### Return Value

true if the control is visible; otherwise, false. The default is true.

#### Remarks

Controls that refer to a data source field are visible only when the visible property is set to true on both the control and the underlying data source field. If you set the property on the data source field instead of on the control, you guarantee that the field is handled consistently throughout the form. This makes upgrades easier.

### Method OnModified

    private void OnModified([FormDataObject sender], [FormDataFieldEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnValidated

    private void OnValidated([FormDataObject sender], [FormDataFieldEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method modified

Indicates that the field has been successfully validated and modified in the current record.

    public void modified()

#### Remarks

This method is called from the modified method on controls if the validation methods returned true. You can overriding this method to allow for recalculation of other values that are based on the modified values. The call to the super() method guarantees that the modifiedField method on the table is called. Modified means that the value of the field on the current record has changed, but the value is not written to the database before the record is saved.

### Method OnValidating

    private void OnValidating([FormDataObject sender], [FormDataFieldEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method restore

    public void restore()

### Method lookup

    public void lookup(FormControl formControl, str filterStr)

#### Parameters

formControl  

<!-- -->

filterStr  

### Method dataChanged

    public void dataChanged()

### Method jumpRef

    public void jumpRef()

### Method context

    public void context()

### Method find

    public void find()

### Method filter

    public void filter([str filterStr], [NoYes clearPrev])

#### Parameters

filterStr  

<!-- -->

clearPrev  

### Method performFormLookup

    public void performFormLookup(xFormRun form, FormControl formControl)

#### Parameters

form  

<!-- -->

formControl  

## Class FormDataRow
    class FormDataRow extends Object

### Remarks

### Examples

### Methods

| Method                                                                       | Description                                          |
|------------------------------------------------------------------------------|------------------------------------------------------|
| public Object associatedObject(\[Object value\], \[boolean notifyDetached\]) |                                                      |
| public boolean isDetached()                                                  |                                                      |
| public int rowIndex()                                                        |                                                      |
| private void new()                                                           | Initializes a new instance of the FormDataRow class. |
| public void clearAssociatedObject()                                          |                                                      |

### Method associatedObject

    public Object associatedObject([Object value], [boolean notifyDetached])

#### Parameters

value  

<!-- -->

notifyDetached  

#### Return Value

### Method isDetached

    public boolean isDetached()

#### Return Value

### Method rowIndex

    public int rowIndex()

#### Return Value

### Method new

Initializes a new instance of the FormDataRow class.

    private void new()

### Method clearAssociatedObject

    public void clearAssociatedObject()

## Class FormDataSource
    class FormDataSource extends FormObjectSet

The FormDataSource class contains properties that define the behavior of data sources in forms.

### Remarks

By overriding the methods on the class, you can customize the behavior for the method actions, such as insertion or validation, for a specific form. The FormDataSource class is also used to determine how the data source table is related to other data sources (tables) that are displayed in the form. To override some of the methods in the FormDataSource class, right-click the Methods node for a form data source, and then click Override Method. When you create methods on a form, you should use a \_ds identifier to reference the FormDataSource object for a particular class. For example, CustTrans\_ds references the FormDataSource object for the CustTrans data source on the form, and CustTrans\_ds.executeQuery() executes the FormDataSource.executeQuery method on the CustTrans data source. Several FormDataSource methods return a FormObjectSet object. To use the methods that are defined on the FormDataSource method on this object, you must typecast it to a FormDataSource object.

### Examples

The following example supplies a custom query for a field instead of the automatically generated query. It overrides the performFormLookup method on the field.

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

### Methods

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
| public str name(\[str value\])                                                                                                 | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.                  |
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

### Method active

Retrieves data from joined data sources when a user navigates to a new record and then sets the new record as the current record.

    public int active()

#### Return Value

Always returns 1.

#### Remarks

The active method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking active.

### Method allowCheck

    public boolean allowCheck([boolean value])

#### Parameters

value  

#### Return Value

### Method allowCreate

    public boolean allowCreate([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDeferredLoad

    public boolean allowDeferredLoad([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDelete

    public boolean allowDelete([boolean value])

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

### Method allRowsLoaded

    public boolean allRowsLoaded()

#### Return Value

### Method anyMarked

Checks whether any records in the underlying cache are marked.

    public boolean anyMarked()

#### Return Value

true if any records are marked; otherwise, false.

#### Remarks

Records in a data source can be marked (selected) for actions such as deletion or copying by using the FormDataSource.markedRecord method.

### Method autoNotify

    public boolean autoNotify([boolean value])

#### Parameters

value  

#### Return Value

### Method autoQuery

    public boolean autoQuery([boolean value])

#### Parameters

value  

#### Return Value

### Method autoSearch

    public boolean autoSearch([boolean value])

#### Parameters

value  

#### Return Value

### Method bindField

    public str bindField(FieldId fieldId)

#### Parameters

fieldId  

#### Return Value

### Method bindDataMethod

    public str bindDataMethod(str dataMethodName)

#### Parameters

dataMethodName  

#### Return Value

### Method cacheAddMethod

Registers the specified display or edit method for caching.

    public boolean cacheAddMethod(str methodName, [boolean updateOnWrite])

#### Parameters

methodName  
A Boolean value that determines whether the cached value is updated automatically when the record is written; optional.

<!-- -->

updateOnWrite  
A Boolean value that determines whether the cached value is updated automatically when the record is written; optional.

#### Return Value

true if the method was registered successfully; otherwise, false.

#### Remarks

Cached methods perform calculations on fetched data, and then the calculated values are passed to the client together with the data. The calculated values are updated on reread. By default, the values are also update on write and create. This method should be called after initialization of the data source, but before any data is fetched. Therefore, the call to this method should be put after the call to the super method in the init method. The updateOnWrite parameter also determines whether the display or edit method value should be calculated and cached when a new record is created. To manually update the cached value for the display or edit method, call the FormDataSource.cacheCalculateMethod method. Only table methods that have the display or edit keyword can be cached. Methods that are written on the form or the form data source cannot be cached. Do not register display or edit methods that are not used on the form. Those methods are calculated for each record, even though the values are never shown.

#### Examples

The following example registers two methods for caching on the VendTransOpen table.

    public void init() 
    { 
        super(); 
        this.cacheAddMethod(tablemethodstr(VendTransOpen, 
            nextCashDiscDate)); 
        this.cacheAddMethod(tablemethodstr(VendTransOpen, 
            nextCashDiscAmount)); 
    }

### Method cacheCalculateMethod

Calls the specified cached method and updates the value in the cache for the current record.

    public boolean cacheCalculateMethod(str methodName)

#### Parameters

methodName  
The name of the table method to call.

#### Return Value

true if the value has been updated; otherwise, false.

#### Remarks

The cached value is updated only if the method name that was supplied was previously registered as a cached method by using the FormDataSource.cacheAddMethod method. The cacheCalculate method is particularly useful if you want to update cached values only when certain conditions are met. In this case, set the updateOnWrite parameter in the call to the FormDataSource.cacheAddMethod method to false, and then manually update the cache, such as by using the write method on the data source.

#### Examples

The following example recalculates cached values by using the nextCashDiscDate method and the nextCashDiscAmount method, both of the VendTransOpen table.

    public void write() 
    { 
        super(); 
        vendTransOpen_ds.cacheCalculateMethod(tablemethodstr( 
            VendTransOpen, nextCashDiscDate)); 
        vendTransOpen_ds.cacheCalculateMethod(tablemethodstr( 
            VendTransOpen, nextCashDiscAmount)); 
    }

### Method cacheOnlyMode

    public boolean cacheOnlyMode([boolean value])

#### Parameters

value  

#### Return Value

### Method canCreate

    public boolean canCreate()

#### Return Value

### Method canDelete

    public boolean canDelete()

#### Return Value

### Method canEdit

    public boolean canEdit()

#### Return Value

### Method clientPageSize

    public int clientPageSize([int pageSize])

#### Parameters

pageSize  

#### Return Value

### Method company

    public str company([str value])

#### Parameters

value  

#### Return Value

### Method counterField

    public FieldId counterField([FieldId value])

#### Parameters

value  

#### Return Value

### Method crossCompanyAutoQuery

    public boolean crossCompanyAutoQuery([boolean value])

#### Parameters

value  

#### Return Value

### Method cursor

Has no functionality in the FormObjectSet class.

    public Common cursor([int rowIndex])

#### Parameters

rowIndex  

#### Return Value

#### Remarks

This method is overridden by the FormDataSource.cursor method, which returns the currently active record in the table that is referenced by the data source.

### Method defaultMark

Sets the default mark value for records in a form, which determines whether records are marked when they have been selected in a grid.

    public int defaultMark([int value])

#### Parameters

value  
The default mark value for records in the form. The standard default mark value for records is 1, but this value can be overridden by setting the value parameter. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form when they have been selected.

#### Return Value

The default mark value for records in the form.

#### Remarks

This method is executed when a user clicks the top-left corner in a grid control to select all the records in the grid. The defaultMark method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; defaultMark.

### Method delayActive

    public boolean delayActive([boolean value])

#### Parameters

value  

#### Return Value

### Method extends

    public int extends([AnyType value])

#### Parameters

value  

#### Return Value

### Method findRecord

Finds the specified record in the data source and makes it the current record.

    public boolean findRecord(Common record)

#### Parameters

record  
The record to find.

#### Return Value

true if the record was found; otherwise, false.

#### Remarks

This method is activated when the FormDataSource.findValue method is called. The findRecord method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking findRecord.

### Method findValue

Finds the specified value in the data source and makes the record that has that value the current record that uses the FormDataSource.findRecord method.

    public boolean findValue(FieldId field, str value)

#### Parameters

field  
The value to find.

<!-- -->

value  
The value to find.

#### Return Value

true if the value is found; otherwise, false.

#### Remarks

This method is called when a user clicks FindValue in the shortcut menu on a form control. The findValue method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking findValue.

#### Examples

The following example stores the ID of the current record before it tries to modify data. If the update fails, the data source is positioned on the original record.

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

### Method positionToRecord

    public boolean positionToRecord(Common record)

#### Parameters

record  

#### Return Value

### Method positionToRecordByValue

    public boolean positionToRecordByValue(FieldId field, str value)

#### Parameters

field  

<!-- -->

value  

#### Return Value

### Method first

Moves focus to the first record in the data source.

    public int first()

#### Return Value

A non-zero value if focus is successfully moved to the first record.

#### Remarks

This method is called when a user selects the first record in a form by pressing CTRL+HOME. The first method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click first.

#### Examples

The following example overrides the first method for the InventTransPostingFinancial data source on the InventTrans form and returns the last record in another data source that is used on the form.

    int first() 
    { 
        return inventTrans_ds.first(); 
    }

### Method forceWrite

    public boolean forceWrite([boolean value])

#### Parameters

value  

#### Return Value

### Method functionObject

    public FormObject functionObject(str name)

#### Parameters

name  

#### Return Value

### Method getDataRow

    public FormDataRow getDataRow([int rowIndex], [boolean allowFetchAhead])

#### Parameters

rowIndex  

<!-- -->

allowFetchAhead  

#### Return Value

### Method getFirst

Retrieves the first record in a data set.

    public Common getFirst([int mark], [boolean fetchAhead])

#### Parameters

mark  
A Boolean value; optional. The default value is true.

<!-- -->

fetchAhead  
A Boolean value; optional. The default value is true.

#### Return Value

The first record in the data set.

#### Remarks

If the mark parameter is not 0 (zero), the first record that is marked with the specified value is returned, and subsequent calls to the FormDataSource.getNext method return marked records. If the fetchAhead parameter is set to false, only cached records are returned. If it is set to true, additional records are found and added to the cache, but the operation can become very time-consuming when it is performed on a large record set. When records in a grid are multiselected, the records are marked with the value 1. The following examples illustrate how to retrieve a marked or unmarked record: // Get first recordformDataSource.getFirst();// Get first record marked with 2formDataSource.getFirst(2); // Get first cached record marked with 1formDataSource.getFirst(1, false);

#### Examples

The following example determines whether two records are selected in a form.

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

### Method getNext

Returns the next record that meets the criteria that are set up in an earlier call to the FormDataSource.getFirst method.

    public Common getNext()

#### Return Value

The next record in the dataset.

#### Remarks

Depending on the initialization that is performed in the call to the FormDataSource.getFirst method, the getNext method might return only records that have a particular mark value, and it might return records from the cache.

#### Examples

The following example determines whether two records are selected in a form.

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

### Method id

Retrieves the ID of the data source.

    public int id()

#### Return Value

The ID of the data source.

#### Examples

The following example converts form data sources to their data source IDs.

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

### Method index

    public IndexId index([IndexId value])

#### Parameters

value  

#### Return Value

### Method insertAtEnd

    public boolean insertAtEnd([boolean value])

#### Parameters

value  

#### Return Value

### Method insertIfEmpty

    public boolean insertIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method isBaseDataSource

    public boolean isBaseDataSource()

#### Return Value

### Method isInheritanceDataSource

    public boolean isInheritanceDataSource()

#### Return Value

### Method isOptionalRecordCreated

    private boolean isOptionalRecordCreated([boolean set], Common record, [boolean value])

#### Parameters

set  

<!-- -->

record  

<!-- -->

value  

#### Return Value

### Method isReferenceDataSource

    public boolean isReferenceDataSource()

#### Return Value

### Method joinRelation

    public str joinRelation([str value])

#### Parameters

value  

#### Return Value

### Method joinRelationAsDictRelation

    public DictRelation joinRelationAsDictRelation()

#### Return Value

### Method joinSource

    public int joinSource([AnyType value])

#### Parameters

value  

#### Return Value

### Method joinSourceDataSource

    public FormDataSource joinSourceDataSource()

#### Return Value

### Method last

Moves the mouse pointer to the last record in the data source.

    public int last()

#### Return Value

A non-zero value if the mouse pointer is successfully moved to the last record.

#### Remarks

The last method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking last.

#### Examples

The following example overrides the last method for the InventDim data source on the WMSOrderTransport form and returns the last record in the other data source that is used on the form.

    int last() 
    { 
        return WMSOrder_ds.last(); 
    }

### Method leave

Provides notification when the mouse pointer is moved to the next record or to another data source.

    public boolean leave()

#### Return Value

Always returns true, unless the method is overridden.

#### Remarks

This method is often overridden to implement record-level input validation. The leave method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking leave.

#### Examples

The following example overrides the leave method to perform data validation before the current record is left. The method returns false if the data is invalid.

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

### Method leaveRecord

Provides notification when the focus moves to another record or item in the form.

    public boolean leaveRecord([boolean forceUpdate])

#### Parameters

forceUpdate  

#### Return Value

true if the operation succeeds; otherwise, false.

#### Remarks

The method might fail and return false if changes could not be validated or written. It is recommended that you not override this method. Instead, override the FormDataSource.leave method. If you do override the leaveRecord method, you must call the super method to make sure that the kernel implementation of the method is executed.

### Method resolvePartLinks

    public container resolvePartLinks([str relationName], [int partTableId])

#### Parameters

relationName  

<!-- -->

partTableId  

#### Return Value

### Method linkType

    public int linkType([int value])

#### Parameters

value  

#### Return Value

### Method mark

    public int mark([int value])

#### Parameters

value  

#### Return Value

### Method markAllLoadedRecords

    public boolean markAllLoadedRecords([int value])

#### Parameters

value  

#### Return Value

### Method markRecord

Marks the specified record by using the specified mark value.

    public int markRecord(AnyType record, [int mark])

#### Parameters

record  
The value that is associated with a marked record; optional. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form.

<!-- -->

mark  
The value that is associated with a marked record; optional. A value other than 0 (zero) causes the record to be displayed as marked in grids in the form.

#### Return Value

A non-zero integer if the record has been marked.

#### Remarks

Use this method instead of the FormDataSource.mark method if the record has been found by using a select statement or a method call outside the form.

### Method markRecords

    public boolean markRecords(Array markedRecordIds)

#### Parameters

markedRecordIds  

#### Return Value

### Method masterInheritanceDataSource

    public FormDataSource masterInheritanceDataSource()

#### Return Value

### Method maxAccessRight

    public int maxAccessRight([int value])

#### Parameters

value  

#### Return Value

### Method maxRecordsToLoad

    public int maxRecordsToLoad([int value])

#### Parameters

value  

#### Return Value

### Method maxPagingRowCountValue

    public Int64 maxPagingRowCountValue([Int64 newValue])

#### Parameters

newValue  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name for the data source; optional.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must start with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

#### Examples

The following example creates a QueryBuildDataSource object for a form data source. The FormDataSource.name method is used to specify the name of the QueryBuildDataSource object.

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

### Method next

Moves the focus to the next record in the data source.

    public int next()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

The next method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click next.

#### Examples

The following example overrides the next method on a data source to return the next record from a different data source.

    int next() 
    { 
        return inventTrans_ds.next(); 
    }

### Method nextPage

Moves a specified number of records forward in the data source.

    public int nextPage(int pageSize)

#### Parameters

pageSize  
The number of records to skip.

#### Return Value

A non-zero integer if the operation succeeds.

### Method numberOfRowsLoaded

    public int numberOfRowsLoaded([boolean redirectToMasterDS])

#### Parameters

redirectToMasterDS  

#### Return Value

### Method object

Returns an instance of the FormDataObject class that has the specified ID.

    public FormDataObject object(FieldId fieldId, [int arrayIndex])

#### Parameters

fieldId  

<!-- -->

arrayIndex  

#### Return Value

An instance of the FormDataObject class that has the ID that is specified in the objectId parameter.

#### Examples

The following example creates a FormDataObject object for the RepositoryFolder field in the SysVersionControlParameters table, and then sets the AllowEdit property for the field to true.

    public void initFormDatasource(FormDataSource _formDataSource) 
    { 
        FormDataObject dataObject = _formDataSource.object( 
            fieldnum(SysVersionControlParameters, RepositoryFolder)); 
        if (dataObject) 
        { 
            dataObject.allowEdit(true); 
        } 
    }

### Method onlyFetchActive

    public boolean onlyFetchActive([boolean value])

#### Parameters

value  

#### Return Value

### Method optionalRecordMode

    public int optionalRecordMode([int value])

#### Parameters

value  

#### Return Value

### Method pageSize

    public int pageSize()

#### Return Value

### Method pagingEnabled

    public boolean pagingEnabled()

#### Return Value

### Method parentTitleFields

    public TitleFields parentTitleFields(Common record)

#### Parameters

record  

#### Return Value

### Method prev

Moves the focus to the previous record in the data source.

    public int prev()

#### Return Value

A non-zero integer if the operation succeeds.

#### Remarks

This method can be used to iterate through the records of a data source in reverse order. The prev method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click prev.

#### Examples

The following example overrides the prev method on a data source to return the previous record from a different data source.

    int prev() 
    { 
        return inventTrans_ds.prev(); 
    }

### Method prevPage

Moves the focus back by a specified number of records in the data source.

    public int prevPage(int pageSize)

#### Parameters

pageSize  
The number of records to move back by.

#### Return Value

A non-zero integer if the operation succeeds.

### Method query

    public Query query([Query value])

#### Parameters

value  

#### Return Value

### Method queryBuildDataSource

    public QueryBuildDataSource queryBuildDataSource()

#### Return Value

### Method queryRun

    public QueryRun queryRun([QueryRun value])

#### Parameters

value  

#### Return Value

### Method queryRunQueryBuildDataSource

    public QueryBuildDataSource queryRunQueryBuildDataSource()

#### Return Value

### Method recordsMarked

    public Array recordsMarked()

#### Return Value

### Method startPosition

    public int startPosition([int value])

#### Parameters

value  

#### Return Value

### Method startRowIndex

    public int startRowIndex()

#### Return Value

### Method table

Gets or sets the table ID associated with the object.

    public TableId table([TableId value])

#### Parameters

value  

#### Return Value

The current value of the table ID associated with the object.

### Method titleFields

    public TitleFields titleFields(Common record)

#### Parameters

record  

#### Return Value

### Method totalNumberOfRows

    public int totalNumberOfRows()

#### Return Value

### Method validateDelete

Requests that the user confirm the deletion of a record from the data source.

    public boolean validateDelete()

#### Return Value

true if the deletion is performed successfully; otherwise, false.

#### Remarks

This method calls the validateDelete method on the data source table. The FormDataSource.validateDelete method is called by the FormDataSource.delete method. Use this method to add custom data validation checks whenever they are required. The validateDelete method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking validateDelete.

#### Examples

The following example does not call the super() method and returns true. This supresses the display of the delete confirmation message box.

    public boolean validateDelete() 
    { 
        // Do not display warning dialog. 
        return true; 
    }

### Method validateWrite

Determines whether data is valid and ready to be written.

    public boolean validateWrite()

#### Return Value

Returns true if data is valid; otherwise, false.

#### Remarks

This method is called from the FormDataSource.write method. If false is returned, the write operation is aborted and an error message is displayed. Override this method to add custom validation routines to your data source. The validateWrite method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking validateWrite. The call to the super() method in this method calls the validateWrite method on the table that is used as a data source. Therefore, the return value of the super() method should be examined. If you override the method, it should return true only if the super() method also returns true.

### Method validTimeStateAutoQuery

    public int validTimeStateAutoQuery([int value])

#### Parameters

value  

#### Return Value

### Method validTimeStateUpdate

    public int validTimeStateUpdate([int value])

#### Parameters

value  

#### Return Value

### Method delete

Deletes the current record from the data source.

    public void delete()

#### Remarks

This method is called when a user deletes a record in a form. The delete method calls the FormDataSource.validateDelete method. If the validateDelete method returns true, the record is deleted. After the deletion, the cursor is positioned on the next record (if there is one). The delete method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking delete.

#### Examples

The following example overrides the delete method on the Errors data source for the SysCompilerOutput form. The method updates the number of errors that are displayed in the Compiler output form after an error has been removed.

    public void delete() 
    { 
        super(); 
        sysCompilerOutput.updateCounters(); 
    }

### Method addFieldToSelectionList

    public void addFieldToSelectionList(FieldId fieldId)

#### Parameters

fieldId  

### Method cacheRemoveRecord

Removes the specified record from the underlying cache of the data source.

    public void cacheRemoveRecord([Common record])

#### Parameters

record  
The record to remove from the cache; optional.

#### Remarks

You must enclose data modification statements in a ttsbegin/ttscommit block.

#### Examples

The following example deletes the inventTable record from the cache of the data source.

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

### Method OnValidatedWrite

    private void OnValidatedWrite([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method reread

Rereads the current record from the database.

    public void reread()

#### Remarks

Call this method to update the record with the latest changes from the database. The reread method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click reread.

#### Examples

The following example uses the reread method as part of a method that is used to update a table.

    void doRefresh() 
    { 
        salesTable_ds.reread(); 
        salesTable_ds.refresh(); 
        salesLine_ds.reread(); 
        salesLine_ds.refresh(); 
        interCompanyPurchSalesReference_ds.executeQuery(); 
    }

### Method rereadJoinHierarchy

    public void rereadJoinHierarchy()

### Method OnRefreshed

    private void OnRefreshed([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnValidatedDelete

    private void OnValidatedDelete([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method markChanged

    public void markChanged()

### Method setPagingParameters

    public void setPagingParameters(boolean pagingEnabled, int startRowIndex, int pageSize)

#### Parameters

pagingEnabled  

<!-- -->

startRowIndex  

<!-- -->

pageSize  

### Method deleted

    public void deleted()

### Method print

Prints the current record.

    public void print(PrintMedium target)

#### Parameters

target  
The print medium to use to print the record.

#### Remarks

The current record is printed by using the system's auto report facilities (the SysTableReport report, which is located in the Reports node). The print method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click print.

### Method OnReread

    private void OnReread([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method research

Is overridden by the FormDataSource.research method.

    public void research([boolean retainPosition])

#### Parameters

retainPosition  
A Boolean value that indicates whether to maintain the position in the grid after the method is completed.

#### Remarks

This method has no functionality in the FormObjectSet class. It is overridden by the FormDataSource.research method, which updates the database search that is defined by the filters and sorts that are currently applied to the form.

### Method createTypes

    public void createTypes(Map concreteTypesToCreate, [boolean append], [boolean implicitCreate], [boolean explicitCreate])

#### Parameters

concreteTypesToCreate  

<!-- -->

append  

<!-- -->

implicitCreate  

<!-- -->

explicitCreate  

### Method OnCreated

    private void OnCreated([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnQueryExecuted

    private void OnQueryExecuted([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method written

    public void written()

### Method filter

Filters records in the data source.

    public void filter(FieldId field, str value)

#### Parameters

field  
The filtering condition.

<!-- -->

value  
The filtering condition.

#### Remarks

The filter method can be overridden on a form data source to extend the standard filtering functionality. Right-click the Methods node under the data source, point to Override Method, and then click filter.

### Method refresh

Updates the form by updating the view of all the records in the data source.

    public void refresh()

#### Remarks

The contents of the records are redrawn without loading from disk. You can, for example, use refresh if you have to update while a lengthy operation is running. Use the FormDataSource.refreshEx method if you do not want to refresh all the records. The refresh method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click refresh.

#### Examples

The following example overrides the write method on a data source so that it updates records in a different data source after a write operation.

    public void write() 
    { 
        super(); 
        EPParameters_ds.research(); 
        EPParameters_ds.refresh(); 
    }

### Method write

Calls the FormDataSource.validateWrite method and manages the database write operation.

    public void write()

#### Remarks

This method is invoked when a user inserts a new record or updates an existing one. The refreshEx method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click refreshEx.

### Method executeQuery

Executes the data source query and displays the records that are retrieved.

    public void executeQuery()

#### Remarks

This method is executed when a form is opened for data display. The executeQuery method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking executeQuery.

#### Examples

The following example executes a data source query in response to a tab page activation event.

    public void pageActivated() 
    { 
        monday_ds.executeQuery(); 
        super(); 
    }

### Method setRecord

    public void setRecord(Common record)

#### Parameters

record  

### Method refreshEx

Updates the view of the specified records.

    public void refreshEx([AnyType pos])

#### Parameters

pos  
The number of the record to refresh; optional. If a value of -1 is specified, all records are updated. If a value of -2 is specified, all marked records and all records that have display options specified are updated. The default value is -2.

#### Remarks

The refreshEx method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking refreshEx.

### Method setCurrent

    public void setCurrent()

### Method OnValidatingDelete

    private void OnValidatingDelete([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method writing

    public void writing()

### Method OnWritten

    private void OnWritten([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method clearDisplayOption

Clears display options that were previously specified for a record and then redraws the record.

    public void clearDisplayOption(Common record)

#### Parameters

record  
The record to redraw.

#### Remarks

Display options are set by using the FormDataSource.displayOption method.

#### Examples

The following example redraws the first record in a data source.

    public void run() 
    { 
        super(); 
        sysRecordTmpTemplate_ds.clearDisplayOption( 
            sysRecordTmpTemplate_ds.getFirst()); 
    }

### Method OnMarkChanged

    private void OnMarkChanged([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnLeftRecord

    private void OnLeftRecord([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnDeleted

    private void OnDeleted([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method removeFilter

Resets the query for the data source.

    public void removeFilter()

#### Remarks

This method is called when a user clicks the Cancel Filter command in the shortcut menu on a form control. The removeFilter method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click removeFilter. For example, removeFilter removes all modifications to the original query that is generated by the FormDataSource.init method.

### Method OnInitialized

    private void OnInitialized([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnPostLinkActive

    private void OnPostLinkActive([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnSelectionChanged

    private void OnSelectionChanged([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method deleting

    public void deleting()

### Method observe

    public void observe()

### Method OnWriting

    private void OnWriting([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnActivated

    private void OnActivated([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method removeFieldFromSelectionList

    public void removeFieldFromSelectionList(FieldId fieldId)

#### Parameters

fieldId  

### Method OnCreating

    private void OnCreating([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method rereadReferenceDataSources

    public void rereadReferenceDataSources()

### Method OnValidatingWrite

    private void OnValidatingWrite([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method prompt

Activates the standard form, SysQueryForm, that is used to limit a query range.

    public void prompt()

#### Remarks

This method is called when a user clicks the Filter records command on the Command menu or presses CTRL+F3. The prompt method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click prompt.

### Method OnQueryExecuting

    private void OnQueryExecuting([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method OnInitValue

    private void OnInitValue([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method clearReferenceData

    public void clearReferenceData(FieldId fieldId)

#### Parameters

fieldId  

### Method cursorNotify

Notifies the application about a cursor event.

    public void cursorNotify(int event)

#### Parameters

event  
The cursor event identifier. The following table shows the available cursor events.

#### Remarks

This method can be overridden to implement custom handling of cursor events. However, the super() method has to be called first to enable the kernel to handle the event as appropriate.

### Method displayOption

Sets the text color and the background color for a record in the data source.

    public void displayOption(Common record, FormRowDisplayOption options)

#### Parameters

record  
The FormRowDisplayOption object that encapsulates the desired record display properties.

<!-- -->

options  
The FormRowDisplayOption object that encapsulates the desired record display properties.

#### Remarks

This method is executed one time for each record before the record is displayed in a form. The displayOption method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click displayOption.

#### Examples

The following example overrides the displayOption method to set display options from a stored profile and to override the background color that is based on the settings for the particular record.

    public void displayOption(Common _record, FormRowDisplayOption 
        _options) 
    { 
        JmgProfileTable profile; 
        profile = _record; 
        _options.backColor(profile.Color); 
        super(_record, _options); 
    }

### Method create

Creates a new record in the data source.

    public void create([boolean append])

#### Parameters

append  
A Boolean value that indicates whether to insert the record after or before the current cursor position. If it is set to true, the new record is inserted after the current record.

#### Remarks

This method is called when a user creates a new record in a data source, such as by using the default shortcut key for insertion (CTRL+N). The create method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; create.

### Method init

Creates a data source query that is based on the data source properties.

    public void init()

#### Remarks

This method is called when the form is opened. The query that is generated by the method is used to the load data so that it can be displayed in the form. The init method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click init.

#### Examples

The following example overrides the init method on a data source to specify the sorting order for the data source.

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

### Method linkActive

Calls the FormDataSource.exeuteQuery method on data sources that are linked to the current data source.

    public void linkActive()

#### Remarks

This method is executed when a user moves to another record in the master data source. This causes an update to all linked data sources. The super() call in the FormDataSource.active method calls the FormDataSource.linkActive method on all linked child data sources if the LinkType property on the parent data source is set to Passive, Delayed, or Active. The linkActive method can be overridden on a form data source. Right-click the Methods node under the data source, point to Override Method, and then click linkActive.

### Method selectionChanged

    public void selectionChanged()

### Method OnDeleting

    private void OnDeleting([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method addReferenceFieldToSelectionList

    public void addReferenceFieldToSelectionList(FieldId fieldId, str referenceFieldGroupName)

#### Parameters

fieldId  

<!-- -->

referenceFieldGroupName  

### Method initValue

Initializes field values in a new record.

    public void initValue()

#### Remarks

This method is called when a new record is created. It populates the record with initial values for the fields. The initValue method can be overridden on a form data source by right-clicking the Methods node under the data source, pointing to Override Method, and then clicking initValue.

#### Examples

The following example overrides FormDataSource.initValue so that the TaxLimitBase field is initialized with a particular value.

    public void initValue() 
    { 
        super(); 
        taxTable.TaxLimitBase = TaxLimitBase::InvoiceWithoutVAT; 
    }

### Method deleteMarked

Deletes all marked (selected) records from a data source.

    public void deleteMarked()

#### Remarks

If no records have been selected, the FormDataSource.delete method is executed. The operation can be interrupted by pressing CTRL+BREAK. The deleteMarked method can be overridden on a form data source. Right-click the Methods node under the data source, and then select Override Method &gt; deleteMarked.

#### Examples

The following example overrides the deleteMarked method to let users confirm whether they want to delete the marked records.

    public void deleteMarked() 
    { 
        if (Box::yesNo("@SYS79428", DialogButton::Yes, "@SYS79319")) 
            super(); 
    }

### Method OnLeavingRecord

    private void OnLeavingRecord([FormDataSource sender], [FormDataSourceEventArgs e])

#### Parameters

sender  

<!-- -->

e  

## Class FormDateControl
    class FormDateControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                                                     |
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
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int dateDay(\[int value\])                                                                           |                                                                                                                                                                         |
| public int dateFormat(\[int value\])                                                                        |                                                                                                                                                                         |
| public int dateMonth(\[int value\])                                                                         |                                                                                                                                                                         |
| public int dateSeparator(\[int value\])                                                                     |                                                                                                                                                                         |
| public Date dateValue(\[Date value\])                                                                       |                                                                                                                                                                         |
| public int dateYear(\[int value\])                                                                          |                                                                                                                                                                         |
| public int direction(\[int value\])                                                                         |                                                                                                                                                                         |
| public int displayHeight(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayHeightMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayHeightValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayLength(\[int value\], \[AutoMode mode\])                                                  |                                                                                                                                                                         |
| public AutoMode displayLengthMode(\[AutoMode mode\])                                                        |                                                                                                                                                                         |
| public int displayLengthValue(\[int value\])                                                                |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that id displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
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
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
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
| public str maxDateLabel(\[str value\])                                                                      |                                                                                                                                                                         |
| public str maxDateLabelText()                                                                               |                                                                                                                                                                         |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public container posFromChar(int charIndex)                                                                 |                                                                                                                                                                         |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean replaceOnLookup(\[boolean value\])                                                           |                                                                                                                                                                         |
| public int searchAfterInput(\[int value\])                                                                  |                                                                                                                                                                         |
| public int searchMode(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int style(\[int value\])                                                                             |                                                                                                                                                                         |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                              |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 | Sets or returns the underline property for the text in the control.                                                                                                     |
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
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void scrollCursor()                                                                                  |                                                                                                                                                                         |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| public void lineScroll(int dx, int dy)                                                                      |                                                                                                                                                                         |
| public void setSelection(int charIndexFrom, int charIndexTo)                                                |                                                                                                                                                                         |
| public void textChange()                                                                                    |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void pasteText(str pasteStr, \[boolean InsertSel\])                                                  |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void setCursorPos(int x, int y)                                                                      |                                                                                                                                                                         |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |

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

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

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
An integer value that indicates the y-coordinate of the mouse pointer The coordinate is relative to the upper-left corner of the control.

<!-- -->

y  
An integer value that indicates the y-coordinate of the mouse pointer The coordinate is relative to the upper-left corner of the control.

#### Return Value

0 (zero) if the event has been handled.

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method bold

Gets or sets the weight of font used to output text in the control.

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

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

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

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

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

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

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

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateValue

    public Date dateValue([Date value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method direction

    public int direction([int value])

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

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal, or in both.

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

Retrieves the text that id displayed when the form control is dragged.

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

The enabled property allows controls to be enabled or disabled at run time. For example, you can disable objects that do not apply to the current state of the application. You can also disable a control that is used only for display purposes, such as an error message, which provides read-only information.

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

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

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

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

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

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

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
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control; optional.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that specified by the neededSetupRights parameter; otherwise, false.

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

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

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

### Method maxDateLabel

    public str maxDateLabel([str value])

#### Parameters

value  

#### Return Value

### Method maxDateLabelText

    public str maxDateLabelText()

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

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

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

### Method replaceOnLookup

    public boolean replaceOnLookup([boolean value])

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

### Method underline

Sets or returns the underline property for the text in the control.

    public boolean underline([boolean value])

#### Parameters

value  
The value to assign to the underline property of the control; optional.

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

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

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

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

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

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

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

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method scrollCursor

    public void scrollCursor()

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

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnValidating

    private void OnValidating([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method lineScroll

    public void lineScroll(int dx, int dy)

#### Parameters

dx  

<!-- -->

dy  

### Method setSelection

    public void setSelection(int charIndexFrom, int charIndexTo)

#### Parameters

charIndexFrom  

<!-- -->

charIndexTo  

### Method textChange

    public void textChange()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

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

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method jumpRef

    public void jumpRef()

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

### Method setCursorPos

    public void setCursorPos(int x, int y)

#### Parameters

x  

<!-- -->

y  

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

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method lookup

    public void lookup()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method undo

    public void undo()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method displayControl

Displays the control.

    public void displayControl()

## Class FormDateTimeControl
    class FormDateTimeControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                             |
|-------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                |
| public int alignment(\[int value\])                                                                         |                                                                                                                                                                         |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int arrayIndex(\[int value\])                                                                        |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                |
| public int cacheDataMethod(\[int value\])                                                                   |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                      |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                           |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 |                                                                                                                                                                         |
| public FieldId dataField(\[FieldId value\])                                                                 |                                                                                                                                                                         |
| public str dataMethod(\[str value\])                                                                        |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int dateDay(\[int value\])                                                                           |                                                                                                                                                                         |
| public int dateFormat(\[int value\])                                                                        |                                                                                                                                                                         |
| public int dateMonth(\[int value\])                                                                         |                                                                                                                                                                         |
| public int dateSeparator(\[int value\])                                                                     |                                                                                                                                                                         |
| public DateTime dateTimeValue(\[DateTime value\])                                                           |                                                                                                                                                                         |
| public int dateYear(\[int value\])                                                                          |                                                                                                                                                                         |
| public int displayOption(\[int value\])                                                                     |                                                                                                                                                                         |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                     |
| public ExtendedTypeId extendedDataType(\[ExtendedTypeId value\])                                            |                                                                                                                                                                         |
| public int fastTabSummary(\[int value\])                                                                    |                                                                                                                                                                         |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                               |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                     |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                          | Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                           |
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
| public int lookupButton(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean mandatory(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public str maxDateLabel(\[str value\])                                                                      |                                                                                                                                                                         |
| public str maxDateLabelText()                                                                               |                                                                                                                                                                         |
| public boolean modified()                                                                                   |                                                                                                                                                                         |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                  |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                         |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                           |
| public str previewPartRef(\[str value\])                                                                    |                                                                                                                                                                         |
| public int promptrect(\[int value\])                                                                        |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean showLabel(\[boolean value\])                                                                 |                                                                                                                                                                         |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                         |
| public int timeFormat(\[int value\])                                                                        |                                                                                                                                                                         |
| public int timeHours(\[int value\])                                                                         |                                                                                                                                                                         |
| public int timeMinute(\[int value\])                                                                        |                                                                                                                                                                         |
| public int timeSeconds(\[int value\])                                                                       |                                                                                                                                                                         |
| public int timeSeparator(\[int value\])                                                                     |                                                                                                                                                                         |
| public Timezone timeZone(\[Timezone timeZone\])                                                             |                                                                                                                                                                         |
| public int timeZoneIndicator(\[int value\])                                                                 |                                                                                                                                                                         |
| public int timezonePreference(\[int value\])                                                                |                                                                                                                                                                         |
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
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean validate()                                                                                   |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public int viewEditMode(\[int value\])                                                                      |                                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                  |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                          |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void performTypeLookup(\[int userType\], \[int arrayIndex\], \[SelectableDataArea company\])         |                                                                                                                                                                         |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| private void OnValidating(\[FormControl sender\], \[FormControlEventArgs e\])                               |                                                                                                                                                                         |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                       |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                           |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                    |                                                                                                                                                                         |
| public void timeTextChange()                                                                                |                                                                                                                                                                         |
| public void performDBLookup(\[FieldId fieldId\], \[TableId tableId\], \[SelectableDataArea company\])       |                                                                                                                                                                         |
| public void dateTextChange()                                                                                |                                                                                                                                                                         |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                   |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                         |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                              |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                 |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void enter()                                                                                         |                                                                                                                                                                         |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                          |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                         |
| private void OnValidated(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                         |
| public void performFormLookup(xFormRun form)                                                                |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                         |
| public void lookup()                                                                                        |                                                                                                                                                                         |
| private void OnLookup(\[FormControl sender\], \[FormControlEventArgs e\])                                   |                                                                                                                                                                         |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                               |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                |
| public void undo()                                                                                          |                                                                                                                                                                         |
| public void setUTCString(str UTC\_Formatted String)                                                         |                                                                                                                                                                         |
| private void OnModified(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |
| public void jumpRef()                                                                                       |                                                                                                                                                                         |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                         |

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
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

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
The property is set to this value; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

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

Gets or sets the weight of font used to output text in the control.

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

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

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

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key being assigned to the control; optional.

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

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method dateDay

    public int dateDay([int value])

#### Parameters

value  

#### Return Value

### Method dateFormat

    public int dateFormat([int value])

#### Parameters

value  

#### Return Value

### Method dateMonth

    public int dateMonth([int value])

#### Parameters

value  

#### Return Value

### Method dateSeparator

    public int dateSeparator([int value])

#### Parameters

value  

#### Return Value

### Method dateTimeValue

    public DateTime dateTimeValue([DateTime value])

#### Parameters

value  

#### Return Value

### Method dateYear

    public int dateYear([int value])

#### Parameters

value  

#### Return Value

### Method displayOption

    public int displayOption([int value])

#### Parameters

value  

#### Return Value

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer data type that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the FormControl::dragLeave method, the FormControl::dragOver method, and the FormControl::dragOverEx method to specify the behavior.

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
An Integer data type that indicates how the height is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An Integer data type value that indicates how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An Integer data type that specifies the height in pixels; optional.

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

Gets or sets the help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet.The help text must not exceed 250 characters.

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
A value from the FormAllowUserSetup enumeration that specifies the level of customization that is being queried for the control; optional.

#### Return Value

true if the control, design, and parent containers allow for the level of customization that specified by the neededSetupRights parameter; otherwise, false.

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

The label determines which text is displayed in the control or adjacent to it.The label property value cannot exceed 250 characters.

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

### Method maxDateLabel

    public str maxDateLabel([str value])

#### Parameters

value  

#### Return Value

### Method maxDateLabelText

    public str maxDateLabelText()

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

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control; optional.

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

### Method promptrect

    public int promptrect([int value])

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

### Method timeFormat

    public int timeFormat([int value])

#### Parameters

value  

#### Return Value

### Method timeHours

    public int timeHours([int value])

#### Parameters

value  

#### Return Value

### Method timeMinute

    public int timeMinute([int value])

#### Parameters

value  

#### Return Value

### Method timeSeconds

    public int timeSeconds([int value])

#### Parameters

value  

#### Return Value

### Method timeSeparator

    public int timeSeparator([int value])

#### Parameters

value  

#### Return Value

### Method timeZone

    public Timezone timeZone([Timezone timeZone])

#### Parameters

timeZone  

#### Return Value

### Method timeZoneIndicator

    public int timeZoneIndicator([int value])

#### Parameters

value  

#### Return Value

### Method timezonePreference

    public int timezonePreference([int value])

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

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width for the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method validate

    public boolean validate()

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

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
An Integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An Integer data type that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An Integer data type value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An Integer data type that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method performTypeLookup

    public void performTypeLookup([int userType], [int arrayIndex], [SelectableDataArea company])

#### Parameters

userType  

<!-- -->

arrayIndex  

<!-- -->

company  

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

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

### Method cut

Cuts the contents of the control.

    public void cut()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

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

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method timeTextChange

    public void timeTextChange()

### Method performDBLookup

    public void performDBLookup([FieldId fieldId], [TableId tableId], [SelectableDataArea company])

#### Parameters

fieldId  

<!-- -->

tableId  

<!-- -->

company  

### Method dateTextChange

    public void dateTextChange()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method displayControl

Displays the control.

    public void displayControl()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method enter

    public void enter()

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method OnValidated

    private void OnValidated([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method performFormLookup

    public void performFormLookup(xFormRun form)

#### Parameters

form  

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lookup

    public void lookup()

### Method OnLookup

    private void OnLookup([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method undo

    public void undo()

### Method setUTCString

    public void setUTCString(str UTC_Formatted String)

#### Parameters

UTC\_Formatted String  

### Method OnModified

    private void OnModified([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method jumpRef

    public void jumpRef()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

## Class FormDesign
    class FormDesign extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                         |
|---------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                     |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                     |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                     |
| public boolean alignChild(\[boolean value\])                                                                        |                                                                     |
| public boolean alignChildren(\[boolean value\])                                                                     |                                                                     |
| public boolean allowDocking(\[boolean value\])                                                                      |                                                                     |
| public boolean allowFormCompanyChange(\[boolean value\])                                                            |                                                                     |
| public boolean allowImplicitParent(\[boolean value\])                                                               |                                                                     |
| public int allowUserSetup(\[int value\])                                                                            |                                                                     |
| public boolean alwaysOnTop(\[boolean value\])                                                                       |                                                                     |
| public int arrangeGuide(\[int value\])                                                                              |                                                                     |
| public int arrangeMethod(\[int value\])                                                                             |                                                                     |
| public int arrangeWhen(\[int value\])                                                                               |                                                                     |
| public int backgroundColor(\[int value\])                                                                           | Gets or sets the background color of the control.                   |
| public int bold(\[int value\])                                                                                      | Gets or sets the weight of font used to output text in the control. |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |                                                                     |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |                                                                     |
| public int bottomMarginValue(\[int value\])                                                                         |                                                                     |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |                                                                     |
| public boolean canContain(FormControl control)                                                                      |                                                                     |
| public str caption(\[str value\])                                                                                   | Gets or set the caption of the control.                             |
| public int characterSet(\[int value\])                                                                              | Gets or sets the character set of the font.                         |
| public int colorScheme(\[int value\])                                                                               | Gets or sets the color scheme of the control.                       |
| public int columns(\[int value\], \[ColumnsMode mode\])                                                             |                                                                     |
| public ColumnsMode columnsMode(\[ColumnsMode mode\])                                                                |                                                                     |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |                                                                     |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |                                                                     |
| public int columnspaceValue(\[int value\])                                                                          |                                                                     |
| public int columnsValue(\[int value\])                                                                              |                                                                     |
| public boolean contains(FormControl control)                                                                        |                                                                     |
| public FormControl control(int controlId)                                                                           |                                                                     |
| public int controlCount()                                                                                           |                                                                     |
| public FormControl controlName(str controlName)                                                                     |                                                                     |
| public FormControl controlNum(int controlNo)                                                                        |                                                                     |
| public str cssClass(\[str value\])                                                                                  |                                                                     |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source to be used by the control or the form.   |
| public str defaultAction(\[str value\])                                                                             |                                                                     |
| public str font(\[str value\])                                                                                      | Gets or sets the name of the font for the control to use.           |
| public int fontSize(\[int value\])                                                                                  | Gets or sets the size of the font for the control to use.           |
| public int frame(\[int value\])                                                                                     |                                                                     |
| public boolean hasUserSetting()                                                                                     |                                                                     |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                             |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.      |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                             |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |                                                                     |
| public boolean hideToolbar(\[boolean value\])                                                                       |                                                                     |
| public int imagemode(\[int value\])                                                                                 |                                                                     |
| public str imageName(\[str value\])                                                                                 |                                                                     |
| public int imageResource(\[int value\])                                                                             |                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            |                                                                     |
| public boolean italic(\[boolean value\])                                                                            |                                                                     |
| public int labelBold(\[int value\])                                                                                 |                                                                     |
| public int labelCharacterSet(\[int value\])                                                                         |                                                                     |
| public str labelFont(\[str value\])                                                                                 |                                                                     |
| public int labelFontSize(\[int value\])                                                                             |                                                                     |
| public boolean labelItalic(\[boolean value\])                                                                       |                                                                     |
| public boolean labelUnderline(\[boolean value\])                                                                    |                                                                     |
| public int left(int value, \[int mode\])                                                                            |                                                                     |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |                                                                     |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |                                                                     |
| public int leftMarginValue(\[int value\])                                                                           |                                                                     |
| public int leftMode(\[int value\])                                                                                  |                                                                     |
| public int leftValue(\[int value\])                                                                                 |                                                                     |
| public str localWebMenu(\[str value\])                                                                              |                                                                     |
| public boolean maximizeBox(\[boolean value\])                                                                       |                                                                     |
| public boolean minimizeBox(\[boolean value\])                                                                       |                                                                     |
| public int mode(\[int value\])                                                                                      |                                                                     |
| public int moveControl(int controlId, \[int insertAfterControlId\])                                                 |                                                                     |
| public str newRecordAction(\[str value\])                                                                           |                                                                     |
| public container SysObsoleteAttribute()                                                                             |                                                                     |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |                                                                     |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |                                                                     |
| public int rightMarginValue(\[int value\])                                                                          |                                                                     |
| public boolean saveSize(\[boolean value\])                                                                          |                                                                     |
| public int scrollbars(\[int value\])                                                                                |                                                                     |
| public boolean setCompany(\[boolean value\])                                                                        |                                                                     |
| public int showDeleteButton(\[int value\])                                                                          |                                                                     |
| public int showNewButton(\[int value\])                                                                             |                                                                     |
| public int showWebHelp(\[int value\])                                                                               |                                                                     |
| public int statusBarStyle(\[int value\])                                                                            |                                                                     |
| public int style(\[int value\])                                                                                     |                                                                     |
| public int submitMethod(\[int value\])                                                                              |                                                                     |
| public boolean supportReload(\[boolean value\])                                                                     |                                                                     |
| public int titleDatasource(\[AnyType value\])                                                                       |                                                                     |
| public int top(int value, \[int mode\])                                                                             |                                                                     |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |                                                                     |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |                                                                     |
| public int topMarginValue(\[int value\])                                                                            |                                                                     |
| public int topMode(\[int value\])                                                                                   |                                                                     |
| public int topValue(\[int value\])                                                                                  |                                                                     |
| public boolean underline(\[boolean value\])                                                                         |                                                                     |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                     |
| public int useCaptionFromMenuItem(\[int value\])                                                                    |                                                                     |
| public boolean userSettingAllowSave()                                                                               |                                                                     |
| public boolean useUserLayout(\[boolean value\])                                                                     |                                                                     |
| public int viewEditMode(\[int value\])                                                                              |                                                                     |
| public boolean visible(\[boolean value\])                                                                           |                                                                     |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                              |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.      |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                              |
| public int windowResize(\[int value\])                                                                              |                                                                     |
| public int windowType(\[int value\])                                                                                |                                                                     |
| public int workflowDatasource(\[AnyType value\])                                                                    |                                                                     |
| public boolean workflowEnabled(\[boolean value\])                                                                   |                                                                     |
| public str workflowType(\[str value\])                                                                              |                                                                     |
| public int dialogSize(\[int value\])                                                                                |                                                                     |
| public void resetUserSetting()                                                                                      |                                                                     |
| public void removeControl(\[int controlId\])                                                                        |                                                                     |
| public void finalize()                                                                                              |                                                                     |

### Method addControl

    public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])

#### Parameters

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addControlEx

    public FormControl addControlEx(str controlClass, str controlName, [FormControl insertAfter])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addDataField

    public FormControl addDataField(int dataSourceId, FieldId fieldId, [FormControl insertAfter], [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

insertAfter  

<!-- -->

arrayIndex  

#### Return Value

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

### Method allowDocking

    public boolean allowDocking([boolean value])

#### Parameters

value  

#### Return Value

### Method allowFormCompanyChange

    public boolean allowFormCompanyChange([boolean value])

#### Parameters

value  

#### Return Value

### Method allowImplicitParent

    public boolean allowImplicitParent([boolean value])

#### Parameters

value  

#### Return Value

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method alwaysOnTop

    public boolean alwaysOnTop([boolean value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

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

### Method bold

Gets or sets the weight of font used to output text in the control.

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

### Method canAddDataField

    public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Return Value

### Method canContain

    public boolean canContain(FormControl control)

#### Parameters

control  

#### Return Value

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

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of Microsoft Windows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Microsoft Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Microsoft Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET.For more information, see the LOGFONT structure on the MSDN Web site, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method columns

    public int columns([int value], [ColumnsMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public ColumnsMode columnsMode([ColumnsMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method contains

    public boolean contains(FormControl control)

#### Parameters

control  

#### Return Value

### Method control

    public FormControl control(int controlId)

#### Parameters

controlId  

#### Return Value

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlName

    public FormControl controlName(str controlName)

#### Parameters

controlName  

#### Return Value

### Method controlNum

    public FormControl controlNum(int controlNo)

#### Parameters

controlNo  

#### Return Value

### Method cssClass

    public str cssClass([str value])

#### Parameters

value  

#### Return Value

### Method dataSource

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method defaultAction

    public str defaultAction([str value])

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

### Method frame

    public int frame([int value])

#### Parameters

value  

#### Return Value

### Method hasUserSetting

    public boolean hasUserSetting()

#### Return Value

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

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

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

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

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

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

#### Parameters

value  

#### Return Value

### Method hideToolbar

    public boolean hideToolbar([boolean value])

#### Parameters

value  

#### Return Value

### Method imagemode

    public int imagemode([int value])

#### Parameters

value  

#### Return Value

### Method imageName

    public str imageName([str value])

#### Parameters

value  

#### Return Value

### Method imageResource

    public int imageResource([int value])

#### Parameters

value  

#### Return Value

### Method isUserSetupEnabled

    public boolean isUserSetupEnabled(int neededSetupRights)

#### Parameters

neededSetupRights  

#### Return Value

### Method italic

    public boolean italic([boolean value])

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

### Method labelItalic

    public boolean labelItalic([boolean value])

#### Parameters

value  

#### Return Value

### Method labelUnderline

    public boolean labelUnderline([boolean value])

#### Parameters

value  

#### Return Value

### Method left

    public int left(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

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

    public int leftMode([int value])

#### Parameters

value  

#### Return Value

### Method leftValue

    public int leftValue([int value])

#### Parameters

value  

#### Return Value

### Method localWebMenu

    public str localWebMenu([str value])

#### Parameters

value  

#### Return Value

### Method maximizeBox

    public boolean maximizeBox([boolean value])

#### Parameters

value  

#### Return Value

### Method minimizeBox

    public boolean minimizeBox([boolean value])

#### Parameters

value  

#### Return Value

### Method mode

    public int mode([int value])

#### Parameters

value  

#### Return Value

### Method moveControl

    public int moveControl(int controlId, [int insertAfterControlId])

#### Parameters

controlId  

<!-- -->

insertAfterControlId  

#### Return Value

### Method newRecordAction

    public str newRecordAction([str value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

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

### Method saveSize

    public boolean saveSize([boolean value])

#### Parameters

value  

#### Return Value

### Method scrollbars

    public int scrollbars([int value])

#### Parameters

value  

#### Return Value

### Method setCompany

    public boolean setCompany([boolean value])

#### Parameters

value  

#### Return Value

### Method showDeleteButton

    public int showDeleteButton([int value])

#### Parameters

value  

#### Return Value

### Method showNewButton

    public int showNewButton([int value])

#### Parameters

value  

#### Return Value

### Method showWebHelp

    public int showWebHelp([int value])

#### Parameters

value  

#### Return Value

### Method statusBarStyle

    public int statusBarStyle([int value])

#### Parameters

value  

#### Return Value

### Method style

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method submitMethod

    public int submitMethod([int value])

#### Parameters

value  

#### Return Value

### Method supportReload

    public boolean supportReload([boolean value])

#### Parameters

value  

#### Return Value

### Method titleDatasource

    public int titleDatasource([AnyType value])

#### Parameters

value  

#### Return Value

### Method top

    public int top(int value, [int mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

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

    public int topMode([int value])

#### Parameters

value  

#### Return Value

### Method topValue

    public int topValue([int value])

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

### Method useCaptionFromMenuItem

    public int useCaptionFromMenuItem([int value])

#### Parameters

value  

#### Return Value

### Method userSettingAllowSave

    public boolean userSettingAllowSave()

#### Return Value

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method viewEditMode

    public int viewEditMode([int value])

#### Parameters

value  

#### Return Value

### Method visible

    public boolean visible([boolean value])

#### Parameters

value  

#### Return Value

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

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

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

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

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

### Method windowResize

    public int windowResize([int value])

#### Parameters

value  

#### Return Value

### Method windowType

    public int windowType([int value])

#### Parameters

value  

#### Return Value

### Method workflowDatasource

    public int workflowDatasource([AnyType value])

#### Parameters

value  

#### Return Value

### Method workflowEnabled

    public boolean workflowEnabled([boolean value])

#### Parameters

value  

#### Return Value

### Method workflowType

    public str workflowType([str value])

#### Parameters

value  

#### Return Value

### Method dialogSize

    public int dialogSize([int value])

#### Parameters

value  

#### Return Value

### Method resetUserSetting

    public void resetUserSetting()

### Method removeControl

    public void removeControl([int controlId])

#### Parameters

controlId  

### Method finalize

    public void finalize()

## Class FormDesignView
    class FormDesignView extends ObjectRun

### Remarks

### Examples

### Methods

| Method                                                 | Description                                     |
|--------------------------------------------------------|-------------------------------------------------|
| public FormBuildDesign design(\[int value\])           |                                                 |
| public Form form(\[Form value\])                       |                                                 |
| public str name()                                      |                                                 |
| public FormBuildObjectSet objectPool(\[AnyType pool\]) |                                                 |
| public void finalize()                                 |                                                 |
| public void new(\[str name\], \[Form form\])           | Initializes a new instance of the Object class. |

### Method design

    public FormBuildDesign design([int value])

#### Parameters

value  

#### Return Value

### Method form

    public Form form([Form value])

#### Parameters

value  

#### Return Value

### Method name

    public str name()

#### Return Value

### Method objectPool

    public FormBuildObjectSet objectPool([AnyType pool])

#### Parameters

pool  

#### Return Value

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the Object class.

    public void new([str name], [Form form])

#### Parameters

name  

<!-- -->

form  

## Class FormDropDialogButtonControl
    class FormDropDialogButtonControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                      | Description                                                                                                                                                                                                           |
|-------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public boolean alignControl(\[boolean value\])                                                              | Determines whether to align the control.                                                                                                                                                                              |
| public int alignment(\[int value\])                                                                         | Changes the alignment of the text in the control. Values are Left, right, or center, to align the control appropriately.                                                                                              |
| public boolean allowEdit(\[boolean value\])                                                                 | Determines whether the user can change the contents of the control.                                                                                                                                                   |
| public boolean allowSysSetup()                                                                              | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                                                                   |
| public boolean autoDeclaration(\[boolean value\])                                                           | Determines whether the system can declare a member variable that has the same name as the control.                                                                                                                    |
| public boolean autoRefreshData(\[boolean value\])                                                           | Specifies whether the data from the data source that is associated with the control will be refreshed when the button is clicked. The default value is No.                                                            |
| public int backgroundColor(\[int value\])                                                                   | Gets or sets the background color of the control.                                                                                                                                                                     |
| public int backStyle(\[int value\])                                                                         | Determiness whether the control background can be transparent.                                                                                                                                                        |
| public int beginDrag(int x, int y)                                                                          | Is called when the user starts to drag a form control.                                                                                                                                                                |
| public boolean big(\[boolean value\])                                                                       |                                                                                                                                                                                                                       |
| public int bold(\[int value\])                                                                              | Gets or sets the weight of font used to output text in the control.                                                                                                                                                   |
| public int border(\[int value\])                                                                            | Gets or sets the style of the borderline of the control.                                                                                                                                                              |
| public int buttonDisplay(\[int value\])                                                                     | Gets or sets the appearance of the button control.                                                                                                                                                                    |
| public container calcControlSize(int chars, int lines)                                                      | Retrieves the size of the control.                                                                                                                                                                                    |
| public str caption(\[str value\])                                                                           | Gets or set the caption of the control.                                                                                                                                                                               |
| public int characterSet(\[int value\])                                                                      | Gets or sets the character set of the font.                                                                                                                                                                           |
| public int colorScheme(\[int value\])                                                                       | Gets or sets the color scheme of the control.                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                    | Gets or sets the configuration key that is assigned to the control.                                                                                                                                                   |
| public List configurationKeyEx()                                                                            | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                                                                      |
| public int copyCallerQuery(\[int value\])                                                                   | Specifies whether to copy the query from the calling form to the target form. This enables the target form to display the same data that was being viewed in the original form. The default value is Auto.            |
| public str countryRegionCodes(\[str value\])                                                                | Gets or sets the comma-separated list of country/region codes for the control.                                                                                                                                        |
| public FieldId countryRegionContextField(\[FieldId value\])                                                 | Specifies the field that will be used to identify the country context. See CountryRegionCodes.                                                                                                                        |
| public str dataRelationPath(\[str value\])                                                                  | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                                                                         |
| public int dataSource(\[AnyType value\])                                                                    | Gets or sets a data source to be used by the control or the form.                                                                                                                                                     |
| public boolean defaultButton(\[boolean value\])                                                             | Determines whether the button should be the default button in the form.                                                                                                                                               |
| public str disabledImage(\[str value\])                                                                     | Gets or sets the disabled image of the button.                                                                                                                                                                        |
| public int disabledImageLocation(\[int value\])                                                             |                                                                                                                                                                                                                       |
| public int disabledResource(\[int value\])                                                                  | Gets or sets the resource ID of the image to use as the disabled button image.                                                                                                                                        |
| public int displayTarget(\[int value\])                                                                     | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.                                               |
| public int dragDrop(\[int value\])                                                                          | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                                                                     |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                           | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                                                                        |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                               | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                                                                      |
| public str dragText()                                                                                       | Retrieves the text that is displayed when the form control is dragged.                                                                                                                                                |
| public boolean enabled(\[boolean value\])                                                                   | Determines whether to enable or disable the object.                                                                                                                                                                   |
| public str font(\[str value\])                                                                              | Gets or sets the name of the font for the control to use.                                                                                                                                                             |
| public int fontSize(\[int value\])                                                                          | Gets or sets the size of the font for the control to use.                                                                                                                                                             |
| public boolean forcedToOverflow(\[boolean value\])                                                          |                                                                                                                                                                                                                       |
| public int foregroundColor(\[int value\])                                                                   | Gets or sets the text color for the control to use.                                                                                                                                                                   |
| public int formViewOption(\[int value\])                                                                    | Specifies the form mode to use. Options include Auto, Grid, and Details. The default is Auto.                                                                                                                         |
| public boolean hasChanged(\[boolean val\])                                                                  | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                                                              |
| public boolean hasUserSetting()                                                                             | Indicates whether the control has custom user settings.                                                                                                                                                               |
| public int height(int value, \[int mode\])                                                                  | Gets or sets the height of the control.                                                                                                                                                                               |
| public int heightMode(\[int value\])                                                                        | Gets or sets a calculation mode for the height of the control.                                                                                                                                                        |
| public int heightValue(\[int value\])                                                                       | Gets or sets the height of the control.                                                                                                                                                                               |
| public str helpField()                                                                                      | Retrieves the Help text for the control.                                                                                                                                                                              |
| public str helpText(\[str value\])                                                                          | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                                                              |
| public str hierarchyParent(\[str value\])                                                                   | Gets or sets the HierarchyParent property value of the control.                                                                                                                                                       |
| public int hWnd()                                                                                           | Retrieves the Windows handle for the control.                                                                                                                                                                         |
| public int imageLocation(\[int value\])                                                                     |                                                                                                                                                                                                                       |
| public boolean isContainer()                                                                                |                                                                                                                                                                                                                       |
| public boolean isDisplayed()                                                                                | Retrieves a value that indicates whether the control is displayed.                                                                                                                                                    |
| public boolean isRestricted()                                                                               | Retrieves a value that indicates whether the control is restricted.                                                                                                                                                   |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                    | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                                                                 |
| public boolean italic(\[boolean value\])                                                                    |                                                                                                                                                                                                                       |
| public str keyTip(\[str value\])                                                                            |                                                                                                                                                                                                                       |
| public int left(int value, \[int mode\])                                                                    | Gets or sets the horizontal position of the control in the form.                                                                                                                                                      |
| public int leftMode(\[int value\])                                                                          | Sets the horizontal arrange mode for the control in the form.                                                                                                                                                         |
| public int leftValue(\[int value\])                                                                         | Gets or sets the horizontal position of the control in the form.                                                                                                                                                      |
| public boolean markAsUserAdd(\[boolean value\])                                                             | Marks or unmarks the control as a user-added control.                                                                                                                                                                 |
| public xMenuFunction menufunction()                                                                         |                                                                                                                                                                                                                       |
| public str menuItemName(\[str value\])                                                                      | Determines which menu item is run for a DropDialogButton control.                                                                                                                                                     |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                             | Is called when the control is double-clicked by the user.                                                                                                                                                             |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user clicks the mouse button over the control.                                                                                                                                                     |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                 | Is called when the user moves the mouse pointer over the control.                                                                                                                                                     |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                   | Is called when the user releases the mouse button over the control area.                                                                                                                                              |
| public int multiSelect(\[int value\])                                                                       |                                                                                                                                                                                                                       |
| public str name(\[str value\])                                                                              | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.                                                                               |
| public int neededPermission(\[int value\])                                                                  | Specifies the minimum permission level that is required to be allowed access to the control.                                                                                                                          |
| public int needsRecord(\[int value\])                                                                       | Specifies whether a button is enabled if no record is present. The default value is No.                                                                                                                               |
| public str normalImage(\[str value\])                                                                       |                                                                                                                                                                                                                       |
| public int normalResource(\[int value\])                                                                    |                                                                                                                                                                                                                       |
| public int openMode(\[int value\])                                                                          | Specifies the view mode of the target form. The possible values include Auto, View, Edit, and New. The default is Auto. You may use this property to specify whether the target form opens in edit or read-only mode. |
| public container SysObsoleteAttribute()                                                                     |                                                                                                                                                                                                                       |
| public str parameters(\[str value\])                                                                        | Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.                                                                                                                |
| public FormControl parentControl()                                                                          | Retrieves the parent control for the control.                                                                                                                                                                         |
| public boolean primary(\[boolean value\])                                                                   |                                                                                                                                                                                                                       |
| public boolean saveRecord(\[boolean value\])                                                                |                                                                                                                                                                                                                       |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                   | Sets or returns the ID of the security key for the control.                                                                                                                                                           |
| public boolean sendExternalContext(\[boolean value\])                                                       | Specifies whether the external record context of this form should be used as the menu item external record context. The default value is No.                                                                          |
| public int shortkey(\[int value\])                                                                          |                                                                                                                                                                                                                       |
| public int showContextMenu(int menuHandle)                                                                  | Shows the shortcut menu for the control.                                                                                                                                                                              |
| public boolean showShortCut(\[boolean value\])                                                              |                                                                                                                                                                                                                       |
| public boolean skip(\[boolean value\])                                                                      | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                                                                       |
| public int sort(\[SortOrder sortDirection\])                                                                |                                                                                                                                                                                                                       |
| public int style(\[int value\])                                                                             | Specifies the style of the form. This property controls the form design pattern being used with the form. The default is Auto.                                                                                        |
| public str text(\[str value\])                                                                              |                                                                                                                                                                                                                       |
| public str toolTip()                                                                                        | Retrieves the tooltip text for the control.                                                                                                                                                                           |
| public int top(int value, \[int mode\])                                                                     | Gets or sets the vertical position of the control in the form.                                                                                                                                                        |
| public int topMode(\[int value\])                                                                           | Sets the vertical arrange mode for the control in the form.                                                                                                                                                           |
| public int topValue(\[int value\])                                                                          | Gets or sets the vertical position of the control in the form.                                                                                                                                                        |
| public int type(\[int value\])                                                                              | Specifies the type of the control. Read-only.                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                 |                                                                                                                                                                                                                       |
| public boolean SysObsoleteAttribute(container data)                                                         |                                                                                                                                                                                                                       |
| public int userData(\[int value\])                                                                          | Gets or sets the user data for the control.                                                                                                                                                                           |
| public int userDataItem(\[int value\])                                                                      | Gets or sets the user data item for the control.                                                                                                                                                                      |
| public int userDataItems(\[int value\])                                                                     | Gets or sets the number of user data items for the control.                                                                                                                                                           |
| public int userDisable(\[int value\])                                                                       | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                                                                   |
| public int userHeight(\[int value\])                                                                        | Gets or sets the custom user height for the control.                                                                                                                                                                  |
| public int userHide(\[int value\])                                                                          | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                                                                    |
| public int userOrgContainer(\[int value\])                                                                  | Gets or sets the organization container for the control.                                                                                                                                                              |
| public int userOrgSibling(\[int value\])                                                                    | Gets or sets the organization sibling for the control.                                                                                                                                                                |
| public str userPromptText(\[str value\])                                                                    | Gets or sets the user label text for the control.                                                                                                                                                                     |
| public int userSecurityLevel(\[int value\])                                                                 | Gets or sets the user security level for the control.                                                                                                                                                                 |
| public int userSkip(\[int value\])                                                                          | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                                                                  |
| public int userWidth(\[int value\])                                                                         | Sets or returns the width of the control in pixels.                                                                                                                                                                   |
| public boolean value(\[boolean value\])                                                                     |                                                                                                                                                                                                                       |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                | Gets or sets the vertical spacing of the control in the form.                                                                                                                                                         |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                      | Sets the vertical spacing mode for the control in the form.                                                                                                                                                           |
| public int verticalSpacingValue(\[int value\])                                                              | Gets or sets the vertical spacing of the control in the form.                                                                                                                                                         |
| public boolean visible(\[boolean value\])                                                                   | Sets or returns a value that indicates whether the control is visible.                                                                                                                                                |
| public int width(int value, \[int mode\])                                                                   | Gets or sets the width of the control.                                                                                                                                                                                |
| public int widthMode(\[int value\])                                                                         | Gets or sets the calculation mode of the width of the control.                                                                                                                                                        |
| public int widthValue(\[int value\])                                                                        | Gets or sets the width of the control.                                                                                                                                                                                |
| public void gotFocus()                                                                                      | Indicates that the control has received focus.                                                                                                                                                                        |
| public void inputSearch(str searchStr)                                                                      | Performs data filtering for the control, based on the specified string.                                                                                                                                               |
| public void filter(\[str filterStr\])                                                                       |                                                                                                                                                                                                                       |
| public void prefColumnSize(int width, int height)                                                           | Specifies the preferred column width and height for the form control.                                                                                                                                                 |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                                                                    |
| public void mouseLeave()                                                                                    | Indicates that the mouse pointer has left the control.                                                                                                                                                                |
| private void OnDialogClosed(\[FormControl sender\], \[FormControlEventArgs e\])                             |                                                                                                                                                                                                                       |
| public void clicked()                                                                                       |                                                                                                                                                                                                                       |
| private void OnClicked(\[FormControl sender\], \[FormControlEventArgs e\])                                  |                                                                                                                                                                                                                       |
| public void lostFocus()                                                                                     | Indicates that the control has lost focus.                                                                                                                                                                            |
| public void jumpRef()                                                                                       |                                                                                                                                                                                                                       |
| public void context()                                                                                       | Shows the shortcut menu for the control.                                                                                                                                                                              |
| public void displayControl()                                                                                | Displays the control.                                                                                                                                                                                                 |
| public void dialogClosed(xFormRun formRun)                                                                  |                                                                                                                                                                                                                       |
| public void endDrag()                                                                                       | Is called when the user has finished dragging a form control.                                                                                                                                                         |
| public void dialogInitialized(xFormRun formRun)                                                             |                                                                                                                                                                                                                       |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                |                                                                                                                                                                                                                       |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                                                                  |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                 |                                                                                                                                                                                                                       |
| public void resetUserSetting()                                                                              | Resets the user settings for the control.                                                                                                                                                                             |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                               | Is called when the user moves the mouse pointer into the control area.                                                                                                                                                |
| public void setFocus()                                                                                      | Sets the focus on the control.                                                                                                                                                                                        |
| public void cut()                                                                                           | Cuts the contents of the control.                                                                                                                                                                                     |
| public void dragLeave()                                                                                     | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                                                                      |
| public void paste()                                                                                         | Pastes the contents of the clipboard into the control.                                                                                                                                                                |
| public void copy()                                                                                          | Copies the contents of the control to the clipboard.                                                                                                                                                                  |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\]) |                                                                                                                                                                                                                       |

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

### Method alignment

Changes the alignment of the text in the control. Values are Left, right, or center, to align the control appropriately.

    public int alignment([int value])

#### Parameters

value  

#### Return Value

### Method allowEdit

Determines whether the user can change the contents of the control.

    public boolean allowEdit([boolean value])

#### Parameters

value  
The value to assign to the allowEdit property.

#### Return Value

true if the control can be edited; otherwise, false.

#### Remarks

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

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
The new value of the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

### Method autoRefreshData

Specifies whether the data from the data source that is associated with the control will be refreshed when the button is clicked. The default value is No.

    public boolean autoRefreshData([boolean value])

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

### Method big

    public boolean big([boolean value])

#### Parameters

value  

#### Return Value

### Method bold

Gets or sets the weight of font used to output text in the control.

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

The integer that is returned contains the style of the borderline of the control as follows:

| Value. | Description. |
|--------|--------------|
| 0      | Auto.        |
| 1      | 3D.          |
| 2      | Single line. |
| 3      | Flat.        |
| 4      | None.        |

### Method buttonDisplay

Gets or sets the appearance of the button control.

    public int buttonDisplay([int value])

#### Parameters

value  

#### Return Value

An integer between zero and five, inclusive.

#### Remarks

The value of the property defines whether the text, the image, or both should be displayed on the button. This property also controls relative positions of text and image if both are displayed.The integer value that is returned contains the appearace of the button control as follows:

| Value. | Description.                                                     |
|--------|------------------------------------------------------------------|
| 0      | Text only.                                                       |
| 1      | Image Only.                                                      |
| 2      | Text and image; the image is displayed below the text.           |
| 3      | Text and image; the image is displayed above the text.           |
| 4      | Text and image; the image is displayed to the left of the text.  |
| 5      | Text and image; the image is displayed to the right of the text. |

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

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                         |
|--------|--------------------------------|
| 0      | Default.                       |
| 1      | The Microsoft Windows palette. |
| 2      | The true-color scheme.         |

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key being assigned to the control; optional.

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

### Method copyCallerQuery

Specifies whether to copy the query from the calling form to the target form. This enables the target form to display the same data that was being viewed in the original form. The default value is Auto.

    public int copyCallerQuery([int value])

#### Parameters

value  

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

Specifies the field that will be used to identify the country context. See CountryRegionCodes.

    public FieldId countryRegionContextField([FieldId value])

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

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method defaultButton

Determines whether the button should be the default button in the form.

    public boolean defaultButton([boolean value])

#### Parameters

value  

#### Return Value

true if the button should be the default button; otherwise, false.

### Method disabledImage

Gets or sets the disabled image of the button.

    public str disabledImage([str value])

#### Parameters

value  

#### Return Value

The full name of an image file. The system supports all of the GDI-supported image formats.

#### Remarks

This property has precedence over the disabledResource property. It is used if both of these properties are set.

### Method disabledImageLocation

    public int disabledImageLocation([int value])

#### Parameters

value  

#### Return Value

### Method disabledResource

Gets or sets the resource ID of the image to use as the disabled button image.

    public int disabledResource([int value])

#### Parameters

value  

#### Return Value

The resource ID of the image to use as the disabled button image. Both icon and bitmap images are supported.

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An integer that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave , the dragOver, and the dragOverEx to specify the behavior.

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

### Method forcedToOverflow

    public boolean forcedToOverflow([boolean value])

#### Parameters

value  

#### Return Value

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

### Method formViewOption

Specifies the form mode to use. Options include Auto, Grid, and Details. The default is Auto.

    public int formViewOption([int value])

#### Parameters

value  

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
An integer that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

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

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

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

The helpField method cannot be used to set the value of the Help text. Use the helpText mehod to set the value of the Help text.

### Method helpText

Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.

    public str helpText([str value])

#### Parameters

value  
The value that is assigned as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

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

### Method imageLocation

    public int imageLocation([int value])

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

Retrieves a value that indicates whether the control allows for the specified level of customization.

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

### Method italic

    public boolean italic([boolean value])

#### Parameters

value  

#### Return Value

### Method keyTip

    public str keyTip([str value])

#### Parameters

value  

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

### Method menufunction

    public xMenuFunction menufunction()

#### Return Value

### Method menuItemName

Determines which menu item is run for a DropDialogButton control.

    public str menuItemName([str value])

#### Parameters

value  

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

### Method multiSelect

    public int multiSelect([int value])

#### Parameters

value  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
-   It cannot exceed 250 characters.
-   It can include numbers and underscore (\_) characters.
-   It cannot include punctuation or spaces.
-   Tables cannot have the same name as other public objects, such as extended data types, base enums, or classes.

### Method neededPermission

Specifies the minimum permission level that is required to be allowed access to the control.

    public int neededPermission([int value])

#### Parameters

value  

#### Return Value

#### Remarks

The possible values are as follows:

-   None
-   Read
-   Update
-   Create
-   Correct
-   Delete
-   Manual

The default value is None.

### Method needsRecord

Specifies whether a button is enabled if no record is present. The default value is No.

    public int needsRecord([int value])

#### Parameters

value  

#### Return Value

### Method normalImage

    public str normalImage([str value])

#### Parameters

value  

#### Return Value

### Method normalResource

    public int normalResource([int value])

#### Parameters

value  

#### Return Value

### Method openMode

Specifies the view mode of the target form. The possible values include Auto, View, Edit, and New. The default is Auto. You may use this property to specify whether the target form opens in edit or read-only mode.

    public int openMode([int value])

#### Parameters

value  

#### Return Value

### Method SysObsoleteAttribute

    public container SysObsoleteAttribute()

#### Return Value

### Method parameters

Gets or sets the list of parameters that are passed to objects taht are run by the MenuFunction class.

    public str parameters([str value])

#### Parameters

value  

#### Return Value

The list of parameters that are passed to the object.

#### Remarks

The parameters string format is Parameter1=Value1, Parameter2=Value2, and so on.cts ignore passed, unrecognized parameters.

### Method parentControl

Retrieves the parent control for the control.

    public FormControl parentControl()

#### Return Value

The parent control for the control.

### Method primary

    public boolean primary([boolean value])

#### Parameters

value  

#### Return Value

### Method saveRecord

    public boolean saveRecord([boolean value])

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

### Method sendExternalContext

Specifies whether the external record context of this form should be used as the menu item external record context. The default value is No.

    public boolean sendExternalContext([boolean value])

#### Parameters

value  

#### Return Value

### Method shortkey

    public int shortkey([int value])

#### Parameters

value  

#### Return Value

### Method showContextMenu

Shows the shortcut menu for the control.

    public int showContextMenu(int menuHandle)

#### Parameters

menuHandle  
The ID of the menu to show.

#### Return Value

An integer value that indicates whether the call succeeded.

### Method showShortCut

    public boolean showShortCut([boolean value])

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

Specifies the style of the form. This property controls the form design pattern being used with the form. The default is Auto.

    public int style([int value])

#### Parameters

value  

#### Return Value

### Method text

    public str text([str value])

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

Specifies the type of the control. Read-only.

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

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method value

    public boolean value([boolean value])

#### Parameters

value  

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

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

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

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

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

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

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

### Method mouseLeave

Indicates that the mouse pointer has left the control.

    public void mouseLeave()

### Method OnDialogClosed

    private void OnDialogClosed([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method clicked

    public void clicked()

### Method OnClicked

    private void OnClicked([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method jumpRef

    public void jumpRef()

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method displayControl

Displays the control.

    public void displayControl()

### Method dialogClosed

    public void dialogClosed(xFormRun formRun)

#### Parameters

formRun  

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method dialogInitialized

    public void dialogInitialized(xFormRun formRun)

#### Parameters

formRun  

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

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

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

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

### Method cut

Cuts the contents of the control.

    public void cut()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

## Class FormEventArgs
    class FormEventArgs

### Remarks

### Examples

### Methods

| Method | Description |
|--------|-------------|

## Class FormFastTabHeaderControl
    class FormFastTabHeaderControl extends FormControl

### Remarks

### Examples

### Methods

| Method                                                                                                              | Description                                                                                                                                                             |
|---------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| public FormControl addControl(FormControlType controlType, str controlName, \[FormControl insertAfter\])            |                                                                                                                                                                         |
| public FormControl addControlEx(str controlClass, str controlName, \[FormControl insertAfter\])                     |                                                                                                                                                                         |
| public FormControl addDataField(int dataSourceId, FieldId fieldId, \[FormControl insertAfter\], \[int arrayIndex\]) |                                                                                                                                                                         |
| public boolean alignChild(\[boolean value\])                                                                        |                                                                                                                                                                         |
| public boolean alignChildren(\[boolean value\])                                                                     |                                                                                                                                                                         |
| public boolean alignControl(\[boolean value\])                                                                      | Determines whether to align the control.                                                                                                                                |
| public boolean allowEdit(\[boolean value\])                                                                         | Determines whether the user can change the contents of the control.                                                                                                     |
| public boolean allowSysSetup()                                                                                      | Retrieves a value that indicates whether the control is shown in the SysSetup form.                                                                                     |
| public int allowUserSetup(\[int value\])                                                                            |                                                                                                                                                                         |
| public int arrangeGuide(\[int value\])                                                                              |                                                                                                                                                                         |
| public int arrangeMethod(\[int value\])                                                                             |                                                                                                                                                                         |
| public int arrangeWhen(\[int value\])                                                                               |                                                                                                                                                                         |
| public boolean autoDeclaration(\[boolean value\])                                                                   | Determines whether the system can declare a member variable that has the same name as the control.                                                                      |
| public int backgroundColor(\[int value\])                                                                           | Gets or sets the background color of the control.                                                                                                                       |
| public int backStyle(\[int value\])                                                                                 | Determiness whether the control background can be transparent.                                                                                                          |
| public int beginDrag(int x, int y)                                                                                  | Is called when the user starts to drag a form control.                                                                                                                  |
| public int bold(\[int value\])                                                                                      | Gets or sets the weight of font used to output text in the control.                                                                                                     |
| public int bottomMargin(\[int value\], \[AutoMode mode\])                                                           |                                                                                                                                                                         |
| public AutoMode bottomMarginMode(\[AutoMode mode\])                                                                 |                                                                                                                                                                         |
| public int bottomMarginValue(\[int value\])                                                                         |                                                                                                                                                                         |
| public container calcControlSize(int chars, int lines)                                                              | Retrieves the size of the control.                                                                                                                                      |
| public boolean canAddDataField(int dataSourceId, FieldId fieldId, \[int arrayIndex\])                               |                                                                                                                                                                         |
| public boolean canContain(FormControl control)                                                                      |                                                                                                                                                                         |
| public str caption(\[str value\])                                                                                   | Gets or set the caption of the control.                                                                                                                                 |
| public int characterSet(\[int value\])                                                                              | Gets or sets the character set of the font.                                                                                                                             |
| public int colorScheme(\[int value\])                                                                               | Gets or sets the color scheme of the control.                                                                                                                           |
| public int columns(\[int value\], \[AutoMode mode\])                                                                |                                                                                                                                                                         |
| public AutoMode columnsMode(\[AutoMode mode\])                                                                      |                                                                                                                                                                         |
| public int columnspace(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                                         |
| public AutoMode columnspaceMode(\[AutoMode mode\])                                                                  |                                                                                                                                                                         |
| public int columnspaceValue(\[int value\])                                                                          |                                                                                                                                                                         |
| public int columnsValue(\[int value\])                                                                              |                                                                                                                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])                                            | Gets or sets the configuration key that is assigned to the control.                                                                                                     |
| public List configurationKeyEx()                                                                                    | Retrieves a list that contains the IDs of configuration keys that are in effect for the control.                                                                        |
| public boolean contains(FormControl control)                                                                        |                                                                                                                                                                         |
| public int controlCount()                                                                                           |                                                                                                                                                                         |
| public FormControl controlNum(int controlNo)                                                                        |                                                                                                                                                                         |
| public str countryRegionCodes(\[str value\])                                                                        | Gets or sets the comma-separated list of country/region codes for the control.                                                                                          |
| public FieldId countryRegionContextField(\[FieldId value\])                                                         |                                                                                                                                                                         |
| public str dataRelationPath(\[str value\])                                                                          | Gets or sets the period-delimited list of relations that links the field binding of the DataField object to a relative table.                                           |
| public int dataSource(\[AnyType value\])                                                                            | Gets or sets a data source to be used by the control or the form.                                                                                                       |
| public int displayTarget(\[int value\])                                                                             | Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both. |
| public int dragDrop(\[int value\])                                                                                  | Determines whether to enable or disable drag-and-drop operations for the control.                                                                                       |
| public FormDrag dragOver(FormControl dragSource, FormDrag dragMode, int x, int y)                                   | Raises the dragOver event to indicate that a mouse drag operation is over the current control.                                                                          |
| public FormDrag dragOverEx(Array dragSource, FormDrag dragMode, int x, int y)                                       | Raises the dragOverEx event to indicate that a mouse drag operation is over the current control.                                                                        |
| public str dragText()                                                                                               | Retrieves the text that is displayed when the form control is dragged.                                                                                                  |
| public boolean enabled(\[boolean value\])                                                                           | Determines whether to enable or disable the object.                                                                                                                     |
| public str font(\[str value\])                                                                                      | Gets or sets the name of the font for the control to use.                                                                                                               |
| public int fontSize(\[int value\])                                                                                  | Gets or sets the size of the font for the control to use.                                                                                                               |
| public boolean hasChanged(\[boolean val\])                                                                          | Sets or returns a value that indicates whether the contents of the control have changed.                                                                                |
| public boolean hasUserSetting()                                                                                     | Indicates whether the control has custom user settings.                                                                                                                 |
| public int height(int value, \[int mode\])                                                                          | Gets or sets the height of the control.                                                                                                                                 |
| public int heightMode(\[int value\])                                                                                | Gets or sets a calculation mode for the height of the control.                                                                                                          |
| public int heightValue(\[int value\])                                                                               | Gets or sets the height of the control.                                                                                                                                 |
| public str helpField()                                                                                              | Retrieves the Help text for the control.                                                                                                                                |
| public str helpText(\[str value\])                                                                                  | Gets or sets the Help text to display at the bottom of the screen when a field or control is pointed to.                                                                |
| public boolean hideIfEmpty(\[boolean value\])                                                                       |                                                                                                                                                                         |
| public str hierarchyParent(\[str value\])                                                                           | Gets or sets the HierarchyParent property value of the control.                                                                                                         |
| public int hWnd()                                                                                                   | Retrieves the Windows handle for the control.                                                                                                                           |
| public boolean isContainer()                                                                                        |                                                                                                                                                                         |
| public boolean isDisplayed()                                                                                        | Retrieves a value that indicates whether the control is displayed.                                                                                                      |
| public boolean isRestricted()                                                                                       | Retrieves a value that indicates whether the control is restricted.                                                                                                     |
| public boolean isUserSetupEnabled(int neededSetupRights)                                                            | Retrieves a value that indicates whether the control allows for the specified level of customization.                                                                   |
| public boolean italic(\[boolean value\])                                                                            |                                                                                                                                                                         |
| public boolean leave()                                                                                              |                                                                                                                                                                         |
| public int left(int value, \[int mode\])                                                                            | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public int leftMargin(\[int value\], \[AutoMode mode\])                                                             |                                                                                                                                                                         |
| public AutoMode leftMarginMode(\[AutoMode mode\])                                                                   |                                                                                                                                                                         |
| public int leftMarginValue(\[int value\])                                                                           |                                                                                                                                                                         |
| public int leftMode(\[int value\])                                                                                  | Sets the horizontal arrange mode for the control in the form.                                                                                                           |
| public int leftValue(\[int value\])                                                                                 | Gets or sets the horizontal position of the control in the form.                                                                                                        |
| public boolean markAsUserAdd(\[boolean value\])                                                                     | Marks or unmarks the control as a user-added control.                                                                                                                   |
| public int mouseDblClick(int x, int y, int button, boolean Ctrl, boolean Shift)                                     | Is called when the control is double-clicked by the user.                                                                                                               |
| public int mouseDown(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user clicks the mouse button over the control.                                                                                                       |
| public int mouseMove(int x, int y, int button, boolean Ctrl, boolean Shift)                                         | Is called when the user moves the mouse pointer over the control.                                                                                                       |
| public int mouseUp(int x, int y, int button, boolean Ctrl, boolean Shift)                                           | Is called when the user releases the mouse button over the control area.                                                                                                |
| public int moveControl(int controlId, \[int insertAfterId\])                                                        |                                                                                                                                                                         |
| public str name(\[str value\])                                                                                      | Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.                                 |
| public int neededPermission(\[int value\])                                                                          |                                                                                                                                                                         |
| public container SysObsoleteAttribute()                                                                             |                                                                                                                                                                         |
| public FormControl parentControl()                                                                                  | Retrieves the parent control for the control.                                                                                                                           |
| public int rightMargin(\[int value\], \[AutoMode mode\])                                                            |                                                                                                                                                                         |
| public AutoMode rightMarginMode(\[AutoMode mode\])                                                                  |                                                                                                                                                                         |
| public int rightMarginValue(\[int value\])                                                                          |                                                                                                                                                                         |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                                                           | Sets or returns the ID of the security key for the control.                                                                                                             |
| public int showContextMenu(int menuHandle)                                                                          | Shows the shortcut menu for the control.                                                                                                                                |
| public boolean skip(\[boolean value\])                                                                              | Sets or returns a value that indicates whether the control is skipped when the user presses the TAB key to move to the control.                                         |
| public int sort(\[SortOrder sortDirection\])                                                                        |                                                                                                                                                                         |
| public str toolTip()                                                                                                | Retrieves the tooltip text for the control.                                                                                                                             |
| public int top(int value, \[int mode\])                                                                             | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int topMargin(\[int value\], \[AutoMode mode\])                                                              |                                                                                                                                                                         |
| public AutoMode topMarginMode(\[AutoMode mode\])                                                                    |                                                                                                                                                                         |
| public int topMarginValue(\[int value\])                                                                            |                                                                                                                                                                         |
| public int topMode(\[int value\])                                                                                   | Sets the vertical arrange mode for the control in the form.                                                                                                             |
| public int topValue(\[int value\])                                                                                  | Gets or sets the vertical position of the control in the form.                                                                                                          |
| public int type(\[int value\])                                                                                      |                                                                                                                                                                         |
| public boolean underline(\[boolean value\])                                                                         |                                                                                                                                                                         |
| public boolean SysObsoleteAttribute(container data)                                                                 |                                                                                                                                                                         |
| public int userData(\[int value\])                                                                                  | Gets or sets the user data for the control.                                                                                                                             |
| public int userDataItem(\[int value\])                                                                              | Gets or sets the user data item for the control.                                                                                                                        |
| public int userDataItems(\[int value\])                                                                             | Gets or sets the number of user data items for the control.                                                                                                             |
| public int userDisable(\[int value\])                                                                               | Gets or sets the value that indicates whether the control is disabled for the user.                                                                                     |
| public int userHeight(\[int value\])                                                                                | Gets or sets the custom user height for the control.                                                                                                                    |
| public int userHide(\[int value\])                                                                                  | Gets or sets the value that indicates whether the control is hidden from the user.                                                                                      |
| public int userOrgContainer(\[int value\])                                                                          | Gets or sets the organization container for the control.                                                                                                                |
| public int userOrgSibling(\[int value\])                                                                            | Gets or sets the organization sibling for the control.                                                                                                                  |
| public str userPromptText(\[str value\])                                                                            | Gets or sets the user label text for the control.                                                                                                                       |
| public int userSecurityLevel(\[int value\])                                                                         | Gets or sets the user security level for the control.                                                                                                                   |
| public int userSkip(\[int value\])                                                                                  | Sets or returns the value that indicates whether the form control is skipped when the user presses the TAB key to navigate the controls in the form.                    |
| public int userWidth(\[int value\])                                                                                 | Sets or returns the width of the control in pixels.                                                                                                                     |
| public boolean useUserLayout(\[boolean value\])                                                                     |                                                                                                                                                                         |
| public int verticalSpacing(\[int value\], \[AutoMode mode\])                                                        | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public AutoMode verticalSpacingMode(\[AutoMode mode\])                                                              | Sets the vertical spacing mode for the control in the form.                                                                                                             |
| public int verticalSpacingValue(\[int value\])                                                                      | Gets or sets the vertical spacing of the control in the form.                                                                                                           |
| public boolean visible(\[boolean value\])                                                                           | Sets or returns a value that indicates whether the control is visible.                                                                                                  |
| public int width(int value, \[int mode\])                                                                           | Gets or sets the width of the control.                                                                                                                                  |
| public int widthMode(\[int value\])                                                                                 | Gets or sets the calculation mode of the width of the control.                                                                                                          |
| public int widthValue(\[int value\])                                                                                | Gets or sets the width of the control.                                                                                                                                  |
| public void filter(\[str filterStr\])                                                                               |                                                                                                                                                                         |
| private void OnLeaving(\[FormControl sender\], \[FormControlEventArgs e\])                                          |                                                                                                                                                                         |
| public void jumpRef()                                                                                               |                                                                                                                                                                         |
| public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, \[Object overrideObject\])         |                                                                                                                                                                         |
| public void gotFocus()                                                                                              | Indicates that the control has received focus.                                                                                                                          |
| private void OnGotFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                         |                                                                                                                                                                         |
| public void setFocus()                                                                                              | Sets the focus on the control.                                                                                                                                          |
| public void mouseEnter(int x, int y, int button, boolean Ctrl, boolean Shift)                                       | Is called when the user moves the mouse pointer into the control area.                                                                                                  |
| public void arrange()                                                                                               |                                                                                                                                                                         |
| public void endDrag()                                                                                               | Is called when the user has finished dragging a form control.                                                                                                           |
| public void paste()                                                                                                 | Pastes the contents of the clipboard into the control.                                                                                                                  |
| public void drop(FormControl dragSource, FormDrag dragMode, int x, int y)                                           | Raises the drop event to indicate that a drop operation is being performed on the current control.                                                                      |
| public void resetUserSetting()                                                                                      | Resets the user settings for the control.                                                                                                                               |
| private void OnLostFocus(\[FormControl sender\], \[FormControlEventArgs e\])                                        |                                                                                                                                                                         |
| public void mouseLeave()                                                                                            | Indicates that the mouse pointer has left the control.                                                                                                                  |
| public void dropEx(Array dragSource, FormDrag dragMode, int x, int y)                                               | Raises the dropEx event to indicate that a drop operation is being performed on the current control.                                                                    |
| public void prefColumnSize(int width, int height)                                                                   | Specifies the preferred column width and height for the form control.                                                                                                   |
| public void copy()                                                                                                  | Copies the contents of the control to the clipboard.                                                                                                                    |
| public void enter()                                                                                                 |                                                                                                                                                                         |
| private void OnEnter(\[FormControl sender\], \[FormControlEventArgs e\])                                            |                                                                                                                                                                         |
| public void context()                                                                                               | Shows the shortcut menu for the control.                                                                                                                                |
| public void displayControl()                                                                                        | Displays the control.                                                                                                                                                   |
| public void cut()                                                                                                   | Cuts the contents of the control.                                                                                                                                       |
| public void lostFocus()                                                                                             | Indicates that the control has lost focus.                                                                                                                              |
| public void dragLeave()                                                                                             | Raises the dragLeave event to indicate that a mouse drag operation has left the current control.                                                                        |
| public void inputSearch(str searchStr)                                                                              | Performs data filtering for the control, based on the specified string.                                                                                                 |

### Method addControl

    public FormControl addControl(FormControlType controlType, str controlName, [FormControl insertAfter])

#### Parameters

controlType  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addControlEx

    public FormControl addControlEx(str controlClass, str controlName, [FormControl insertAfter])

#### Parameters

controlClass  

<!-- -->

controlName  

<!-- -->

insertAfter  

#### Return Value

### Method addDataField

    public FormControl addDataField(int dataSourceId, FieldId fieldId, [FormControl insertAfter], [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

insertAfter  

<!-- -->

arrayIndex  

#### Return Value

### Method alignChild

    public boolean alignChild([boolean value])

#### Parameters

value  

#### Return Value

### Method alignChildren

    public boolean alignChildren([boolean value])

#### Parameters

value  

#### Return Value

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

When this property is set on a container control, modifications are disabled or enabled for all controls within the container.

### Method allowSysSetup

Retrieves a value that indicates whether the control is shown in the SysSetup form.

    public boolean allowSysSetup()

#### Return Value

true if the control is shown in the SysSetup form; otherwise, false.

### Method allowUserSetup

    public int allowUserSetup([int value])

#### Parameters

value  

#### Return Value

### Method arrangeGuide

    public int arrangeGuide([int value])

#### Parameters

value  

#### Return Value

### Method arrangeMethod

    public int arrangeMethod([int value])

#### Parameters

value  

#### Return Value

### Method arrangeWhen

    public int arrangeWhen([int value])

#### Parameters

value  

#### Return Value

### Method autoDeclaration

Determines whether the system can declare a member variable that has the same name as the control.

    public boolean autoDeclaration([boolean value])

#### Parameters

value  
The value to which to set the property; optional.

#### Return Value

true if the member variable can be declared for this control; otherwise, false.

#### Remarks

Controls cannot have identical names.

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

Gets or sets the weight of font used to output text in the control.

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

### Method canAddDataField

    public boolean canAddDataField(int dataSourceId, FieldId fieldId, [int arrayIndex])

#### Parameters

dataSourceId  

<!-- -->

fieldId  

<!-- -->

arrayIndex  

#### Return Value

### Method canContain

    public boolean canContain(FormControl control)

#### Parameters

control  

#### Return Value

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

The values for the integer that is returned indicate the character set according to the following table:

| Value. | Description.         |
|--------|----------------------|
| 0      | ANSI\_CHARSET        |
| 1      | DEFAULT\_CHARSET     |
| 2      | SYMBOL\_CHARSET      |
| 77     | MAC\_CHARSET         |
| 128    | SHIFTJIS\_CHARSET    |
| 129    | HANGUL\_CHARSET      |
| 134    | GB2312\_CHARSET      |
| 136    | CHINESEBIG5\_CHARSET |
| 161    | GREEK\_CHARSET       |
| 162    | TURKISH\_CHARSET     |
| 163    | VIETNAMESE\_CHARSET  |
| 186    | BALTIC\_CHARSET      |
| 204    | RUSSIAN\_CHARSET     |
| 238    | EASTEUROPE\_CHARSET  |
| 255    | OEM\_CHARSET         |

The value in the following table is for the Korean language edition of MicrosoftWindows.

| Value. | Description.   |
|--------|----------------|
| 130    | JOHAB\_CHARSET |

The values in the following table are for the Middle East language edition of Windows.

| Value. | Description.    |
|--------|-----------------|
| 177    | HEBREW\_CHARSET |
| 178    | ARABIC\_CHARSET |

The value in the following table is for the Thai language edition of Windows.

| Value. | Description.  |
|--------|---------------|
| 222    | THAI\_CHARSET |

The default character set is set to a value based on the current system locale. For example, when the system locale is English (United States), it is set as ANSI\_CHARSET. For more information, see the LOGFONT structure on the MSDN website, http://go.microsoft.com/fwlink/?LinkID=85972.

### Method colorScheme

Gets or sets the color scheme of the control.

    public int colorScheme([int value])

#### Parameters

value  

#### Return Value

An integer between zero and two, inclusive.

#### Remarks

The color scheme is defined according to the following table:

| Value. | Style.                 |
|--------|------------------------|
| 0      | Default.               |
| 1      | The Windows palette.   |
| 2      | The true-color scheme. |

### Method columns

    public int columns([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnsMode

    public AutoMode columnsMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspace

    public int columnspace([int value], [AutoMode mode])

#### Parameters

value  

<!-- -->

mode  

#### Return Value

### Method columnspaceMode

    public AutoMode columnspaceMode([AutoMode mode])

#### Parameters

mode  

#### Return Value

### Method columnspaceValue

    public int columnspaceValue([int value])

#### Parameters

value  

#### Return Value

### Method columnsValue

    public int columnsValue([int value])

#### Parameters

value  

#### Return Value

### Method configurationKey

Gets or sets the configuration key that is assigned to the control.

    public ConfigurationKeyId configurationKey([ConfigurationKeyId value])

#### Parameters

value  
The ID of the configuration key being assigned to the control; optional.

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

### Method contains

    public boolean contains(FormControl control)

#### Parameters

control  

#### Return Value

### Method controlCount

    public int controlCount()

#### Return Value

### Method controlNum

    public FormControl controlNum(int controlNo)

#### Parameters

controlNo  

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

Gets or sets a data source to be used by the control or the form.

    public int dataSource([AnyType value])

#### Parameters

value  

#### Return Value

The identifier of the data source to be used.

### Method displayTarget

Gets or sets the value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal for Microsoft Dynamics 365 for Operations, or in both.

    public int displayTarget([int value])

#### Parameters

value  
The integer value that indicates where the control is displayed; optional.

#### Return Value

The value that indicates whether the control is displayed in the Microsoft Dynamics 365 for Operations client, in Enterprise Portal, or in both.

### Method dragDrop

Determines whether to enable or disable drag-and-drop operations for the control.

    public int dragDrop([int value])

#### Parameters

value  
An Integer data type that indicates whether drag-and-drop behavior is enabled; optional.

#### Return Value

1 if drag-and-drop operations are enabled; otherwise, false.

#### Remarks

Use the dragLeave, dragOver, and dragOverEx methods to specify the behavior.

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
An integer data type that indicates how the height is calculated; optional.

<!-- -->

mode  
An integer data type that indicates how the height is calculated; optional.

#### Return Value

The height of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the height according to the following table:

| Mode.            | Height calculation.                                                                       |
|------------------|-------------------------------------------------------------------------------------------|
| -1 Exact.        | The exact height in pixels of the controls is used.                                       |
| 0 Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| 1 Column height. | The layout of the form determines the height of the control.                              |

The height and height calculation mode can be set separately.

### Method heightMode

Gets or sets a calculation mode for the height of the control.

    public int heightMode([int value])

#### Parameters

value  
An integer data type value that indicates how control height is calculated; optional.

#### Return Value

The calculation mode.

#### Remarks

Calculate the height according to the following table:

| Mode.          | Height Calculation.                                                                       |
|----------------|-------------------------------------------------------------------------------------------|
| Exact.         | The exact height in pixels of the controls is used.                                       |
| Auto.          | The height of the control is calculated automatically and the value parameter is ignored. |
| Column height. | The layout of the form determines the height of the control.                              |

The height of the control might change when the mode is set to auto or column height.

### Method heightValue

Gets or sets the height of the control.

    public int heightValue([int value])

#### Parameters

value  
An integer data type that specifies the height in pixels; optional.

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
The value that is assigned as the Help text for the control.

#### Return Value

The string to be displayed at the bottom of the screen.

#### Remarks

Set the HelpText property for an object by using the property sheet. The Help text must not exceed 250 characters.

### Method hideIfEmpty

    public boolean hideIfEmpty([boolean value])

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

Retrieves a value that indicates whether the control allows for the specified level of customization.

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

### Method italic

    public boolean italic([boolean value])

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

### Method moveControl

    public int moveControl(int controlId, [int insertAfterId])

#### Parameters

controlId  

<!-- -->

insertAfterId  

#### Return Value

### Method name

Gets or sets the name that is used in code to identify a form, report, table, query, or other Microsoft Dynamics 365 for Operations application object.

    public str name([str value])

#### Parameters

value  
The name to assign to the control.

#### Return Value

The name that is used in code to identify an application object.

#### Remarks

The name property value of an object must meet the following criteria to avoid code conflicts:

-   It must begin with a letter.
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

true if the control is skipped when the user presses the TAB key to move to the control; otherwise, false.

#### Remarks

If the enabled property is true, the allowEdit property is false, and the skip property is true, the user cannot change the contents of the control but can still copy the contents of the control.

### Method sort

    public int sort([SortOrder sortDirection])

#### Parameters

sortDirection  

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

Sets or returns the width of the control in pixels.

    public int userWidth([int value])

#### Parameters

value  
The number of pixels to use as the width of the control; optional.

#### Return Value

The number of pixels that the user specified as the width of the control; 0 (zero) if the user did not specify a character width.

#### Remarks

The userWidth method returns the width in pixels, based on six times the number of characters. For example, if the user has specified 30 characters as the width of the control, the return value is 6 \* 30 = 180. To specify the width of the control in characters, users can right-click the control to open the setup form where the character specification is made.

### Method useUserLayout

    public boolean useUserLayout([boolean value])

#### Parameters

value  

#### Return Value

### Method verticalSpacing

Gets or sets the vertical spacing of the control in the form.

    public int verticalSpacing([int value], [AutoMode mode])

#### Parameters

value  
An integer value that indicates the AutoMode for the control; optional.

<!-- -->

mode  
An integer value that indicates the AutoMode for the control; optional.

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
An integer data type that indicates how the width is calculated; optional.

<!-- -->

mode  
An integer data type that indicates how the width is calculated; optional.

#### Return Value

The width of the control in pixels.

#### Remarks

Exact mode is used if the value parameter is omitted.Calculate the width according to the following table:

| Mode.           | Width calculation.                                                                       |
|-----------------|------------------------------------------------------------------------------------------|
| -1 Exact.       | The exact width in pixels of the controls is used.                                       |
| 0 Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| 1 Column width. | The layout of the form determines the width of the control.                              |

The width and width calculation mode can be set separately.

### Method widthMode

Gets or sets the calculation mode of the width of the control.

    public int widthMode([int value])

#### Parameters

value  
An integer data type value that indicates how control width is calculated; optional.

#### Return Value

An integer value that indicates the current calculation mode.

#### Remarks

Calculate the width according to the following table:

| Mode.         | Width Calculation.                                                                       |
|---------------|------------------------------------------------------------------------------------------|
| Exact.        | The exact width in pixels of the controls is used.                                       |
| Auto.         | The width of the control is calculated automatically and the value parameter is ignored. |
| Column width. | The layout of the form determines the width of the control.                              |

The width of the control might change when the mode is set to auto or column width.

### Method widthValue

Gets or sets the width of the control.

    public int widthValue([int value])

#### Parameters

value  
An integer data type that specifies the width in pixels; optional.

#### Return Value

The width in pixels of the control.

#### Remarks

To change the width of the control, use the exact width calculation mode.

### Method filter

    public void filter([str filterStr])

#### Parameters

filterStr  

### Method OnLeaving

    private void OnLeaving([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method jumpRef

    public void jumpRef()

### Method registerOverrideMethod

    public void registerOverrideMethod(str methodToOverride, str objectMethodToCall, [Object overrideObject])

#### Parameters

methodToOverride  

<!-- -->

objectMethodToCall  

<!-- -->

overrideObject  

### Method gotFocus

Indicates that the control has received focus.

    public void gotFocus()

### Method OnGotFocus

    private void OnGotFocus([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method setFocus

Sets the focus on the control.

    public void setFocus()

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

### Method arrange

    public void arrange()

### Method endDrag

Is called when the user has finished dragging a form control.

    public void endDrag()

#### Remarks

This event is not raised unless the DragDrop property is enabled for the control and a beginDrag event has already been started. To drag a control, a user presses the mouse button in the control area and then moves the mouse pointer.

### Method paste

Pastes the contents of the clipboard into the control.

    public void paste()

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

### Method resetUserSetting

Resets the user settings for the control.

    public void resetUserSetting()

### Method OnLostFocus

    private void OnLostFocus([FormControl sender], [FormControlEventArgs e])

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

### Method prefColumnSize

Specifies the preferred column width and height for the form control.

    public void prefColumnSize(int width, int height)

#### Parameters

width  
The preferred height of the control.

<!-- -->

height  
The preferred height of the control.

### Method copy

Copies the contents of the control to the clipboard.

    public void copy()

### Method enter

    public void enter()

### Method OnEnter

    private void OnEnter([FormControl sender], [FormControlEventArgs e])

#### Parameters

sender  

<!-- -->

e  

### Method context

Shows the shortcut menu for the control.

    public void context()

### Method displayControl

Displays the control.

    public void displayControl()

### Method cut

Cuts the contents of the control.

    public void cut()

### Method lostFocus

Indicates that the control has lost focus.

    public void lostFocus()

### Method dragLeave

Raises the dragLeave event to indicate that a mouse drag operation has left the current control.

    public void dragLeave()

### Method inputSearch

Performs data filtering for the control, based on the specified string.

    public void inputSearch(str searchStr)

#### Parameters

searchStr  
The string value to use to filter data; optional.



