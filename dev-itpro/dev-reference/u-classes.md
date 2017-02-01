---
# required metadata

title: U Classes | Microsoft Docs
description: System API classes that start with the letter U.
author: RobinARH
manager: AnnBe
ms.date: 2016-02-23 23:49:03
ms.topic: article
ms.prod: 
ms.service: Dynamics365Operations
ms.technology: 

# optional metadata

# keywords: 
# ROBOTS: 
audience: Developer
# ms.devlang: 
ms.reviewer: RobinARH
ms.suite: Released- Dynamics AX 7.0.0
# ms.tgt_pltfrm: 
ms.custom: 51691
ms.assetid: 2cbaa8b1-ee72-4838-9ed0-2cd244af8fc1
ms.region: Global
# ms.industry: 
ms.author: robinr

---

# U Classes

System API classes that start with the letter U.

Class UnitofWork
----------------

    class UnitofWork extends Object

### Remarks

### Examples

### Methods

| Method                                                       | Description                                         |
|--------------------------------------------------------------|-----------------------------------------------------|
| public boolean getByKey(Common record)                       |                                                     |
| public void updateonSaveChanges(Common record)               |                                                     |
| public void saveChanges(\[UserConnection user\_connection\]) |                                                     |
| public void deleteonSaveChanges(Common record)               |                                                     |
| public void insertonSaveChanges(Common record)               |                                                     |
| public void finalize()                                       |                                                     |
| public void new()                                            | Initializes a new instance of the UnitofWork class. |
| public void clear()                                          |                                                     |

### Method getByKey

    public boolean getByKey(Common record)

#### Parameters

record  

#### Return Value

### Method updateonSaveChanges

    public void updateonSaveChanges(Common record)

#### Parameters

record  

### Method saveChanges

    public void saveChanges([UserConnection user_connection])

#### Parameters

user\_connection  

### Method deleteonSaveChanges

    public void deleteonSaveChanges(Common record)

#### Parameters

record  

### Method insertonSaveChanges

    public void insertonSaveChanges(Common record)

#### Parameters

record  

### Method finalize

    public void finalize()

### Method new

Initializes a new instance of the UnitofWork class.

    public void new()

### Method clear

    public void clear()

## Class UserConnection
    class UserConnection extends Connection

The UserConnection class represents an auxiliary connection to the SQL database, based on the same logon properties as the main connection.

### Remarks

SQL statements are executed, and results are returned in the context of a UserConnection class. The UserConnection class can be used to obtain a separate transaction scope.

### Examples

    static void example()  
    { 
        UserConnection Con; 
        Statement Stmt; 
        Str sql; 
        ResultSet R; 
        SqlStatementExecutePermission perm; 
        Con = new UserConnection(); 
        sql = 'SELECT VALUE FROM SQLSYSTEMVARIABLES'; 
        Stmt = Con.createStatement(); 
        perm = new SqlStatementExecutePermission(sql); 
        // Check for permission to use the statement. 
        perm.assert(); 
        R = Stmt.executeQuery(sql); 
        while ( R.next() ) 
        { 
            print R.getString(1); 
        } 
    }

### Methods

| Method                                                | Description                                         |
|-------------------------------------------------------|-----------------------------------------------------|
| public void new(\[boolean generateNewTransactionID\]) | Initializes a new instance of the Connection class. |

### Method new

Initializes a new instance of the Connection class.

    public void new([boolean generateNewTransactionID])

#### Parameters

generateNewTransactionID  

## Class UserMenuList
    class UserMenuList extends TreeNode

The UserMenuList class enables you to create, read, update, and delete X++ code and metadata.

### Remarks

### Examples

### Methods

| Method                               | Description |
|--------------------------------------|-------------|
| public void createMenu(\[str name\]) |             |

### Method createMenu

    public void createMenu([str name])

#### Parameters

name  

## Class UserSetup
    class UserSetup extends TreeNode

The UserSetup class provides an interface for setting user parameters.

### Remarks

This class is used mainly in the SysUserSetup form. This class lets you create, read, update, and delete X++ code and metadata. Make sure that the user has access to the development security key (SysDevelopment) before this API is called.

### Examples

### Methods

| Method                                  | Description |
|-----------------------------------------|-------------|
| public boolean xRef(\[boolean enable\]) |             |
| public void setUserSetup(Common cursor) |             |
| public void setDefaults(Common cursor)  |             |

### Method xRef

    public boolean xRef([boolean enable])

#### Parameters

enable  

#### Return Value

### Method setUserSetup

    public void setUserSetup(Common cursor)

#### Parameters

cursor  

### Method setDefaults

    public void setDefaults(Common cursor)

#### Parameters

cursor  

## Class UtilFile
    class UtilFile extends Object

### Remarks

### Examples

### Methods

| Method                                                      | Description                                                      |
|-------------------------------------------------------------|------------------------------------------------------------------|
| public boolean aodFileExist(UtilEntryLevel layer)           |                                                                  |
| public int importAODFile(UtilEntryLevel layer, int modelId) |                                                                  |
| public str layers()                                         |                                                                  |
| public boolean needReindex()                                |                                                                  |
| public void check(str layer, str action)                    |                                                                  |
| public void new(str fileType)                               | Initializes a new instance of the Object class.                  |
| public void reindex()                                       | Lets you create, read, update, and delete X++ code and metadata. |
| public void flushCache()                                    |                                                                  |

### Method aodFileExist

    public boolean aodFileExist(UtilEntryLevel layer)

#### Parameters

layer  

#### Return Value

### Method importAODFile

    public int importAODFile(UtilEntryLevel layer, int modelId)

#### Parameters

layer  

<!-- -->

modelId  

#### Return Value

### Method layers

    public str layers()

#### Return Value

### Method needReindex

    public boolean needReindex()

#### Return Value

### Method check

    public void check(str layer, str action)

#### Parameters

layer  

<!-- -->

action  

### Method new

Initializes a new instance of the Object class.

    public void new(str fileType)

#### Parameters

fileType  

### Method reindex

Lets you create, read, update, and delete X++ code and metadata.

    public void reindex()

#### Remarks

Make sure that the user has access to the development security key (SysDevelopment) before you call this API.

#### Examples

The following example calls the UtilFile.reindex method. It checks whether the user has the required security key before you perform a modification.

    server static public void Main(Args _args) 
    { 
        UtilFile u; 
        u = new UtilFile("util"); 
        if (u) 
        { 
            u.reindex(); 
        } 
    }

### Method flushCache

    public void flushCache()

