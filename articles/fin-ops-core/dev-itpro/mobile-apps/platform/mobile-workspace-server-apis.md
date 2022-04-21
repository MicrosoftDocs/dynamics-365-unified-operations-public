---
# required metadata

title: Server-side development (workspace X++ APIs)
description: This topic describes the platform that supports the mobile phone app, providing rich offline and mobile interactions, and an easy-to-use designer experience.
author: tonyafehr
ms.date: 11/10/2017
ms.topic: article
ms.prod:
ms.technology:

# optional metadata
# ms.search.form:
# ROBOTS:
audience: Developer, IT Pro
ms.reviewer: tfehr
ms.custom: 255544
ms.search.region: Global
# ms.search.industry: 
ms.author: tfehr
ms.search.validFrom: 2016-11-30
ms.dyn365.ops.version: Platform update 3

---
# Server-side development (workspace X++ APIs)

[!include [banner](../../includes/banner.md)]

## Class SysAppActionAttribute

SysAppActionAttribute used for decorating methods defining actions of workspace

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppActionAttribute class |
| pageMethodName | str | Gets the get method name that forms the page under which this task resides |
| actionTitle | str | Gets the Action Title |
| actionDescription | str | Gets the Action Description |
| crudOperationType | SysAppCRUDOperation | Gets the Crud Operation Type like Create, Update, Delete |

### Method new

Creates a new instance of SysAppActionAttribute class

```xpp
public void new ([str _actionTitle], [str _actionDescription], [SysAppCRUDOperation _crudOperationType], [str _pageMethodName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _actionTitle | str | True | Action title
| _actionDescription | str | True | Action description
| _crudOperationType | SysAppCRUDOperation | True | CRUD operation like Create, Update, Delete
| _pageMethodName | str | True | Name of the method constructing parent page

### Method pageMethodName

Gets the get method name that forms the page under which this task resides

```xpp
public str pageMethodName ()
```

#### Return Value

The page method name that forms the page under which this task resides

### Method actionTitle

Gets the Action Title

```xpp
public str actionTitle ()
```

#### Return Value

The action title

### Method actionDescription

Gets the Action Description

```xpp
public str actionDescription ()
```

#### Return Value

The page description

### Method crudOperationType

Gets the Crud Operation Type like Create, Update, Delete

```xpp
public SysAppCRUDOperation crudOperationType ()
```

#### Return Value

The Crud Operation Type like Create, Update, Delete

## Class SysAppActionMetadata

This class can be used to access and update AX mobile workspace action metadata

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void |  |
| getActionName | str | Returns the action name |
| actionTitle | str | Gets or sets the action title |
| actionDescription | str | Gets or sets the action description |
| actionHidden | boolean | Gets or sets whether action is hidden |
| actionOrder | int | Gets or sets the action order |
| getControl | SysAppControlMetadata | Returns the control on the current action having the provided control name |
| getControlEnumerator | MapEnumerator | Returns a map enumerator that can be used to enumerate action controls.  Where Key is control name and value is of type SysAppControlMetadata |

### Method new

```xpp
public void new (Microsoft.Dynamics.Client.ServerForm.App.TaskMetadata _taskmetadata)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _taskmetadata | Microsoft.Dynamics.Client.ServerForm.App.TaskMetadata | False |

### Method getActionName

Returns the action name

```xpp
public str getActionName ()
```

#### Return Value

The action name

### Method actionTitle

Gets or sets the action title

```xpp
public str actionTitle ([str _actionTitle])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _actionTitle | str | True | The action title

#### Return Value

The action title

### Method actionDescription

Gets or sets the action description

```xpp
public str actionDescription ([str _actionDescription])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _actionDescription | str | True | The action description

#### Return Value

The action description

### Method actionHidden

Gets or sets whether action is hidden

```xpp
public boolean actionHidden ([boolean _actionHidden])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _actionHidden | boolean | True | Action hidden value

#### Return Value

True if the action is hidden; otherwise false

### Method actionOrder

Gets or sets the action order

```xpp
public int actionOrder ([int _actionOrder])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _actionOrder | int | True | The action order

#### Return Value

The action order

### Method getControl

Returns the control on the current action having the provided control name

```xpp
public SysAppControlMetadata getControl (str _controlName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _controlName | str | False | The control name that will be used to search for control

#### Return Value

An object of SysAppControlMetadata is returned if a control with the provided control name exist on the action; otherwise null

### Method getControlEnumerator

Returns a map enumerator that can be used to enumerate action controls.  Where Key is control name and value is of type SysAppControlMetadata

```xpp
public MapEnumerator getControlEnumerator ()
```

#### Return Value

A map enumerator

## Class SysAppAttributeHelper

SysAppAttributeHelper class for fetching attributes from all the extended class

### Methods

| Method name | Returns | Description |
|---|---|---|
| getAttributeFromClass | SysAttribute | gets attribute from class |

### Method getAttributeFromClass

gets attribute from class

```xpp
public SysAttribute getAttributeFromClass (SysDictClass _sysClass, SysAppAttributeType _attributeType)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _sysClass | SysDictClass | False | class for which attributes is required
| _attributeType | SysAppAttributeType | False | Type of attribute like SysAppEntityAttribute

## Class SysAppCollectionAttribute

SysAppCollectionAttribute used for decorating methods forming list control

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Constructor |

### Method new

Constructor

```xpp
public void new (str _itemContractName, [str _label], [str _relationshipName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|
| _itemContractName | str | False | Data contract name of list item
| _label | str | True | List control label
| _relationshipName | str | True | Relationship name. By default the entity name of the list item is used as relationship name

## Class SysAppControlMetadata

Represents an X++ wrapper over the managed ControlMetadata object to facilitate.  passing around the object as X++ object

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of the control metadata |
| getBaseLanguageId | str | Returns the base language ID for the app |
| getControlName | str | Returns the control name |
| controlLabel | str | Gets and sets the control label |
| controlHidden | boolean | Gets and sets whether the control is hidden |
| controlOrder | int | Gets or sets the control order |
| controlMandatory | boolean | Gets or sets the control mandatory |
| controlAllowNegative | boolean | Gets or sets the control allow negative |
| controlMaxLength | int | Gets or sets the control max length |
| getProperty | `anytype` | Gets the control property referenced by the key |
| setProperty | void | Sets the control property referenced by the key |

### Method new

Creates a new instance of the control metadata

```xpp
public void new (Microsoft.Dynamics.Client.ServerForm.App.ControlMetadata _controlMetadata, [str _baseLanguageId])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlMetadata | Microsoft.Dynamics.Client.ServerForm.App.ControlMetadata | False | The controlMetadata object
| _baseLanguageId | str | True | The base language

### Method getBaseLanguageId

Returns the base language ID for the app

```xpp
public str getBaseLanguageId ()
```

#### Return Value

The base language ID

### Method getControlName

Returns the control name

```xpp
public str getControlName ()
```

#### Return Value

The control name

### Method controlLabel

Gets and sets the control label

```xpp
public str controlLabel ([str _controlLabel])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlLabel | str | True | The control label

#### Return Value

The control label

### Method controlHidden

Gets and sets whether the control is hidden

```xpp
public boolean controlHidden ([boolean _controlHidden])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlHidden | boolean | True | Control hidden value

#### Return Value

True if the control is hidden; otherwise false

### Method controlOrder

Gets or sets the control order

```xpp
public int controlOrder ([int _controlOrder])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlOrder | int | True | The control order

#### Return Value

The control order

### Method controlMandatory

Gets or sets the control mandatory

```xpp
public boolean controlMandatory ([boolean _controlMandatory])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlMandatory | boolean | True | The control mandatory

#### Return Value

The control mandatory

### Method controlAllowNegative

Gets or sets the control allow negative

```xpp
public boolean controlAllowNegative ([boolean _controlAllowNegative])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlAllowNegative | boolean | True | The control allows negative

#### Return Value

The control allows negative

### Method controlMaxLength

Gets or sets the control max length

```xpp
public int controlMaxLength ([int _controlMaxLength])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlMaxLength | int | True | The control max length

#### Return Value

The control max length

### Method getProperty

Gets the control property referenced by the key

```xpp
public anytype getProperty (str _key)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _key | str | False | The name of the control property

#### Return Value

The property value

### Method setProperty

Sets the control property referenced by the key

```xpp
public void setProperty (str _key, anytype _value)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _key | str | False | The name of the control property
| _value | anytype | False | The value of the control property

## Class SysAppEntityAttribute

SysAppEntityAttribute used for decorating data contract entities

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Constructor |
| name | str | Gets the name of the entity |
| entityKey | str | Gets the entity key |

### Method new

Constructor

```xpp
public void new (str _name, str _entityKey)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _name | str | False | Entity name
| _entityKey | str | False | Name of the entity's key

### Method name

Gets the name of the entity

```xpp
public str name ()
```

#### Return Value

Name of the entity

### Method entityKey

Gets the entity key

```xpp
public str entityKey ()
```

#### Return Value

Entity key

## Class SysAppEntityContext

SysAppEntityContext used for defining entity context

### Methods

| Method name | Returns | Description |
|---|---|---|
| constructFromParams | SysAppEntityContext | Constructs SysAppEntityContext from entityName and entityId |
| constructFromBuffer | SysAppEntityContext | Constructs SysAppEntityContext from table buffer |
| entityName | str | Entity name on which filter applies |
| entityId | str | Field value on which filter applies |

### Method constructFromParams

Constructs SysAppEntityContext from entityName and entityId

```xpp
public SysAppEntityContext constructFromParams (str _entityName, str _entityId)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityName | str | False | Entity name
| _entityId | str | False | Entity value

#### Return Value

Instance of SysAppEntityContext

### Method constructFromBuffer

Constructs SysAppEntityContext from table buffer

```xpp
public SysAppEntityContext constructFromBuffer (Common _tableBuffer)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _tableBuffer | Common | False | table buffer forming the entity

#### Return Value

Instance of SysAppEntityContext

### Method entityName

Entity name on which filter applies

```xpp
public str entityName ([str _entityName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityName | str | True | Entity name

#### Return Value

Entity name

### Method entityId

Field value on which filter applies

```xpp
public str entityId ([str _entityId])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityId | str | True | Entity value

#### Return Value

Entity value

## Class SysAppFieldAttribute

SysAppFieldAttribute used for decorating methods forming bound fields

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppFieldAttribute class |

### Method new

Creates a new instance of SysAppFieldAttribute class

```xpp
public void new (str _fieldName, str _label)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _fieldName | str | False | Entity field name with which control is bound
| _label | str | False | Control label

## Class SysAppFieldMultiSelectHelper

A helper class to provide helper methods for multi select scenarios used with D365 mobile app

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppFieldMultiSelectHelper class |
| getSelectedRecIds | container | Returns a container of recIds of the records that were selected |
| getSelectedValues | container | Returns a container of selected values |
| getSelectedRecords | Common | Returns a buffer that contains all the selected records..  The buffer is marked as temp..  Later a while-Select can be used to iterate through all the records |
| setControlValue | void | A setter to set the multiselect control value |

### Method new

Creates a new instance of SysAppFieldMultiSelectHelper class

```xpp
public void new (TableId _multiSelectTableId, FieldId _valueFieldId, FormStringControl _multiSelectControl)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _multiSelectTableId | TableId | False | The backing tableId for the field
| _valueFieldId | FieldId | False | The fieldId for the field that will be shown in the multi select control
| _multiSelectControl | FormStringControl | False | The string control that will be the multi select control

### Method getSelectedRecIds

Returns a container of recIds of the records that were selected

```xpp
public container getSelectedRecIds ()
```

#### Return Value

A container of recOds for the records that were selected

### Method getSelectedValues

Returns a container of selected values

```xpp
public container getSelectedValues ()
```

#### Return Value

A container of selected values

### Method getSelectedRecords

Returns a buffer that contains all the selected records..  The buffer is marked as temp..  Later a while-Select can be used to iterate through all the records

```xpp
public Common getSelectedRecords ()
```

#### Return Value

A buffer containing all the selected records

### Method setControlValue

A setter to set the multi select control value

```xpp
public void setControlValue (str _value)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _value | str | False | A colon separated value that will be used by SysAppFieldMultiSelectHelper

## Class SysAppFilterContext

SysAppFilterContext class that holds context values

### Methods

| Method name | Returns | Description |
|---|---|---|
| entityName | str | Entity name on which filter applies |
| filterFieldName | str | Field name on which filter applies |
| filterFieldValueList | List | Gets the list of filter field values based on which filter happens |
| operator | str | Operator based on which result will be fetched |
| addFilterFieldValue | void | Adds filter field value |

### Method entityName

Entity name on which filter applies

```xpp
public str entityName ([str _entityName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityName | str | True | Entity name on which filter applies

#### Return Value

Entity name on which filter applies

### Method filterFieldName

Field name on which filter applies

```xpp
public str filterFieldName ([str _filterFieldName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _filterFieldName | str | True | Field name on which filter applies

#### Return Value

Field name on which filter applies

### Method filterFieldValueList

Gets the list of filter field values based on which filter happens

```xpp
public List filterFieldValueList ()
```

#### Return Value

List of filter field values based on which filter happens

### Method operator

Operator based on which result will be fetched

```xpp
public str operator ([str _operator])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _operator | str | True | Operator based on which result will be fetched

#### Return Value

Operator based on which result will be fetched

### Method addFilterFieldValue

Adds filter field value

```xpp
public void addFilterFieldValue ( _filterFieldValueList)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _filterFieldValueList |  | False | Filter field values based on which filter happens

## Class SysAppLookUpAttribute

SysAppPageAttribute used for decorating pages that are also lookup pages

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppLookUpAttribute class |
| displayFieldName | str | Gets the display field name of lookup control |
| valueFieldName | str | Gets the value field name of lookup control |

### Method new

Creates a new instance of SysAppLookUpAttribute class

```xpp
public void new (str _displayFieldName, str _valueFieldName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _displayFieldName | str | False | Lookup display field. Name of any control of lookup page
| _valueFieldName | str | False | Lookup value field. Name of control formed by root data contract constructing lookup page

### Method displayFieldName

Gets the display field name of lookup control

```xpp
public str displayFieldName ()
```

#### Return Value

The display field name of lookup control

### Method valueFieldName

Gets the value field name of lookup control

```xpp
public str valueFieldName ()
```

#### Return Value

The value field name of lookup control

## Class SysAppLookupFieldAttribute

SysAppLookupFieldAttribute used for decorating look up fields of action

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppLookupFieldAttribute class |
| entityName | str | Gets the name of the entity with which lookup page is related |

### Method new

Creates a new instance of SysAppLookupFieldAttribute class

```xpp
public void new ( _name)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _name |  | False | Name of the entity with which lookup page is related

### Method entityName

Gets the name of the entity with which lookup page is related

```xpp
public str entityName ()
```

#### Return Value

Name of the entity

## Class SysAppPageAttribute

SysAppPageAttribute used for decorating methods defining page of workspace

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppPageAttribute class |
| pageTitle | str | Gets the Page Title of the page |
| pageDescription | str | Gets the Page Description |

### Method new

Creates a new instance of SysAppPageAttribute class

```xpp
public void new ([str _pageTitle], [str _pageDescription])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageTitle | str | True | The page title
| _pageDescription | str | True | The page description

### Method pageTitle

Gets the Page Title of the page

```xpp
public str pageTitle ()
```

#### Return Value

The page title

### Method pageDescription

Gets the Page Description

```xpp
public str pageDescription ()
```

#### Return Value

The page description

## Class SysAppPageMetadata

This class can be used to access and update AX mobile workspace page metadata

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void |  |
| getPageName | str | Returns the page name |
| pageTitle | str | Gets and sets the page title |
| pageDescription | str | Gets or sets the page description |
| pageHidden | boolean | Gets and sets whether the page is hidden in the workspace |
| pageOrder | int | Gets or sets the page order |
| getControl | SysAppControlMetadata | Returns the control on the current page having the provided control name |
| getControlEnumerator | MapEnumerator | Returns a map enumerator that can be used to enumerate page controls.  Where Key is control name and value is of type SysAppControlMetadata |

### Method new

```xpp
public void new (Microsoft.Dynamics.Client.ServerForm.App.PageMetadata _pageMetadata)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageMetadata | Microsoft.Dynamics.Client.ServerForm.App.PageMetadata | False |

### Method getPageName

Returns the page name

```xpp
public str getPageName ()
```

#### Return Value

The page name

### Method pageTitle

Gets and sets the page title

```xpp
public str pageTitle ([str _pageTitle])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageTitle | str | True | The page title

#### Return Value

The page title

### Method pageDescription

Gets or sets the page description

```xpp
public str pageDescription ([str _pageDescription])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageDescription | str | True | The page description

#### Return Value

The page description>

### Method pageHidden

Gets and sets whether the page is hidden in the workspace

```xpp
public boolean pageHidden ([boolean _pageHidden])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageHidden | boolean | True | page hidden value

#### Return Value

True if the current page is hidden in workspace; otherwise false

### Method pageOrder

Gets or sets the page order

```xpp
public int pageOrder ([int _pageOrder])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageOrder | int | True | The page order

#### Return Value

The page order

### Method getControl

Returns the control on the current page having the provided control name

```xpp
public SysAppControlMetadata getControl (str _controlName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _controlName | str | False | The control name that will be used to search for control

#### Return Value

An object of SysAppControlMetadata is returned if a control with the provided control name exist on the page; otherwise null

### Method getControlEnumerator

Returns a map enumerator that can be used to enumerate page controls.  Where Key is control name and value is of type SysAppControlMetadata

```xpp
public MapEnumerator getControlEnumerator ()
```

#### Return Value

A map enumerator

## Class SysAppProjectionAttribute

SysAppProjectionAttribute used for decorating methods forming unbound fields

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppControlMetadataAttributes class |

### Method new

Creates a new instance of SysAppControlMetadataAttributes class

```xpp
public void new (str _label)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _label | str | False | Control label

## Class SysAppRelationalAttribute

SysAppRelationalAttribute used for decorating reference controls

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Constructor |

### Method new

Constructor

```xpp
public void new ([str _name])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _name | str | True | Property name of the referenced entity

## Class SysAppRequestParams

Request class for X++ methods generating details and action pages

### Methods

| Method name | Returns | Description |
|---|---|---|
| entityContext | SysAppEntityContext | Entity context of the request |
| filterContext | List | List of SysAppFilterContext for filter contexts |

### Method entityContext

Entity context of the request

```xpp
public SysAppEntityContext entityContext ([SysAppEntityContext _entityContext])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityContext | SysAppEntityContext | True | Entity context of the request

#### Return Value

Entity context of the request

### Method filterContext

List of SysAppFilterContext for filter contexts

```xpp
public List filterContext ([List _filterContext])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _filterContext | List | True | List of SysAppFilterContext for filter contexts of page

#### Return Value

List of SysAppFilterContext for filter contexts of page

## Class SysAppResponse

SysAppResponse class.  This class holds the response object for generated pages and actions

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void |  |
| jobId | str | Job ID of the request |
| data | Microsoft.Dynamics.Client.ServerForm.App.CompositeData | Data of the page |
| failedInAppCall | boolean | Data of the page |
| commits | List | Commits after task is completed |
| messages | List | Job ID of the request |
| addMessage | void | Adds message |
| addCommit | void | Adds commits |

### Method new

```xpp
public void new ()
```

### Method jobId

Job ID of the request

```xpp
public str jobId ()
```

#### Return Value

jobid of the request

### Method data

Data of the page

```xpp
public Microsoft.Dynamics.Client.ServerForm.App.CompositeData data ([Microsoft.Dynamics.Client.ServerForm.App.CompositeData _data])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _data | Microsoft.Dynamics.Client.ServerForm.App.CompositeData | True | Data of the page

#### Return Value

Data of the page

### Method failedInAppCall

Data of the page

```xpp
public boolean failedInAppCall ([boolean _failedInAppCall])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _failedInAppCall | boolean | True | Sets to true if it fails in calling application code

#### Return Value

True when fails in calling application code

### Method commits

Commits after task is completed

```xpp
public List commits ()
```

#### Return Value

Commits after task is completed

### Method messages

Job ID of the request

```xpp
public List messages ()
```

#### Return Value

Messages after task is completed

### Method addMessage

Adds message

```xpp
public void addMessage (SysAppResponseMessage _message)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _message | SysAppResponseMessage | False | message as SysAppResponseMessage object

### Method addCommit

Adds commits

```xpp
public void addCommit (SysAppEntityContext _entityContext)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _entityContext | SysAppEntityContext | False | Entity context containing entity name and entity ID of the entity that is committed

## Class SysAppResponseMessage

SysAppResponseMessage class for response messages

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppResponseMessage class |
| text | str | Gets the message text |
| type | SysAppMessageType | Gets the message type: info, error, warning |

### Method new

Creates a new instance of SysAppResponseMessage class

```xpp
public void new (str _text, [SysAppMessageType _type])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _text | str | False | The message text
| _type | SysAppMessageType | True | Message Type: info, error, warning

### Method text

Gets the message text

```xpp
public str text ()
```

#### Return Value

The message text

### Method type

Gets the message type: info, error, warning

```xpp
public SysAppMessageType type ()
```

#### Return Value

The message type: info, error, warning

## Class SysAppSecurityAttribute

SysAppSecurityAttribute used for decorating methods forming pages and actions.  specifies security attribute of page or action

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppSecurityAttribute class.  This will help in checking if the user logged in has access to the specified menu item and menu item type |
| menuItemType | MenuItemType | Gets the Menu Item Type of the page |
| menuItemName | MenuItemName | Gets the Menu Item Name of the page |

### Method new

Creates a new instance of SysAppSecurityAttribute class.  This will help in checking if the user logged in has access to the specified menu item and menu item type

```xpp
public void new ([MenuItemName _menuItemName], [MenuItemType _menuItemType])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _menuItemName | MenuItemName | True | Menu Item Name of the page
| _menuItemType | MenuItemType | True | Menu Item Type of the page like action, display, or output

### Method menuItemType

Gets the Menu Item Type of the page

```xpp
public MenuItemType menuItemType ()
```

#### Return Value

Menu Item Type of the page

### Method menuItemName

Gets the Menu Item Name of the page

```xpp
public MenuItemName menuItemName ()
```

#### Return Value

Menu Item Name of the page

## Class SysAppWorkspace

This is the base class of mobile workspace. Mobile workspace classes need to extend from this class

### Methods

| Method name | Returns | Description |
|---|---|---|
| getEnumValues | List | Called during workspace initialization. Can be used to modify the enum values that are returned to AX mobile |
| getWorkspaceMetadata | SysAppWorkspaceMetadata | Called during workspace initialization. Can be used to modify the workspace metadata |
| onBeginAppJob | void | Called before the start of execution of AX mobile job |
| onEndAppJob | void | Called after the end of execution of AX mobile job |
| workspaceHidden | boolean | Can be used to control whether the workspace is hidden or not.  Checks that the current user has access menu item specified by SysAppWorkspaceSecurityAttribute on the workspace class.  If the attribute is not specified on the class then it always returns false |

### Method getEnumValues

Called during workspace initialization. Can be used to modify the enum values that are returned to AX mobile

```xpp
public List getEnumValues (EnumName _enumName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _enumName | EnumName | False | The enum name

#### Return Value

A list of enum value

### Method getWorkspaceMetadata

Called during workspace initialization. Can be used to modify the workspace metadata

```xpp
public SysAppWorkspaceMetadata getWorkspaceMetadata ()
```

#### Return Value

An object representing the workspace metadata

### Method onBeginAppJob

Called before the start of execution of AX mobile job

```xpp
public void onBeginAppJob (SysAppJobRequest _sysAppJobRequest)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _sysAppJobRequest | SysAppJobRequest | False | A class containing job request parameters

### Method onEndAppJob

Called after the end of execution of AX mobile job

```xpp
public void onEndAppJob (SysAppJobResponse _sysAppJobResponse)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _sysAppJobResponse | SysAppJobResponse | False | A class containing job response parameters

### Method workspaceHidden

Can be used to control whether the workspace is hidden or not.  Checks that the current user has access menu item specified by SysAppWorkspaceSecurityAttribute on the workspace class.  If the attribute is not specified on the class then it always returns false

```xpp
public boolean workspaceHidden ()
```

#### Return Value

Returns true if the workspace is hidden otherwise false

## Class SysAppWorkspaceAttribute

Applied on classes that are extended from SysAppWorkspace

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of SysAppWorkspaceAttribute class |
| AppId | str | Gets or sets the AppId of the workspace |
| AppResourceName | str | Gets or sets the AOT Resource name that contains the workspace |
| WorkspaceHidden | boolean | Gets or sets if the workspace is hidden from designer |

### Method new

Creates a new instance of SysAppWorkspaceAttribute class

```xpp
public void new (str _appId, [str _appResourceName], [boolean _workspaceHidden])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _appId | str | False | The appId of the workspace
| _appResourceName | str | True | The AOT resource name that contains the workspace
| _workspaceHidden | boolean | True | The workspace is hidden from designer

### Method AppId

Gets or sets the AppId of the workspace

```xpp
public str AppId ([str _appId])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _appId | str | True | The AppId of the workspace

#### Return Value

The AppId of the workspace

### Method AppResourceName

Gets or sets the AOT Resource name that contains the workspace

```xpp
public str AppResourceName ([str _appResourceName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _appResourceName | str | True | The AOT Resource name that contains the workspace

#### Return Value

The AOT Resource name that contains the workspace

### Method WorkspaceHidden

Gets or sets if the workspace is hidden from designer

```xpp
public boolean WorkspaceHidden ([boolean _workspaceHidden])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceHidden | boolean | True | The workspace hidden

#### Return Value

Whether the workspace is hidden from designer or not

## Class SysAppWorkspaceMetadata

This class can be used to access and update metadata of an AX mobile workspace

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void |  |
| addConfig | void | Adds a custom config to the mobile workspace metadata |
| getPage | SysAppPageMetadata | Returns the page with the pageName provided |
| getPageEnumerator | MapEnumerator | Returns a map enumerator that can be used to enumerate workspace pages.  Where key is page name and value is of type SysAppPageMetadata |
| getAction | SysAppActionMetadata | Returns the action with the actionName provided |
| getActionEnumerator | MapEnumerator | Returns a map enumerator that can be used to enumerate workspace actions.  Where key is action name and value is of type SysAppActionMetadata |
| getPageNameForRecordingId | str | Returns a pageName if the provided recordingId is used by a workspace page |
| getActionNameForRecordingId | str | Returns a actionName if the provided recordingId is used by a workspace action |
| workspaceTitle | str | Gets and sets the workspace title |
| workspaceDescription | str | Gets and sets the workspace description |

### Method new

```xpp
public void new (str _appId, [SysAppWorkspaceAttribute _attribute])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _appId | str | False |
| _attribute | SysAppWorkspaceAttribute | True |

### Method addConfig

Adds a custom config to the mobile workspace metadata

```xpp
public void addConfig (str _configName, object _configValue)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _configName | str | False | A config name
| _configValue | object | False | An object of an X++ data contract class

### Method getPage

Returns the page with the pageName provided

```xpp
public SysAppPageMetadata getPage (str _pageName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _pageName | str | False | A page name

#### Return Value

Returns the pageMetadata if a page with the provided name exists; otherwise null

### Method getPageEnumerator

Returns a map enumerator that can be used to enumerate workspace pages.  Where key is page name and value is of type SysAppPageMetadata

```xpp
public MapEnumerator getPageEnumerator ()
```

#### Return Value

A map enumerator

### Method getAction

Returns the action with the actionName provided

```xpp
public SysAppActionMetadata getAction (str _actionName)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _actionName | str | False | An action name

#### Return Value

Returns the ActionMetadata if an action with the provided name exists; otherwise null

### Method getActionEnumerator

Returns a map enumerator that can be used to enumerate workspace actions.  Where key is action name and value is of type SysAppActionMetadata

```xpp
public MapEnumerator getActionEnumerator ()
```

#### Return Value

A map enumerator

### Method getPageNameForRecordingId

Returns a pageName if the provided recordingId is used by a workspace page

```xpp
public str getPageNameForRecordingId (str _recordingId)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _recordingId | str | False | A recordingId

#### Return Value

A page name if the supplied recordingId is used by a workspace page; otherwise empty string

### Method getActionNameForRecordingId

Returns a actionName if the provided recordingId is used by a workspace action

```xpp
public str getActionNameForRecordingId (str _recordingId)
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _recordingId | str | False | A recordingId

#### Return Value

An action name if the supplied recordingId is used by a workspace action; otherwise empty string

### Method workspaceTitle

Gets and sets the workspace title

```xpp
public str workspaceTitle ([str _workspaceTitle])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceTitle | str | True | The workspace title

#### Return Value

The workspace title

### Method workspaceDescription

Gets and sets the workspace description

```xpp
public str workspaceDescription ([str _workspaceDescription])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceDescription | str | True | The workspace description

#### Return Value

The workspace description

## Class SysAppWorkspaceSecurityAttribute

Controls the visibility based of workspace based on the menu item tied to this attribute

### Methods

| Method name | Returns | Description |
|---|---|---|
| new | void | Creates a new instance of attribute |
| WorkspaceMenuItemName | MenuItemName | Gets or sets the workspace menuItem for the workspace security attribute |
| WorkspaceMenuItemType | MenuItemType | Gets or sets the workspace menu item type for the workspace security attribute |

### Method new

Creates a new instance of attribute

```xpp
public void new (MenuItemName _workspaceMenuItemName, [MenuItemType _workspaceMenuItemType])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceMenuItemName | MenuItemName | False | The menu item name to which the workspace needs to be tied
| _workspaceMenuItemType | MenuItemType | True | The menu item type

### Method WorkspaceMenuItemName

Gets or sets the workspace menuItem for the workspace security attribute

```xpp
public MenuItemName WorkspaceMenuItemName ([MenuItemName _workspaceMenuItemName])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceMenuItemName | MenuItemName | True | The workspace menu item for the workspace security attribute

#### Return Value

The workspace menu item for the workspace security attribute

### Method WorkspaceMenuItemType

Gets or sets the workspace menu item type for the workspace security attribute

```xpp
public MenuItemType WorkspaceMenuItemType ([MenuItemType _workspaceMenuItemType])
```

#### Parameters

| Parameter name |  Parameter type | Optional | Description |
|---|---|---|---|
| _workspaceMenuItemType | MenuItemType | True | The workspace menu item type for the `workspacesecurity` attribute

#### Return Value

The workspace menu item type for the workspace security attribute


[!INCLUDE[footer-include](../../../../includes/footer-banner.md)]