---
title: CodeAccessPermission class
description: This topic describes the CodeAccessPermission class.
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

# Class CodeAccessPermission

[!include [banner](../../includes/banner.md)]

```xpp
class CodeAccessPermission extends Object
```

The CodeAccessPermission class defines the underlying structure of code access permissions.

## Remarks

The following classes extend the CodeAccessPermission class: ExecutePermission, FileIOPermission, InteropPermission, RunAsPermission, SkipAOSValidationPermission, SqlDataDictionaryPermission, SqlStatementExecutePermission, and SysDatabaseLogPermission.

## Examples

The following code example shows a class that is derived from the CodeAccessPermission class.

```xpp
final class SysTestCodeAccessPermission extends CodeAccessPermission 
{ 
    str data; 
}
```

This code example illustrates a step in the process of protecting an API.

## Methods

| Method                                                 | Description                                                                                                                                       |
|--------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| public CodeAccessPermission copy()                     | Creates and returns a copy of a permission class object.                                                                                          |
| public boolean isSubsetOf(CodeAccessPermission target) | Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.                         |
| public void new()                                      | Initializes a new instance of the CodeAccessPermission class.                                                                                     |
| public void assert()                                   | Declares that the calling code can invoke an API that is protected by a permission.                                                               |
| public void demand()                                   | Checks the call stack to determine whether the permission that is required to invoke an API has been granted to the calling code.                 |
| ::public static void revertAssert()                    | Causes a previous call to the CodeAccessPermission.assert and CodeAccessPermission::assertMultiple methods to be removed and no longer in effect. |
| ::public static void assertMultiple(Set permissionSet) | Declares that the calling code can invoke an API that is protected by any of the permissions in a specified collection.                           |

## Method copy

Creates and returns a copy of a permission class object.

```xpp
public CodeAccessPermission copy()
```

### Return Value - copy

A copy of the derived class object.

### Remarks - copy

You can override this method as part of the process of making an API more secure.

### Examples - copy

The following code example shows how to override the copy method to create and return a copy of a class that is derived from the CodeAccessPermission class.

```xpp
public CodeAccessPermission copy() 
{ 
    return new SysTestCodeAccessPermission(_data); 
}
```

## Method isSubsetOf

Determines whether a current permission is a subset of the specified permission when it is overridden by a derived class.

```xpp
public boolean isSubsetOf(CodeAccessPermission target)
```

### Parameters - isSubsetOf

target  
A CodeAccessPermission class object.

### Return Value - isSubsetOf

true if a current permission is a subset of a specified permission; otherwise, false.

### Remarks - isSubsetOf

You can override the method as part of the process of making an API more secure.

### Examples - isSubsetOf

The following example shows how to override the isSubsetOf method to determine whether permissions that are stored in the current object are located in \_target.

```xpp
public boolean isSubsetOf(CodeAccessPermission _target) 
{ 
    SysTestCodeAccessPermission sysTarget = _target; 
    return this.handle() == _target.handle(); 
}
```

## Method new

Initializes a new instance of the CodeAccessPermission class.

```xpp
public void new()
```

## Method assert

Declares that the calling code can invoke an API that is protected by a permission.

```xpp
public void assert()
```

### Remarks - assert

You must call the assert method in the derived class for a protected API before you invoke the API. For more information about APIs that are protected by permissions, see Secured APIs. You must call the assert method on the same tier, usually the server tier, that the corresponding CodeAccessPermission::demand method is called on before the protected API is executed. Call a method on the server tier from one of the following:

-   A server static method
-   A class instance method that is set to run on the server by using the RunOn class property

Multiple, successive calls to the assert method in the same calling code are not supported. Either call the CodeAccessPermission::revertAssert method between each call to the assert method, or call the CodeAccessPermission::assertMultiple method. If you make multiple, successive calls to the assertmethod, the Infolog displays an error when you execute the code.

### Examples - assert

The following code example shows a call to the assert method before the AsciiIo Class class that is protected by a permission is invoked. The assert method is a member of the FileIOPermission class that is derived from the CodeAccessPermission class.

```xpp
server static void main(Args args) 
{ 
    FileIoPermission _perm; 
    AsciiIo a; 
```


```xpp
    _perm = new FileIoPermission("c:\File.txt",'r'); 
    _perm.assert(); 
```

```xpp
    // Invoke the protected API. 
    a = new AsciiIo("c:\File.txt",'r'); 
}
```

## Method demand

Checks the call stack to determine whether the permission that is required to invoke an API has been granted to the calling code.

```xpp
public void demand()
```

### Examples - demand

The following code example shows a call to the demand method before the API functionality is executed, to determine whether permission to access the resource that is specified by the data variable has been granted to code that is calling the API.

```xpp
public static void main(str data) 
{ 
    SysTestCodeAccessPermission p = new SysTestCodeAccessPermission(data); 
    p.demand(); 
```

```xpp
    //Add functionality 
}
```

This code example illustrates a step in the process of protecting an API.

## Method revertAssert

Causes a previous call to the CodeAccessPermission.assert and CodeAccessPermission::assertMultiple methods to be removed and no longer in effect.

```xpp
public static void revertAssert()
```

### Remarks - revertAssert

When you have multiple calls to the assert method in the same calling code, you must call the revertAssert method between each call. Otherwise, the Infolog displays an error when you execute the code. When you call the assert method only one time, or when you call the CodeAccessPermission::assertMultiple method, we recommend that you still call the revertAssert method after you invoke the protected API to limit the scope of the assert.

### Examples - revertAssert

The following code example shows a call to the CodeAccessPermission::revertAssert method after the user calls the CodeAccessPermission.assert method and the AsciiIo class that is protected by a permission.

```xpp
server static void main(Args args) 
{ 
    FileIoPermission _perm; 
    AsciiIo a; 
```


```xpp
    _perm = new FileIoPermission("c:\File.txt",'r'); 
    _perm.assert(); 
```

```xpp
    //invoke protected API 
    a = new AsciiIo("c:\File.txt",'r'); 
```

```xpp
    // Optionally call revertAssert() to limit scope of assert. 
    CodeAccessPermission::revertAssert(); 
}
```

## Method assertMultiple

Declares that the calling code can invoke an API that is protected by any of the permissions in a specified collection.

```xpp
public static void assertMultiple(Set permissionSet)
```

### Parameters - assertMultiple

permissionSet  
A Set class object that contains a collection of permissions.

### Remarks - assertMultiple

You call the assertMultple method instead of making multiple, successive calls to the CodeAccessPermission.assert and CodeAccessPermission::revertAssert methods in the same calling code.

### Examples - assertMultiple

The following code example calls the CodeAccessPermission::assertMultple method. Then the code example calls the WinAPIServer::createFile method, which would fail without the previous call to the CodeAccessPermission::assertMultple method. The code example is a static method that you can add to a new class that you create. You can call this static method from an X++ job by using one line of code that resembles MyClass::RunOnServerPermissionTest. In the code example, the WinAPIServer class has several secure methods. The WinAPIServer class runs on the server tier, not on the client tier. Therefore the code example method must also run on the server tier. Otherwise, any permission asserts that are made on the client tier are ignored by methods that run on the server tier. This is why the server keyword is included in the method declaration of the code example. The server keyword on the method takes precedence over the RunOn property value that is specified on the class.

```xpp
server
    static public void RunOnServerPermissionTest()
{
    Set permissionSet;
    str fileName = @"C:\TestFile75a.txt";
    boolean boolFileDeleted;
```

```xpp
    permissionSet =  new Set(Types::Class);
    permissionSet.add(new FileIoPermission(fileName,'rw'));
```

```xpp
    CodeAccessPermission::assertMultiple(permissionSet);
    //--- Permissions are set, now perform file operations.
```

```xpp
    WinAPIServer::createFile(fileName);
    boolFileDeleted = WinAPI::deleteFile(fileName);
```

```xpp
    if (boolFileDeleted)
    {
        info("The file was deleted. Good.");
    }
    else
    {
        error("The file was not deleted. Error.");
    }
}
```

