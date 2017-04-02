---
# required metadata

title: S Classes
description: System API classes that start with the letter S.
author: RobinARH
manager: AnnBe
ms date: 2017-04-04
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
ms.custom: 51751
ms.assetid: cb7c0fd3-34ec-407b-ad78-1007a67d70d5
ms.search.region: Global
# ms.search.industry: 
ms.author: robinr
ms.search.validFrom: 2016-02-28
ms.dyn365.ops.version: AX 7.0.0

---

# S Classes

System API classes that start with the letter S.

Class ScannerClass
------------------

    class ScannerClass extends Object

### Remarks

### Examples

### Methods

| Method                                                                                       | Description                                     |
|----------------------------------------------------------------------------------------------|-------------------------------------------------|
| public int col()                                                                             |                                                 |
| public Date dateValue()                                                                      |                                                 |
| public int firstSymbol()                                                                     |                                                 |
| public Int64 int64Value()                                                                    |                                                 |
| public int intValue()                                                                        |                                                 |
| public int line()                                                                            |                                                 |
| public int nextSymbol()                                                                      |                                                 |
| public Real realValue()                                                                      |                                                 |
| public int startColumn()                                                                     |                                                 |
| public str string()                                                                          |                                                 |
| public str strValue()                                                                        |                                                 |
| public void localMacroDefine(str text, int startLine, int startPos, int endLine, int endPos) |                                                 |
| public void lineComment(str text, int startLine, int startPos, int endLine, int endPos)      |                                                 |
| public void macroDefine(str text, int startLine, int startPos, int endLine, int endPos)      |                                                 |
| public void new(str source)                                                                  | Initializes a new instance of the Object class. |
| public void comment(str text, int startLine, int startPos, int endLine, int endPos)          |                                                 |

### Method col

    public int col()

#### Return Value

### Method dateValue

    public Date dateValue()

#### Return Value

### Method firstSymbol

    public int firstSymbol()

#### Return Value

### Method int64Value

    public Int64 int64Value()

#### Return Value

### Method intValue

    public int intValue()

#### Return Value

### Method line

    public int line()

#### Return Value

### Method nextSymbol

    public int nextSymbol()

#### Return Value

### Method realValue

    public Real realValue()

#### Return Value

### Method startColumn

    public int startColumn()

#### Return Value

### Method string

    public str string()

#### Return Value

### Method strValue

    public str strValue()

#### Return Value

### Method localMacroDefine

    public void localMacroDefine(str text, int startLine, int startPos, int endLine, int endPos)

#### Parameters

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

### Method lineComment

    public void lineComment(str text, int startLine, int startPos, int endLine, int endPos)

#### Parameters

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

### Method macroDefine

    public void macroDefine(str text, int startLine, int startPos, int endLine, int endPos)

#### Parameters

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

### Method new

Initializes a new instance of the Object class.

    public void new(str source)

#### Parameters

source  

### Method comment

    public void comment(str text, int startLine, int startPos, int endLine, int endPos)

#### Parameters

text  

<!-- -->

startLine  

<!-- -->

startPos  

<!-- -->

endLine  

<!-- -->

endPos  

## Class SearchParm
    class SearchParm extends Object

The SearchParm class serves as an interface between the kernel and the sysTreeSearch class, and enables searches in the Microsoft Dynamics 365 for Operations5 for Operations Application Object Tree (AOT).

### Remarks

### Examples

### Methods

| Method                                          | Description |
|-------------------------------------------------|-------------|
| public str nodeName(\[str name\])               |             |
| public int nodeType(\[int type\])               |             |
| public str nodeTypeArray()                      |             |
| public str propertyName(\[str name\])           |             |
| public str propertyValue(\[str value\])         |             |
| public str replaceString(\[str replaceString\]) |             |
| public int searchFlag(\[int flag\])             |             |
| public str searchString(\[str searchString\])   |             |
| public int searchType(\[int type\])             |             |
| public boolean startSearch()                    |             |
| public TreeNode topNode(\[TreeNode node\])      |             |
| public str topNodeName(\[str name\])            |             |
| public int topNodeType(\[int type\])            |             |
| public void preSearch()                         |             |
| public void killSearch()                        |             |

### Method nodeName

    public str nodeName([str name])

#### Parameters

name  

#### Return Value

### Method nodeType

    public int nodeType([int type])

#### Parameters

type  

#### Return Value

### Method nodeTypeArray

    public str nodeTypeArray()

#### Return Value

### Method propertyName

    public str propertyName([str name])

#### Parameters

name  

#### Return Value

### Method propertyValue

    public str propertyValue([str value])

#### Parameters

value  

#### Return Value

### Method replaceString

    public str replaceString([str replaceString])

#### Parameters

replaceString  

#### Return Value

### Method searchFlag

    public int searchFlag([int flag])

#### Parameters

flag  

#### Return Value

### Method searchString

    public str searchString([str searchString])

#### Parameters

searchString  

#### Return Value

### Method searchType

    public int searchType([int type])

#### Parameters

type  

#### Return Value

### Method startSearch

    public boolean startSearch()

#### Return Value

### Method topNode

    public TreeNode topNode([TreeNode node])

#### Parameters

node  

#### Return Value

### Method topNodeName

    public str topNodeName([str name])

#### Parameters

name  

#### Return Value

### Method topNodeType

    public int topNodeType([int type])

#### Parameters

type  

#### Return Value

### Method preSearch

    public void preSearch()

### Method killSearch

    public void killSearch()

## Class SecureNode
    class SecureNode extends TreeNode

The SecureNode class lets you create, read, update, and delete X++ code and metadata.

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                                                          | Description                                                             |
|---------------------------------------------------------------------------------|-------------------------------------------------------------------------|
| public boolean checkAccessRights()                                              |                                                                         |
| public ConfigurationKeyId configurationKey(\[ConfigurationKeyId value\])        | Gets or sets the configuration key that is assigned to the control.     |
| public ConfigurationKeyId countryConfigurationkey(\[ConfigurationKeyId value\]) |                                                                         |
| public boolean extendedDataSecurity(\[boolean value\])                          |                                                                         |
| public boolean isWeb()                                                          |                                                                         |
| public int neededAccessLevel(\[int value\])                                     | Gets or sets the neededAccessLevel property for the MenuFunction class. |
| public SecurityKeyId securityKey(\[SecurityKeyId value\])                       |                                                                         |
| public ConfigurationKeyId webConfigurationkey(\[ConfigurationKeyId value\])     |                                                                         |

### Method checkAccessRights

    public boolean checkAccessRights()

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

### Method countryConfigurationkey

    public ConfigurationKeyId countryConfigurationkey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

### Method extendedDataSecurity

    public boolean extendedDataSecurity([boolean value])

#### Parameters

value  

#### Return Value

### Method isWeb

    public boolean isWeb()

#### Return Value

### Method neededAccessLevel

Gets or sets the neededAccessLevel property for the MenuFunction class.

    public int neededAccessLevel([int value])

#### Parameters

value  

#### Return Value

The current value of the neededAccessLevel property.

#### Remarks

The possible values for the AccessType system enumuration value are as follows:

-   AccessType::NoAccess.
-   AccessType::View.
-   AccessType::Edit.
-   AccessType::Add.
-   AccessType::Delete.

### Method securityKey

    public SecurityKeyId securityKey([SecurityKeyId value])

#### Parameters

value  

#### Return Value

### Method webConfigurationkey

    public ConfigurationKeyId webConfigurationkey([ConfigurationKeyId value])

#### Parameters

value  

#### Return Value

## Class SecurityContext
    class SecurityContext extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                | Description |
|-------------------------------------------------------------------------------------------------------|-------------|
| public boolean isTableOperationAllowed(int tableId, StatementType operation, \[DataAreaId dataArea\]) |             |
| ::public static SecurityContext current()                                                             |             |
| ::public static SecurityContext constructFromEntryPoint(SecurableType type, str name, str childName)  |             |
| public boolean equal(SecurityContext context)                                                         |             |
| public SecurableType securableType()                                                                  |             |
| public str securableName()                                                                            |             |
| public str securableChildName()                                                                       |             |
| public void push()                                                                                    |             |
| ::public static void pop()                                                                            |             |
| private void new()                                                                                    |             |

### Method isTableOperationAllowed

    public boolean isTableOperationAllowed(int tableId, StatementType operation, [DataAreaId dataArea])

#### Parameters

tableId  

<!-- -->

operation  

<!-- -->

dataArea  

#### Return Value

### Method current

    public static SecurityContext current()

#### Return Value

### Method constructFromEntryPoint

    public static SecurityContext constructFromEntryPoint(SecurableType type, str name, str childName)

#### Parameters

type  

<!-- -->

name  

<!-- -->

childName  

#### Return Value

### Method equal

    public boolean equal(SecurityContext context)

#### Parameters

context  

#### Return Value

### Method securableType

    public SecurableType securableType()

#### Return Value

### Method securableName

    public str securableName()

#### Return Value

### Method securableChildName

    public str securableChildName()

#### Return Value

### Method push

    public void push()

### Method pop

    public static void pop()

### Method new

    private void new()

## Class SecurityPolicy
    class SecurityPolicy extends Object

The SecurityPolicy class holds the information about the security policies.

### Remarks

### Examples

### Methods

| Method                                                                 | Description                                             |
|------------------------------------------------------------------------|---------------------------------------------------------|
| ::public static void synchronizeAllPolicies()                          |                                                         |
| ::public static void synchronizePolicy(UtilElementName securityPolicy) |                                                         |
| public void new()                                                      | Initializes a new instance of the SecurityPolicy class. |

### Method synchronizeAllPolicies

    public static void synchronizeAllPolicies()

### Method synchronizePolicy

    public static void synchronizePolicy(UtilElementName securityPolicy)

#### Parameters

securityPolicy  

### Method new

Initializes a new instance of the SecurityPolicy class.

    public void new()

## Class SecurityRights
    class SecurityRights extends Object

The SecurityRights class holds the information about the security rights and permissions management.

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                 | Description                                                            |
|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------|
| public boolean hasDataServiceAccess(SecurableName name, StatementType operation, \[SecurableChildName fieldName\])                                                                     |                                                                        |
| public boolean hasDataServiceMethodAccess(SecurableName name, StatementType operation, SecurableChildName methodName)                                                                  |                                                                        |
| public AccessRight dataManagementAccessRight(SecurableName dataEntityName, \[SecurableChildName fieldName\])                                                                           |                                                                        |
| public str listDataServiceAccess(SecurableName name, \[SecurableChildName context\])                                                                                                   |                                                                        |
| public AccessRight fieldAccessRight(TableName tableName, FieldName fieldName, \[Common record\], \[DataAreaId dataArea\], \[boolean includeDerived\], \[AutoAuthzMode autoAuthzMode\]) | Retrieves the access rights for the field of the table.                |
| public AccessRight formControlAccessRight(FormName form, UtilElementName control, \[Common record\], \[DataAreaId dataArea\])                                                          | Retrieves the access rights for the form control.                      |
| public container getSelectableCompanies()                                                                                                                                              |                                                                        |
| public boolean hasMenuAccess(MenuName menu, \[boolean isWebMenu\])                                                                                                                     | Checks whether the user has access to the specified menu.              |
| public boolean hasMenuItemAccess(SecurableType type, MenuItemName menuItem, \[Common record\], \[DataAreaId dataArea\])                                                                | Checks whether the user has access to the specified menu item.         |
| public boolean SysObsoleteAttribute(ClassName class, MethodName method)                                                                                                                |                                                                        |
| public boolean hasServiceOperationAccess(UtilElementName service, UtilElementName operation)                                                                                           | Checks whether the user has access to the specified service operation. |
| public boolean isDeveloper()                                                                                                                                                           |                                                                        |
| public boolean isSystemAdministrator()                                                                                                                                                 | Checks whether the current user is a system administrator.             |
| public AccessRight menuItemAccessRight(SecurableType type, MenuItemName menuItem, \[DataAreaId dataArea\])                                                                             | Retrieves the access rights for the menu item.                         |
| public AccessRight tableAccessRight(TableName tableName, \[Common record\], \[DataAreaId dataArea\], \[boolean includeDerived\], \[AutoAuthzMode autoAuthzMode\])                      | Retrieves the access rights for the table.                             |
| public SecurityTableRights tableFieldAccessRights(TableName tableName, \[Common record\], \[DataAreaId dataArea\], \[boolean includeDerived\], \[AutoAuthzMode autoAuthzMode\])        | Retrieves the field access rights for the table.                       |
| public Set variableAccessFields(TableName tableName, \[AccessRight targetAccess\], \[DataAreaId dataArea\])                                                                            | Retrieves a set of the table field IDs.                                |
| public AccessRight webContentAccessRight(SecurableType type, WebContentItemName name)                                                                                                  | Retrieves the access rights for the web content item.                  |
| ::public static SecurityRights construct()                                                                                                                                             | Creates a new security rights instance for the current user.           |
| ::public static SecurityRights newUser(UserId user)                                                                                                                                    | Creates a new security rights instance for the specified user.         |
| private void new()                                                                                                                                                                     | Initializes a new instance of the SecurityRights class.                |
| public void populateSelectableCompanies()                                                                                                                                              | Populates the selectable companies.                                    |

### Method hasDataServiceAccess

    public boolean hasDataServiceAccess(SecurableName name, StatementType operation, [SecurableChildName fieldName])

#### Parameters

name  

<!-- -->

operation  

<!-- -->

fieldName  

#### Return Value

### Method hasDataServiceMethodAccess

    public boolean hasDataServiceMethodAccess(SecurableName name, StatementType operation, SecurableChildName methodName)

#### Parameters

name  

<!-- -->

operation  

<!-- -->

methodName  

#### Return Value

### Method dataManagementAccessRight

    public AccessRight dataManagementAccessRight(SecurableName dataEntityName, [SecurableChildName fieldName])

#### Parameters

dataEntityName  

<!-- -->

fieldName  

#### Return Value

### Method listDataServiceAccess

    public str listDataServiceAccess(SecurableName name, [SecurableChildName context])

#### Parameters

name  

<!-- -->

context  

#### Return Value

### Method fieldAccessRight

Retrieves the access rights for the field of the table.

    public AccessRight fieldAccessRight(TableName tableName, FieldName fieldName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])

#### Parameters

tableName  

<!-- -->

fieldName  

<!-- -->

record  

<!-- -->

dataArea  

<!-- -->

includeDerived  

<!-- -->

autoAuthzMode  

#### Return Value

The AccesRight instance for the field of the table.

### Method formControlAccessRight

Retrieves the access rights for the form control.

    public AccessRight formControlAccessRight(FormName form, UtilElementName control, [Common record], [DataAreaId dataArea])

#### Parameters

form  

<!-- -->

control  

<!-- -->

record  

<!-- -->

dataArea  

#### Return Value

The AccesRight instance for the form control.

### Method getSelectableCompanies

    public container getSelectableCompanies()

#### Return Value

### Method hasMenuAccess

Checks whether the user has access to the specified menu.

    public boolean hasMenuAccess(MenuName menu, [boolean isWebMenu])

#### Parameters

menu  

<!-- -->

isWebMenu  

#### Return Value

true if the user has access to the menu; otherwise, false.

### Method hasMenuItemAccess

Checks whether the user has access to the specified menu item.

    public boolean hasMenuItemAccess(SecurableType type, MenuItemName menuItem, [Common record], [DataAreaId dataArea])

#### Parameters

type  

<!-- -->

menuItem  

<!-- -->

record  

<!-- -->

dataArea  

#### Return Value

true if the user has access to the menu item; otherwise, false.

### Method SysObsoleteAttribute

    public boolean SysObsoleteAttribute(ClassName class, MethodName method)

#### Parameters

class  

<!-- -->

method  

#### Return Value

### Method hasServiceOperationAccess

Checks whether the user has access to the specified service operation.

    public boolean hasServiceOperationAccess(UtilElementName service, UtilElementName operation)

#### Parameters

service  

<!-- -->

operation  

#### Return Value

true if user has access to the service operation; otherwise, false.

### Method isDeveloper

    public boolean isDeveloper()

#### Return Value

### Method isSystemAdministrator

Checks whether the current user is a system administrator.

    public boolean isSystemAdministrator()

#### Return Value

true if the current user is a system administrator; otherwise, false.

### Method menuItemAccessRight

Retrieves the access rights for the menu item.

    public AccessRight menuItemAccessRight(SecurableType type, MenuItemName menuItem, [DataAreaId dataArea])

#### Parameters

type  

<!-- -->

menuItem  

<!-- -->

dataArea  

#### Return Value

The AccesRight instance for the item.

### Method tableAccessRight

Retrieves the access rights for the table.

    public AccessRight tableAccessRight(TableName tableName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])

#### Parameters

tableName  

<!-- -->

record  

<!-- -->

dataArea  

<!-- -->

includeDerived  

<!-- -->

autoAuthzMode  

#### Return Value

The AccesRight instance for the table.

### Method tableFieldAccessRights

Retrieves the field access rights for the table.

    public SecurityTableRights tableFieldAccessRights(TableName tableName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])

#### Parameters

tableName  

<!-- -->

record  

<!-- -->

dataArea  

<!-- -->

includeDerived  

<!-- -->

autoAuthzMode  

#### Return Value

The SecurityTableRights instance for the table.

### Method variableAccessFields

Retrieves a set of the table field IDs.

    public Set variableAccessFields(TableName tableName, [AccessRight targetAccess], [DataAreaId dataArea])

#### Parameters

tableName  

<!-- -->

targetAccess  

<!-- -->

dataArea  

#### Return Value

A set of the table field IDs.

### Method webContentAccessRight

Retrieves the access rights for the web content item.

    public AccessRight webContentAccessRight(SecurableType type, WebContentItemName name)

#### Parameters

type  

<!-- -->

name  

#### Return Value

The AccesRight instance for the item.

### Method construct

Creates a new security rights instance for the current user.

    public static SecurityRights construct()

#### Return Value

The SecurityRights instance that was created.

### Method newUser

Creates a new security rights instance for the specified user.

    public static SecurityRights newUser(UserId user)

#### Parameters

user  

#### Return Value

The SecurityRights instance that was created.

### Method new

Initializes a new instance of the SecurityRights class.

    private void new()

### Method populateSelectableCompanies

Populates the selectable companies.

    public void populateSelectableCompanies()

## Class SecuritySkipFlush
    class SecuritySkipFlush extends Object

### Remarks

### Examples

### Methods

| Method              | Description                                                |
|---------------------|------------------------------------------------------------|
| public void clear() |                                                            |
| public void new()   | Initializes a new instance of the SecuritySkipFlush class. |
| public void set()   |                                                            |

### Method clear

    public void clear()

### Method new

Initializes a new instance of the SecuritySkipFlush class.

    public void new()

### Method set

    public void set()

## Class SecurityTableRights
    class SecurityTableRights extends Object

The SecurityTableRights class holds the information about the table security rights.

### Remarks

### Examples

### Methods

| Method                                                   | Description                                               |
|----------------------------------------------------------|-----------------------------------------------------------|
| public AccessRight fieldAccessRight(FieldName fieldName) | Gets the access rights for the field of the table.        |
| public AccessRight tableAccessRight()                    | Gets the access rights for the table.                     |
| private void new()                                       | Initializes an instance of the SecurityTableRights class. |

### Method fieldAccessRight

Gets the access rights for the field of the table.

    public AccessRight fieldAccessRight(FieldName fieldName)

#### Parameters

fieldName  

#### Return Value

The AccesRight instance for the field.

### Method tableAccessRight

Gets the access rights for the table.

    public AccessRight tableAccessRight()

#### Return Value

The AccesRight instance for the table.

### Method new

Initializes an instance of the SecurityTableRights class.

    private void new()

## Class SecurityUtil
    class SecurityUtil extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                 | Description                                                                |
|------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------|
| ::public static boolean isImplicitFlushMode()                                                                          | Indicates whether implicit security flushing mode is on.                   |
| ::public static int getRoleEffectiveAccess(Int64 roleID, str secObjectName, int secObjectType, str secObjectChildName) | Retrieves an effective access for role value of securable object.          |
| ::public static container getRolePermissions(Int64 roleID)                                                             | Gets a container of securable objects and their effective access.          |
| ::public static boolean sysAdminMode(\[boolean active\])                                                               | Gets and sets the security administrator mode.                             |
| ::public static void refreshRolePermissions(Int64 roleID)                                                              | Retrieves the effective access of a specified role for a securable object. |
| ::public static void runSecondPassAutoInference()                                                                      | Runs the second pass auto inference.                                       |
| ::public static void flushPermissions()                                                                                | Flushes the permissions.                                                   |
| public void new()                                                                                                      | Initializes a new instance of the SecurityUtil class.                      |
| ::public static void flushAll()                                                                                        |                                                                            |

### Method isImplicitFlushMode

Indicates whether implicit security flushing mode is on.

    public static boolean isImplicitFlushMode()

#### Return Value

A Boolean value.

### Method getRoleEffectiveAccess

Retrieves an effective access for role value of securable object.

    public static int getRoleEffectiveAccess(Int64 roleID, str secObjectName, int secObjectType, str secObjectChildName)

#### Parameters

roleID  

<!-- -->

secObjectName  

<!-- -->

secObjectType  

<!-- -->

secObjectChildName  

#### Return Value

The effective access value.

### Method getRolePermissions

Gets a container of securable objects and their effective access.

    public static container getRolePermissions(Int64 roleID)

#### Parameters

roleID  
The role ID.

#### Return Value

A container of securable objects and their effective access.

### Method sysAdminMode

Gets and sets the security administrator mode.

    public static boolean sysAdminMode([boolean active])

#### Parameters

active  
A Boolean value.

#### Return Value

The old state of the security administrator mode.

### Method refreshRolePermissions

Retrieves the effective access of a specified role for a securable object.

    public static void refreshRolePermissions(Int64 roleID)

#### Parameters

roleID  

### Method runSecondPassAutoInference

Runs the second pass auto inference.

    public static void runSecondPassAutoInference()

### Method flushPermissions

Flushes the permissions.

    public static void flushPermissions()

### Method new

Initializes a new instance of the SecurityUtil class.

    public void new()

### Method flushAll

    public static void flushAll()

## Class SegmentEnteredEventArgs
    class SegmentEnteredEventArgs extends Object

### Remarks

### Examples

### Methods

| Method                                                   | Description |
|----------------------------------------------------------|-------------|
| public boolean isAllValuesEnabled(\[boolean enabled\])   |             |
| public boolean isMRUEnabled(\[boolean enabled\])         |             |
| public boolean isValidValuesEnabled(\[boolean enabled\]) |             |

### Method isAllValuesEnabled

    public boolean isAllValuesEnabled([boolean enabled])

#### Parameters

enabled  

#### Return Value

### Method isMRUEnabled

    public boolean isMRUEnabled([boolean enabled])

#### Parameters

enabled  

#### Return Value

### Method isValidValuesEnabled

    public boolean isValidValuesEnabled([boolean enabled])

#### Parameters

enabled  

#### Return Value

## Class SegmentValueChangedEventArgs
    class SegmentValueChangedEventArgs extends Object

### Remarks

### Examples

### Methods

| Method                       | Description |
|------------------------------|-------------|
| public FormSegment segment() |             |
| public AnyType selectedTag() |             |

### Method segment

    public FormSegment segment()

#### Return Value

### Method selectedTag

    public AnyType selectedTag()

#### Return Value

## Class Sequence
    class Sequence extends Object

The Sequence class lets you perform transactions outside the main transaction scope, typically for some kind of sequence, or voucher number generation.

### Remarks

Microsoft Dynamics 365 for Operations5 for Operations deals with three kinds of connections: The main user connection, an auxiliary system connection, and user connections. The first is used for the application logic. The second is used for internal sequence number generation (specifically the built-in field RecId). The third is used for the application maintained separate connections. This class provides an interface to the auxiliary system connection for number generation. However, it may be a better solution to use the UserConnection class, as this is the method the application uses or flexibility, and to avoid concurrency problems with the kernel's sequence number generation.

### Examples

    static void example() 
    { 
        Sequence S = new Sequence("mySequence",1,100,10000); 
        print S.nextval(10);           // 100 in current company (the subkey) 
        print S.nextval(10);           // 110 in current company (the subkey) 
        print S.nextval(1,"MMM");      // 100 in subkey "MMM" 
        print S.nextval(1,"MMM");      // 101 in subkey "MMM" 
    }

### Methods

| Method                                                                                                        | Description                                                                                 |
|---------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| public Int64 currval(\[str Subkey1\], \[int Subkey2\])                                                        | Gets the current sequence number from the sequence, without incrementing the counter value. |
| public Int64 nextval(Int64 Increment, \[str Subkey1\], \[int Subkey2\])                                       | Returns the next sequence number from the sequence and then increments the counter value.   |
| public void new(str Name, int Id, Int64 InitialValue, Int64 MaxValue, \[boolean Cycle\], \[Int64 CacheSize\]) | Initializes a new instance of the Object class.                                             |

### Method currval

Gets the current sequence number from the sequence, without incrementing the counter value.

    public Int64 currval([str Subkey1], [int Subkey2])

#### Parameters

Subkey1  

<!-- -->

Subkey2  

#### Return Value

The current sequence number from the sequence.

### Method nextval

Returns the next sequence number from the sequence and then increments the counter value.

    public Int64 nextval(Int64 Increment, [str Subkey1], [int Subkey2])

#### Parameters

Increment  

<!-- -->

Subkey1  

<!-- -->

Subkey2  

#### Return Value

The next sequence number available.

### Method new

Initializes a new instance of the Object class.

    public void new(str Name, int Id, Int64 InitialValue, Int64 MaxValue, [boolean Cycle], [Int64 CacheSize])

#### Parameters

Name  

<!-- -->

Id  

<!-- -->

InitialValue  

<!-- -->

MaxValue  

<!-- -->

Cycle  

<!-- -->

CacheSize  

## Class Set
    class Set extends Object

The Set class is used for the storage and retrieval of data from a collection in which the values of the elements contained are unique and serve as the key values according to which the data is automatically ordered.

### Remarks

The values may be of any X++ type. All values in the set must have the same type. When a value that is already stored in the set is added, it is ignored and does not increase the number of elements in the set. The values stored in the set can be traversed by using objects of type SetEnumerator. The contents of a set are stored in a way that facilitates efficient look up of the elements.

### Examples

The following example checks whether any of the values in one set, the noConfigs set, are found in a second set, the yesConfigs set. If they are, they are removed from the yesConfigs set.

    Set             noConfigs; 
    Set             yesConfigs; 
    ConfigId        configId; 
    SetEnumerator   se; 
    ; 
    se = noConfigs.getEnumerator(); 
    while (se.moveNext()) 
    { 
        configId    = se.current(); 
        if (yesConfigs.in(configId)) 
        { 
            yesConfigs.remove(configId); 
        } 
    }

### Methods

| Method                                               | Description                                                                                                                       |
|------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------|
| public boolean add(AnyType arg)                      | Adds an element to the set.                                                                                                       |
| public str definitionString()                        | Returns a description of the type of the elements in the set.                                                                     |
| public int elements()                                | Returns the number of elements in the set.                                                                                        |
| public boolean empty()                               | Determines whether the set is empty.                                                                                              |
| public boolean equal(Set set)                        | Determines whether a set is identical to the current set.                                                                         |
| public SetEnumerator getEnumerator()                 | Creates an enumerator for a set, which allows you to traverse the set.                                                            |
| public boolean in(AnyType arg)                       | Determines whether a specified element is a member of the set.                                                                    |
| public container pack()                              | Serializes the current instance of the Set class.                                                                                 |
| public boolean remove(AnyType arg)                   | Removes an element from the set.                                                                                                  |
| public str toString()                                | Returns a string describing the contents of the set.                                                                              |
| public Types typeId()                                | Returns the type of the values in the set.                                                                                        |
| public str xml(\[int indent\])                       | Returns an XML string that represents the current object.                                                                         |
| ::public static Set create(container container)      | Creates a set from the container obtained from a prior call to the Set.pack method.                                               |
| ::public static Set createFromXML(Object xmlnode)    |                                                                                                                                   |
| ::public static Set difference(Set set1, Set set2)   | Calculates and retrieves the set containing the elements from set1 that are not found in set2.                                    |
| ::public static Set intersection(Set set1, Set set2) | Calculates and returns the identical values found in two sets.                                                                    |
| ::public static Set union(Set set1, Set set2)        | Calculates and retrieves the union of two given sets. This is the set that contains the values found in at least one of the sets. |
| public void new(Types Type)                          | Creates a set that can contain elements of the specified type.                                                                    |

### Method add

Adds an element to the set.

    public boolean add(AnyType arg)

#### Parameters

arg  
The element to add to the set.

#### Return Value

true if the element is added to the set; otherwise, false.

#### Remarks

The element added to a set must be of the same type as the type assigned to the set when it was created. An element will not be added if it already exists in the set.

#### Examples

The following example creates a set, adds some integers to it, and then prints out the contents of the set.

    { 
        // Create a set of integers 
        Set is = new Set (Types::Integer); 
        int i; 
        ;  
        // Add values 0 to 9 to the set 
        for (i = 0; i < 10; i++) 
        { 
            is.add(i); 
        } 
        print is.toString(); 
        pause; 
    }

### Method definitionString

Returns a description of the type of the elements in the set.

    public str definitionString()

#### Return Value

A string that contains a definition of the set.

#### Remarks

To print a list of the values within the set, use Set.toString.

#### Examples

The following example creates a set of integers. The definitionString method is used to print a description of the set.

    { 
        // Declare a set of integers 
        Set is = new Set (Types::Integer);  
        ; 
        // Add some integers to the set 
        print is.add(1); 
        print is.add(2); 
        print is.add(1); 
        // Print a description of the set 
        print is.definitionString(); 
        // Print a description of the set elements 
        print is.toString(); 
        pause; 
    }

### Method elements

Returns the number of elements in the set.

    public int elements()

#### Return Value

The number of elements in the set.

#### Examples

The following example packs the contents of a set into a container. The elements method is used to test whether the set has any contents. If there are no contents, a nullNothingnullptrunita null reference (Nothing in Visual Basic) container is returned.

    public static container intSet2Con(Set _intSet) 
    { 
        SetEnumerator se; 
        container     intCon; 
        ; 
        if (!_intSet || !_intSet.elements()) 
        { 
            return conNull(); 
        } 
        se = _intSet.getEnumerator(); 
        while (se.moveNext()) 
        { 
            intCon += se.current(); 
        } 
        return intCon; 
    }

### Method empty

Determines whether the set is empty.

    public boolean empty()

#### Return Value

true if the set is empty; otherwise, false.

#### Remarks

This is equivalent to (elements() == 0).

#### Examples

The following example tests whether there are any elements in a set.

    { 
        Set mySet = new Set(Types::Integer); 
        ; 
        // ... 
        if (mySet.empty()) 
        { 
            print "There are no values in the set"; 
        } 
    }

### Method equal

Determines whether a set is identical to the current set.

    public boolean equal(Set set)

#### Parameters

set  
The set to be compared with the current set.

#### Return Value

true if the set is the same as the current set; otherwise, false.

#### Remarks

For two sets to be equal, they must have the same type and the same number of elements, and all elements must be the same.

#### Examples

The following example creates two sets of integers, adds some values to them, and then compares them to see whether the sets are the same.

    { 
        Set is1 = new Set (Types::Integer); 
        Set is2 = new Set (Types::Integer); 
        ; 
        is1.add(1); 
        is1.add(2); 
        is1.add(3); 
        is2.add(2); 
        is2.add(4); 
        if (is1.equal(is2)) 
        { 
            print "The sets are equal"; 
            pause; 
        } 
        else 
        { 
             print "The sets are not equal"; 
             pause; 
         } 
    }

### Method getEnumerator

Creates an enumerator for a set, which allows you to traverse the set.

    public SetEnumerator getEnumerator()

#### Return Value

A SetEnumerator object for the current set.

#### Examples

The following example packs the contents of a set into a container. The getEnumerator method is used to create an enumerator for the set. Therefore, that the elements in the set can be traversed and added to the container.

    public static container intSet2Con(Set _intSet) 
    { 
        SetEnumerator se; 
        container     intCon; 
        ; 
        if (!_intSet || !_intSet.elements()) 
        { 
            return conNull(); 
        } 
        se = _intSet.getEnumerator(); 
        while (se.moveNext()) 
        { 
            intCon += se.current(); 
        } 
        return intCon; 
    }

### Method in

Determines whether a specified element is a member of the set.

    public boolean in(AnyType arg)

#### Parameters

arg  
The element to check. The type of the element must be the same as the type that was specified for the set.

#### Return Value

true if the specified element is found in the set; otherwise, false.

#### Examples

The following example loads the contents a particular change list in the version control system, if the in method returns false. The changeSet set contains a list of the change list numbers that already have the content loaded.

    public void pageActivated() 
    { 
        SysVersionControlTmpItem contentsAddition; 
        if (!changeSet.in(changes.ChangeNumber)) 
        { 
            startLengthyOperation(); 
            contentsAddition = versioncontrol.getChangeNumberContents( 
                changes.ChangeNumber); 
            while select contentsAddition 
            { 
                contentsItem.data(contentsAddition); 
                contentsItem.insert(); 
            } 
            contents_ds.executeQuery(); 
            changeSet.add(changes.ChangeNumber); 
        } 
        super(); 
    }

### Method pack

Serializes the current instance of the Set class.

    public container pack()

#### Return Value

A container that contains the current instance of the Set class.

#### Remarks

The container created by this method contains 3 elements before the first element from the set:

-   A version number for the container
-   An integer that identifies the data type of the set elements
-   The number of elements in the set

If the keys or the values are objects, the pack method is called on each object to create a subcontainer. You can create a new set from the resulting container by using the Set::create method.

#### Examples

The following example creates a set of 10 integers, packs it into a container, and then creates a new set with contents identical to the original one.

    { 
        Set is1, is = new Set (Types::Integer); 
        int i; 
        container packedSet; 
        ; 
        // Create a set containing the first 10 integers. 
        for (i = 1; i <= 10; i++) 
        { 
            is.add(i); 
        } 
        // Pack it down in a container... 
        packedSet = is.pack(); 
        // ... and restore it 
        is1 = Set::create(packedSet); 
        print is1.toString(); 
        pause; 
    }

### Method remove

Removes an element from the set.

    public boolean remove(AnyType arg)

#### Parameters

arg  
The element to remove.

#### Return Value

true if the element was found and removed; otherwise, false.

#### Examples

The following example checks whether any of the values in one set, the noConfigs set, are found in a second set, the yesConfigs set. If they are found, they are removed from the yesConfigs set.

    Set             noConfigs; 
    Set             yesConfigs; 
    ConfigId        configId; 
    SetEnumerator   se; 
    ; 
    se = noConfigs.getEnumerator(); 
    while (se.moveNext()) 
    { 
        configId    = se.current(); 
        if (yesConfigs.in(configId)) 
        { 
            yesConfigs.remove(configId); 
        } 
    }

### Method toString

Returns a string describing the contents of the set.

    public str toString()

#### Return Value

A string that describes the contents of the set.

#### Remarks

Use the to get the description of a single element within a set.

#### Examples

The following example creates a set of strings, and then prints out a description of the set and a description of the set contents.

    { 
        // Declare a set of strings 
        Set names = new Set (Types::String); 
        ; 
        // Add some values to the set. 
        names.add("Peter"); 
        names.add("Paul"); 
        names.add("Mary"); 
        print names.definitionString(); 
        print names.toString(); 
        pause; 
    }

### Method typeId

Returns the type of the values in the set.

    public Types typeId()

#### Return Value

The type of the values in the set.

#### Remarks

The type of the constituent elements is determined when the set is created.

#### Examples

The following example instantiates a new set with the same type as an existing set.

    { 
        Set set1 = new Set(Types::Integer); 
        Set set2; 
       ; 
        set2 = new Set(set1.typeId()); 
        print set2.typeId(); 
        pause; 
    }

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method create

Creates a set from the container obtained from a prior call to the Set.pack method.

    public static Set create(container container)

#### Parameters

container  
The container that holds the packed set.

#### Return Value

A set equal to the one that was packed into the container.

#### Remarks

If the values are objects, the objects must have an unpack method that is called to reestablish their internal state from the container.

#### Examples

The following example creates a set and packs it into a container. The create method is then used to unpack the container and create a set identical to the original one.

    { 
        Set is1, is = new Set (Types::Integer); 
        int i; 
        container packedSet; 
        ; 
        // Add 10 integers (0 - 9) to the set 
        for (i = 1; i <= 10; i++) 
        { 
            is.add(i); 
        } 
        // Pack the set into a container... 
        packedSet = is.pack(); 
        // ... and restore it 
        is1 = Set::create(packedSet); 
        print is1.toString(); 
        pause; 
    }

### Method createFromXML

    public static Set createFromXML(Object xmlnode)

#### Parameters

xmlnode  

#### Return Value

### Method difference

Calculates and retrieves the set containing the elements from set1 that are not found in set2.

    public static Set difference(Set set1, Set set2)

#### Parameters

set1  
The set to check.

<!-- -->

set2  
The set to check.

#### Return Value

A set containing the elements from set1 that are not found in set2.

#### Remarks

The two sets to be compared must be of the same type.

#### Examples

The following example creates one set that contains the integers 1, 2, and 3, and one set that contains the integers 2 and 4. The difference method is used to create a set that contains the elements in the first set that are not in the second set (1 and 3).

    { 
        Set is = new Set (Types::Integer); 
        Set is2, is1 = new Set (Types::Integer); 
        ; 
        is.add(1); 
        is.add(2); 
        is.add(3); 
        is1.add(2); 
        is1.add(4); 
        is2 = Set::difference(is, is1); 
        // prints "{1, 3}" 
        print is2.toString(); 
        pause; 
    }

### Method intersection

Calculates and returns the identical values found in two sets.

    public static Set intersection(Set set1, Set set2)

#### Parameters

set1  
The second set to be compared.

<!-- -->

set2  
The second set to be compared.

#### Return Value

A set containing the elements found in both sets.

#### Examples

The following example creates two sets of integers and adds some values to them. It then prints a list of the values that are that is contained in both sets.

    { 
        Set is = new Set (Types::Integer); 
        Set is2, is1 = new Set (Types::Integer); 
        ; 
        is.add(1); 
        is.add(2); 
        is.add(3); 
        is1.add(2); 
        is1.add(4); 
        is2 = Set::intersection(is, is1); 
        // Prints "{2}" because 2 is contained in both is and is2. 
        print is2.toString(); 
    }

### Method union

Calculates and retrieves the union of two given sets. This is the set that contains the values found in at least one of the sets.

    public static Set union(Set set1, Set set2)

#### Parameters

set1  
The second of the two sets that are compared.

<!-- -->

set2  
The second of the two sets that are compared.

#### Return Value

The set containing elements found in set1 or set2.

#### Remarks

The two sets that are compared must be of the same type.

#### Examples

The following example creates two sets of integers and adds some values to them. It then creates a new set that contains all the values that are contained in either of the sets.

    { 
        Set is = new Set (Types::Integer); 
        Set is2, is1 = new Set (Types::Integer); 
        ; 
        is.add(1); 
        is.add(2); 
        is.add(3); 
        is1.add(2); 
        is1.add(4); 
        is2 = Set::union(is, is1); 
        // Prints "{1, 2, 3, 4}". 
        print is2.toString(); 
        pause; 
    }

### Method new

Creates a set that can contain elements of the specified type.

    public void new(Types Type)

#### Parameters

Type  
The type of the elements within the set.

#### Remarks

The type of the set cannot be changed after the set has been created.

#### Examples

The following example creates a set of integers and a set of objects.

    { 
        // Create a set of integers. 
        Set is = new Set (Types::Integer); 
        // Create a set of objects. 
        Set os = new Set (Types::Class); 
    }

## Class SetEnumerator
    class SetEnumerator extends Object

The SetEnumerator class lets you traverse the elements in a set.

### Remarks

Set enumerators start before the first element in the set. You must call the SetEnumerator.moveNext method to make it point to the first element in the set. As a best practice, use the SetEnumerator class instead of the SetIterator class, because enumerators are automatically created on the same tier as the set when the set.getEnumerator method is called. This helps you avoid a potential problem in code that is marked as Called from, where the iterator and set can be on separate tiers. In addition, set enumerators require less code than set iterators and therefore perform slightly better.

### Examples

### Methods

| Method                        | Description                                                                                                |
|-------------------------------|------------------------------------------------------------------------------------------------------------|
| public AnyType current()      | Retrieves the value that is pointed to by the enumerator.                                                  |
| public str definitionString() | Returns a description of the enumerator.                                                                   |
| public boolean moveNext()     | Determines whether the enumerator denotes a valid set element.                                             |
| public str toString()         | Retrieves a description of the contents of the element in the set that the enumerator currently points to. |
| public void reset()           | Moves the enumerator to the start of the set.                                                              |

### Method current

Retrieves the value that is pointed to by the enumerator.

    public AnyType current()

#### Return Value

The value that is currently pointed to in the set.

#### Remarks

The type of the return value is determined by the type of items in the set. You must call the SetEnumerator.moveNext method before you call the current method.

### Method definitionString

Returns a description of the enumerator.

    public str definitionString()

#### Return Value

A string that contains a description of the enumerator.

#### Remarks

For example, an enumerator for a set of integers would return "int set enumerator".

#### Examples

The following example creates a set and an enumerator for the set. The definitionString method is used to print a description of the enumerator.

    { 
        Set mySet = new Set(Types::Integer); 
        SetEnumerator enumerator; 
        int i; 
        // Add some elements to the set. 
       for (i = 0; i < 10; i++) 
        { 
            mySet.add(i); 
        } 
        // Set the enumerator. 
        enumerator = mySet.getEnumerator(); 
        print enumerator.definitionString(); 
        pause; 
    }

### Method moveNext

Determines whether the enumerator denotes a valid set element.

    public boolean moveNext()

#### Return Value

true if the current position in the set holds a valid element; otherwise, false.

#### Remarks

Set enumerators start before the first element in the set. You must call the moveNext method to make it point to the first element in the set.

### Method toString

Retrieves a description of the contents of the element in the set that the enumerator currently points to.

    public str toString()

#### Return Value

A string that contains a description of the current element in the set.

#### Examples

The following example creates a set of integers, and then prints the content of the first and second elements in the set.

    { 
        Set mySet = new Set(Types::Integer); 
        SetEnumerator  enumerator; 
        int i; 
         // Add some elements to the set. 
        for (i = 0; i < 10; i++) 
        { 
            mySet.add(i); 
        } 
        // Set the enumerator. 
        enumerator = mySet.getEnumerator(); 
        // Go to the beginning of the enumerator. 
        enumerator.reset(); 
        // Go to the first element in the set. 
        enumerator.moveNext(); 
        // Print the first item in the set. 
        print enumerator.toString(); 
        pause; 
        enumerator.moveNext(); 
        // Print the second element in the set. 
        print enumerator.toString(); 
        pause; 
    }

### Method reset

Moves the enumerator to the start of the set.

    public void reset()

#### Remarks

The reset method moves the enumerator to the start of the set, in front of the first element in the set. You must call the SetEnumerator.moveNext method to make it point to the first element in the set.

#### Examples

The following example creates a set and then creates an enumerator for the set. It uses the reset method to move to the start of the set and then uses the moveNext method to move to the first element in the set.

    { 
        Set mySet = new Set(Types::Integer); 
        SetEnumerator  enumerator; 
        int i; 
         // Add some elements to the set. 
        for (i = 0; i < 10; i++) 
        { 
            mySet.add(i); 
        } 
        // Set the enumerator. 
        enumerator = mySet.getEnumerator(); 
        // Go to beginning of enumerator. 
        enumerator.reset(); 
        // Go to the first element in the set. 
        enumerator.moveNext(); 
        // Print the first item in the set. 
        print enumerator.toString(); 
        pause; 
    }

## Class SetIterator
    class SetIterator extends Object

The SetIterator class allows you to iterate over the elements in a set.

### Remarks

Set iterators may be viewed as pointers into the sets over which they iterate. Functionality is available to start the iteration, to determine whether more elements are available, and to fetch the element pointed to by the iterator. Newly created set iterators are positioned at the first element in the set. The order in which the elements occur during iteration is defined not by the sequence in which the elements are inserted, but by the ordering of the elements. Elements with lower values appear before elements with higher values. The usual ordering for the types is used. If the constituent elements are objects; however, the addresses of the objects are used to supply the ordering. No specific ordering may consequently be inferred. The addresses of the objects are transient by nature. It is best practice to use the class instead of the SetIterator class. This avoids problems if you are accessing the set on one tier with an iterator on another tier. Set iterators and the sets over which they iterate must be on the same client/server side. If you use SetIterator and code is marked as Called from, it is possible that the set and the iterator will end up on different tiers, and the code will fail. If you use SetEnumerator, the enumerator is automatically created on the same tier as the set. Also, to move to the next item in a set, you must explicitly call the more and next methods if you are using a set iterator. If you use SetEnumerator, you only have to call moveNext method.

### Examples

The following example creates a set of integers and then adds four values to it. It then iterates through the set that is printing out information about each set element.

        Set s1 = new Set (Types::Integer); 
        int theElement; 
        SetIterator it; 
        ; 
        // Add some elements. 
        s1.add(3); 
        s1.add(4); 
        s1.add(13); 
        s1.add(1); 
        // Start a traversal of the elements in the set. 
        it = new SetIterator(s1); 
        // Prints "(begin)[1]". 
        print it.toString(); 
        // The elements are fetched in the order: 1, 3, 4, 13. 
        while (it.more()) 
        { 
            theElement = it.value(); 
            print theElement; 
             // Fetch the next element. 
            it.next(); 
        } 
        pause; 
    }

### Methods

| Method                        | Description                                                                                            |
|-------------------------------|--------------------------------------------------------------------------------------------------------|
| public str definitionString() | Returns a textual representation of the type of the iterator.                                          |
| public boolean more()         | Determines whether the iterator denotes a valid set element.                                           |
| public str toString()         | Returns a textual representation of the current element in the set that is pointed to by the iterator. |
| public AnyType value()        | Retrieves the value that the iterator is pointing to.                                                  |
| public void next()            | Moves the iterator to the next element.                                                                |
| public void new(Set set)      | Creates a new iterator for a set.                                                                      |
| public void begin()           | Moves the iterator to the start of the set.                                                            |
| public void delete()          | Removes the element that is pointed to by the iterator of the set.                                     |
| public void end()             | Moves the iterator past the last element in the set.                                                   |

### Method definitionString

Returns a textual representation of the type of the iterator.

    public str definitionString()

#### Return Value

A string that indicates the type of the iterator.

### Method more

Determines whether the iterator denotes a valid set element.

    public boolean more()

#### Return Value

true if the iterator denotes a valid element; otherwise, false.

#### Remarks

Attempting to access an element that is pointed to by an iterator when this method returns false will result in an error. This method will check only whether the iterator points to a valid element. It will not check whether there are more elements in the set.

#### Examples

The following example uses the SetIterator.more method to check whether there are more elements in the set before it runs through the while loop, which deletes all the odd elements from the set.

    { 
        Set iset = new Set (Types::Integer); 
        SetIterator it; 
        int i; 
        ; 
        for (i = 1; i <= 10; i++) 
        { 
            iset.add(i); 
        } 
        // Delete all odd elements 
        it = new SetIterator(iset); 
        while (it.more()) 
        { 
            if (it.value() mod 2 != 0) 
            { 
                // The value is odd. Delete and skip to next element. 
                it.delete(); 
            } 
            else 
            { 
                it.next(); 
            } 
        } 
        print iset.toString(); 
        pause; 
    }

### Method toString

Returns a textual representation of the current element in the set that is pointed to by the iterator.

    public str toString()

#### Return Value

A string that is the textual representation of the current element in the set.

#### Remarks

If the iterator points to the first element in the set, the string will contain an indication of this, in the following format: "(begin)\[value\]" If the iterator does not point to an element (that is, if more() returns false), the string returned is: "(end)" If the iterator points to a value the string is: "\[value\]" where value is a string representation of the element value.

#### Examples

The following example uses the SetIterator.toString method to print a description of the value in the set that the iterator points to before it starts traversing the set.

    { 
        Set s1 = new Set (Types::Integer); 
        int theElement; 
        SetIterator it; 
        // Add some elements 
        s1.add(3); 
        s1.add(4); 
        s1.add(13); 
        s1.add(1);  
        // Start a traversal of the elements in the set 
        it = new SetIterator(s1); 
        // The elements are fetched in the order: 1, 3, 4, 13 
        print it.toString(); // Prints "(begin)[1]" 
        while (it.more()) 
        { 
            theElement = it.value(); 
            print theElement; 
            // Fetch the next element 
            it.next(); 
        } 
        pause; 
    }

### Method value

Retrieves the value that the iterator is pointing to.

    public AnyType value()

#### Return Value

The value denoted by the iterator.

#### Remarks

Use SetIterator.more to check whether an element exists before trying to retrieve the key value of the set element.

#### Examples

The following example uses the SetIterator.value method to print the value of the current item in the set.

    { 
        Set s1 = new Set (Types::Integer); 
        SetIterator it; 
        // Add some elements 
        s1.add(3); 
        s1.add(4); 
        s1.add(13); 
        s1.add(1);  
        // Start a traversal of the elements in the set 
        it = new SetIterator(s1); 
        // Prints "(begin)[1]" 
        print it.toString();  
        // The elements are fetched in the order: 1, 3, 4, 13 
        while (it.more()) 
        { 
            print it.value(); 
            // Fetch the next element 
            it.next(); 
        } 
        pause; 
    }

### Method next

Moves the iterator to the next element.

    public void next()

#### Remarks

Use SetIterator.more to determine whether the iterator points to a valid element.

#### Examples

The following example uses the SetIterator.next method to move the iterator to the next element in the set, before testing whether there is another element, and if there is another element, adding the value to a container.

    static public void saveSequence(classId _classId, Set _sequence) 
    { 
        SysCheckListItemTable sysCheckListItemTable; 
        SetIterator           si; 
        container             con = connull(); 
        if (_sequence) 
        { 
            si = new SetIterator(_sequence); 
            si.begin(); 
            while (si.more()) 
            { 
                 con += si.value(); 
                 si.next(); 
            } 
        } 
        //... 
    }

### Method new

Creates a new iterator for a set.

    public void new(Set set)

#### Parameters

set  
The set to iterate over.

#### Remarks

The iterator is positioned at the first value in the set, if the set is not empty.

#### Examples

The following example creates a set of integers and then creates an iterator for that set

    Set s1 = new Set (Types::Integer); 
    SetIterator it; 
    it = new SetIterator(s1);

### Method begin

Moves the iterator to the start of the set.

    public void begin()

#### Remarks

Newly created set iterators are positioned at the first element in the set. Typically, you do not need to call the begin method before you start to iterate through the set; you need to do that only if you want to reset the pointer later on.

#### Examples

The following example returns set of class IDs of the classes that implement the specified interface, that is, the \_id class. An iterator is used to remove classes from the set if they are superclasses, and the \_onlyLeafClasses parameter is set to true. The begin method is used to reset the iterator after the superclasses have been removed from the set.

    public static Set getImplements( 
        classId _id,  
        boolean _onlyLeafClasses = true) 
    { 
        Dictionary dictionary = new Dictionary(); 
        SysDictClass sysDictClass; 
        boolean removed; 
        Set set = new Set(Types::Integer); 
        SetIterator setIterator = new SetIterator(set); 
        int i; 
        for (i=1;i<=dictionary.classCnt();i++) 
        { 
            sysDictClass = new SysDictClass(dictionary.classCnt2Id(i)); 
            if (sysDictClass.isImplementing(_id)) 
            { 
                set.add(sysDictClass.id()); 
            } 
        } 
        //No superclasses included in return set 
        if (_onlyLeafClasses) 
        { 
            // begin method not needed here; only for clarity 
            setIterator.begin();  
            while (setIterator.more()) 
            { 
                removed = false; 
                sysDictClass = new SysDictClass(setIterator.value()); 
                while (sysDictClass.extend()) 
                { 
                    removed = removed | set.remove(sysDictClass.extend()); 
                    sysDictClass = new SysDictClass(sysDictClass.extend()); 
                } 
                if (removed) 
                { 
                    // Restart search 
                    setIterator.begin();  
                } 
                else 
                { 
                    setIterator.next(); 
                } 
            } 
        } 
        return set; 
    }

### Method delete

Removes the element that is pointed to by the iterator of the set.

    public void delete()

#### Remarks

The iterator will point to the next element after calling this method.

#### Examples

The following example deletes all the odd elements from the set.

    { 
        Set iset = new Set (Types::Integer); 
        SetIterator it; 
        int i; 
        for (i = 1; i <= 10; i++) 
        { 
            iset.add(i); 
        } 
        // Delete all odd elements 
        it = new SetIterator(iset); 
        while (it.more()) 
        { 
            if (it.value() mod 2 != 0) 
            { 
                // The value is odd. Delete and skip to next element. 
                it.delete(); 
            } 
            else 
            { 
                it.next(); 
            } 
        } 
        print iset.toString(); 
        pause; 
    }

### Method end

Moves the iterator past the last element in the set.

    public void end()

#### Remarks

After executing this method, the more method will return false.

## Class SkipAOSValidationPermission
    class SkipAOSValidationPermission extends CodeAccessPermission

The SkipAOSValidationPermission class controls the ability to skip AOS validation and check permissions for specific APIs.

### Remarks

For a list of all protected APIs, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission.demand method is called on before the protected API is executed. Call a method on the server tier from one of the following: A server static method –or– A class instance method that is set to run on the server by using the RunOn class property.

### Examples

### Methods

| Method                                                 | Description                                                                                                         |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                            |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when overridden by a derived class. |
| public void new()                                      | Initializes a new instance of the SkipAOSValidationPermission class.                                                |

### Method copy

Creates and returns a copy of a permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the derived class object.

#### Remarks

You can override this method as part of the process of making an API more secure. For more information, see .

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when overridden by a derived class.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You can override the method as part of the process of making an API more secure. For more information, see .

### Method new

Initializes a new instance of the SkipAOSValidationPermission class.

    public void new()

#### Examples

The following code example demonstrates how to create an instance of the SkipAOSValidationPermission class.

    server static void main(Args args) 
    { 
        SkipAOSValidationPermission perm; 
        ; 
        perm = new SkipAOSValidationPermission(); 
    }

## Class SqlDataDictionary
    class SqlDataDictionary extends Object

The SqlDataDictionary class provides a collection of methods for data dictionary maintenance.

### Remarks

This API has a built-in authorization check that is invoked at run time. Calls to members of the SQLDataDictionary class by users without access to the development security key (SysDevelopment) results in an exception.

### Examples

The following example checks whether the UserInfo table exists in the database.

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

### Methods

| Method                                                                                                               | Description                                                                                                                   |
|----------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------|
| public int indexCreate(\[TableId tableId\], \[IndexId indexId\])                                                     | Creates the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database. You can also use this method to re-create indexes. |
| public str indexCreateDDL(TableId tableId)                                                                           | Generates and returns the SQL statements needed to create the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table.                      |
| public int indexDrop(\[TableId tableId\], \[IndexId indexId\], \[boolean onlyNonUnique\])                            | Drops the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.                                                      |
| public str name(str bmsname, \[FieldId fieldId\], \[int arrayindex\])                                                | Translates any object name into a valid SQL database object-name; that is, valid for the database currently connected.        |
| public int tableCreate(\[boolean indexes\], \[TableId tableId\])                                                     | Creates one or more Microsoft Dynamics 365 for Operations5 for Operations tables in the SQL database. Also, provides an option to create for index.           |
| public str tableCreateDDL(TableId tableId)                                                                           | Generates and returns the SQL statement to create an Microsoft Dynamics 365 for Operations5 for Operations table.                                             |
| public int tableDrop(TableId tableId, \[boolean prompt\_before\_drop\])                                              | Drops the Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.                                                                    |
| public str tableDropDDL(TableId tableId)                                                                             | Generates and returns the SQL statement to drop an Microsoft Dynamics 365 for Operations5 for Operations table.                                               |
| public boolean tableEmpty(TableId tableId, \[str company\], \[boolean not\_this\_company\])                          | Returns true if table is not empty; otherwise false.                                                                          |
| public boolean tableExist(str sqltablename, \[boolean use\_within\_transaction\])                                    | Returns true if table exists; otherwise false.                                                                                |
| public int tableMetaData(TableId tableId)                                                                            | Fills the SqlDescribe table with data dictionary meta data.                                                                   |
| public int tableReindex(\[TableId tableId\], \[IndexId indexId\])                                                    | Updates index for the table.                                                                                                  |
| public int tableSynchronize(TableId tableId, \[boolean update\_dict\_info\_only\], \[boolean check\_indexes\])       | Synchronizes the Microsoft Dynamics 365 for Operations5 for Operations table and the table of the SQL database.                                               |
| public int tableTruncate(TableId tableId, \[boolean prompt\_before\_truncate\], \[boolean truncate\_system\_table\]) | Truncates the Microsoft Dynamics 365 for Operations5 for Operations table.                                                                                    |
| public str tableTruncateDDL(TableId tableId)                                                                         | Generates and returns a SQL statement to truncate an Microsoft Dynamics 365 for Operations5 for Operations table.                                             |
| ::public static int synchronize(\[boolean synchronize\_all\])                                                        | Synchronizes the Microsoft Dynamics 365 for Operations5 for Operations data dictionary and the data dictionary of the SQL database.                           |
| public void new()                                                                                                    | Initializes a new instance of the SqlDataDictionary class.                                                                    |
| public void tableDelete(TableId tableId)                                                                             | Deletes the Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.                                                                  |

### Method indexCreate

Creates the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database. You can also use this method to re-create indexes.

    public int indexCreate([TableId tableId], [IndexId indexId])

#### Parameters

tableId  
The index handle (0 for all); optional.

<!-- -->

indexId  
The index handle (0 for all); optional.

#### Return Value

0 if the method succeeds.

#### Remarks

This method can be used to re-create indexes. Use 0 for the parameters to indicate all tables or indexes.

#### Examples

    { 
        SqlDataDictionary DD = new SqlDataDictionary(); 
        DD.indexCreate(TableName2Id("Address")); 
    }

### Method indexCreateDDL

Generates and returns the SQL statements needed to create the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table.

    public str indexCreateDDL(TableId tableId)

#### Parameters

tableId  
The table handle that the index should be created for.

#### Return Value

Returns SQL statements to create the indexes of the Microsoft Dynamics 365 for Operations5 for Operations table.

### Method indexDrop

Drops the indexes of an Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.

    public int indexDrop([TableId tableId], [IndexId indexId], [boolean onlyNonUnique])

#### Parameters

tableId  

<!-- -->

indexId  

<!-- -->

onlyNonUnique  

#### Return Value

Zero if the method succeeds.

#### Remarks

Use 0 for the parameters to indicate all tables or indexes.

#### Examples

    { 
        SqlDataDictionary DD = new SqlDataDictionary(); 
        DD.indexDrop(TableName2Id("Address")); 
    }

### Method name

Translates any object name into a valid SQL database object-name; that is, valid for the database currently connected.

    public str name(str bmsname, [FieldId fieldId], [int arrayindex])

#### Parameters

bmsname  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

<!-- -->

fieldId  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

<!-- -->

arrayindex  
A field index (0 for not applicable), that is, an array field's arrayindex'th entry, such as Dimension\[2\]; optional.

#### Return Value

The valid object name.

#### Remarks

Because names may be truncated, a unique object identifier may be supplied. Also, a third parameter enables the method to return discrete SQL field names for Microsoft Dynamics 365 for Operations5 for Operations array fields.

### Method tableCreate

Creates one or more Microsoft Dynamics 365 for Operations5 for Operations tables in the SQL database. Also, provides an option to create for index.

    public int tableCreate([boolean indexes], [TableId tableId])

#### Parameters

indexes  
The table handle (0 for all); optional.

<!-- -->

tableId  
The table handle (0 for all); optional.

#### Return Value

Zero if the method succeeds.

#### Remarks

Used for low-level maintenance only.

#### Examples

    { 
        SqlDataDictionary DD = new SqlDataDictionary(); 
        DD.tableCreate(TableName2Id("Address")); 
    }

### Method tableCreateDDL

Generates and returns the SQL statement to create an Microsoft Dynamics 365 for Operations5 for Operations table.

    public str tableCreateDDL(TableId tableId)

#### Parameters

tableId  
The table handle of the table to be created.

#### Return Value

The SQL statement to create an Microsoft Dynamics 365 for Operations5 for Operations table.

### Method tableDrop

Drops the Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.

    public int tableDrop(TableId tableId, [boolean prompt_before_drop])

#### Parameters

tableId  
A boolean flag that determines whether to ask user before dropping the table; optional. By default, true.

<!-- -->

prompt\_before\_drop  
A boolean flag that determines whether to ask user before dropping the table; optional. By default, true.

#### Return Value

Zero if the method succeeds.

### Method tableDropDDL

Generates and returns the SQL statement to drop an Microsoft Dynamics 365 for Operations5 for Operations table.

    public str tableDropDDL(TableId tableId)

#### Parameters

tableId  
The table to be dropped.

#### Return Value

The SQL statement that drops the specified Microsoft Dynamics 365 for Operations5 for Operations table.

### Method tableEmpty

Returns true if table is not empty; otherwise false.

    public boolean tableEmpty(TableId tableId, [str company], [boolean not_this_company])

#### Parameters

tableId  
If true exludes records that belongs to the company from the query; optional. By default, false.

<!-- -->

company  
If true exludes records that belongs to the company from the query; optional. By default, false.

<!-- -->

not\_this\_company  
If true exludes records that belongs to the company from the query; optional. By default, false.

#### Return Value

true if the table empty; otherwise, false.

### Method tableExist

Returns true if table exists; otherwise false.

    public boolean tableExist(str sqltablename, [boolean use_within_transaction])

#### Parameters

sqltablename  
A boolean flag that determines whether transactions are to used; optional. By default, false.

<!-- -->

use\_within\_transaction  
A boolean flag that determines whether transactions are to used; optional. By default, false.

#### Return Value

true if the table exists; otherwise, false.

### Method tableMetaData

Fills the SqlDescribe table with data dictionary meta data.

    public int tableMetaData(TableId tableId)

#### Parameters

tableId  
The table handle.

#### Return Value

true if the method succeeds.

### Method tableReindex

Updates index for the table.

    public int tableReindex([TableId tableId], [IndexId indexId])

#### Parameters

tableId  
The index handle (0 for all); optional. By default, 0.

<!-- -->

indexId  
The index handle (0 for all); optional. By default, 0.

#### Return Value

Zero if the method succeeds.

### Method tableSynchronize

Synchronizes the Microsoft Dynamics 365 for Operations5 for Operations table and the table of the SQL database.

    public int tableSynchronize(TableId tableId, [boolean update_dict_info_only], [boolean check_indexes])

#### Parameters

tableId  
When set forces reindex of the table indexes; optional. By default, true.

<!-- -->

update\_dict\_info\_only  
When set forces reindex of the table indexes; optional. By default, true.

<!-- -->

check\_indexes  
When set forces reindex of the table indexes; optional. By default, true.

#### Return Value

true if the method succeeds.

### Method tableTruncate

Truncates the Microsoft Dynamics 365 for Operations5 for Operations table.

    public int tableTruncate(TableId tableId, [boolean prompt_before_truncate], [boolean truncate_system_table])

#### Parameters

tableId  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

<!-- -->

prompt\_before\_truncate  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

<!-- -->

truncate\_system\_table  
A boolean flag that determines whether to truncate table in case if selected table is system; optional. By default, false.

#### Return Value

Zero if the method succeeds.

### Method tableTruncateDDL

Generates and returns a SQL statement to truncate an Microsoft Dynamics 365 for Operations5 for Operations table.

    public str tableTruncateDDL(TableId tableId)

#### Parameters

tableId  
The table handle of the table to be truncated.

#### Return Value

The SQL statement to truncate the table.

### Method synchronize

Synchronizes the Microsoft Dynamics 365 for Operations5 for Operations data dictionary and the data dictionary of the SQL database.

    public static int synchronize([boolean synchronize_all])

#### Parameters

synchronize\_all  
A boolean flag that determines whether to synchronize all tables; optional. If true, this method synchronizes all tables (instead of only those marked dirty by the Microsoft Dynamics 365 for Operations5 for Operations kernel). By default, false.

#### Return Value

true if synchronization was successful; otherwise false.

### Method new

Initializes a new instance of the SqlDataDictionary class.

    public void new()

### Method tableDelete

Deletes the Microsoft Dynamics 365 for Operations5 for Operations table in the SQL database.

    public void tableDelete(TableId tableId)

#### Parameters

tableId  

## Class SqlDataDictionaryPermission
    class SqlDataDictionaryPermission extends CodeAccessPermission

The SqlDataDictionaryPermission class controls the ability to access the methods on the and is designed to check permissions for specific APIs. For a list of all protected APIs, see Secured APIs.

### Remarks

You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property.

### Examples

The following example deletes data from the xRefNames table. The assert method is called to declare that the code can then instantiate the AsciiIo class that is used to read and write data to a file.

    { 
        DictTable dictTable = new DictTable(tablenum(xRefNames)); 
        str sqlTableName; 
        SqlDataDictionary sqlTable; 
        if (dictTable && dictTable.enabled()) 
        { 
            sqlTableName = dictTable.name(DbBackend::Sql); 
            sqlTable = new SqlDataDictionary(); 
            // Try to truncate only if the table does exist 
            // in the SQL database. 
            if (sqlTable.tableExist(sqlTableName)) 
            { 
                new SqlDataDictionaryPermission( 
                    methodstr(SqlDataDictionary, tableTruncate)).assert(); 
                sqlTable.tableTruncate(tablenum(xRefNames)); 
                CodeAccessPermission::revertAssert(); 
            } 
        } 
    }

### Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new(IdentifierName methodName)             | Creates a new instance of the SQLDataDictionaryPermission class.                 |

### Method copy

Creates and returns a copy of the current permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the current permission object.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise, false.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

### Method new

Creates a new instance of the SQLDataDictionaryPermission class.

    public void new(IdentifierName methodName)

#### Parameters

methodName  
The string that represents the name of the method to be called.

#### Examples

The following code example deletes the data in the xRefNames table.

    server static void main(Args _args) 
    { 
        DictTable dictTable = new DictTable(tablenum(xRefNames)); 
        str sqlTableName; 
        SqlDataDictionary sqlTable; 
        if (dictTable && dictTable.enabled()) 
        { 
            sqlTableName = dictTable.name(DbBackend::Sql); 
            sqlTable = new SqlDataDictionary(); 
            // Only try to truncate if the table does exist 
            // in the SQL database 
            if (sqlTable.tableExist(sqlTableName)) 
            { 
                new SqlDataDictionaryPermission( 
                    methodstr(SqlDataDictionary, tableTruncate)).assert(); 
                sqlTable.tableTruncate(tablenum(xRefNames)); 
                CodeAccessPermission::revertAssert(); 
            } 
        } 
    }

## Class SqlStatementExecutePermission
    class SqlStatementExecutePermission extends CodeAccessPermission

Controls the ability to use SQL in Microsoft Dynamics 365 for Operations5 for Operations.

### Remarks

This class is designed to check permissions for specific APIs. For a list of all protected APIs, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method –or–
-   A class instance method that is set to run on the server by using the RunOn class property

### Examples

This example performs an SQL query on the CustTable table, which runs on the server. The result of the query is stored in the \_resultSet object. The assert method is called to declare that the code can then instantiate the AsciiIo class that is used to read and write data to a file.

    server static void main(Args _args) 
    { 
        DictTable  _dictTable; 
        Connection _connection; 
        Statement  _statement; 
        str        _sql; 
        ResultSet  _resultSet; 
        SqlStatementExecutePermission _perm; 
        _dictTable = new DictTable(tableNum(CustTable)); 
        if (_dictTable != null) 
            { 
               _connection = new Connection(); 
               _sql = strfmt( "SELECT * FROM %1", _dictTable.name(DbBackend::Sql) ); 
               _perm = new SqlStatementExecutePermission(_sql); 
               // Check for permission to use the _statement. 
               _perm.assert(); 
               _statement = _connection.createStatement(); 
               _resultSet = _statement.executeQuery(_sql); 
               // End the scope of the assert call. 
               CodeAccessPermission::revertAssert(); 
            } 
    }

### Methods

| Method                                                 | Description                                                                      |
|--------------------------------------------------------|----------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of the current permission class object.               |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission. |
| public void new(str sqlStatement)                      | Creates a new instance of the SQLStatementExecutePermission class.               |

### Method copy

Creates and returns a copy of the current permission class object.

    public CodeAccessPermission copy()

#### Return Value

A copy of the current permission object.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

### Method isSubsetOf

Determines whether a current permission is a subset of the specified permission.

    public boolean isSubsetOf(CodeAccessPermission target)

#### Parameters

target  
A CodeAccessPermission class object.

#### Return Value

true if a current permission is a subset of a specified permission; otherwise false.

#### Remarks

You override this method when you derive a class from the CodeAccessPermission class. For more information, see .

### Method new

Creates a new instance of the SQLStatementExecutePermission class.

    public void new(str sqlStatement)

#### Parameters

sqlStatement  
The SQL string to be executed.

#### Examples

The following example performs an SQL query on the CustTable table, which runs on the server. The result of the query is stored in the resultSet object.

    server static void main(Args _args) 
    { 
        DictTable  dictTable; 
        Connection connection; 
        Statement  statement; 
        str        sql; 
        ResultSet  resultSet; 
        SqlStatementExecutePermission perm; 
        dictTable = new DictTable(tableNum(CustTable)); 
        if (dictTable != null) 
            { 
               connection = new Connection(); 
               sql = strfmt( "SELECT * FROM %1", dictTable.name(DbBackend::Sql) ); 
               //Instantiate the permission class 
               perm = new SqlStatementExecutePermission(sql); 
               //check for permission to use statement 
               perm.assert(); 
               statement = connection.createStatement(); 
               resultSet = statement.executeQuery(sql); 
               //end the scope of the assert call 
               CodeAccessPermission::revertAssert(); 
            } 
    }

## Class SqlSyncPending
    class SqlSyncPending extends Object

### Remarks

### Examples

### Methods

| Method                                               | Description                                             |
|------------------------------------------------------|---------------------------------------------------------|
| public ConfigurationKeyId configurationKeyTouched()  |                                                         |
| public boolean databaseTouched(\[boolean newValue\]) |                                                         |
| public ExtendedTypeId extendedDataTypeTouched()      |                                                         |
| public TableId indexesTouched()                      |                                                         |
| public TableId relationTouched()                     |                                                         |
| public TableId tableDeleted()                        |                                                         |
| public TableId tableTouched()                        |                                                         |
| public void new()                                    | Initializes a new instance of the SqlSyncPending class. |

### Method configurationKeyTouched

    public ConfigurationKeyId configurationKeyTouched()

#### Return Value

### Method databaseTouched

    public boolean databaseTouched([boolean newValue])

#### Parameters

newValue  

#### Return Value

### Method extendedDataTypeTouched

    public ExtendedTypeId extendedDataTypeTouched()

#### Return Value

### Method indexesTouched

    public TableId indexesTouched()

#### Return Value

### Method relationTouched

    public TableId relationTouched()

#### Return Value

### Method tableDeleted

    public TableId tableDeleted()

#### Return Value

### Method tableTouched

    public TableId tableTouched()

#### Return Value

### Method new

Initializes a new instance of the SqlSyncPending class.

    public void new()

## Class SqlSystem
    class SqlSystem extends Object

The SqlSystem class holds information about the active SQL system, typically login information.

### Remarks

### Examples

### Methods

| Method                                                                                                                                   | Description                                                                                             |
|------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------|
| public LoginProperty createLoginProperty()                                                                                               | Creates the login property to the Microsoft Dynamics 365 for Operations5 for Operations database.                                       |
| public DatabaseId databaseId()                                                                                                           | Returns the Microsoft Dynamics 365 for Operations5 for Operations ID for the database vendor used as the SQL database backend.          |
| public str databaseName()                                                                                                                | Returns the name of the database vendor used as the SQL database backend.                               |
| public boolean dbRequestedUnicodeEnabled()                                                                                               | Retrieves the value that indicates if Unicode is supported in the database.                             |
| public str filenameDeadlocks(str Userid)                                                                                                 | Retrieves the name of the user specific deadlocks trace logfile.                                        |
| public str filenameQuerytimelimit(str Userid)                                                                                            | Retrieves the name of the user specific querytime limit logfile.                                        |
| public str filenameSqlTrace(str Userid)                                                                                                  | Retrieves the filename of the SQL trace log file for specific user.                                     |
| public str filenameWarnings(str Userid)                                                                                                  | Retrieves the name of the user specific warnings log file.                                              |
| public str logfileName(\[boolean fromCommandline\])                                                                                      | Retrieves the name of the standard Microsoft Dynamics 365 for Operations5 for Operations SQL error log file.                            |
| public str loginConnectString()                                                                                                          | Retrieves the full ODBC connection string.                                                              |
| public str loginDatabase()                                                                                                               | Retrieves the name of the database currently connected to.                                              |
| public str loginDSN()                                                                                                                    | Retrieves the open database connectivity (ODBC) data source name (DSN) used to connect to the database. |
| public str loginName()                                                                                                                   | Retrieves the user name that is used to log-in to the database.                                         |
| public str loginServer()                                                                                                                 | Retrieves the name of the database server currently connected to.                                       |
| public str monocaseFmt(\[TableId tableId\], \[FieldId fieldId\], \[boolean includingFieldName\], \[boolean considerSystemVariables\])    | Retrieves the format string that is used for casting the string to one case (e.g. "NLS\_LOWER(%1)").    |
| public str sqlLiteral(AnyType data, \[boolean forWhereClause\], \[boolean likeOperand\], \[boolean rightJustify\], \[int stringLength\]) | Formats the input AX datatype to correct SQL type.                                                      |
| ::public static boolean clusteredIndexes()                                                                                               |                                                                                                         |
| ::public static str databaseBackendDesc()                                                                                                |                                                                                                         |
| ::public static DatabaseId databaseBackendId()                                                                                           |                                                                                                         |
| ::public static str databaseBackendName()                                                                                                |                                                                                                         |
| ::public static DatabaseCLI databaseCallLevelInterface()                                                                                 |                                                                                                         |
| ::public static int databaseHints(\[int new\_hint\_value\])                                                                              |                                                                                                         |
| ::public static boolean functionalIndexes()                                                                                              |                                                                                                         |
| ::public static str modelDatabaseBackendName()                                                                                           | Retrieves the name of the model database AOS currently connected to.                                    |
| ::public static str managedConnectionString()                                                                                            |                                                                                                         |
| public void new()                                                                                                                        | Initializes a new instance of the SqlSystem class.                                                      |
| public void logfileWrite(str Text)                                                                                                       | Writes a text string into the standard Microsoft Dynamics 365 for Operations5 for Operations SQL error logfile.                         |

### Method createLoginProperty

Creates the login property to the Microsoft Dynamics 365 for Operations5 for Operations database.

    public LoginProperty createLoginProperty()

#### Return Value

The login property that was created.

### Method databaseId

Returns the Microsoft Dynamics 365 for Operations5 for Operations ID for the database vendor used as the SQL database backend.

    public DatabaseId databaseId()

#### Return Value

The Microsoft Dynamics 365 for Operations5 for Operations ID for the database vendor used as the SQL database backend.

#### Remarks

If Microsoft Dynamics 365 for Operations5 for Operations cannot determine the database vendor for any reason, the enumeration DbBackend::UNKNOWN is returned.

### Method databaseName

Returns the name of the database vendor used as the SQL database backend.

    public str databaseName()

#### Return Value

The name of the database vendor used as the SQL database backend.

### Method dbRequestedUnicodeEnabled

Retrieves the value that indicates if Unicode is supported in the database.

    public boolean dbRequestedUnicodeEnabled()

#### Return Value

The value that indicates if Unicode is suported in the database.

### Method filenameDeadlocks

Retrieves the name of the user specific deadlocks trace logfile.

    public str filenameDeadlocks(str Userid)

#### Parameters

Userid  

#### Return Value

The name of the user specific to deadlocks trace log file.

### Method filenameQuerytimelimit

Retrieves the name of the user specific querytime limit logfile.

    public str filenameQuerytimelimit(str Userid)

#### Parameters

Userid  

#### Return Value

The name of the user specific querytime limit logfile.

### Method filenameSqlTrace

Retrieves the filename of the SQL trace log file for specific user.

    public str filenameSqlTrace(str Userid)

#### Parameters

Userid  
The User Id.

#### Return Value

The filename of SQL trace log.

### Method filenameWarnings

Retrieves the name of the user specific warnings log file.

    public str filenameWarnings(str Userid)

#### Parameters

Userid  
The identifier of interested user.

#### Return Value

The name of the user specific warnings log file.

### Method logfileName

Retrieves the name of the standard Microsoft Dynamics 365 for Operations5 for Operations SQL error log file.

    public str logfileName([boolean fromCommandline])

#### Parameters

fromCommandline  
A boolean value. Passing a non-zero value as parameter makes the call return the logfile name passed on the command line; optional.

#### Return Value

The file name of the standard Microsoft Dynamics 365 for Operations5 for Operations SQL error log file.

#### Remarks

In version 2.11 or higher, an empty string is returned (for backward compatibility). Use the filenameSqlError method to retrieve the log file name.

### Method loginConnectString

Retrieves the full ODBC connection string.

    public str loginConnectString()

#### Return Value

The full ODBC connection string.

### Method loginDatabase

Retrieves the name of the database currently connected to.

    public str loginDatabase()

#### Return Value

The name of the database currently connected to.

#### Examples

    { 
        SqlSystem SqlSystem = new SqlSystem(); 
        print SqlSystem.loginDatabase(); 
    }

### Method loginDSN

Retrieves the open database connectivity (ODBC) data source name (DSN) used to connect to the database.

    public str loginDSN()

#### Return Value

The name of the ODBC data source name that is used for connecting to the database.

#### Remarks

The default DSN is "BMSDSN".

#### Examples

    { 
        SqlSystem SqlSystem = new SqlSystem(); 
        print SqlSystem.loginDSN(); 
    }

### Method loginName

Retrieves the user name that is used to log-in to the database.

    public str loginName()

#### Return Value

The user name that is used to log-in to the database.

#### Examples

    { 
        SqlSystem SqlSystem = new SqlSystem(); 
        print SqlSystem.loginName(); 
    }

### Method loginServer

Retrieves the name of the database server currently connected to.

    public str loginServer()

#### Return Value

The name of the database currently connected to.

#### Remarks

An empty string is returned if the database does not support a server concept.

#### Examples

    { 
        SqlSystem SqlSystem = new SqlSystem(); 
        print SqlSystem.loginServer(); 
    }

### Method monocaseFmt

Retrieves the format string that is used for casting the string to one case (e.g. "NLS\_LOWER(%1)").

    public str monocaseFmt([TableId tableId], [FieldId fieldId], [boolean includingFieldName], [boolean considerSystemVariables])

#### Parameters

tableId  

<!-- -->

fieldId  

<!-- -->

includingFieldName  

<!-- -->

considerSystemVariables  

#### Return Value

The format string that is used for casting the string to one case.

#### Remarks

Microsoft Dynamics 365 for Operations5 for Operations style for placeholder(s) is used (i.e. "%1").

### Method sqlLiteral

Formats the input AX datatype to correct SQL type.

    public str sqlLiteral(AnyType data, [boolean forWhereClause], [boolean likeOperand], [boolean rightJustify], [int stringLength])

#### Parameters

data  
The length of the string.By default equals zero.

<!-- -->

forWhereClause  
The length of the string.By default equals zero.

<!-- -->

likeOperand  
The length of the string.By default equals zero.

<!-- -->

rightJustify  
The length of the string.By default equals zero.

<!-- -->

stringLength  
The length of the string.By default equals zero.

#### Return Value

The formatted SQL type string.

### Method clusteredIndexes

    public static boolean clusteredIndexes()

#### Return Value

### Method databaseBackendDesc

    public static str databaseBackendDesc()

#### Return Value

### Method databaseBackendId

    public static DatabaseId databaseBackendId()

#### Return Value

### Method databaseBackendName

    public static str databaseBackendName()

#### Return Value

### Method databaseCallLevelInterface

    public static DatabaseCLI databaseCallLevelInterface()

#### Return Value

### Method databaseHints

    public static int databaseHints([int new_hint_value])

#### Parameters

new\_hint\_value  

#### Return Value

### Method functionalIndexes

    public static boolean functionalIndexes()

#### Return Value

### Method modelDatabaseBackendName

Retrieves the name of the model database AOS currently connected to.

    public static str modelDatabaseBackendName()

#### Return Value

The name of the model database currently connected to.

### Method managedConnectionString

    public static str managedConnectionString()

#### Return Value

### Method new

Initializes a new instance of the SqlSystem class.

    public void new()

### Method logfileWrite

Writes a text string into the standard Microsoft Dynamics 365 for Operations5 for Operations SQL error logfile.

    public void logfileWrite(str Text)

#### Parameters

Text  
The text (for example, a bookmark) to write to the logfile.

#### Remarks

Following an error situation of any kind (which is logged in the logfile), you may want to insert a personal bookmark that explains the current scenario.

#### Examples

    static void myExample(Args _args) 
    { 
        SqlSystem SqlSystem; 
        SqlSystem = new SqlSystem(); 
        SqlSystem.logfileWrite("Recheck the returned data."); 
    }

## Class SSRSReportAutoDesignNode
    class SSRSReportAutoDesignNode extends SSRSReportDesignNode

### Remarks

### Examples

### Methods

| Method                                              | Description                                                                        |
|-----------------------------------------------------|------------------------------------------------------------------------------------|
| public str getCrossReferences()                     | Retrieves the cross-references by using the specified SSRSReportDesignNode object. |
| public void setCrossReferences(str crossReferences) | Sets the cross-references by using the specified SSRSReportDesignNode object.      |

### Method getCrossReferences

Retrieves the cross-references by using the specified SSRSReportDesignNode object.

    public str getCrossReferences()

#### Return Value

The cross-references in XML format.

### Method setCrossReferences

Sets the cross-references by using the specified SSRSReportDesignNode object.

    public void setCrossReferences(str crossReferences)

#### Parameters

crossReferences  
The cross-references in XML format.

#### Remarks

This method only updates the cross-reference XML stored on the specified SSRSReportDesignNode object. It does not update the cross-reference system.

## Class SSRSReportConceptNode
    class SSRSReportConceptNode extends xResourceNode

The SSRSReportConceptNode class lets you create, read, update, and delete SSRS reports, data sources, style templates, and images in the Microsoft Dynamics 365 for Operations5 for Operations Application Object Tree (AOT).

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                                     | Description                                                                   |
|------------------------------------------------------------|-------------------------------------------------------------------------------|
| public str AOTgetSource()                                  | Returns the source code of this node.                                         |
| public str getCrossReferences()                            | Retrieves the cross-references by the specified SSRSReportConceptNode object. |
| public void allowCaching(\[boolean allow\])                |                                                                               |
| public void setCrossReferences(str crossReferences)        | Sets the cross-references by the specified SSRSReportConceptNode object.      |
| public void AOTsetSource(str source, \[boolean isStatic\]) | Sets the source code of this node.                                            |

### Method AOTgetSource

Returns the source code of this node.

    public str AOTgetSource()

#### Return Value

The string that contains the source code, if any; otherwise, nullNothingnullptrunita null reference (Nothing in Visual Basic).

#### Remarks

This function is overridden by nodes that have source code.

### Method getCrossReferences

Retrieves the cross-references by the specified SSRSReportConceptNode object.

    public str getCrossReferences()

#### Return Value

The cross-references by the specified SSRSReportConceptNode object in XML format.

### Method allowCaching

    public void allowCaching([boolean allow])

#### Parameters

allow  

### Method setCrossReferences

Sets the cross-references by the specified SSRSReportConceptNode object.

    public void setCrossReferences(str crossReferences)

#### Parameters

crossReferences  
The cross-references by the specified SSRSReportConceptNode object in XML format.

#### Remarks

This method only updates the cross-reference XML stored on the specified SSRSReportConceptNode object. It does not update the cross-reference system.

### Method AOTsetSource

Sets the source code of this node.

    public void AOTsetSource(str source, [boolean isStatic])

#### Parameters

source  
The value that specifies whether the method is static; optional.

<!-- -->

isStatic  
The value that specifies whether the method is static; optional.

#### Remarks

This method is overridden by nodes that have source code.

## Class SSRSReportDesignNode
    class SSRSReportDesignNode extends xResourceNode

The SSRSReportDesignNode class lets you create, read, update, and delete Microsoft SQL Server Reporting Services reports, data sources, style templates, and images in the Microsoft Dynamics 365 for Operations5 for Operations Application Object Tree (AOT).

### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before calling this API.

### Examples

### Methods

| Method                                              | Description                                                                  |
|-----------------------------------------------------|------------------------------------------------------------------------------|
| public str getCrossReferences()                     | Retrieves the cross-references by the specified SSRSReportDesignNode object. |
| public void setCrossReferences(str crossReferences) | Sets the cross-references by the specified SSRSReportDesignNode object.      |

### Method getCrossReferences

Retrieves the cross-references by the specified SSRSReportDesignNode object.

    public str getCrossReferences()

#### Return Value

The cross-references by the specified SSRSReportDesignNode object in XML format.

### Method setCrossReferences

Sets the cross-references by the specified SSRSReportDesignNode object.

    public void setCrossReferences(str crossReferences)

#### Parameters

crossReferences  
The cross-references by the specified SSRSReportDesignNode object in XML format.

#### Remarks

This method only updates the cross-reference XML stored on the specified SSRSReportDesignNode object. It does not update the cross-reference system.

## Class SSRSReportPrecisionDesignNode
    class SSRSReportPrecisionDesignNode extends SSRSReportDesignNode

### Remarks

### Examples

### Methods

| Method                                              | Description                                                                  |
|-----------------------------------------------------|------------------------------------------------------------------------------|
| public str getCrossReferences()                     | Retrieves the cross-references to the specified SSRSReportDesignNode object. |
| public void setCrossReferences(str crossReferences) | Sets the cross-references to the specified SSRSReportDesignNode object.      |

### Method getCrossReferences

Retrieves the cross-references to the specified SSRSReportDesignNode object.

    public str getCrossReferences()

#### Return Value

The cross-references to the specified SSRSReportDesignNode object in XML format.

### Method setCrossReferences

Sets the cross-references to the specified SSRSReportDesignNode object.

    public void setCrossReferences(str crossReferences)

#### Parameters

crossReferences  
The cross-references to the specified SSRSReportDesignNode object in XML format.

#### Remarks

This method only updates the cross-reference XML that is stored on the specified SSRSReportDesignNode object. It does not update the cross-reference system.

## Class Statement
    class Statement extends Object

The Statement class executes a static SQL statement and obtains the results it produces.

### Remarks

Only one per Statement can be open at any point in time. Therefore, if the reading of one ResultSet is interleaved with the reading of another, each must have been generated by different Statements. Record and field level securities are not enforced on the Statement class. Therefore, make sure you are not exposing data returned to the user without doing explicit security validation. All statement executed methods implicitly close a statement's current ResultSet if an open one exists.

### Examples

    static void example() 
    { 
        Connection Con; 
        Statement Stmt; 
        ResultSet R; 
        SqlStatementExecutePermission perm; 
        str sql = 'SELECT VALUE FROM SQLSYSTEMVARIABLES'; 
        Con = new Connection(); 
        Stmt = Con.createStatement(); 
        perm = new SqlStatementExecutePermission(sql); 
        perm.assert(); 
        R = Stmt.executeQuery(sql); 
        while ( R.next() ) 
        { 
            print R.getString(1); 
        } 
    }

### Methods

| Method                                       | Description                                                                                       |
|----------------------------------------------|---------------------------------------------------------------------------------------------------|
| public ResultSet executeQuery(str statement) | Executes an SQL statement that returns an instance of the .                                       |
| public int executeUpdate(str statement)      | Executes a SQL INSERT, UPDATE, or DELETE statement.                                               |
| public int getLastError()                    | Retrieves the error code returned by the SQL database backend for the last SQL operation.         |
| public str getLastErrorText()                | Retrieves the error text that is returned by the SQL database backend for the last SQL operation. |
| public int getMaxFieldSize()                 | Returns the current maximum column size limit, if any.                                            |
| public void close()                          | Releases the database resources of a statement object.                                            |
| public void setMaxFieldSize(int max)         | Sets the maximum column size limit.                                                               |

### Method executeQuery

Executes an SQL statement that returns an instance of the .

    public ResultSet executeQuery(str statement)

#### Parameters

statement  
The string that contains the SQL statement that is used to retrieve the result set.

#### Return Value

The object that contains the data returned from the query.

#### Remarks

If users control input to the executeQuery method, an SQL injection threat can occur. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the . The following are safer alternatives for executing SQL statements:

-   Queries
-   Views
-   X++ select statements

Record level security is not enforced on the Statement class. If data is exposed to the user, perform explicit security validation.

#### Examples

The following example performs an SQL query on CustTable, which runs on the server. The result of the query is stored in the resultSet object.

    server static void main(Args _args) 
    { 
        DictTable  dictTable; 
        Connection connection; 
        Statement  statement; 
        str        sql; 
        ResultSet  resultSet; 
        SqlStatementExecutePermission perm; 
        dictTable = new DictTable(tableNum(CustTable)); 
        if (dictTable != null) 
            { 
               connection = new Connection(); 
               sql = strfmt( "SELECT * FROM %1", dictTable.name(DbBackend::Sql) ); 
               perm = new SqlStatementExecutePermission(sql); 
               // Check for permission to use the statement. 
               perm.assert(); 
               statement = connection.createStatement(); 
               resultSet = statement.executeQuery(sql); 
               // End the scope of the assert call. 
               CodeAccessPermission::revertAssert(); 
            } 
    }

### Method executeUpdate

Executes a SQL INSERT, UPDATE, or DELETE statement.

    public int executeUpdate(str statement)

#### Parameters

statement  
The string that contains the SQL statement being passed to the database.

#### Return Value

An updated row count; otherwise, 0 (zero) for SQL statements that return nothing.

#### Remarks

SQL statements that return nothing, such as SQLDDL statements, can also be executed. If users control input to the executeUpdate method, an SQL injection thread can occur. Therefore, this method runs under Code Access Security. Calls to this method on the server require permission from the . The following are safer alternatives for interacting with the database:

-   Queries
-   Views
-   X++ select statements

Record level security is not enforced on the Statement class. If data is exposed to the user, perform explicit security validation.

### Method getLastError

Retrieves the error code returned by the SQL database backend for the last SQL operation.

    public int getLastError()

#### Return Value

The error code returned by the SQL database backend for the last SQL operation; or 0 for success.

#### Examples

    static void StatementGetLastError()  
    { 
        str sql, sql2; 
        UserConnection Connection = new UserConnection(); 
        Statement Statement = Connection.createStatement(); 
        boolean clear_infolog = false; 
        print "-Delete-a-non-existing-record-(valid statement)-----------"; 
        sql = "delete from zipcode where Recid = 2"; 
        new SqlStatementExecutePermission(sql).assert(); 
        Statement.executeUpdate(sql); 
        print " Error code was: ", Statement.getLastError(); 
        print " Error message was '", Statement.getLastErrorText(), "'"; 
        try 
        { 
            print "\n"; 
            print "-Delete-from-a-non-existing-table-(invalid statement)---    --"; 
            sql2 = "delete from StrangeTable07"; 
            new SqlStatementExecutePermission(sql2).assert(); 
            Statement.executeUpdate(sql2); 
        } 
        catch (exception::Error) 
        { 
            print "Exception was caught:"; 
            print " Error code was: ", Statement.getLastError(); 
            print " Error message was '", Statement.getLastErrorText(), "'"; 
        } 
        CodeAccessPermission::revertAssert(); 
        pause; 
    }

### Method getLastErrorText

Retrieves the error text that is returned by the SQL database backend for the last SQL operation.

    public str getLastErrorText()

#### Return Value

The error text that is provided by the SQL database for the last SQL operation.

### Method getMaxFieldSize

Returns the current maximum column size limit, if any.

    public int getMaxFieldSize()

#### Return Value

The current maximum column size limit; 0 means unlimited.

#### Remarks

The maxFieldSize limit (in bytes) is the maximum amount of data returned for any column value; it only applies to binary, varbinary, longvarbinary, char, varchar, and longvarchar columns. If the limit is exceeded, the excess data is silently discarded.

### Method close

Releases the database resources of a statement object.

    public void close()

### Method setMaxFieldSize

Sets the maximum column size limit.

    public void setMaxFieldSize(int max)

#### Parameters

max  
The new max column size limit; 0 means unlimited.

#### Remarks

The maxFieldSize limit (in bytes) is set to limit the size of data that can be returned for any column value; it only applies to binary, varbinary, longvarbinary, char, varchar, and longvarchar fields. If the limit is exceeded, the excess data is silently discarded. For maximum portability, use values greater than 256.

## Class Struct
    class Struct extends Object

A struct holds several values of any X++ type, to group the information about a specific entity.

### Remarks

A struct (short for structure) is an entity that can hold several values of any X++ type. Structs are used to group information about a specific entity. For example, you might want to store information about a customer's name, age and address and then treat this compound information as one item. The items in a struct are specified by a data type and a name. Items are added when the struct is created by using the new method, or they are created after the struct has been created by using the add method. If you add an item by using the add method, you specify the value for the item at the same time, and the data type is inferred from this value. If you add an item during the instantiation of the struct, you need to use the value or the valueIndex method to assign a value to it. The items in a struct can be of any of the data types found in the Types system enum, including: string, integer, real, date, container, record, and class. The items in a struct are arranged in alphabetical order of the item names. The fields in a struct can be traversed by using the fields, fieldName, and fieldType methods. Structs can be packed into containers and later restored by using the Struct::create method. Structs have some similarities to X++ containers. However, a container is a value type and is built into the X++ language. You can create nested containers, but you cannot create nested structs. X++ classes can store information in much the same way as structs. But although classes can supply methods to manipulate the data, no such facility is provided for structs, and there is no concept of overriding or extension. Classes can only be created in the AOT, but structs exist solely in the context of the code in which they are created. Class member variables are private to the class, so accessor functions must be coded for them for the values to be used from outside the class. The items within a struct are publicly accessible.

### Examples

The following example creates a struct with two items and then assigns values to those items. A new item is then added by using the Struct.add method; the data type of the item is inferred from the value assigned to it. The struct is then packed into a container and used to create a new struct, a copy of the original struct.

    { 
        Struct s = new struct ("int age; str name"); 
        Struct copy; 
        container c; 
        int i; 
        // Add values to the items 
        s.value("age", 25); 
        s.value("name", "Jane Dow"); 
      // Add a new item; data type is inferred from value 
        s.add("Shoesize", 45); 
        // Print the definition of the struct 
        print s.definitionString(); 
        // Prints the type and name of all items in the struct 
        for (i =  1;   i <= s.fields();i++) 
        { 
             print s.fieldType(i), " ", s.fieldName(i); 
        }  
        // Pack the struct into a container and restore it into copy 
        c = s.pack(); 
        copy = Struct::create(c); 
        print copy.definitionString(); 
        pause; 
    }

### Methods

| Method                                                        | Description                                                                                   |
|---------------------------------------------------------------|-----------------------------------------------------------------------------------------------|
| public boolean add(str fieldName, AnyType value)              | Adds a new item to the struct and assigns the specified value to it.                          |
| public str definitionString()                                 | Returns a description of the names and types of the elements in the struct.                   |
| public boolean exists(str fieldName)                          | Determines whether a particular item exists in a struct.                                      |
| public str fieldName(int index)                               | Returns the name of the item in the struct at the specified position.                         |
| public int fields()                                           | Returns the number of items in the struct.                                                    |
| public Types fieldType(int index)                             | Returns the data type of the item in the struct at the specified position.                    |
| public int index(str fieldName)                               | Calculates the position of an item in the struct based on its name.                           |
| public container pack()                                       | Serializes the current instance of the Struct class.                                          |
| public boolean remove(str fieldName)                          | Removes an item from a struct.                                                                |
| public str toString()                                         | Returns a string that describes the contents of the struct.                                   |
| public AnyType value(str fieldName, \[AnyType value\])        | Gets or sets the value for a specified item in a struct.                                      |
| public str valueImage(int index)                              | Returns a string that describes the value of the item at a particular position in the struct. |
| public AnyType valueIndex(int index, \[AnyType value\])       | Gets or sets the value of the item at a specified position in a struct.                       |
| public str xml(\[int indent\])                                | Returns an XML string that represents the current object.                                     |
| ::public static Struct create(container container)            | Creates a struct from a container that is obtained from a prior call to Struct.pack.          |
| ::public static Struct createFromXML(Object xmlnode)          |                                                                                               |
| ::public static boolean equal(Struct struct1, Struct struct2) | Determines whether two structs are equal.                                                     |
| ::public static Struct merge(Struct struct1, Struct struct2)  | Combines two structs to create a new struct.                                                  |
| public void new(VarArg specifier)                             | Creates a struct.                                                                             |

### Method add

Adds a new item to the struct and assigns the specified value to it.

    public boolean add(str fieldName, AnyType value)

#### Parameters

fieldName  
The value to assign to the new item. This value defines the type of the item.

<!-- -->

value  
The value to assign to the new item. This value defines the type of the item.

#### Return Value

true if the value has been added to the struct; false if the value could not be added (if it already existed in the struct).

#### Remarks

The type of the value is inferred from content of the value. The items in a struct are arranged in alphabetical order according to the item names. The value of an item in a struct can be changed by using the Struct.value or the Struct.valueIndex method.

#### Examples

The following example creates a struct with two items name and age fields and assigns values to those items. The add method is then used to create an additional item the shoeSize variable, with a value of 43. The type of the value determines the type of the new item, int.

    { 
        Struct s = new Struct ("str name; int age"); 
        // Prints number of items (2) 
        print s.fields(); 
        // Values are assigned to the two items 
        s.value("name", "John"); 
        s.value("age", 34); 
        //Another item is added to the struct 
        s.add("shoeSize", 43); 
        // Prints number of item (3) 
        print s.fields(); 
        // Prints a description of the items in the struct 
        print s.definitionString(); 
        pause; 
    }

### Method definitionString

Returns a description of the names and types of the elements in the struct.

    public str definitionString()

#### Return Value

A string that contains a definition of the struct.

#### Remarks

You can use the definitionString method to create a copy of a struct by using the syntax: newStruct = new struct(oldStruct.definitionString());

### Method exists

Determines whether a particular item exists in a struct.

    public boolean exists(str fieldName)

#### Parameters

fieldName  
The name of the item to check for.

#### Return Value

true if the item exists in the struct; otherwise, false.

#### Examples

The following example tests whether a particular item exists in a struct, and if not, it adds the item and assigns a value to it using the Struct.add method.

    client server static void setProp( 
        Struct     properties, 
        str        name, 
        anytype   value 
        ) 
    { 
        if (! properties.exists(name)) 
        { 
            properties.add(name,nullValue(value)); 
        } 
        properties.value(name,value); 
    }

### Method fieldName

Returns the name of the item in the struct at the specified position.

    public str fieldName(int index)

#### Parameters

index  
The position in the struct at which you want to retrieve the item name.

#### Return Value

The name of the item at the position specified by index.

#### Remarks

If index is not found, an empty string is returned.

#### Examples

The following example creates a struct from a container and then uses the Struct.fields method to iterate through the contents of the container. The fieldName method is used to test the name of each item in the struct, and a specific action is run depending on the value of this name.

    boolean unpack(container packed) 
    { 
        Struct      unpackedProperties; 
        container   structCon; 
        Counter     i; 
        [#currentList,structCon] = packed; 
        unpackedProperties = Struct::create(structCon); 
        for (i=1;i<=unpackedProperties.fields();i++) 
        { 
            switch (unpackedProperties.fieldName(i)) 
            { 
                case #closedOk: 
                    break; 
                case #PropertyCaption: 
                    if (! dialogForm  
                        || dialogForm  
                        && ! dialogForm.form().design().caption()) 
                        this.caption(unpackedProperties.valueIndex(i)); 
                    break; 
                case #dialogFormname: 
                    // Do nothing 
                    break; 
                case #PropertyAlwaysOnTop: 
                    this.alwaysOnTop(unpackedProperties.valueIndex(i)); 
                    break; 
                case #PropertyWindowType: 
                    this.windowType(unpackedProperties.valueIndex(i)); 
                    break; 
                case #defaultButton: 
                    this.defaultButton(unpackedProperties.valueIndex(i)); 
                    break; 
                default: 
                    throw error(strfmt( 
                        "@SYS67326",unpackedProperties.fieldName(i), 
                         classId2Name(classidget(this)))); 
            } 
        } 
        return true; 
    }

### Method fields

Returns the number of items in the struct.

    public int fields()

#### Return Value

The number of items in the struct.

#### Remarks

To find the position of an item in a struct, use the Struct.index method.

#### Examples

The following example creates a struct from a container and then uses the fields method to iterate through the contents of the container.

    boolean unpack(container packed) 
    { 
        Struct      unpackedProperties; 
        container   structCon; 
        Counter     i; 
        [#currentList,structCon] = packed; 
        unpackedProperties = Struct::create(structCon); 
        for (i=1;i<=unpackedProperties.fields();i++) 
        { 
            switch (unpackedProperties.fieldName(i)) 
            { 
                case #closedOk: 
                    break; 
                case #PropertyCaption: 
                    if (! dialogForm  
                        || dialogForm  
                        && ! dialogForm.form().design().caption()) 
                        this.caption(unpackedProperties.valueIndex(i)); 
                    break; 
                case #dialogFormname: 
                    // Do nothing 
                    break; 
                case #PropertyAlwaysOnTop: 
                    this.alwaysOnTop(unpackedProperties.valueIndex(i)); 
                    break; 
                case #PropertyWindowType: 
                    this.windowType(unpackedProperties.valueIndex(i)); 
                    break; 
                case #defaultButton: 
                    this.defaultButton(unpackedProperties.valueIndex(i)); 
                    break; 
                default: 
                    throw error(strfmt( 
                        "@SYS67326",unpackedProperties.fieldName(i), 
                         classId2Name(classidget(this)))); 
            } 
        } 
        return true; 
    }

### Method fieldType

Returns the data type of the item in the struct at the specified position.

    public Types fieldType(int index)

#### Parameters

index  
The position in the struct that you want to retrieve the data type for.

#### Return Value

The data type of the item at the position specified by index.

#### Remarks

The possible values are supplied by the system enum. If index is not found, the return value is Types::void. You can determine the position of a particular item in a struct by using the Struct.index method

### Method index

Calculates the position of an item in the struct based on its name.

    public int index(str fieldName)

#### Parameters

fieldName  
The name of the item for which to return the position.

#### Return Value

The position of the item.

#### Remarks

The items in a struct are arranged in alphabetical order according to the item names. If there is no item with the name fieldName, 0 is returned.

### Method pack

Serializes the current instance of the Struct class.

    public container pack()

#### Return Value

A container that contains the current instance of the Struct class.

#### Remarks

The pack method is called on each field that holds an object, to yield a (sub) container. The struct may be recreated from the container by using the Struct.create method.

#### Examples

The following example creates a struct with two items in it (name and age), and then adds values to the items. The struct is packed into a container, and this container is then used to create a new struct.

    {  
        container packedStruct;  
        Struct s1, s = new Struct ("str name; int age"); 
        s.value ("name", "Jane Dow");  
        s.value ("age", 34); 
        // Struct is packed into a container 
        packedStruct = s.pack();  
        // A new struct is created from the container 
        s1 = Struct::create(packedStruct); 
        // Both structs have the same contents 
        print s.toString();  
        print s1.toString();  
        pause;  
    }

### Method remove

Removes an item from a struct.

    public boolean remove(str fieldName)

#### Parameters

fieldName  
The name of the item you want to remove.

#### Return Value

true if the item was found (and removed); otherwise, false.

#### Remarks

The name you specify for the fieldName parameter must be the name of the item as it was specified in the instantiation of the struct or the name of the item as it was added using the Struct.add method. The name must be enclosed in quotes (" ").

#### Examples

The following example creates a struct with two items in it and prints a description of these items. One of the items is then removed by using the remove method.

    { 
        Struct s = new Struct ("str name; int age"); 
        // Values are assigned to the two items 
        s.value("name", "John"); 
        s.value("age", 34); 
        // Prints a description of the items in the struct 
        print s.definitionString(); 
        pause; 
        // Removes the name field 
        s.remove("name"); 
        // Describes remaining items in the struct 
        print s.definitionString(); 
        pause; 
    }

### Method toString

Returns a string that describes the contents of the struct.

    public str toString()

#### Return Value

A string that describes the contents of the struct.

### Method value

Gets or sets the value for a specified item in a struct.

    public AnyType value(str fieldName, [AnyType value])

#### Parameters

fieldName  
The value to assign to the item; optional.

<!-- -->

value  
The value to assign to the item; optional.

#### Return Value

The value of the specified item.

#### Remarks

An exception is raised if there is no item with the specified name in the struct. The name of an item in a struct may be retrieved by using the Struct.fieldName method. You can add a new item to a struct and assign a value to it at the same time by using the Struct.add method. To assign a new value to an item based on its position in the struct, use the Struct.valueIndex method.

#### Examples

The following example creates a struct with two items in it and then uses the value method to assign values to those two items.

    { 
        Struct s = new Struct ("str name; int age"); 
        // Set the values 
        s.value("name", "Jane Dow"); 
        s.value("age", 34); 
        // Print the values 
        print s.value("name"); 
        print s.value("age"); 
        pause; 
    }

### Method valueImage

Returns a string that describes the value of the item at a particular position in the struct.

    public str valueImage(int index)

#### Parameters

index  
The position of the item that you want to return a description for.

#### Return Value

A string that describes the value of the item.

#### Remarks

The items in a struct are in alphabetical order according to the names of the items. If there is no item at the position specified by index, an exception is raised.

### Method valueIndex

Gets or sets the value of the item at a specified position in a struct.

    public AnyType valueIndex(int index, [AnyType value])

#### Parameters

index  
The value to assign to the item at the position specified by index; optional.

<!-- -->

value  
The value to assign to the item at the position specified by index; optional.

#### Return Value

The value of the item at the position specified by index.

#### Remarks

An exception is raised if there is no item at the position specified by index. The position of an item in a struct can be retrieved by using the Struct.index method.

### Method xml

Returns an XML string that represents the current object.

    public str xml([int indent])

#### Parameters

indent  
The amount of indentation of the returned XML string; optional.

#### Return Value

An XML string that represents the current object.

#### Remarks

This method can be overridden to return values that are meaningful for that type.

### Method create

Creates a struct from a container that is obtained from a prior call to Struct.pack.

    public static Struct create(container container)

#### Parameters

container  
A container that contains the packed struct.

#### Return Value

A struct equal to the one that was packed into the specified container.

#### Remarks

If the struct contains objects, these objects must have an unpack method that is called to re-establish their internal state from the container.

#### Examples

The following example creates a struct with two items in it (name and age), and then adds values to the items. The struct is packed into a container, and this container is then unpacked to create a new struct.

    {  
        container packedStruct;  
        Struct s1, s = new Struct ("str name; int age"); 
        s.value ("name", "Jane Dow");  
        s.value ("age", 34); 
        // Struct is packed into a container 
        packedStruct = s.pack();  
        // A new struct is created from the container 
        s1 = Struct::create(packedStruct); 
        // Both structs have the same contents 
        print s.toString();  
        print s1.toString();  
        pause;  
    }

### Method createFromXML

    public static Struct createFromXML(Object xmlnode)

#### Parameters

xmlnode  

#### Return Value

### Method equal

Determines whether two structs are equal.

    public static boolean equal(Struct struct1, Struct struct2)

#### Parameters

struct1  
The second of the two structs to be compared.

<!-- -->

struct2  
The second of the two structs to be compared.

#### Return Value

true if the structs are equal; otherwise, false.

#### Remarks

Two structs are equal if they have the same number of fields, the field names are the same, and each field is the same type and has the same value.

### Method merge

Combines two structs to create a new struct.

    public static Struct merge(Struct struct1, Struct struct2)

#### Parameters

struct1  
The struct that will be added to the end of the first struct to create a new struct.

<!-- -->

struct2  
The struct that will be added to the end of the first struct to create a new struct.

#### Return Value

The new struct.

#### Remarks

struct2 is added to the end of struct1. This means that the order of the items in the new struct will be: all the items in struct1, arranged in alphabetical order of the item names, followed by all the items in struct2, arranged in alphabetical order of the item names. If both structs contain an item with the same name, only the item from the first struct will be included.

#### Examples

The following example creates two structs called person and address, and then merges them into a new struct called allInfo.

    { 
        container packedStruct; 
        Struct person = new Struct ("str name; int age"); 
        Struct address = new Struct ("str street; str city; str country"); 
        Struct allInfo; 
        person.value ("name", "Jane Dow"); 
        person.value ("age", 34); 
        address.value ("street", "Downing street 10"); 
        address.value ("country", "Great Britain"); 
        address.value ("city", " London"); 
        allInfo = Struct::merge(person, address); 
        print allInfo.toString(); 
        pause; 
    }

### Method new

Creates a struct.

    public void new(VarArg specifier)

#### Parameters

specifier  
One or more pairs that specify the data type of an item followed by the name of the item as a string.

#### Remarks

The data type of the item can be specified using the name of a primitive data type or by using the system enum. The items in a struct can be of any of the data types found in the Types system enum, including: string, integer, real, date, container, record, and class. You can create a copy of a struct by using the Struct.definitionString method to create a new struct, as illustrated in the example below. After you have created a struct, you can add new items using the Struct.add method and set the value of items in the struct by using the Struct.value or Struct.valueIndex method.

#### Examples

The following example creates two structs with the same definition and then adds 2 values and an additional item and value to one of them (s1). This struct is then copied to create a new struct by using the Struct.definitionString method.

    { 
        Struct s1, s2, s3; 
        // The two constructors below create the same struct 
        s1 = new Struct(Types::Integer, "age", Types::String, "name"); 
        s2 = new Struct ("int age; str name"); 
        // Print the definitions 
        print s1.definitionString(); 
        print s2.definitionString(); 
        s1.value("age", 25); 
        s1.value("name", "Jane Dow"); 
        // Add a field at runtime 
        s1.add("Shoesize", 45); 
        print s1.definitionString(); 
        print s1.toString(); 
        // Create a container with age, name and shoesize, 
        // using definitionString 
        s3 = new struct(s1.definitionString()); 
        print s3.definitionString(); 
        pause; 
    }

## Class SurrogateFKReplacementHelper
    class SurrogateFKReplacementHelper extends Object

### Remarks

### Examples

### Methods

| Method                                                                                                                                                                                                             | Description                                     |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------|
| public Map addDefaultRequiredJoins(QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)                                                                                             |                                                 |
| public Map addRequiredJoins(List requiredJoinsAsRelationPathList, QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)                                                              |                                                 |
| public List displayBindings(str replacementFieldGroupName, \[boolean distinctBindingsOnly\])                                                                                                                       |                                                 |
| public List displayValuesFromQueryRun(QueryRun queryRun, str replacementFieldGroupName, \[boolean isRootPrimaryKeyDataSource\], \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\])                   |                                                 |
| public List displayValuesFromRecID(Int64 recIDValue, str replacementFieldGroupName, \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\])                                                               |                                                 |
| public List displayValuesFromRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName, \[boolean trimSecuredValues\], \[boolean distinctBindingsOnly\]) |                                                 |
| public FilterValue displayValue(Common resolvedCursor, FieldBinding displayBinding, \[boolean isRootPrimaryKeyDataSource\])                                                                                        |                                                 |
| public str extendedDataType()                                                                                                                                                                                      |                                                 |
| public Query generateResolveReferenceQuery(List requiredJoinsAsRelationPathList, List filterValuesAsFilterValueList)                                                                                               |                                                 |
| public boolean isResolvedReferenceAmbiguous(Query query)                                                                                                                                                           |                                                 |
| public str primaryKeyTableName()                                                                                                                                                                                   |                                                 |
| public Map queryBuildDataSourceBindingsForQuery(Query query, str replacementFieldGroupName, \[boolean isRootPrimaryKeyDataSource\])                                                                                |                                                 |
| public Map queryBuildDataSourceBindingsForRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName)                                                     |                                                 |
| public Common resolveReference(Query query, \[boolean ignoreAmbiguousReference\])                                                                                                                                  |                                                 |
| public FieldBinding surrogateForeignKeyFieldBinding()                                                                                                                                                              |                                                 |
| ::public static SurrogateFKReplacementHelper construct(FieldBinding surrogateForeignKeyBinding)                                                                                                                    |                                                 |
| ::public static SurrogateFKReplacementHelper constructForEDT(str edtName)                                                                                                                                          |                                                 |
| ::public static SurrogateFKReplacementHelper constructForPKTable(str pkTableName)                                                                                                                                  |                                                 |
| ::public static str defaultPrimaryKeyQueryDataSourceName()                                                                                                                                                         |                                                 |
| ::public static str DEPRECATED\_WorkflowCaption(str tableName, str fieldName, Int64 recIDValue)                                                                                                                    |                                                 |
| ::public static str implicitReplacementFieldGroupName()                                                                                                                                                            |                                                 |
| private void new(FieldBinding surrogateForeignKeyBinding)                                                                                                                                                          | Initializes a new instance of the Object class. |

### Method addDefaultRequiredJoins

    public Map addDefaultRequiredJoins(QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)

#### Parameters

foreignKeyQueryBuildDataSource  

<!-- -->

replacementFieldGroupName  

#### Return Value

### Method addRequiredJoins

    public Map addRequiredJoins(List requiredJoinsAsRelationPathList, QueryBuildDataSource foreignKeyQueryBuildDataSource, str replacementFieldGroupName)

#### Parameters

requiredJoinsAsRelationPathList  

<!-- -->

foreignKeyQueryBuildDataSource  

<!-- -->

replacementFieldGroupName  

#### Return Value

### Method displayBindings

    public List displayBindings(str replacementFieldGroupName, [boolean distinctBindingsOnly])

#### Parameters

replacementFieldGroupName  

<!-- -->

distinctBindingsOnly  

#### Return Value

### Method displayValuesFromQueryRun

    public List displayValuesFromQueryRun(QueryRun queryRun, str replacementFieldGroupName, [boolean isRootPrimaryKeyDataSource], [boolean trimSecuredValues], [boolean distinctBindingsOnly])

#### Parameters

queryRun  

<!-- -->

replacementFieldGroupName  

<!-- -->

isRootPrimaryKeyDataSource  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

#### Return Value

### Method displayValuesFromRecID

    public List displayValuesFromRecID(Int64 recIDValue, str replacementFieldGroupName, [boolean trimSecuredValues], [boolean distinctBindingsOnly])

#### Parameters

recIDValue  

<!-- -->

replacementFieldGroupName  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

#### Return Value

### Method displayValuesFromRootDS

    public List displayValuesFromRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName, [boolean trimSecuredValues], [boolean distinctBindingsOnly])

#### Parameters

rootQueryBuildDataSource  

<!-- -->

isPrimaryKeyDataSource  

<!-- -->

replacementFieldGroupName  

<!-- -->

trimSecuredValues  

<!-- -->

distinctBindingsOnly  

#### Return Value

### Method displayValue

    public FilterValue displayValue(Common resolvedCursor, FieldBinding displayBinding, [boolean isRootPrimaryKeyDataSource])

#### Parameters

resolvedCursor  

<!-- -->

displayBinding  

<!-- -->

isRootPrimaryKeyDataSource  

#### Return Value

### Method extendedDataType

    public str extendedDataType()

#### Return Value

### Method generateResolveReferenceQuery

    public Query generateResolveReferenceQuery(List requiredJoinsAsRelationPathList, List filterValuesAsFilterValueList)

#### Parameters

requiredJoinsAsRelationPathList  

<!-- -->

filterValuesAsFilterValueList  

#### Return Value

### Method isResolvedReferenceAmbiguous

    public boolean isResolvedReferenceAmbiguous(Query query)

#### Parameters

query  

#### Return Value

### Method primaryKeyTableName

    public str primaryKeyTableName()

#### Return Value

### Method queryBuildDataSourceBindingsForQuery

    public Map queryBuildDataSourceBindingsForQuery(Query query, str replacementFieldGroupName, [boolean isRootPrimaryKeyDataSource])

#### Parameters

query  

<!-- -->

replacementFieldGroupName  

<!-- -->

isRootPrimaryKeyDataSource  

#### Return Value

### Method queryBuildDataSourceBindingsForRootDS

    public Map queryBuildDataSourceBindingsForRootDS(QueryBuildDataSource rootQueryBuildDataSource, boolean isPrimaryKeyDataSource, str replacementFieldGroupName)

#### Parameters

rootQueryBuildDataSource  

<!-- -->

isPrimaryKeyDataSource  

<!-- -->

replacementFieldGroupName  

#### Return Value

### Method resolveReference

    public Common resolveReference(Query query, [boolean ignoreAmbiguousReference])

#### Parameters

query  

<!-- -->

ignoreAmbiguousReference  

#### Return Value

### Method surrogateForeignKeyFieldBinding

    public FieldBinding surrogateForeignKeyFieldBinding()

#### Return Value

### Method construct

    public static SurrogateFKReplacementHelper construct(FieldBinding surrogateForeignKeyBinding)

#### Parameters

surrogateForeignKeyBinding  

#### Return Value

### Method constructForEDT

    public static SurrogateFKReplacementHelper constructForEDT(str edtName)

#### Parameters

edtName  

#### Return Value

### Method constructForPKTable

    public static SurrogateFKReplacementHelper constructForPKTable(str pkTableName)

#### Parameters

pkTableName  

#### Return Value

### Method defaultPrimaryKeyQueryDataSourceName

    public static str defaultPrimaryKeyQueryDataSourceName()

#### Return Value

### Method DEPRECATED\_WorkflowCaption

    public static str DEPRECATED_WorkflowCaption(str tableName, str fieldName, Int64 recIDValue)

#### Parameters

tableName  

<!-- -->

fieldName  

<!-- -->

recIDValue  

#### Return Value

### Method implicitReplacementFieldGroupName

    public static str implicitReplacementFieldGroupName()

#### Return Value

### Method new

Initializes a new instance of the Object class.

    private void new(FieldBinding surrogateForeignKeyBinding)

#### Parameters

surrogateForeignKeyBinding  

## Class SysGlobalObjectCache
    class SysGlobalObjectCache extends Object

### Remarks

### Examples

### Methods

| Method                                                                           | Description                                                   |
|----------------------------------------------------------------------------------|---------------------------------------------------------------|
| public container find(GlobalObjectCacheScope scope, container key)               |                                                               |
| public void finalize()                                                           |                                                               |
| public void remove(GlobalObjectCacheScope scope, container key)                  |                                                               |
| public void print(GlobalObjectCacheScope scope)                                  |                                                               |
| public void clear(GlobalObjectCacheScope scope)                                  |                                                               |
| ::public static void clearAllCaches()                                            |                                                               |
| public void new()                                                                | Initializes a new instance of the SysGlobalObjectCache class. |
| public void insert(GlobalObjectCacheScope scope, container key, container value) |                                                               |

### Method find

    public container find(GlobalObjectCacheScope scope, container key)

#### Parameters

scope  

<!-- -->

key  

#### Return Value

### Method finalize

    public void finalize()

### Method remove

    public void remove(GlobalObjectCacheScope scope, container key)

#### Parameters

scope  

<!-- -->

key  

### Method print

    public void print(GlobalObjectCacheScope scope)

#### Parameters

scope  

### Method clear

    public void clear(GlobalObjectCacheScope scope)

#### Parameters

scope  

### Method clearAllCaches

    public static void clearAllCaches()

### Method new

Initializes a new instance of the SysGlobalObjectCache class.

    public void new()

### Method insert

    public void insert(GlobalObjectCacheScope scope, container key, container value)

#### Parameters

scope  

<!-- -->

key  

<!-- -->

value  

## Class SystemMonitor
    class SystemMonitor extends Object

### Remarks

### Examples

### Methods

| Method                                                                | Description                                            |
|-----------------------------------------------------------------------|--------------------------------------------------------|
| ::public static container allClientCounters()                         |                                                        |
| ::public static container allServerCounters()                         |                                                        |
| ::public static int getClientCounter(SystemMonitorCounter counter)    |                                                        |
| ::public static container getClientInternals()                        |                                                        |
| ::public static int getCounter(SystemMonitorCounter counter)          |                                                        |
| ::public static int getServerCounter(SystemMonitorCounter counter)    |                                                        |
| ::public static container getServerInternals()                        |                                                        |
| ::public static boolean isRunning()                                   |                                                        |
| ::public static boolean isServerCounter(SystemMonitorCounter counter) |                                                        |
| ::public static container sqlDump()                                   |                                                        |
| ::public static void systemDump(boolean includeSQL)                   |                                                        |
| ::public static void start()                                          |                                                        |
| ::public static void resetServer()                                    |                                                        |
| ::public static void stop()                                           |                                                        |
| public void new()                                                     | Initializes a new instance of the SystemMonitor class. |
| public void finalize()                                                |                                                        |
| ::public static void reset()                                          |                                                        |
| ::public static void resetClient()                                    |                                                        |

### Method allClientCounters

    public static container allClientCounters()

#### Return Value

### Method allServerCounters

    public static container allServerCounters()

#### Return Value

### Method getClientCounter

    public static int getClientCounter(SystemMonitorCounter counter)

#### Parameters

counter  

#### Return Value

### Method getClientInternals

    public static container getClientInternals()

#### Return Value

### Method getCounter

    public static int getCounter(SystemMonitorCounter counter)

#### Parameters

counter  

#### Return Value

### Method getServerCounter

    public static int getServerCounter(SystemMonitorCounter counter)

#### Parameters

counter  

#### Return Value

### Method getServerInternals

    public static container getServerInternals()

#### Return Value

### Method isRunning

    public static boolean isRunning()

#### Return Value

### Method isServerCounter

    public static boolean isServerCounter(SystemMonitorCounter counter)

#### Parameters

counter  

#### Return Value

### Method sqlDump

    public static container sqlDump()

#### Return Value

### Method systemDump

    public static void systemDump(boolean includeSQL)

#### Parameters

includeSQL  

### Method start

    public static void start()

### Method resetServer

    public static void resetServer()

### Method stop

    public static void stop()

### Method new

Initializes a new instance of the SystemMonitor class.

    public void new()

### Method finalize

    public void finalize()

### Method reset

    public static void reset()

### Method resetClient

    public static void resetClient()

## Class systemSequence
    class systemSequence extends Object

The systemSequence class takes manual control of the system sequence generator of Microsoft Dynamics 365 for Operations5 for Operations and delivers unique RecIds for all SQL tables.

### Remarks

When Microsoft Dynamics 365 for Operations5 for Operations inserts records into SQL tables, a unique RecId is assigned to each record—regardless of the company each record is associated with. Use extreme caution when you use this class—data integrity could be destroyed. This class is typically used for data import or export routines, or for very large jobs. The record ID is an int64 data type value. The range in which record IDs are allocated is from 5637144576 to 2^63 (9223372036854775808). RecIds can be used up prematurely if large, unused ranges of RecIds are created. Reclaiming unused ranges of RecIds that lie between used ranges of RecIds is a very complicated process.

### Examples

The following example reserves the int64max value for the CustTable table.

    static public void Main(Args _args) 
    { 
        systemSequence seq; 
        seq = new SystemSequence(); 
        if (seq) 
        { 
            // Allocate 20 recordIds for CustTable table. 
            seq.reserveValues(20, tablenum(CustTable)); 
            // Suspend automatic recId allocation. 
            Seq.suspendRecIds(tablenum(CustTable)); 
            // Manually generate recIds in the range allocated. 
            // Remove the recId suspension. 
            Seq.removeRecIdSuspension(); 
          } 
    }

### Methods

| Method                                                             | Description                                                                                                                     |
|--------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| public Int64 flushValues(TableId tableId)                          | Flushes the reserved recIds from the System Sequence cache for a given table                                                    |
| public Int64 reserveTransids(Int64 nReserved, \[TableId tableId\]) |                                                                                                                                 |
| public Int64 reserveValues(Int64 nReserved, TableId tableId)       | Preallocates a range of recIds that can be allocated to new records when the automatic assignment of recIds has been suspended. |
| public void suspendTransIds(TableId tableId)                       |                                                                                                                                 |
| public void suspendRecIds(TableId tableId)                         |                                                                                                                                 |
| public void removeRecIdSuspension(\[TableId tableId\])             |                                                                                                                                 |
| public void new()                                                  | Initializes a new instance of the systemSequence class.                                                                         |
| public void removeTransIdSuspension(\[TableId tableId\])           |                                                                                                                                 |

### Method flushValues

Flushes the reserved recIds from the System Sequence cache for a given table

    public Int64 flushValues(TableId tableId)

#### Parameters

tableId  

#### Return Value

The number of recIds flushed from the cache.

#### Remarks

Subsequent inserts on the table reserve the recIds for the table and System Sequence cache is populated with the reserved range of recIds for the table.

### Method reserveTransids

    public Int64 reserveTransids(Int64 nReserved, [TableId tableId])

#### Parameters

nReserved  

<!-- -->

tableId  

#### Return Value

### Method reserveValues

Preallocates a range of recIds that can be allocated to new records when the automatic assignment of recIds has been suspended.

    public Int64 reserveValues(Int64 nReserved, TableId tableId)

#### Parameters

nReserved  

<!-- -->

tableId  

#### Return Value

The first usable reserved recId.

#### Remarks

The range of recIds that you reserved are reserved immediately.

### Method suspendTransIds

    public void suspendTransIds(TableId tableId)

#### Parameters

tableId  

### Method suspendRecIds

    public void suspendRecIds(TableId tableId)

#### Parameters

tableId  

### Method removeRecIdSuspension

    public void removeRecIdSuspension([TableId tableId])

#### Parameters

tableId  

### Method new

Initializes a new instance of the systemSequence class.

    public void new()

### Method removeTransIdSuspension

    public void removeTransIdSuspension([TableId tableId])

#### Parameters

tableId  



