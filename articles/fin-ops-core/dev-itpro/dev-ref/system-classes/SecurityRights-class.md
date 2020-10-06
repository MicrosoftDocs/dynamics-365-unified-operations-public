---
title: SecurityRights class
description: This topic describes the SecurityRights class.
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

# Class SecurityRights

[!include [banner](../../includes/banner.md)]

```xpp
class SecurityRights extends Object
```

The SecurityRights class holds the information about the security rights and permissions management.

## Remarks

## Examples

## Methods

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

## Method hasDataServiceAccess

```xpp
public boolean hasDataServiceAccess(SecurableName name, StatementType operation, [SecurableChildName fieldName])
```

### Parameters - hasDataServiceAccess

name  

<!-- -->

operation  

<!-- -->

fieldName  

### Return Value - hasDataServiceAccess

## Method hasDataServiceMethodAccess

```xpp
public boolean hasDataServiceMethodAccess(SecurableName name, StatementType operation, SecurableChildName methodName)
```

### Parameters - hasDataServiceMethodAccess

name  

<!-- -->

operation  

<!-- -->

methodName  

### Return Value - hasDataServiceMethodAccess

## Method dataManagementAccessRight

```xpp
public AccessRight dataManagementAccessRight(SecurableName dataEntityName, [SecurableChildName fieldName])
```

### Parameters - dataManagementAccessRight

dataEntityName  

<!-- -->

fieldName  

### Return Value - dataManagementAccessRight

## Method listDataServiceAccess

```xpp
public str listDataServiceAccess(SecurableName name, [SecurableChildName context])
```

### Parameters - listDataServiceAccess

name  

<!-- -->

context  

### Return Value - listDataServiceAccess

## Method fieldAccessRight

Retrieves the access rights for the field of the table.

```xpp
public AccessRight fieldAccessRight(TableName tableName, FieldName fieldName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])
```

### Parameters - fieldAccessRight

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

### Return Value - fieldAccessRight

The AccesRight instance for the field of the table.

## Method formControlAccessRight

Retrieves the access rights for the form control.

```xpp
public AccessRight formControlAccessRight(FormName form, UtilElementName control, [Common record], [DataAreaId dataArea])
```

### Parameters - formControlAccessRight

form  

<!-- -->

control  

<!-- -->

record  

<!-- -->

dataArea  

### Return Value - formControlAccessRight

The AccesRight instance for the form control.

## Method getSelectableCompanies

```xpp
public container getSelectableCompanies()
```

### Return Value - getSelectableCompanies

## Method hasMenuAccess

Checks whether the user has access to the specified menu.

```xpp
public boolean hasMenuAccess(MenuName menu, [boolean isWebMenu])
```

### Parameters - hasMenuAccess

menu  

<!-- -->

isWebMenu  

### Return Value - hasMenuAccess

true if the user has access to the menu; otherwise, false.

## Method hasMenuItemAccess

Checks whether the user has access to the specified menu item.

```xpp
public boolean hasMenuItemAccess(SecurableType type, MenuItemName menuItem, [Common record], [DataAreaId dataArea])
```

### Parameters - hasMenuItemAccess

type  

<!-- -->

menuItem  

<!-- -->

record  

<!-- -->

dataArea  

### Return Value - hasMenuItemAccess

true if the user has access to the menu item; otherwise, false.

## Method SysObsoleteAttribute

```xpp
public boolean SysObsoleteAttribute(ClassName class, MethodName method)
```

### Parameters - SysObsoleteAttribute

class  

<!-- -->

method  

### Return Value - SysObsoleteAttribute

## Method hasServiceOperationAccess

Checks whether the user has access to the specified service operation.

```xpp
public boolean hasServiceOperationAccess(UtilElementName service, UtilElementName operation)
```

### Parameters - hasServiceOperationAccess

service  

<!-- -->

operation  

### Return Value - hasServiceOperationAccess

true if user has access to the service operation; otherwise, false.

## Method isDeveloper

```xpp
public boolean isDeveloper()
```

### Return Value - isDeveloper

## Method isSystemAdministrator

Checks whether the current user is a system administrator.

```xpp
public boolean isSystemAdministrator()
```

### Return Value - isSystemAdministrator

true if the current user is a system administrator; otherwise, false.

## Method menuItemAccessRight

Retrieves the access rights for the menu item.

```xpp
public AccessRight menuItemAccessRight(SecurableType type, MenuItemName menuItem, [DataAreaId dataArea])
```

### Parameters - menuItemAccessRight

type  

<!-- -->

menuItem  

<!-- -->

dataArea  

### Return Value - menuItemAccessRight

The AccesRight instance for the item.

## Method tableAccessRight

Retrieves the access rights for the table.

```xpp
public AccessRight tableAccessRight(TableName tableName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])
```

### Parameters - tableAccessRight

tableName  

<!-- -->

record  

<!-- -->

dataArea  

<!-- -->

includeDerived  

<!-- -->

autoAuthzMode  

### Return Value - tableAccessRight

The AccesRight instance for the table.

## Method tableFieldAccessRights

Retrieves the field access rights for the table.

```xpp
public SecurityTableRights tableFieldAccessRights(TableName tableName, [Common record], [DataAreaId dataArea], [boolean includeDerived], [AutoAuthzMode autoAuthzMode])
```

### Parameters - tableFieldAccessRights

tableName  

<!-- -->

record  

<!-- -->

dataArea  

<!-- -->

includeDerived  

<!-- -->

autoAuthzMode  

### Return Value - tableFieldAccessRights

The SecurityTableRights instance for the table.

## Method variableAccessFields

Retrieves a set of the table field IDs.

```xpp
public Set variableAccessFields(TableName tableName, [AccessRight targetAccess], [DataAreaId dataArea])
```

### Parameters - variableAccessFields

tableName  

<!-- -->

targetAccess  

<!-- -->

dataArea  

### Return Value - variableAccessFields

A set of the table field IDs.

## Method webContentAccessRight

Retrieves the access rights for the web content item.

```xpp
public AccessRight webContentAccessRight(SecurableType type, WebContentItemName name)
```

### Parameters - webContentAccessRight

type  

<!-- -->

name  

### Return Value - webContentAccessRight

The AccesRight instance for the item.

## Method construct

Creates a new security rights instance for the current user.

```xpp
public static SecurityRights construct()
```

### Return Value - construct

The SecurityRights instance that was created.

## Method newUser

Creates a new security rights instance for the specified user.

```xpp
public static SecurityRights newUser(UserId user)
```

### Parameters - newUser

user  

### Return Value - newUser

The SecurityRights instance that was created.

## Method new

Initializes a new instance of the SecurityRights class.

```xpp
private void new()
```

## Method populateSelectableCompanies

Populates the selectable companies.

```xpp
public void populateSelectableCompanies()
```

